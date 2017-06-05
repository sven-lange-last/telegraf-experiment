# telegraf-experiment

```
docker run --rm influxdb influxd config > influxdb.conf
vi influxdb.conf
docker run --rm --detach --name influxdb -p 8083:8083 -p 8086:8086 -p 25826:25826/udp -v $PWD/influxdb:/var/lib/influxdb -v $PWD/influxdb.conf:/etc/influxdb/influxdb.conf:ro -v $PWD/types.db:/usr/share/collectd/types.db:ro influxdb
```

```
docker run --rm --detach --name grafana -p 3000:3000 -v $PWD/grafana:/var/lib/grafana  --link influxdb grafana/grafana
```

```
docker run --rm --detach --privileged --net=container:influxdb --name telegraf --pid=host telegraf
```

```
dd if=/dev/zero of=/tmp/hd-fillup.zeros bs=1G count=5
```

elasticsearch-cloudformation
============================

### /etc/default/elasticsearch

Set's a dynamic heap size of 80% of the installes memory.

```
phymem=$(awk -F":" '~/MemTotal/{print }' /proc/meminfo )
size=$(echo $phymem | grep -o  [0-9]*)
size=$(calc $size/1000.0*0.8)
size=$( printf "%.0f" $size )
ES_HEAP_SIZE=${size}m
```

### /etc/elasticsearch/elasticsearch.yml

access_key and secret_key are used to access the Amazon EC2 API to find nodes in the same cluster.

```
cloud.aws.access_key: <access_key>
cloud.aws.secret_key: <secret_key>
cloud.aws.region: eu-west-1
discovery.type: ec2
```

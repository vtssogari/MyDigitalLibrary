# Spark Thrift Server Note

### Sharing the connection or spawn new connection
```
spark.sql.hive.thriftServer.singleSession=false|true
```

### Result set will return using false - collect( return all )  or true - iterator ( return incremental chunk )

```
spark.sql.thriftServer.incrementalCollect=false|true
```

### example configuration

```
./sbin/start-thriftserver.sh \
  --hiveconf hive.server2.thrift.port=<listening-port> \
  --hiveconf hive.server2.thrift.bind.host=<listening-host> \
  --master <master-uri>
  --conf spark.sql.thriftServer.incrementalCollect=true
  --conf spark.sql.hive.thriftServer.singleSession=true
  
```

### register UDF, UADF

CREATE TEMPORARY FUNCTION RankPercentile AS 'org.hue.udf.MyUpper'


Use the SHOW FUNCTIONS command to confirm taht your UDF has been registered properly.


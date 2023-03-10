# Filter and predicates

## Proposal

Create data in mongodb using one connector and filtering per origin topic

## Running the demo

Create a mongo db and change the data/mongosink-template.json to data/mongosink.json with connection data.

```shell
    ./start-cluster.sh
```

Then add some content

```shell
kafka-avro-console-producer --bootstrap-server localhost:19092 --topic topic-test-t1 --property value.schema.id=1 --property auto.register=false --property use.latest.version=true --property schema.registry.url=http://localhost:8081
{"field1" : "t1", "field2": "t1"}

kafka-avro-console-producer --bootstrap-server localhost:19092 --topic topic-test-t2 --property value.schema.id=1 --property auto.register=false --property use.latest.version=true --property schema.registry.url=http://localhost:8081
{"field1" : "t2", "field2": "t2"}

kafka-avro-console-producer --bootstrap-server localhost:19092 --topic topic-test-t3 --property value.schema.id=1 --property auto.register=false --property use.latest.version=true --property schema.registry.url=http://localhost:8081
{"field1" : "t3", "field2": "t3"}
```

### Clean-up

1. Stop the consumer (control C)
2. Clean the docker cluster `docker-compose down -v`


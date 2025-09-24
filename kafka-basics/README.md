#### Pre requisites:
 wsl --install : install Ubuntu(default) <br>
 wsl -l -v : list linux systems <br>
 wsl -d Ubuntu : start Ubuntu <br>

#### Download Kafka on WSL:
 https://kafka.apache.org/downloads

#### Start the Kafka environment:
 https://kafka.apache.org/documentation/#quickstart

#### On WSL:
 cd kafka_2.13-4.0.0 <br>
 KAFKA_CLUSTER_ID="\$(bin/kafka-storage.sh random-uuid)" <br>
 bin/kafka-storage.sh format --standalone -t \$KAFKA_CLUSTER_ID -c config/server.properties <br>
 bin/kafka-server-start.sh config/server.properties : start kafka <br>

#### bootstrap server
 fetch hostname using 'hostname -I' on WSL (eg. 172.24.101.122) to connect to kafka cluster <br>
 use this hostname when setting kafka properties <br>
 <i>properties.setProperty("bootstrap.servers", "172.24.101.122:9092");</i>



### CLI commands
#### create a topic with 3 partitions
 kafka-topics.sh --bootstrap-server localhost:9092 --topic topic_name --create --partitions 3

#### create a topic with 3 partitions and replication factor 2
 kafka-topics.sh --bootstrap-server localhost:9092 --topic third_topic --create --partitions 3 --replication-factor 2

#### produce data
 kafka-console-producer.sh --bootstrap-server localhost:9092 --topic topic_name

#### consume data
 kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic topic_name

#### consuming from beginning
 kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic topic_name --from-beginning

#### list of topics
bin/kafka-topics.sh --bootstrap-server localhost:9092 --list

#### detailed info for a topic
bin/kafka-topics.sh --bootstrap-server localhost:9092 --topic topic_name --describe

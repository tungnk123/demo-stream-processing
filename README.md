# Lambda architecture

## How to run
* `mvn package`
* `docker-compose -p lambda up`
* Wait all services be up and running, then...
* `./project-orchestrate.sh`
* Run realtime job `docker exec spark-master /spark/bin/spark-submit --class com.apssouza.iot.streaming.StreamingProcessor  --master spark://localhost:7077 /opt/spark-data/iot-spark-processor-1.0.0.jar`
* Access the Spark cluster http://localhost:8080
* Run the traffic producer `java -jar iot-kafka-producer/target/iot-kafka-producer-1.0.0.jar`
* Run the service layer (Web app) `java -jar iot-springboot-dashboard/target/iot-springboot-dashboard-1.0.0.jar` 
* Access the dashboard with the data http://localhost:3000/
* Run the batch job `docker exec spark-master /spark/bin/spark-submit --class com.apssouza.iot.batch.BatchProcessor  --master spark://localhost:7077 /opt/spark-data/iot-spark-processor-1.0.0.jar`

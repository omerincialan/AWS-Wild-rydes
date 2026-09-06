BUILD A SERVERLESS APPLICATION - WILDRYDES
1.	Real Time Data Streaming	0
2.	Stream Processing and Analytics with AWS Lambda	0
3.	Stream Aggregation	0
4.	Data Lake	0




1.	Real Time Data Streaming
In this module, I created an Amazon Kinesis stream to collect and store sensor data from our unicorn fleet. Unicorns (as producers) emits data to Kinesis, and as a consumer the role I created accesses to Unicorn Dashboard to monitor Unicorns’ location, health etc.
I used IAM service of AWS to authenticate user access to stream.

2.	Stream Processing and Analytics with AWS Lambda
In this module, we started to add more functionality to project by building a Lambda Function the stream. As data arrives from unicorns to stream, based on specific parameters we set, Lambda Function triggers some actions to be performed such as sending failed queries to a separate place (SQS Queue) and storing write arriving records to a DynamoDB table.
As an error handling method we first used retry settings and then bisect on batch method. While first method discards entire table even if there is only one failed record second one splits the batch into half and process each half separately until only one failed records remains.

3.	Stream Aggregation
Here, I tried to build an analysis layer to the streaming data by using Amazon Kinesis Data Analytics Application. By specifying certain calculations, I could have instant insight from the field. To be able to function properly , I Used AWS Glue and IAM to authenticate users on specific analytics tasks.
My goal was to analyze streaming data of Unicorns every 60 seconds and send the output as a summary row to another analytics environment (DynamoDB)

4.	Data Lake
In this module, I used S3 service of AWS to store my raw data. I also, ran queries on the raw data my unicorns produced at the first module.
I used Kinesis Data Firehose delivery stream to pull data from my stream.
I used Amazon Athena to query my raw data. To improve my query performance my raw data was transformed into Apache Parquet format, by using Amazon Athena I can access to previously transformed data.

As I watch education videos about AWS, I realize that you can do almost anything you need by using AWS services. For example by analyzing travel distance of unicorns in a specific time interval, we can know if they violate speed limits. By tracking their health data, we can offer them timely breaks. 

<img width="468" height="635" alt="image" src="https://github.com/user-attachments/assets/f75c2383-6b48-49da-a0f7-5e7bbf7befee" />

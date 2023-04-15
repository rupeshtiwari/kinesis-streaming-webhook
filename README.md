# Welcome to Kinesis Streaming by GitHub webhook


## Source code for AWS Lambda function to push the payload to Amazon Kinesis

```py
import json
import boto3
import uuid 

def lambda_handler(event, context):
    client = boto3.client('kinesis')
    data = {'order': '2 Icecreams'}
    
    response = client.put_record(
        StreamName='git-data-stream',
        Data=json.dumps(event),
        PartitionKey=str(uuid.uuid4())
    )
    
    return response;
 ```

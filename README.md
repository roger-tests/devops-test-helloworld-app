# devops-test-helloworld-app

This folder contains the files to deploy the devops-test-helloworld-app application in AWS.


# Prerequisites:

* AWS CLI version 2 installed and configured for eu-west-3 (Paris). (https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)

* EB CLI installed. (https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install.html)


# Deployment:

1. Clone the Github repository project:
```
git clone https://github.com/rgvia/devops-test-helloworld-app.git
```

2. Go to the project folder: 
```
cd devops-test-helloworld-app
```

3. Initialize EB CLI:
```
eb init
```

4. Create the environment and deploy the application:
```
eb create devops-test-helloworld-app --cfg ApphelloworldProd-environment-config
```

Notes:
  - Application will run in the 80 port.
  - The deployment will take about 15 minutes. The EB CLI timed out after 10 minutes. The operation might still be running. To keep viewing events, run 'eb events -f'. To set timeout duration, use '--timeout MINUTES'.


# REST API
This application provides a REST API for get users info.

## Health Check
* **URL:**`/actuator/health`
* **Method:**`GET`
* **Response:**  
```json
{"status":"UP"}
```

## Get User
* **URL:**`/users/{userId}`
* **Method:**`GET`
* **Response:**  
```json
{"id":104,"name":"user104","surname":"surname104","type":3}
```

## Get Users by type
Gets the users of the given type. 
* **URL:**`/users?userType={userTypeId}` 
* **Method:**`GET`
* **Response:**  
```json
[
  {"id":23,"name":"user23","surname":"surname23","type":6},
  {"id":32,"name":"user32","surname":"surname32","type":6},
  {"id":38,"name":"user38","surname":"surname38","type":6}
]
```
Possible values of `userType` are between `1` and `10`.

Tweet app revisited to build, test, deploy using an automated CI-CD pipeline with Wercker deployed as containers on AWS.

[![wercker status](https://app.wercker.com/status/9cac93950da19c6b6ae466fc53458cd0/s/master "wercker status")](https://app.wercker.com/project/byKey/9cac93950da19c6b6ae466fc53458cd0)  [![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/dwyl/esta/issues)



Introduction:

This post is to help you set up a CI-CD pipeline using wercker for the application running on docker container. Same can be used to scale out or for bigger applications as well. It would serve as a initial starting point to set up pipeline and workflows on wercker.

This would also help you with Slack integration step to post notifications on your build status. 

Documentations:

<a href="http://devcenter.wercker.com/docs/home">Learn about wercker</a>

<a href="https://www.docker.com/sites/default/files/Docker_CheatSheet_08.09.2016_0.pdf">Docker Commands/Cheat Sheet</a>

Pre-requisites: 

Dockerhub Account to store your docker images - <a href="https://hub.docker.com/">create your free docker hub account</a>

Wercker Account for your CI-CD pipeline - <a href="http://www.wercker.com/pricing">create your free wercker account</a>

A running EC2 Instance. ( Note: <a href="https://docs.docker.com/engine/installation/#prior-releases">Install docker on the EC2 Server</a> )

Application:

<a href="https://github.com/dockersamples/linux_tweet_app">Source Code of the Application's HTML file</a>

Wercker:

1. Integrating werkcer with git. 
On the profile page, open up setting and git connections underneath settings. You would have option to either connect to your github account or bitbucket account.

2. Creating the application. 
Click on the + icon on top right corner to see an option named create an application. Once you click on it, it will auto populate the repositories in the git hub account you had linked earlier. Choose the code repository that you would like to configure the CI pipeline. Configure the access and your application will be created. you are all done!

3. Create the pipelines. 

![Alt text](https://s3.us-east-2.amazonaws.com/devopscafe/pipelineJPG.JPG "Create")

![Alt text](https://s3.us-east-2.amazonaws.com/devopscafe/settings-for-pipeline.JPG "Settings")

4. Create the workflows. 

![Alt text](https://s3.us-east-2.amazonaws.com/devopscafe/workflows.JPG "Create")

5. Environment Variables.

![Alt text](https://s3.us-east-2.amazonaws.com/devopscafe/environment.JPG "Create")


#THE MAGIC SAUCE:

Most of the work happens becuase of the declarations in the wercker.yml. We can include multiple pipelines like build, test, push to dockerhub and deploy to each environments inside of the wercker.yml file.

The build section contains basic install test as of now. You could add in more tests as per the need. 
The build section also contains the slack integration, which will post notifications to your slack channel. 
You will have to  <a href="https://www.docker.com/sites/default/files/Docker_CheatSheet_08.09.2016_0.pdf">configure incoming webhook on slack.</a>

The push to docker contains the syntax declarations on how we push the container to Dockerhub.
The deploy section contains commands to show how we deploy the docker image. 


To Do's in future:

1. Add in ELK stack containers on the same host to monitor the application. ( A learning on how it would work )
2. Deploying through Docker Compose. 
3. Deploying through Kubernetes. 
4. Add test cases and scripts in the build section and post deploy section. 




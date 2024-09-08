## ZOOM BOT DEPLOYMENT 


### 1. Build and push the “Zoom SDK” container to the AWS container registry 
#### 1.1. Ask for the AWS container registry for CueCard (Karthik) ⌛

#### 1.2. Can we spin up a fargate container instance programmatically?(DevOps Help) ⌛
- We need to pass in the Zoom meeting link to the container , so each container would handle exactly one zoom meeting at a time and once the meeting is done the container would terminate.

- Therefore we need to spin up a container when the client wants to record a Zoom meeting with the “join” link to that specific meeting.

#### 1.3.  How can we attach a persistent storage to the containers (DevOps Help) ⌛
The audio files are written to the local storage of the container. We grab the locally stored file and then pass it to the transcription service (i.e assembly.ai).
If we are using serverless containers we need a method of either 

- A : Grabbing the file that was written in the container's local storage before the container is terminated [task definition without completion ] and then moving it to a permanent storage location (like S3). 

OR 

- B : Attaching a persistent storage to the serverless containers (like EFS)  and then grab the audio file from that persistent storage and then move it to a permanent storage location (like S3) 

We would need to decide on either of the above approaches and write out the code. 

    Option A is less costly as we can take advantage of the default storage that is provided by AWS when each new container instance is created (20 GiB all the way to 200 GiB). The question here is “can we access the running container and grab the audio file programmatically  before it's terminated ?”. We would first need to test this out.

### 2. Build the FastAPI Microservice  
### 3. Integration Test with the Client App 


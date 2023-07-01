
# Basic

| Task | Code | 
|----------|----------| 
| Get running containers | ```docker ps``` |
| Get all containers | ```docker ps -a``` |
| Get all containers ids | ```docker ps -qa``` |
| Remove container using name | ```docker rm containerName``` |
| Remove all containers | ```docker rm $(docker ps -qa)``` |
| Get all images | ```docker images``` |
| Remove image using name | ```docker rmi imageName``` |
| Remove all images | ```docker rmi $(docker images)``` |
| Forecefully Remove images | ```docker rmi -f imageName``` |

==container should be stopped before removing it==

# Run

| Task | Code | 
|----------|----------| 
| Pull a container without running | ```docker pull contName``` |
| Run a container | ```docker run contName``` |
| Run in detached mode | ```docker run -d contName```|
| Run in interactive mode | ```docker run -i contName```|
| Run in terminal mode | ```docker run -it contName```|
| Run specific version | ```docker run contName:version```|
| Attach to host port and run | ```docker run -p hostPort:containerPort contName```|

# Environment Variable

| Task | Code | 
|----------|----------| 
| Check Environment Variable | ```docker inspect contName``` |
| Run a container with an Env variable | ```docker run -e envVar:Value contName``` |

# Images

Docker files are for of form : ==Instruction : Argument ==

How to inspect Dockerfile :

1.  Go to the directory
2.  read Dockerfile using any text editor

## Build images form Dockerfile

```docker build -t imageName .```

-   The `docker build` command is used to build a Docker image.
-   The `-t imageName` option specifies the name of the image as "imageName".
-   The `.` indicates the build context, which is the current directory containing the Dockerfile.

Make sure to navigate to the directory where the Dockerfile is located before running this command.

## Check base OS of image

```docker run imageName:version cat /etc/*release*```

# Command and Entrypoint

This controls what command will be executed when an container is run, can be found 
in the last line of Docker file
![](./Images&Links/Pasted%20image%2020230521154531.png)

### Use cases

- To overwrite original command on Dockerfile [Temporary]
```
docker run imageName sleep 5
```

- Update or create new image [Permanent]
![](./Images&Links/Pasted%20image%2020230521155051.png)

- Use ENTRYPOINT to parameterize  [Permanent] , ==throws error when parameter not provided==
![](./Images&Links/Pasted%20image%2020230521155228.png)

- Combination of ENTRYPOINT and COMMAND , CMD acts as a default parameter in this case
![](./Images&Links/Pasted%20image%2020230521155456.png)

# Networking


# Docker Storage Scenario

This repository provides an example scenario for practicing Docker storage operations. The scenario focuses on creating and managing a Docker volume, mounting it in a container, persisting data, and taking backups of the volume.

## Prerequisites

Make sure you have Docker installed on your system. You can download Docker from the official website: [https://www.docker.com/get-started](https://www.docker.com/get-started)

## Getting Started

1. Clone this repository to your local machine:

```
   git clone https://github.com/your-username/docker-storage-training.git
```

2. Change into the project directory

```
cd docker-storage-training
```

3. Create a Docker volume name "myvolume" using the Docker CLI command:

```
docker volume create myvolume
```

4. Start a Docker container and mount the "mvolume" volume to a  specific path inside the container:

```
docker run -d --name mycontainer -v myvolume:/data nginx
```

5. Enter the running container and write some data to the mounted volume

```
docker exec -it mycontainer sh
echo "Hello, Docker" > /data/test.txt
exit
```

6. Stop the container and remove the container

```
docker stop mycontainer
docker rm mycontainer
```
7. Start a new container, mounting the same volume and verify that the data is still available

```
docker run -d --name mycontainer2 -v myvolume:/data nginx
docker exec -it mycontainer2 sh
cat /data/test.txt
```

You should see the content of the "test.txt" file, indicating that the data persisted in the volume even after stopping and removing the previous container.

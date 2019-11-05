# Cassandra Docker Image

This Docker Image runs Cassandra in CentOS 8 and exposes the following ports...

* 9042 - cql port
* 9160 - thrift port
* 7199 - jmx port

# Build and run the Docker image


```bash
docker build -t cassandra .
docker volume create cass
docker run -tid --mount source=cass,target=/var/lib/cassandra --rm -p 9042:9042 -p 9160:9160 -p 7199:7199 --name rhys  cassandra
docker container ls
```

# Verify ports are open on host

* MacOS

```bash
netstat -anp tcp | grep LISTEN
```

* Linux

```bash
netstat -tulpn | grep LISTEN
```

# Access the running container and check Cassandra

```bash
docker exec -ti rhys sh
nodetool status
```

# TODO

* Add volume to persist data
# Add tests for container ports

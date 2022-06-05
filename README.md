# About
Custom Kali Linux OS arm64 distro accessible via VNC, RDP or web and Tor. The web interface will be available on port 6080.

# Platform configuration

No special configuration is necessary, however some recommended variables are available at runtime :

## IPTables

provide _NET_ADMIN_ privileges to update iptables on the bridge network from within docker.

**For more information on Bridge Network refer [here](https://docs.docker.com/network/bridge/)**

There will be risks if allowed on host network ; so create a custom bridge or use default bridge with command : 
```term
--cap-add=NET_ADMIN --cap-add=NET_RAW  --net="bridge" 
```
## Ports

| Port       | Description                                  |
|------------|----------------------------------------------|
| `6080`     | Provides direct access to the VNC server |


# Usage

See the docker-compose [here](https://github.com/yabhinav/kali-docker-arm64/blob/master/docker-compose.yml) or use this command:

## Build

Build image with the command :
``` term
docker build .  -t 'kalitor:latest'
```

## Run container :

To run container without kalitorify :

```term
docker run -p 6080:6080  kali-linux:latest -it bash
```

## Run container (kalitorify):

To run container with kalitorify :

```term
docker run -p 6080:6080 --cap-add=NET_ADMIN --cap-add=NET_RAW  kali-linux:latest -it bash
```

Verify the IP Address and MAC Address wth commands 
```term
sudo ip addr show

```

Start Kalitorify as follows or [refer](https://github.com/yabhinav/kalitorify) :
```term
kalitorify --clearnet
kalitorify --tor
kalitorify -s
sudo ip addr show
```

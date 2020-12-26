# Pihole using Docker-Compose
### Using a macvlan network

## Setup

The connection to the server is a trunk. Vlan 10 contains the network for the Pihole. Gateway 
192.168.0.1/24 resides on the firewall. The Pihole is 192.168.0.2. eth0.10 is the interface.

### Create the macvlan network in Docker

```
$ docker network create -d macvlan \
--subnet=192.168.0.0/24 \
--gateway=192.168.0.1 \
-o parent=eth0.10 macvlan10
```

### Create the docker volumes for persistence

```
$ docker volume create pihole
$ docker volume create pihole-dnsmasq
```

### Run docker-compose

```
$ docker-compose up -d
```

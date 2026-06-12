---
title: "Can't ping router ip and no internet"
date: 2011-05-21
forum: General Help
---

### Post by hej.mich on 2011-05-21
Hi,
A while ago I had to change a bit my network configuration and after that I cannot ping router from ubuntu server and cant get internet access.

Router 192.168.1.1
Ubuntu server 192.168.1.10
Windows PC 192.168.1.20
Other ubuntu 192.168.1.21


Windows PC and Other ubuntu can ping everything
Ubuntu server can ping Windows PC and other ubuntu
Router can ping Windows PC and other ubuntu but not Ubuntu server

```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0
network 192.168.0.0

```

```
 mich@mich-server:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```

It strangely takes a while before line with destination default appears.
```
ip r
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.10
192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.1
default via 192.168.1.1 dev eth0  metric 100

```
```
ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:01:29:d2:a3:9f brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.10/24 brd 192.168.1.255 scope global eth0
    inet6 fe80::201:29ff:fed2:a39f/64 scope link
       valid_lft forever preferred_lft forever
3: eth1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 00:01:29:d2:a3:3b brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.1/24 brd 192.168.0.255 scope global eth1

```

---


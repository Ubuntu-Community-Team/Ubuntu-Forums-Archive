---
title: "Multiple network interfaces"
date: 2006-02-07
forum: General Help
---

### Post by grinchy on 2006-02-07
Hi, I'm just wondering is it possible to use two wireless nics at the same time in order to provide a larger bandwith?

or even get wget to use a specific interface?

---

### Post by lamego on 2006-02-07
I am not a network expert but as I far I can think on it that will depend on your network route configuration.
You can't have 2 different gateways for the same net, what you can is assign different routes to the different cards and to the transfer in paralell (but from differente hosts).

---

### Post by grinchy on 2006-02-07
Whaa? 

Sorry networking is really not one of my strong points
Really what I'm actually looking for is for someone to go through it step by step for me.

Thanks for the quick reply though.

---

### Post by grinchy on 2006-02-15
Can anyone help me out with this?

---

### Post by Iowan on 2006-02-15
I'm certainly no networking expert either (ESPECIALLY wireless), but I remember reading a post about having two (wired) NICs on the same subnet (against the standards - IIRC).  I'd think wireless cards would fall into the same category.  Just my opinion.

---

### Post by compuguy1088 on 2006-07-25
I beleve what your describing is what is called channel bonding, which is built in the linux kernel, with the help with a certain program that starts with if.....anyway, it can be done, but this can only be connected to an expensive commercial switch (like Cisco) or another box with channel bonding. I've actually been trying to figure this out, but up to date documentation seems scarce, or I'm just not looking in the right places..

---

### Post by GoldWing on 2006-07-26
I am wondering the same thing of it is working on ubuntu

first do lsmod to see if bonding is in there.
otherwise do modprobe bonding

these files needs to be adapted (assumming that you have eth0 & eth2 as your nic's)

[root@rblunia1 network-scripts]# ll ifcf*
-rw-r--r--  1 root root 130 Jul 26 14:07 ifcfg-bond0
-rw-r--r--  1 root root  98 Jul 26 13:18 ifcfg-eth0
-rw-r--r--  1 root root 120 Jan 23  2006 ifcfg-eth2
-rw-r--r--  1 root root 254 Jun 21  2001 ifcfg-lo
[root@rblunia1 network-scripts]# pwd
/etc/sysconfig/network-scripts

[root@rblunia1 network-scripts]# cat ifcfg-bond0
DEVICE=bond0
BOOTPROTO=static
ONBOOT=yes
NETWORK=10.26.21.0
NETMASK=255.255.255.0
IPADDR=10.26.21.6
USERCTL=no
GATEWAY=10.26.21.1

[root@rblunia1 network-scripts]# cat  ifcfg-eth0
DEVICE=eth0
BOOTPROTO=none
#HWADDR=00:16:35:C1:7D:D3
ONBOOT=yes
MASTER=bond0
SLAVE=yes
USERCTL=no

do the same for ifcfg-eth2

This is for static IP's, but I think you can do the same with dhcp

then:

[root@rblunia1 network-scripts]# ifup bond0
Enslaving eth0 to bond0
Enslaving eth2 to bond0



[root@rblunia1 network-scripts]# ifconfig
bond0     Link encap:Ethernet  HWaddr 00:16:35:C1:7D:D3
          inet addr:10.26.21.6  Bcast:10.26.21.255  Mask:255.255.255.0
          inet6 addr: fe80::200:ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:546 (546.0 b)

eth0      Link encap:Ethernet  HWaddr 00:16:35:C1:7D:D3
          inet addr:10.26.21.6  Bcast:10.26.21.255  Mask:255.255.255.0
          inet6 addr: fe80::216:35ff:fec1:7dd3/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:546 (546.0 b)
          Interrupt:201

eth2      Link encap:Ethernet  HWaddr 00:16:35:C1:7D:D3
          inet addr:10.26.21.6  Bcast:10.26.21.255  Mask:255.255.255.0
          inet6 addr: fe80::216:35ff:fec1:7dd3/64 Scope:Link
          UP BROADCAST SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217


look at the words 'SLAVE'

/edit

don't forget to put an alias for bonding in the modprobe.conf file

---

### Post by Paris Heng on 2008-03-24
> **GoldWing said:**
> I am wondering the same thing of it is working on ubuntu

first do lsmod to see if bonding is in there.
otherwise do modprobe bonding

these files needs to be adapted (assumming that you have eth0 & eth2 as your nic's)

[root@rblunia1 network-scripts]# ll ifcf*
-rw-r--r--  1 root root 130 Jul 26 14:07 ifcfg-bond0
-rw-r--r--  1 root root  98 Jul 26 13:18 ifcfg-eth0
-rw-r--r--  1 root root 120 Jan 23  2006 ifcfg-eth2
-rw-r--r--  1 root root 254 Jun 21  2001 ifcfg-lo
[root@rblunia1 network-scripts]# pwd
/etc/sysconfig/network-scripts

[root@rblunia1 network-scripts]# cat ifcfg-bond0
DEVICE=bond0
BOOTPROTO=static
ONBOOT=yes
NETWORK=10.26.21.0
NETMASK=255.255.255.0
IPADDR=10.26.21.6
USERCTL=no
GATEWAY=10.26.21.1

[root@rblunia1 network-scripts]# cat  ifcfg-eth0
DEVICE=eth0
BOOTPROTO=none
#HWADDR=00:16:35:C1:7D:D3
ONBOOT=yes
MASTER=bond0
SLAVE=yes
USERCTL=no

do the same for ifcfg-eth2

This is for static IP's, but I think you can do the same with dhcp

then:

[root@rblunia1 network-scripts]# ifup bond0
Enslaving eth0 to bond0
Enslaving eth2 to bond0



[root@rblunia1 network-scripts]# ifconfig
bond0     Link encap:Ethernet  HWaddr 00:16:35:C1:7D:D3
          inet addr:10.26.21.6  Bcast:10.26.21.255  Mask:255.255.255.0
          inet6 addr: fe80::200:ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:546 (546.0 b)

eth0      Link encap:Ethernet  HWaddr 00:16:35:C1:7D:D3
          inet addr:10.26.21.6  Bcast:10.26.21.255  Mask:255.255.255.0
          inet6 addr: fe80::216:35ff:fec1:7dd3/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:546 (546.0 b)
          Interrupt:201

eth2      Link encap:Ethernet  HWaddr 00:16:35:C1:7D:D3
          inet addr:10.26.21.6  Bcast:10.26.21.255  Mask:255.255.255.0
          inet6 addr: fe80::216:35ff:fec1:7dd3/64 Scope:Link
          UP BROADCAST SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217


look at the words 'SLAVE'

/edit

don't forget to put an alias for bonding in the modprobe.conf file


What you have done is in Ethernet, can it be done in wireless?

---


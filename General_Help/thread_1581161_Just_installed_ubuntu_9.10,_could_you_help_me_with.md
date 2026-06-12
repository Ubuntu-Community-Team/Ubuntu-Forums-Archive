---
title: "Just installed ubuntu 9.10, could you help me with some problems?"
date: 2010-09-24
forum: General Help
---

### Post by J-E-N-O-V-A on 2010-09-24
Here is my connection:
```

eth0      Link encap:Ethernet  HWaddr 00:1f:c6:4d:69:d8  
          inet addr:10.3.213.209  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::21f:c6ff:fe4d:69d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32313 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17383 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26476022 (26.4 MB)  TX bytes:3012108 (3.0 MB)
          Interrupt:19 Base address:0xdead 
```
It wont update:
```
sudo apt-get update
[sudo] password for tom: 
Err http://gb.archive.ubuntu.com karmic Release.gpg                            
  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]

```
However it will ping google:
```
PING www.l.google.com (173.194.36.104) 56(84) bytes of data.
64 bytes from lhr14s01-in-f104.1e100.net (173.194.36.104): icmp_seq=1 ttl=51 time=11.4 ms
```
Ultimately all I'm trying to do is to get video chat working. I can browse firefox and that's about it. Empathy IM Client wont connect my hotmail account and if it does I still wont know if my webcam will work.

Furthermore, when I try to open a skype .deb package it gives me this error:
```
Error: Dependency is not satisfiable: libqt4-dbus (>= 4.4.3)
``` which it does similiarly with other .deb packages

---

### Post by searchfgold6789 on 2010-09-24
Well the last problem's easy. Open up a terminal:
```
sudo apt-get install libqt4-dbus
```and try the deb again.

To get video chat to work you must get...software.

---

### Post by andrewthomas on 2010-09-24
Try booting with 

```
ipv6.disable=1
```

---


---
title: "awesome window manager networking problem"
date: 2011-07-07
forum: General Help
---

### Post by shri19 on 2011-07-07
Hi all,

I have installed awesome desktop manager on my system, but i am not able to get the network up. I have tried the usual commands like /etc/init.d/networking start, /etc/init.d/interfaces start, ifconfig eth0 up and all, but none worked so far. the output of ifconfig is as follows.

> eth0      Link encap:Ethernet  HWaddr b8:ac:6f:63:fb:12  
          inet6 addr: fe80::baac:6fff:fe63:fb12/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8056692 errors:21 dropped:0 overruns:0 frame:21
          TX packets:9223504 errors:0 dropped:0 overruns:0 carrier:154
          collisions:0 txqueuelen:1000 
          RX bytes:2288993402 (2.2 GB)  TX bytes:1639408526 (1.6 GB)
          Interrupt:47 

eth1      Link encap:Ethernet  HWaddr 1c:65:9d:1b:e4:00  
          inet6 addr: fe80::1e65:9dff:fe1b:e400/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1624 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1624 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:133460 (133.4 KB)  TX bytes:133460 (133.4 KB)


Also, things work fine when i login through gnome. further it also works when someones logged on gnome and a second user logs in using awesome desktop manager. Please help. Thanks in advance.


--
Shri

---


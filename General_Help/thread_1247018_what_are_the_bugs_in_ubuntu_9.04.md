---
title: "what are the bugs in ubuntu 9.04?"
date: 2009-08-22
forum: General Help
---

### Post by karthick87 on 2009-08-22
Can some list the bugs in ubuntu 9.04 ?? I have tried to setup a network connection in home,and that was a fresh install of ubuntu 9.04 and i have configured pppoe connection using the command "sudo pppoeconf" and it works fine at that time..But after a restart everything got changed..I cant assign a static ip permanently,if i assign it got vanished during the next boot..This is my output of my network connection..

ifconfig:
eth0    Link encap:Ethernet  HWaddr 00:1c:c0:ab:17:70  
          inet6 addr: fe80::21c:c0ff:feab:1770/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8936549 (8.9 MB)  TX bytes:1161832 (1.1 MB)
          Interrupt:252 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13298 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9761082 (9.7 MB)  TX bytes:9761082 (9.7 MB)

/etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by Iowan on 2009-08-22
[Here]("http://ubuntuforums.org/showthread.php?t=1145967") is one list, and [one]("http://ubuntuforums.org/showthread.php?t=1176117") on networking issues.
There is/was a [PPPOE]("https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/339882") bug in Kubuntu.

---


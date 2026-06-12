---
title: "Disappeared wireless"
date: 2011-09-28
forum: General Help
---

### Post by glerikud on 2011-09-28
I'm a linux noob, and i have an interesting problem, with my wireless card.

I have an IBM T43 notebook with a Broadcom BCM4318 wireless stuff. I just installed Ubuntu 11.04 and after a long search i installed some broadcom firmware to make the wifi work. It worked, but after a restart it just gone. Ubuntu can't see the device any more.

Tried:
- reinstalling broadcom drivers
- turning the device on and off

Right before the restart, i deleted some software through the software manager (Bluetooth, etc..). Can this be the problem? Altough i reinstalled it and still not working..

Here's the ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:24:7e:13:11:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8176 (8.1 KB)  TX bytes:8176 (8.1 KB)

```


Hope you can help me. Thanks.

---


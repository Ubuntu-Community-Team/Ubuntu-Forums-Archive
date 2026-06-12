---
title: "Internet connection won't work"
date: 2010-04-19
forum: General Help
---

### Post by Shadow12313 on 2010-04-19
I just changed my wireless connection over to wired and my computer claims it's connected but when I try to open and webpage (or even ping) it can't connect.

Keep in mind I am plugged directly into the router.
Also I'm not sure if this is helpful but, I did have connection sharing for my xbox when I had wireless.

Any help is greatly appreciated but, please hurry because I'm typing this on windows 7 which is driving me further into insanity by the minute.

---

### Post by Shadow12313 on 2010-04-19
Additional information:

eth0      
Link encap:Ethernet  
HWaddr 00:19:66:44:6b:54  
          
inet addr:192.168.1.131  
Bcast:192.168.1.255  
Mask:255.255.255.0
          
inet6 addr: fe80::219:66ff:fe44:6b54/64 Scope:Link
          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          
RX packets:2996 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:370 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          
RX bytes:205898 (205.8 KB)  TX bytes:41183 (41.1 KB)
          
Interrupt:23 Base address:0x2c00

---

### Post by Iowan on 2010-04-19
Looks like the machine has an IP address for eth0 (good start!). I presume you can ping the router. Can you ping internet by IP address (try 74.125.95.99)? What are results of (from a terminal) **route -n** and **cat /etc/resolv.conf**?

---


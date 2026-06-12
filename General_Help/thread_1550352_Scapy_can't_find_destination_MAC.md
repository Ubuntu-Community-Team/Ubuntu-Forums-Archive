---
title: "Scapy can't find destination MAC"
date: 2010-08-10
forum: General Help
---

### Post by Bender59 on 2010-08-10
I'm making a program that uses Scapy to sniff for a packet being sent to a certain host, then sending another packet with the Ethernet, IP and TCP headers identical, but a different payload.

Whenever I try to run this, however, I get these errors:

```
WARNING: No route found for IPv6 destination :: (no default route?)
WARNING: Mac address to reach destination not found. Using broadcast.
```
Does anyone know what I can do to fix these problems?

---

### Post by Bender59 on 2010-08-11
BUMP

Here's output of ifconfig as well:
```
eth0      Link encap:Ethernet  HWaddr 00:19:d1:3d:34:0e  
          inet addr:192.168.0.192  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe3d:340e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2987028 (2.9 MB)  TX bytes:724184 (724.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
```

---

### Post by Bender59 on 2010-08-11
BUMP again.

---


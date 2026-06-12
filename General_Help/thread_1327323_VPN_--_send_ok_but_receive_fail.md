---
title: "VPN -- send ok but receive fail"
date: 2009-11-15
forum: General Help
---

### Post by Morfi777 on 2009-11-15
Hello,

**There is:** My computer (in home) AND Server (somewhere in the world).
[B]
Problem:[/B] When I connect to this VPN I see that data ARE sending, but receiving doesn't move at all.

**info:**

I set up a PPTP VPN on this server and configured it.

The settings are:
localip 91.121.204.145  # this is IP of the server
remoteip 95.49.54.1-254  # this is IP range in my home (I have dynamic IP)

ifconfig on server:
```
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:3c:35:e5
          inet addr:91.121.204.145  Bcast:91.121.204.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:134372188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145845525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1577997864 (1.4 GB)  TX bytes:3343493241 (3.1 GB)
          Interrupt:19 Base address:0x2000

eth0:0    Link encap:Ethernet  HWaddr 00:1c:c0:3c:35:e5
          inet addr:87.98.188.79  Bcast:87.255.255.255  Mask:255.255.255.255
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0x2000

```


**Thanks in Advance!**

---

### Post by Morfi777 on 2009-11-15
like always no one knows. 6 posts 6 thread 6 no answered problems -.-

---


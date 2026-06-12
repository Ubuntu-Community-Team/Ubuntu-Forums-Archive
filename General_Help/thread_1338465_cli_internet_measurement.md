---
title: "cli internet measurement"
date: 2009-11-26
forum: General Help
---

### Post by kpholmes on 2009-11-26
does anyone know a simple command that i can use to check how much data my computer is sending and receiving?

---

### Post by solar george on 2009-11-26
ifconfig tells you how much has been sent and received this boot;
```
eth1      Link encap:Ethernet  HWaddr 00:0c:f1:11:bd:b7
          inet addr:192.168.2.171  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe11:bdb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:104 errors:1 dropped:1 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
[B]          RX bytes:17736 (17.7 KB)  TX bytes:16422 (16.4 KB)
[/B]          Interrupt:11 Base address:0x6000 Memory:fceff000-fcefffff

```
If you use byobu you can add network monitors to the bottom bar from the <F9> menu.

---

### Post by kpholmes on 2009-11-26
that works, but im putting it on a php script so something that would give me a an output more like the command df -h or uptime would be more preferable as it would be more "realtime" but thats an option ill keep in mind. thanks

---

### Post by XCan on 2009-11-26
vnstat in the repos should work nicely. It can show statistics in hours/days/months/years/weeks etc, and also support a live mode.

---


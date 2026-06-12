---
title: "Broken Wired Connection"
date: 2010-11-27
forum: General Help
---

### Post by jim_deadlock on 2010-11-27
I just installed 10.10 on a desktop machine, dual boot with Win XP. Everything went well, it connected and did all the system updates etc. Then one time I rebooted and it wouldn't connect. I've tried rebooting again several times, tried unplugging the modem/router from the power and from the computer then reconnecting everything and starting it up again, no joy. I booted from the Live CD and it connects without any problem, likewise from Win XP. My Network Connections shows 'Auto eth0' and below is the ifconfig output. Any ideas?

```
jim@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:8f:b8:ad:fc  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

---

### Post by jim_deadlock on 2010-11-27
Any suggestions before I resort to a complete reinstall...?

---


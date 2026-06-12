---
title: "ping localhost problem"
date: 2010-03-14
forum: General Help
---

### Post by lvotusk on 2010-03-14
sorry for double posting, but I need help with this.

If I ping localhost (or ping 127.0.0.1 for that matter)

I just get this
From localhost (127.0.0.1) icmp_seq=1 Destination Port Unreachable

ifconfig -a is giving me this

eth0      Link encap:Ethernet  HWaddr 00:21:85:c0:ae:6a  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:85ff:fec0:ae6a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:516 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:414284 (414.2 KB)  TX bytes:81632 (81.6 KB)
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19861 (19.8 KB)  TX bytes:19861 (19.8 KB)


This worked until a couple of days ago when some auto updates were installed. I might as well use sh***y windows if updates are going to break things

---

### Post by Rocket2DMn on 2010-03-14
Can you please post the contents of your /etc/hosts file:
```
cat /etc/hosts
```

---


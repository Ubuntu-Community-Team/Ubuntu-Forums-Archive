---
title: "Wireless Issues"
date: 2010-05-04
forum: General Help
---

### Post by merlin_ie on 2010-05-04
hey all. i've put Jaunty on my friends laptop, but the problem is we can't choose his wireless connection from the list. his connection is the one greyed out and it's an old IBM Thinkpad. here is the output from *ifconfig* (please don't laugh it's a stupid mistake i'm making lol)

eth0      Link encap:Ethernet  HWaddr 00:0d:60:ca:80:13  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:feca:8013/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9932 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:10014057 (10.0 MB)  TX bytes:1949625 (1.9 MB)

eth1      Link encap:Ethernet  HWaddr 00:0e:9b:1f:69:37  
          inet6 addr: fe80::20e:9bff:fe1f:6937/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:759 dropped:0 overruns:0 frame:759
          TX packets:12 errors:12 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:792 (792.0 B)
          Interrupt:11 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---


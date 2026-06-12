---
title: "Squid transparent proxy setup"
date: 2009-08-25
forum: General Help
---

### Post by karthick87 on 2009-08-25
this is my network configuration..
eth0 connected to modem and eth1 connected to XP systems via switch..and this is my output of ifconfig..

eth0      Link encap:Ethernet  HWaddr 00:24:21:3a:ee:72  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:fe3a:ee72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:336354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:297166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:383050952 (383.0 MB)  TX bytes:39779867 (39.7 MB)
          Interrupt:254 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:e0:42:c8:02:1c  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:42ff:fec8:21c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:270600 errors:1 dropped:0 overruns:0 frame:0
          TX packets:307510 errors:0 dropped:0 overruns:0 ceth0      Link encap:Ethernet  HWaddr 00:24:21:3a:ee:72  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:fe3a:ee72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:336354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:297166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:383050952 (383.0 MB)  TX bytes:39779867 (39.7 MB)
          Interrupt:254 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:e0:42:c8:02:1c  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:42ff:fec8:21c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:270600 errors:1 dropped:0 overruns:0 frame:0
          TX packets:307510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34089696 (34.0 MB)  TX bytes:353352911 (353.3 MB)
          Interrupt:16 Memory:fddff000-fddff0ff 
arrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34089696 (34.0 MB)  TX bytes:353352911 (353.3 MB)
          Interrupt:16 Memory:fddff000-fddff0ff 

now i want to setup squid transparent proxy,can someone give me the acl and iptable configuration..

---


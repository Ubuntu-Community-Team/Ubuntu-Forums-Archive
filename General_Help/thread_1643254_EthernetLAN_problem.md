---
title: "Ethernet/LAN problem"
date: 2010-12-11
forum: General Help
---

### Post by arnab_das on 2010-12-11
I have 2 LAN ports. one from the motherboard (on board) and the other from a lan card i bought a few days back. one is use for browsing the net, the other for a media player.

problem is i cant connect to both the eth0 and eth1 at the same time. i have to disconnect one of them to connect to the other. and this really gets irritating as it doesnt always work as flawlessly as it should. what am i doing wrong?

any solution would be of great help.

thanks in advance.

---

### Post by dcstar on 2010-12-11
> **arnab_das said:**
> I have 2 LAN ports. one from the motherboard (on board) and the other from a lan card i bought a few days back. one is use for browsing the net, the other for a media player.

problem is i cant connect to both the eth0 and eth1 at the same time. i have to disconnect one of them to connect to the other. and this really gets irritating as it doesnt always work as flawlessly as it should. what am i doing wrong?
.

Post the output of **ifconfig**.

---

### Post by arnab_das on 2010-12-12
> **dcstar said:**
> Post the output of **ifconfig**.

okay here's what i got:

> $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:67:12:3c:16  
          inet6 addr: fe80::230:67ff:fe12:3c16/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1463483 (1.4 MB)  TX bytes:8898502 (8.8 MB)
          Interrupt:45 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:1e:a6:02:35:d9  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:a6ff:fe02:35d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2042947 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2172823 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1278157262 (1.2 GB)  TX bytes:366803344 (366.8 MB)
          Interrupt:19 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3846 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:386389 (386.3 KB)  TX bytes:386389 (386.3 KB)

---

### Post by arnab_das on 2010-12-12
here's the ifconfig when eth0 (this is connected to media player) is enabled: (eth1 is automatically disconnected)

> $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:67:12:3c:16  
          inet6 addr: fe80::230:67ff:fe12:3c16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:109421 (109.4 KB)  TX bytes:41604 (41.6 KB)
          Interrupt:45 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:1e:a6:02:35:d9  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:a6ff:fe02:35d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13437 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10323973 (10.3 MB)  TX bytes:2480144 (2.4 MB)
          Interrupt:19 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:511559 (511.5 KB)  TX bytes:511559 (511.5 KB)


and here's the ifconfig when eth1 is enabled (eth0 automatically gets disabled)

> $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:67:12:3c:16  
          inet6 addr: fe80::230:67ff:fe12:3c16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1381 errors:0 dropped:0 overruns:0 frame:0
          TX packets:291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:110861 (110.8 KB)  TX bytes:41604 (41.6 KB)
          Interrupt:45 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:1e:a6:02:35:d9  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:a6ff:fe02:35d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12827 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13479 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10328151 (10.3 MB)  TX bytes:2487691 (2.4 MB)
          Interrupt:19 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:519513 (519.5 KB)  TX bytes:519513 (519.5 KB)


---

### Post by arnab_das on 2010-12-12
okay i solved it.

thanks to this tutorial: [http://www.t1shopper.com/tools/calculate/ip-subnet/](http://www.t1shopper.com/tools/calculate/ip-subnet/)

---


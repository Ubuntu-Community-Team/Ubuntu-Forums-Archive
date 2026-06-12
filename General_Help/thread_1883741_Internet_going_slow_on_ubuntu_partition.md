---
title: "Internet going slow on ubuntu partition"
date: 2011-11-19
forum: General Help
---

### Post by brushman on 2011-11-19
Recently I just came home from college (for break). My computer, which has has an ubuntu and windows partition, was fine prior to coming home.

Now that I'm at home and trying to connect to the internet, my connection when on ubuntu is very slow (but still works). On windows on the other hand, the connection is perfectly fine.

Does anyone know what might be the problem?

Thanks

---

### Post by poloshiao on 2011-11-19
From ubuntu terminal:
1. sudo ifconfig -a
2. sudo route -n
Copy the output and paste it here, please.

---

### Post by brushman on 2011-11-20
Here is the output (I wanted to attach it as a nice screenshot but my slow internet made it too hard).



benjamin@benjamin-Studio-1558:~$ **sudo ifconfig -a**
[sudo] password for benjamin:
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:46:31:d2
             UP BROADCAST MULTICAST  MTU:1500  Metric:1
             RX packets:0 errors:0 dropped:0 overruns:0 frame:0
             TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:1000
             RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
             Interrupt:40 Base address:0x8000

lo        Link encap:Local Loopback
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:27:10:1b:76:04
              inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
              inet6 addr: fe80::227:10ff:fe1b:7604/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:1178 errors:0 dropped:0 overruns:0 frame:0
              TX packets:1247 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:791284 (791.2 KB)  TX bytes:217901 (217.9 KB)

benjamin@benjamin-Studio-1558:~$ **sudo route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

---


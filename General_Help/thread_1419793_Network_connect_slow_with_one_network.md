---
title: "Network connect slow with one network"
date: 2010-03-02
forum: General Help
---

### Post by saganomics on 2010-03-02
Ubuntu Karmic 64. Any large download, most notably the load of updates at install, goes very very slowly. It is only on my work network, which we have several xp boxes on that can download quickly. However when attached with my ubuntu box, my speeds start at normal 400 kB/s, but then it drops to about 1500 B/s and stays there.

Sometimes it will go back up momentarily. If I restart the download it speeds up at the start again then slow. Also my network monitor shows a 50% spike every 10 seconds. Is that related.

Also, I changed to a public DNS to see if the DNS was the problem. Same situation.

```
eth0      Link encap:Ethernet  HWaddr 00:21:70:7e:b9:a0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth2      Link encap:Ethernet  HWaddr 00:22:5f:29:4e:dd  
          inet addr:192.168.14.2  Bcast:192.168.14.255  Mask:255.255.255.0
          inet6 addr: fe80::222:5fff:fe29:4edd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51991 errors:0 dropped:0 overruns:0 frame:25836
          TX packets:31358 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71902795 (71.9 MB)  TX bytes:3671970 (3.6 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:126498 (126.4 KB)  TX bytes:126498 (126.4 KB)

```
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.14.0    0.0.0.0         255.255.255.0   U     2      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
0.0.0.0         192.168.14.254  0.0.0.0         UG    0      0        0 eth2
```

---

### Post by labinnsw on 2010-03-09
[See post 7 and the link it contains]("http://ubuntuforums.org/showthread.php?t=1176679")

---


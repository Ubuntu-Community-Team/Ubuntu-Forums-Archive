---
title: "except firefox, not able to access internet at all"
date: 2009-12-03
forum: General Help
---

### Post by thiyagi on 2009-12-03
[LEFT]Except firefox, not able to access internet at all. Plz people dont get fedup by the same question asked in many forums since ubuntu 9.10 has been released. I enjoyed linux very much until ubuntu 9.10 was released.I just installed ubuntu 9.10 happily and was ready to install every appz, but no internet at all. This problem is really weird for me, because i have tried many steps reading many forums nearly for 6 days. I am totally tired now, going to wait for the ubuntu guru's to help...;)

Now let me come to the point,
firefox is working after changing the value of "network.dns.disableIPv6" to true
in about:config.
But not able connect to internet using update manager,ubuntu software center,  almost rest of the applications,

I used the network tools and found this,
Network device:Ethernet Interface(eth0) 
IPv6:ip address as " ::", netmask as"0",scope as "unknown"
IPv4:ip address as"192.168.0.100",netmask as"255.255.255.0"
so i assume that ipv6 is already disabled, 
then even,
[/LEFT]
```
thiyagi@thiyagi-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:15:05:e1  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4269 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3558 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4442832 (4.4 MB)  TX bytes:514833 (514.8 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:22:15:15:12:0a  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

```so its pretty clear internet is working fine, but some app is blocking it. I dont even have firewall app, so what the problem????

---

### Post by jegerjensen on 2009-12-03
can you ping anybody?  What is the output of

```
[...]$ping google.com
```

---

### Post by thiyagi on 2009-12-03
yes of course,
```

thiyagi@thiyagi-desktop:~$ ping google.com
PING google.com (74.125.45.100) 56(84) bytes of data.
64 bytes from google.com (74.125.45.100): icmp_seq=1 ttl=46 time=327 ms
64 bytes from google.com (74.125.45.100): icmp_seq=2 ttl=46 time=324 ms
64 bytes from google.com (74.125.45.100): icmp_seq=3 ttl=46 time=324 ms
64 bytes from google.com (74.125.45.100): icmp_seq=4 ttl=46 time=324 ms
64 bytes from google.com (74.125.45.100): icmp_seq=5 ttl=46 time=327 ms
64 bytes from google.com (74.125.45.100): icmp_seq=6 ttl=46 time=328 ms
64 bytes from google.com (74.125.45.100): icmp_seq=7 ttl=46 time=325 ms
64 bytes from google.com (74.125.45.100): icmp_seq=8 ttl=46 time=326 ms
64 bytes from google.com (74.125.45.100): icmp_seq=9 ttl=46 time=324 ms
64 bytes from google.com (74.125.45.100): icmp_seq=10 ttl=46 time=327 ms
64 bytes from google.com (74.125.45.100): icmp_seq=11 ttl=46 time=324 ms
64 bytes from google.com (74.125.45.100): icmp_seq=12 ttl=46 time=324 ms
64 bytes from google.com (74.125.45.100): icmp_seq=13 ttl=46 time=323 ms
64 bytes from google.com (74.125.45.100): icmp_seq=14 ttl=46 time=322 ms
64 bytes from google.com (74.125.45.100): icmp_seq=15 ttl=46 time=322 ms
64 bytes from google.com (74.125.45.100): icmp_seq=16 ttl=46 time=325 ms
64 bytes from google.com (74.125.45.100): icmp_seq=17 ttl=46 time=324 ms
64 bytes from google.com (74.125.45.100): icmp_seq=18 ttl=46 time=322 ms
 64 bytes from google.com (74.125.45.100): icmp_seq=19 ttl=46 time=324 ms
64 bytes from google.com (74.125.45.100): icmp_seq=20 ttl=46 time=325 ms
64 bytes from google.com (74.125.45.100): icmp_seq=21 ttl=46 time=322 ms
64 bytes from google.com (74.125.45.100): icmp_seq=22 ttl=46 time=325 ms
64 bytes from google.com (74.125.45.100): icmp_seq=23 ttl=46 time=327 ms
^C
--- google.com ping statistics ---
23 packets transmitted, 23 received, 0% packet loss, time 22025ms
rtt min/avg/max/mdev = 322.343/325.083/328.516/1.889 ms

```and even tried in network tools, 
able to ping [www.google.com]("http://www.google.com")
packets transmitted:5
packets received:5
Sucessful packets:100%

---

### Post by thiyagi on 2009-12-08
can anyone help me, 4 days and no reply for this post...

---

### Post by Dennis N on 2009-12-08
You might try disabling ipv6 for the entire system. A way to do that is described here: 

[http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html](http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html)

immediately following the section describing the method for disabling it in firefox.

---

### Post by thiyagi on 2009-12-13
Thank you very much for the reply, but i already did that. As i have mentioned it before..Firefox is working(able to go online). With updates,synaptic and rest of the softwares not able to connect to the internet...

---


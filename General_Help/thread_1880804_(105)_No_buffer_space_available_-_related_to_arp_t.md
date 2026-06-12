---
title: "(105) No buffer space available - related to arp table?"
date: 2011-11-14
forum: General Help
---

### Post by telcoguy on 2011-11-14
Why is Ubuntu doing an arp-request for IP's that are not on the local subnet of the interface? 



```

bestpa@h4x0r:~$ sudo tcpdump  -vvv -n arp 
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes

09:17:24.710888 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 10.33.66.33 tell 10.10.145.13, length 28
09:17:24.711406 ARP, Ethernet (len 6), IPv4 (len 4), Reply 10.33.66.33 is-at 00:00:0c:07:ac:63, length 46
09:17:24.934882 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 10.33.66.32 tell 10.10.145.13, length 28
09:17:24.935332 ARP, Ethernet (len 6), IPv4 (len 4), Reply 10.33.66.32 is-at 00:00:0c:07:ac:63, length 46
09:17:25.014872 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 216.198.139.231 tell 10.10.145.13, length 28
09:17:25.015325 ARP, Ethernet (len 6), IPv4 (len 4), Reply 216.198.139.231 is-at 00:00:0c:07:ac:63, length 46
```The error I’ve been getting from my squid box lately ((105) No buffer space available) corresponds with a dmesg entry telling me neighbor table overflow.  

```

  bestpa@h4x0r:~$ dmesg
  …
  [371203.844141] ipv4: Neighbour table overflow.
  [371203.894697] ipv4: Neighbour table overflow.
  [371203.945323] ipv4: Neighbour table overflow.
  [371204.006787] ipv4: Neighbour table overflow.
  [371204.057160] ipv4: Neighbour table overflow.
  [371204.064572] ipv4: Neighbour table overflow.
  [371204.107918] ipv4: Neighbour table overflow.
  
```I get that message when the machine appears to get clogged up.  Either from the SQUID proxy, or from just trying an outbound ping on a pre-exisitng ssh session.


  ```

 
  bestpa@h4x0r:~$ ping 10.10.10.10
  connect: No buffer space available
```Check out my arp table… .  pretty sure those devices aren’t local to the subnet! 



  
```
bestpa@h4x0r:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:14:4f:9b:71:30  
          inet addr:10.10.145.13  Bcast:10.10.145.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

  
  bestpa@h4x0r:~$ arp -an 
  ? (207.171.7.177) at 00:00:0c:07:ac:63 [ether] on eth0
  ? (75.119.204.53) at 00:00:0c:07:ac:63 [ether] on eth0
  ? (209.85.145.104) at 00:00:0c:07:ac:63 [ether] on eth0
  ? (75.101.130.100) at 00:00:0c:07:ac:63 [ether] on eth0
  ? (216.137.41.219) at 00:00:0c:07:ac:63 [ether] on eth0
  
```Watch my arp table expand as I browse through my squid proxy... 
```

bestpa@h4x0r:~$ while $1
> do
> arp -an | wc -l 
> sleep 10
> done
63
91
127
137
149
167
186
196
210
225
235
^C
bestpa@h4x0r:~$ 


bestpa@h4x0r:~$ uname -a
Linux h4x0r 3.0.0-12-virtual #20-Ubuntu SMP Fri Oct 7 18:19:02 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
bestpa@h4x0r:~$
```I am running 10.11 and have ipv6 disabled.

---

### Post by telcoguy on 2011-11-15
Solved.  The problem was that after my upgrade from 11.04 to 11.10 , the default route went missing!  Instead, the interface IP was used as the Gateway.  UBUNTU, Fix!

```

bestpa@h4x0r:~$ netstat -nr 
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.10.145.13    0.0.0.0         UG        0 0          0 eth0
10.10.145.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0

```



So i used the network utility to specify my default route again.  Now I only have one entry in my ARP table, good.

```
bestpa@h4x0r:~$ ping www.google.com
PING www.l.google.com (72.14.204.147) 56(84) bytes of data.
64 bytes from iad04s01-in-f147.1e100.net (72.14.204.147): icmp_req=1 ttl=50 time=37.4 ms
64 bytes from iad04s01-in-f147.1e100.net (72.14.204.147): icmp_req=2 ttl=50 time=35.7 ms
^C
--- www.l.google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 35.777/36.609/37.442/0.854 ms
bestpa@h4x0r:~$ arp -an 
? (10.10.145.1) at 00:00:0c:07:ac:63 [ether] on eth0
bestpa@h4x0r:~$ 
```

---


---
title: "Removing Firestarter caused loss of internet"
date: 2011-06-30
forum: General Help
---

### Post by laserman on 2011-06-30
A couple of years back, just getting into Ubuntu, I installed Firestarter as an option to aid in networking. Realizing that it really didn't help in my plan, I now want to remove it. In terminal, I typed: 

```
sudo apt-get purge -y firestarter

```
I rebooted, only to find out that I now have no internet connection. 

Typing ifconfig, I get this:


```
eth0      Link encap:Ethernet  HWaddr 00:26:55:c1:05:e9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

eth1      Link encap:Ethernet  HWaddr 00:26:5e:8b:5d:c9  
          inet addr:192.10.10.120  Bcast:192.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5eff:fe8b:5dc9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6291 (6.2 KB)  TX bytes:350 (350.0 B)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:529 errors:0 dropped:0 overruns:0 frame:0
          TX packets:529 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:95839 (95.8 KB)  TX bytes:95839 (95.8 KB)
```

It appears I have an IP address, connected to my router but for some reason, my box is not allowing anything through.

I found this thread [Network doesn't work]("http://ubuntuforums.org/archive/index.php/t-551809.html") that points to the same indications I am getting and even mentioning Firestarter but they just removed rules and then they were off and working. I did perform the recommended steps outlined but it didn't correct my no internet issue. 

I want to completely remove Firestarter. Now I'm stuck, after following the instructions as listed in the link above.

Anyone have any ideas?

---

### Post by laserman on 2011-06-30
It's a mess but posting the results of sudo iptables -nL


```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  68.28.250.92         0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  68.28.250.92         0.0.0.0/0           
ACCEPT     tcp  --  68.28.242.91         0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  68.28.242.91         0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
DROP       all  --  0.0.0.0/0            255.255.255.255     
DROP       all  --  224.0.0.0/8          0.0.0.0/0           
DROP       all  --  0.0.0.0/0            224.0.0.0/8         
DROP       all  --  255.255.255.255      0.0.0.0/0           
DROP       all  --  0.0.0.0/0            0.0.0.0             
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
LSI        all  -f  0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
INBOUND    all  --  0.0.0.0/0            0.0.0.0/0           
INBOUND    all  --  0.0.0.0/0            28.253.17.46        
INBOUND    all  --  0.0.0.0/0            28.253.17.46        
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
TCPMSS     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU 
OUTBOUND   all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            28.253.17.46        state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            28.253.17.46        state RELATED,ESTABLISHED 
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 
ACCEPT     all  --  192.168.0.0/24       0.0.0.0/0           ctstate NEW 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           ctstate RELATED,ESTABLISHED 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  28.253.17.46         68.28.250.92        tcp dpt:53 
ACCEPT     udp  --  28.253.17.46         68.28.250.92        udp dpt:53 
ACCEPT     tcp  --  28.253.17.46         68.28.242.91        tcp dpt:53 
ACCEPT     udp  --  28.253.17.46         68.28.242.91        udp dpt:53 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
DROP       all  --  224.0.0.0/8          0.0.0.0/0           
DROP       all  --  0.0.0.0/0            224.0.0.0/8         
DROP       all  --  255.255.255.255      0.0.0.0/0           
DROP       all  --  0.0.0.0/0            0.0.0.0             
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
OUTBOUND   all  --  0.0.0.0/0            0.0.0.0/0           
OUTBOUND   all  --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (3 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
LSI        all  --  0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
LOG        icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
```

---


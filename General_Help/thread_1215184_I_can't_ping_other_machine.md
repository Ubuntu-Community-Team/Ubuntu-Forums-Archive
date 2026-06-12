---
title: "I can't ping other machine"
date: 2009-07-16
forum: General Help
---

### Post by mmbathan on 2009-07-16
Hi there,
 
I connect twp machines using Vmware in Bridge mode.
 
each machine has static IP address.
 
 
the problem some times I can't ping the machines from each other while some times works.
 
I try to ping the machine it self and it is work 
 
for example: 
```
bagside@bagvapp:~$ ping 192.168.137.111
PING 192.168.137.111 (192.168.137.111) 56(84) bytes of data.
From 192.168.137.129 icmp_seq=1 Destination Host Unreachable
From 192.168.137.129 icmp_seq=2 Destination Host Unreachable
From 192.168.137.129 icmp_seq=3 Destination Host Unreachable
 
--- 192.168.137.111 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4019ms
, pipe 3
bagside@bagvapp:~$ ping 192.168.137.129
PING 192.168.137.129 (192.168.137.129) 56(84) bytes of data.
64 bytes from 192.168.137.129: icmp_seq=1 ttl=64 time=0.195 ms
64 bytes from 192.168.137.129: icmp_seq=2 ttl=64 time=0.073 ms
 
--- 192.168.137.129 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.073/0.134/0.195/0.061 ms
bagside@bagvapp:~$ 

```
 
How can I fix this problem?
 
Regards,

---


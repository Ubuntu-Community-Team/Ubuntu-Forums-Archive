---
title: "OpenVPN Routing Question"
date: 2009-07-01
forum: General Help
---

### Post by aphexcoil on 2009-07-01
I have successfully installed OpenVPN on my Ubuntu server and connected to it from my windows laptop from another location. I can see the server without problems but I cannot ping or access any other machine that is on the same subnet (192.168.2.0/24). 
 
The IP address of my laptop was assigned 10.8.0.6. 
 
I am not sure if this is a firewall issue, a routing issue or iptables.
 
My current routing looks like this: 
 
/sbin/route -n
 
jason@xxxxxxx:/var/log$ sudo /sbin/route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
10.8.0.2 0.0.0.0 255.255.255.255 UH 0 0 0 tun0
192.168.2.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
10.8.0.0 10.8.0.2 255.255.255.0 UG 0 0 0 tun0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
0.0.0.0 192.168.2.1 0.0.0.0 UG 100 0 0 eth0
 
I am trying to ping 192.168.2.102 but am not getting a response through VPN (tun0).
 
Any suggestions would be greatly appreciated!

---


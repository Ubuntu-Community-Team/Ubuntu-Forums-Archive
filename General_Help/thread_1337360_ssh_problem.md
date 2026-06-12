---
title: "ssh problem"
date: 2009-11-25
forum: General Help
---

### Post by r_s on 2009-11-25
hi , I am unable to connect to another machine using ssh
ssh kartik@172.17.11.252
it gives an error ssh: connect to host 172.17.11.252 port 22: Connection refused
 when I ping , it works fine
PING 172.17.11.252 (172.17.11.252) 56(84) bytes of data.
64 bytes from 172.17.11.252: icmp_seq=1 ttl=64 time=0.428 ms
64 bytes from 172.17.11.252: icmp_seq=2 ttl=64 time=0.629 ms
64 bytes from 172.17.11.252: icmp_seq=3 ttl=64 time=0.389 ms
64 bytes from 172.17.11.252: icmp_seq=4 ttl=64 time=0.461 ms
64 bytes from 172.17.11.252: icmp_seq=5 ttl=64 time=0.524 ms
64 bytes from 172.17.11.252: icmp_seq=6 ttl=64 time=0.613 ms
64 bytes from 172.17.11.252: icmp_seq=7 ttl=64 time=0.497 ms

ssh is working fine for some other servers like 192.168.36.205 and sshd is also running
Please help

---

### Post by sedawk on 2009-11-25
Well, "connection refused" normally means that sshd is not
running on the target machine, here 172.17.11.252

If "ssh localhost" works on 172.17.11.252 there might
be something else causing trouble, e.g. a firewall.

---

### Post by r_s on 2009-11-25
yeah thanks ...problem solved, ssh wasn't working on that machine[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by bayvista on 2009-12-07
After upgrading to Karmic 9,10, I could not get SSH to work. Problem solved. SSH is not installed automatically - you have to install it yourself with Synaptic or APT-get.

---


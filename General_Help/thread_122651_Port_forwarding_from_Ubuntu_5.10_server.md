---
title: "Port forwarding from Ubuntu 5.10 server"
date: 2006-01-28
forum: General Help
---

### Post by czk101 on 2006-01-28
Hi all

I recently set up a server in my house using Ubuntu 5.10. I've installed 2 network cards in it and im trying to get portforwarding working, but as im new to linux im not sure if what im doing is right.

Basically I want to be able to FTP, telnet and http from my laptop to my cable tv box via my linux server, so that i can route the tv to my laptop.

My laptop and the eth0 nic on the server are connected to my router, which is connected to the internet. I can ping from one to the other no problem, so  they're connected fine. The ip's on my server are as follows
eth0 ip:192.168.62.100
gateway:192.168.62.1

eth1 ip:192.168.2.1
gw:192.168.1.1

and my cable box is connected to eth1, my cable box details are
ip:192.168.2.2
gw:192.168.2.1

I can ping the cable box from my server, and vice versa, so i know that they're talking too. Ive tried to write script that enables direct communication from my laptop to the box, but so far ive had no luck. Can anyone help?

Cheers in advance

czk

---


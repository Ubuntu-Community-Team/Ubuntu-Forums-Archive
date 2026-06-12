---
title: "ssh to connect to a remote computer behind a router"
date: 2010-01-30
forum: General Help
---

### Post by PauGNU on 2010-01-30
Hi all,

First of all, I want to show you this scheme:

MyPC -> router -> internet <- router <- Mom'spc

I want to connect from my pc to my mom's pc using ssh. The first router doesn't represent a problem, but my mom's router does. Our IPs are both dynamic (anyway, I can easyly know them) and I have opened the port (TCP/UDP) 2100 on the router in order to open a gateway on mom's pc.

The firewall is not enabled on the router, nor on mom's pc. 

Granted all this, now I should be able to connect to that computer using ssh:

ssh user@ip -p 2100

But I can't, I always get a "connection refused". By the way, if I do it on my intranet, I can connect without any problem (to others computers, of course, not mom's).

What's the reason because I always get a connection refused?

Thanks for your help

---

### Post by pbrane on 2010-01-30
I connect to a server like this every day. Are you sure that your mom's PC is running an ssh **server** What OS is running on your mom's PC? The command line you are using is correct. Also the ssh server has to be listening on port 2100. That is not the default sshd port. All you need to open for ssh is TCP, you should not need UDP open on the ssh port. You really should enable the router firewall and only open the ports you need.

---


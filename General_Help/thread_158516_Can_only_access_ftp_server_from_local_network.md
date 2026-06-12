---
title: "Can only access ftp server from local network"
date: 2006-04-11
forum: General Help
---

### Post by illiterate_light on 2006-04-11
I just set up a new install of Ubuntu 5.10, and set up proftpd as an ftp server.  I'm hoping this is a simple problem -- after getting everything set up, I can do everything I need to do on the ftp server from the local network (192.168.0.*), but when I log in from outside the network, I am able to log into the ftp server, but when I try to list a directory, it times out.  I have port forwarding set up on my router, tried messing with hosts.allow and iptables, but I'm pretty much groping in the dark and have made no progress.  Any ideas?

Thanks for any help

---

### Post by rvergara on 2006-04-11
I assume you are port forwarding just port 21. If this is the case, port forward port 20 and 21 and try again.

Ramiro

---

### Post by illiterate_light on 2006-04-11
[QUOTE=rvergara]I assume you are port forwarding just port 21. If this is the case, port forward port 20 and 21 and try again.[/QUOTE]

I'm using port 777.  I just tried changing the forwarding rule so it forwards 776 and 777, but that didn't solve the problem.

I've also noticed that I can do other simple commands, like pwd, del, and cd, but I can't list directory contents from outside the network.  Inside the network, I can do any of these things.

---

### Post by rvergara on 2006-04-11
I use vsftp so I am not sure how to configure proftp.

FTP uses 2 ports, one for control the other for data (hence ports 20 and 21 when you use the default ports). Check and see in your config files which port is which.

I hope this helps

Ramiro

---

### Post by illiterate_light on 2006-04-11
Somehow after changing the port to 21 and then back to 777, everything works now.    Who knows.  Anyway thanks for the tips.

---


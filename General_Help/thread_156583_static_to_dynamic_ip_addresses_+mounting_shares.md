---
title: "static to dynamic ip addresses +mounting shares"
date: 2006-04-07
forum: General Help
---

### Post by damianubuntu on 2006-04-07
Hi,
I have a network of four machines running ubuntu with static ip addresses.  One used to connect to the internet through a modem and then act as gateway.  Now I have a router/switch and have had to change all the ip addresses to dynamic.
BUT my mounted shares through NFS rely on static ip addresses.  Any suggestions?  Thanks

---

### Post by neoroses on 2006-04-07
if i follow you correctly then you want to set up a connection with a static ip?..if so...go to system --> admin --->networking --> then click your connection and then  properties --> change DHCP to static and put in the info =)

---

### Post by damianubuntu on 2006-04-07
Not exactly!  I know how to set it up as static/dhcp, the problem is that the router needs dynamic ip addresses, but NFS file shares needs static ip addresses.
(as far as I know, anyway)

---


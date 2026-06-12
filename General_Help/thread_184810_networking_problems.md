---
title: "networking problems"
date: 2006-05-30
forum: General Help
---

### Post by ilw on 2006-05-30
Hi,
The basic problem is that sometimes i can't ping my laptop (with ubuntu on) from other computers or the router, and sometimes i can. There doesn't seem to be any rhyme or reason as to why it only works sometimes.

My network is a wireless infrastructure one with a WRT54g router (running hyperwrt) as the Access Point. I've recently installed Breezy on my laptop and most things are working fine, however, i was having problems with samba and ssh to an xp machine on the network so i'd been doing all sorts of tests and getting really inconsistent and confusing results. 

I can connect to the internet ok from the laptop, but it is slower than other computers on the network. While fiddling with stuff to get samba working i could sometimes ping the linux box from xp and sometimes couldn't, I figured at first it was because of the stuff i was changing, but eventually i stopped changing stuff and the problem kept on coming and going. I checked from the diagnostics that are available on the router and it has the same intermittent problem, i.e. the router can only sometimes ping my laptop. Pings between the xp machine and router are completely fine

I can ping the router and xp machine fine from the linux box, but I noticed that every 10th ping to hte xp machine has a much higher value (ie most are 1- 2 ms, but every 10th one is >80ms

I don't think the problem is signal strength as its connecting at 36Mb/s, I'm thinking its either my ubuntu setup or some weird incompatibility with hyperwrt. Just for background info the xp machine and laptop both have static ip addresses.  

Sorry about the haphazard order of information, I couldn't think of a good way to put it all... Any help gratefully appreciated as its doing my head in.

---

### Post by Jussi Kukkonen on 2006-05-30
*dmesg* might tell you something, if it is a wireless driver failure or something...

---


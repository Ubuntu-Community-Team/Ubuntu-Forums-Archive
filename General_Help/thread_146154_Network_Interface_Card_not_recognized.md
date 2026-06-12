---
title: "Network Interface Card not recognized"
date: 2006-03-17
forum: General Help
---

### Post by dbpigeon on 2006-03-17
I've tried the liveCD and my ethernet NIC card isn't recognized by Ubuntu 5.10, or the Kororaa liveCD I tried. I think its an Intel 1000 PL, but I'm not positive (I'll check when I get home, in about 30 mins.) During liveCD setup, I use the regular boot, and I get a message about firewire ethernet. I've tried yes and no, but it didn't work either way. Only my 56k modem was listed (for my DSL I have an external modem and a router) in the network config thing. (can't remember what its called.) Any advice? :confused:

---

### Post by Steve1961 on 2006-03-18
[QUOTE=dbpigeon]I've tried the liveCD and my ethernet NIC card isn't recognized by Ubuntu 5.10, or the Kororaa liveCD I tried. I think its an Intel 1000 PL, but I'm not positive (I'll check when I get home, in about 30 mins.) During liveCD setup, I use the regular boot, and I get a message about firewire ethernet. I've tried yes and no, but it didn't work either way. Only my 56k modem was listed (for my DSL I have an external modem and a router) in the network config thing. (can't remember what its called.) Any advice? :confused:[/QUOTE]


Open a terminal and type lspci -v.  In the output your NIC should be listed, along with full details about the make, version, etc..  Once you have the full details search this forum to see if anyone else has managed to get the same NIC working.

---

### Post by dbpigeon on 2006-03-18
OK, thanks. I'll try and get this working.

---


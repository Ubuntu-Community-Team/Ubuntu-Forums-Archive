---
title: "Problem accessing network folders with dolphin"
date: 2009-11-08
forum: General Help
---

### Post by diggedy on 2009-11-08
Im trying to access some network folders on my NAS but with dolphin it wont work. It sees the NAS but tries to use the services ie. media server, it doesnt actually allow me to see actual folders on there.
I used to use gnome and nautilus handled this fine but ive tried to install nautilus on kubuntu and all I get is "nautilus cannot handle "network" locations when trying to browse my network with it

Anyone any ideas on how to remedy either fault?

---

### Post by diggedy on 2009-11-09
anyone?

---

### Post by Maikun on 2009-11-19
Well, I have a similar problem with dolphin. If I click on the network button on the shortcuts panel, I see the 3 posibilities: Samba, network and another for zeroconf.

I have two computers connected to a router, and if I click on network(network:/) I see the two computers. If I click on any of them (network:/<computername>.local where <computername> is the name of the computer), I see an the globe net icon, and if I click on it (network:/<computername>.local/<computername>[00:1e:8c:fc:cb:d9].workstation

I get an error: "File or folder network:/<computername>.local/<computername>[00:1e:8c:fc:cb:d9].workstation
doesn't exist.

The same happens with samba and zeroconf, so there must be some bug there.

---


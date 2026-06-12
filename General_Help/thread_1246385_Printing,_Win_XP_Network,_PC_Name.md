---
title: "Printing, Win XP Network, PC Name"
date: 2009-08-21
forum: General Help
---

### Post by Nugar on 2009-08-21
Hi all,

Apologies if this is no the right forum for this question.

I have a home network. A few months ago I migrated my box to Ubuntu (8.10, now 9.04). I have two other PCs.

All are interconnected thru a Linksys router (also with wireless). It assigns IPs via DHCP.

My son's PC, which runs Win XP, has the printer attached to it.

I can print, no problem.

But what I've been unable to do is defining that box by name on my box. That machine is named "KIDS", but I can't connect to it that way. My box can browse to it, and see the workgroup and machine name, but can't see the printer.

On the other hand, if I use: smb://the_IP_numer_here/R200 I can print with no problems. The problem is that the IP is dynamic, so each time I want to print, i have to launch the Linksys control panel (actually dd-wrt's) and find out what the IP is.

How can I make Ubuntu recognize that XP box by using its name instead of the IP?

Thanks in advance,

---

### Post by starcraft.man on 2009-08-21
An alternate but in my opinion preferred solution is simply to hand out fixed IPs on the internal network, thus each machine has a permanent identifier. Since you've a router from linksys (with nice ddwrt firmware), it's fairly trivial. Log in and go to networking options, search for a page with dhcp reservation listed somewhere. Should allow ya to pick your machines from a list (indicating their MAC addresses) and from there, assign them a permanent IP.

I can get further instructions if you need, but it shouldn't be hard to track down.

---

### Post by Nugar on 2009-08-21
Aha!

That's what I was looking for. 

So if I understand you correctly, I can have, in the same network, both PCs with fixed IPs and PCs wth DHCP assigned IPs, am I reading you correctly?

Cheers,

---


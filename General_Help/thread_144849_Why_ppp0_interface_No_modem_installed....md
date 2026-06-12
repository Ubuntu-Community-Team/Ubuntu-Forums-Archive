---
title: "Why ppp0 interface? No modem installed..."
date: 2006-03-15
forum: General Help
---

### Post by hajk on 2006-03-15
I notice after some recent upgrades that the System --> Administration --> Networking menu shows a (non-configured) ppp0 dial-up interface, in addition to the configured/activated eth0 interface. I wonder where this comes from -- it wasn't there before, there's no modem installed on my computer, and there's no mention of ppp0 in /etc/network/interfaces. 

Synaptic shows that various ppp-related packages are part of the standard installation -- trying to remove them will also remove the ubuntu-desktop package, so I don't want to do that.  

Strange...

---

### Post by Dominus Suus on 2006-03-17
What's your Internet connection?  If you use PPPoE, which labels its connections ppp#, that could explain.

For kicks, you could try configuring your non-existent modem and see what happens when you direct output to it ;)

---

### Post by hajk on 2006-03-17
Yes, I tried that, but then it stops on not being able to autodetect a device -- and there isn't one, of course. No, my box is connected to a router, which is in turn using PPPoA to connect to my ISP. It's very strange... Mind you, its presence  doesn't hurt either.

---


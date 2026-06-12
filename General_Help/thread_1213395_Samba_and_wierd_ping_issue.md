---
title: "Samba and wierd ping issue"
date: 2009-07-14
forum: General Help
---

### Post by bobtown on 2009-07-14
I have been trying to set up drive sharing over my wireless network and during the debugging process I've found something which I'm not sure is connected to Samba issues I am having.  I have two Ubuntu 9.04 desktops running and both are successfully connected to the internet through my wireless router.  I've tried to set up my workgroup, but they can't see each other.  So I go to network tools and try pinging machine 1 from machine 2.  Nothing.  Then I attempt to ping machine 2 from machine 1 and they both start working.  I can then continue to ping machine 1 but if I stop and remain idle for a few minutes, I don't get a response if I begin pinging again.  I see the same problem with port scanning.  It's not a connection issue since I can browse the Internet on machine 1 and still get no ping response on machine 2.  I double checked and made sure that WAN pinging was enabled on my router.

Since I can't even successfully ping or do a port scan on the machine, I'm not suprised I can't share folders.  Anyone have any ideas what might be the cause of this?

---


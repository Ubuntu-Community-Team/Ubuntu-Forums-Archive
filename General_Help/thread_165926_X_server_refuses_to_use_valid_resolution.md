---
title: "X server refuses to use valid resolution"
date: 2006-04-25
forum: General Help
---

### Post by Valhalla on 2006-04-25
I'm trying to install ubuntu on my roommates old Thinkpad.  It is up and running, but the system specs claim the monitor can handle 800x600 at 16bits.  I've even got the framebuffer running at 1024x768-16bit.  However, the x server keeps falling back to 600x400.  The xorg.0.log contains lots of removing of modes.  The relevant sections is 
NEOMAGIC(0): Not using Default Mode "800x600" (Unknown Reason).

If anyone could give me any ideas that would be great.

---

### Post by Hephaistos on 2006-04-27
what is your graphic card? Some kind of intel? If so, trash the computer, go to some store, buy a new computer: That will save years, and at the end it will work properly.

(I had so much trouble with my laptop......... I got angry and just killed it. RIP)

---

### Post by Jason_25 on 2006-04-27
Yeah it could be that bad, laptops suck.  Anyway, if you want help post your xorg.conf and your full Xorg.0.log.

---


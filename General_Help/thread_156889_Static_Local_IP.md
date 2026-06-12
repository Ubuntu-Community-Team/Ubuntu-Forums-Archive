---
title: "Static Local IP?"
date: 2006-04-08
forum: General Help
---

### Post by Griff on 2006-04-08
My router (a linksys) is driving me nuts.  I can handle the random assignment of a local IP during bootup, but changing during the middle of a session?  I always have a ftp server running in the background and I love Azureus.  The FTP server is completely unreachable (obviously) and Azureus doesn't operate at full capacity when the local IP changes.  Having to constantly go in the router to change forwarding options is annoying at the very least.

1. Anyone know what causes this IP to change?  I know one of my roomates turn their comp on and off every time they sit down or leave the room. (I cannot break them of this habit)

2. Is there a way to assign this PC one local IP so on every boot it has the same IP?

3. I found a good Bleach wallscroll that I like a lot.  Is $14 a good price?

Thanks,
Griff

---

### Post by eriefisher on 2006-04-08
In System>>Administration>>Networking you can change from DHCP to static ip address. I think this what you want.

eriefisher

---

### Post by bionnaki on 2006-04-08
you need to set up a static IP.
follow these instructions: [http://www.portforward.com/networking/static-xp.htm](http://www.portforward.com/networking/static-xp.htm)

instead of ipconfig /all
type ifconfig
and then enter the info into networking where eriefisher described
before to forward the proper ports to the proper static ip in your router (see that link for your router)

---

### Post by Griff on 2006-04-08
Awesome! That's exactly what I needed.  Thanks for the quick replys.
:KS :KS 

Griff

---


---
title: "Rootless Xnest/Xephyr equivalent  on Ubuntu"
date: 2009-10-23
forum: General Help
---

### Post by nerdopolis on 2009-10-23
Xming and Cygwin/X can both run rootless (where the guest X server's windows integrate with the current desktop, not as in  an entire real x.org not running as root).

The problem is, is that they are both targeted for Win32 based systems. I dont know if there is any equivalent available for Linux systems, or if Xephyr/Xnest have the ability to do this with an argument. 

Is there any way to do this on Ubuntu?

---

### Post by nerdopolis on 2009-10-24
Wait. I found one. its called xpra

[http://xpra.devloop.org.uk/](http://xpra.devloop.org.uk/)

It runs in two processes, one is the X server from xpra, and one is the forwarder for the rootless display onto your xserver. so if your X.org goes down because of a driver, and you have xpra in display :1, any program using display :1, stays up! (you just need to start the fowarder again to see the apps)

(and yes, the forwarded windows do get compositing. )

EDIT: the windows get compositing applied to them, where they can appear on the cube, and wobble, but the programs running on the display aren't aware of it, so setting the terminal transparency won't work.

---


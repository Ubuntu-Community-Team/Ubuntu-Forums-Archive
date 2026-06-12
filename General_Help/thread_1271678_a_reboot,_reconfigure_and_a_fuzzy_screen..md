---
title: "a reboot, reconfigure and a fuzzy screen."
date: 2009-09-21
forum: General Help
---

### Post by sideaway on 2009-09-21
Ok, I have no idea what I've done here but it's not nice :P

I restarted to play a few games on windows. Which was fine, but upon my return I was greeted with this screen...

[[img]http://img21.imageshack.us/img21/5081/img1842di.jpg[/img]](http://img21.imageshack.us/i/img1842di.jpg/)

I've done an automatic fix via the recovery mode, and I'm now posting to this forum via a live CD. I tried to drop to terminal but I hadn't setup a root password...

Crap, I will be very thankful if anyone can help!

---

### Post by sideaway on 2009-09-21
Bump,


I tried booting with parameters;
init=/bin/bash

dropping me straight to a terminal then

su hamish (which is my username)

I then have the bash terminal looking like
hamish@(none):/$ _

I get no password prompt?
anyway I try;

sudo mount / -o remount,rw

But sudo cannot resolve host (none)

I reboot by holding down alt press sysrq, r, e, i, s, u, b
The old (Reboot Even If System Utterly Broken)

---

### Post by sideaway on 2009-09-21
Ok, I can now successfully get a usable shell... By just adding 'text as a parameter, bah, all that stuffing around with init=/bin/bash for nothing! *sigh*

So in the shell I tried ```
sudo dpkg-reconfigure xserver-xorg
``` But the problem's still exactly the same... should I reinstall gdm or something? I'm really at a loss here guys! Any ideas appreciated :)

---

### Post by sideaway on 2009-09-21
Yuss! "Houston, we have a desktop"

removed fglrx.... I'm going for a reinstall now... brb, hope it doesn't break the system!

Well, thanks to everyone who viewed :P

---


---
title: "All x-buntus are laggy"
date: 2011-05-13
forum: General Help
---

### Post by Naike on 2011-05-13
I've tried Kubuntu and Ubuntu, and while KDE runs much better, it still is a bit laggy.
On GNOME, all animations would be laggy, in a weird way, it is like that fps would drop every 0.5 sec for some time and then continue, choppy and not really smooth. The big problem was however that when I moved a window or so, it wouldn't follow my cursor at all, but would rather update its position like once per second, very laggy, and after installing the compiz settings thing, I tried fiddling around with the settings (also with the OpenGL settings), but that made it worse, and the top bar was just full with artifacts.

When I tried KDE, everything was smoother, but I still have that "micro-lag" with animations, or stuff like scrolling in firefox, it's a bit choppy and it's not smooth like it's supposed to be.

Here are my system specs:
M4A89GTD Pro/USB3 (**890GX chipset**)
Ati HD 5870 (**I installed the fglrx drivers**)
Phenom 2 x4 965BE

The rest shouldn't be of any concern, everything is running at stock speed by the way.

Any help?

---

### Post by 3602 on 2011-05-13
Well you have powerful chips, so that's not a problem.
How are your video drivers? Did you install any through Jockey?

---

### Post by lithopsian on 2011-05-13
Check your hardware acceleration is working.  Sounds like it might not be.

---

### Post by Naike on 2011-05-13
Hey, I'm new to Ubuntu, because my hardware hasn't been fully supported since I first tried it in 2006 or so.
First time I tried my on board LAN card wasn't supported, on this new system I have these current problems.

Anyway, what is Jockey? And how do I check if hardware acceleration is turned on, and where can I turn it on for that matter?
I installed the fglrx drivers through the packet manager.

---

### Post by 3602 on 2011-05-13
"Jockey" is the "Additional Drivers" option found in System - Administration. Or does Unity not have that?
Else you may try installing the fglrx yourself. It is a bit complicated and you may end up without a GUI. I shall provide full details including commands for every step if you request so.

---

### Post by Naike on 2011-05-13
Ah, yeah it appeared in jockey, and it installed fine, and the catalyst control center installed fine too.

But it all just seems choppy, it's also choppy before installing any drivers.

Edit: Just installed ubuntu again for the *n*th time, and still the same.
I have no problems when I'm installing (when I choose install to hard disk), there I can move the installer window, and firefox (by opening a link in the "features" thing while installing) without any lag.
This is really annoying :(

---

### Post by Naike on 2011-05-14
a little bump

Edit: A good example is the firefox loading circle when loading pages.
It will roll, and then speed up/slow down every 1-2 seconds and thus looks choppy.

It's like the whole desktop environment is laggy, except my mouse.

---

### Post by 3602 on 2011-05-14
Interesting... that little circle needs no hardware acceleration to turn. I've ran Maverick without any video drivers before and while I had no OpenGL, I noticed no circle-lagging.
Uh... BIOS? If everything is fine during the live installation process then...

---

### Post by Naike on 2011-05-14
> **3602 said:**
> Interesting... that little circle needs no hardware acceleration to turn. I've ran Maverick without any video drivers before and while I had no OpenGL, I noticed no circle-lagging.
Uh... BIOS? If everything is fine during the live installation process then...

Also in Kubuntu 11.04, the start menu transition animation when switching the bottom tab, is laggy, and is not smooth like in 10.04.
I'm currently using mint 10.04 with GNOMe without problems, I would use Ubuntu 10.04, but it doesn't seem to work with my hardware either, I just get a black screen when I live boot...

---


---
title: "Severe issue...RandR not recognizing my monitor properly!!!"
date: 2009-12-15
forum: General Help
---

### Post by r2rX on 2009-12-15
Greetz guys,

I've been experimenting and trying to get my resolution (of 1600x1200) working at 100Hz (as it's capped at 85Hz).....in the process, and not knowing exactly what or why it happened, RandR (or xrandr) is not detecting my screen properly.

Prior to this incident, it recognized my screen as a Compaq 22", ranging from 320x240 up to 2048x1536.........now amongst the resolutions, it'd display above 60Hz, but not at their peak (i.e. 1600x1200 should work at 100Hz, but capped at 85Hz)...

But now, it recognizes my screen as XXX 22", and can only go up to 1024x768 with either 43Hz or 60Hz.

Now, i'm using the ATi Catalsyt 9.11 drivers, and those seem to be working well so far.

So how do I reset RandR (xrandr) to recognize my monitor, and all the resolutions (and preferably refresh rates) properly?

If I can't figure this out, i'm gonna have to reinstall Ubuntu...which'd suck. :p

IMPORTANT: In the process of experimenting, everything I did had to do with either manually configuring my xorg.conf and/or using the *aticonfig* commands of the ATi drivers. I'd manually specified my monitor, through aticonfig, and reset. Since then, it's been messed. Even after trying to revert the aticonfig command lines I used, and refering to a prior xorg.conf, it still doesn't work......I'm pretty sure it's something to do with RandR and something that was changed.

Any way to reset/reconfigure/re-initialize RandR (or something to that effect, so it can read my screen properly again)?

Currently using Ubuntu 9.10.....all the help is appreciated.

r2rX  :D

---

### Post by r2rX on 2009-12-16
BUMP!!!

Please someone help me!!!

r2rX  :D

---

### Post by jdkchem on 2009-12-16
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by r2rX on 2010-01-01
Thanks for the reply. Although. i'm not quite sure how to proceed from here. :)

Edit: Alright, i've done some research on this and, apparently, there's a gui that's supposed to pop up....but nothing happens.....hmm...

r2rX  :D

---


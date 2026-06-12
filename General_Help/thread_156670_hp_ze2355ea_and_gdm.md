---
title: "hp ze2355ea and gdm"
date: 2006-04-07
forum: General Help
---

### Post by alfiejs on 2006-04-07
I have just gone to all the trouble of repartitioning my laptop's hard drive, and installing ubuntu using 64bit pc edition.  But unfortunately after installation it fails to load the gdm due to x server error saying it can't load.  The exact error message escapes right now, but all i can do is use the text only version, which isn't what i wanted.  Please help me to find the answer to my woes.

---

### Post by nanotube on 2006-04-07
from commandline, try the following:
```
sudo nano /etc/X11/xorg.conf
```
edit the line that looks like
```
Device "ati"
```
(instead of ati it could have something else)
and make it look like
```
Device "vesa"
```
save the file, then reboot and see if X starts.
if it does - great. :) just note that with vesa you will not have 3d acceleration... but it will be a lot nicer to be trying to get the correct video driver once you have a gui, than if you only have the commandline. 
which video card do you have, btw?

---

### Post by alfiejs on 2006-04-08
It's an ATI Radeon Xpress 200M.  Onboard card with shared memory.

---

### Post by alfiejs on 2006-04-08
Cheers, I'm logged in and running in glorious graphics.  Now to make it pretty.

---

### Post by nanotube on 2006-04-08
cool :)

---


---
title: "System hangs if no user input.. resumes if mouse moves"
date: 2010-01-19
forum: General Help
---

### Post by Vestal on 2010-01-19
Basically when installing Ubuntu on my Laptop i am getting this weird problem. Using both the Live CD and once installed if I am not moving the mouse cursor around or doing any type of input after about 10-15 seconds the system Hangs, however if I do some sort of input everything starts running again. I noticed it first when using Gparted from the Live CD, I assumed that once I installed it would resolve itself, however doing the software updates the same problem occurs.

Hardware specs:
Sager NP5793
PM965 motherboard
T9300 processor
Geforce GTX 8800m
4 gigs of Ram

Ubuntu 9.10 64bit


Any help would be appreciated.

---

### Post by Vestal on 2010-01-19
Anyone? I hate bumping but this issue is really ticking me off.. I am assuming it might have something to do with powermanagement but really not sure at all.

---

### Post by Cori on 2010-08-15
Same thing happens here since last year.  I've shied away from Ubuntu because of the issue, but I'm back (other distro is getting on my nerves, too).

No one has any solutions yet?  :(

---

### Post by Vestal on 2010-08-16
Yeah i did find a solution for this.. It has to do with the power management in the OS relating to CPU cycles. 

I basically did the following..

In terminal type 
```
sudo gedit /etc/default/grub
```

Add the following line

```
GRUB_CMDLINE_LINUX="nohz=off"
```

Then run 

```
sudo update-grub
```
This will update grub to include that switch when booting up. Restart and you should no longer see the problem.

---

### Post by Cori on 2010-08-16
Thanks a bunch!  Now my thumb won't fall asleep from moving the trackball every 10 seconds or so. :D

---

### Post by Vestal on 2010-08-16
> **Cori said:**
> Thanks a bunch!  Now my thumb won't fall asleep from moving the trackball every 10 seconds or so. :D

Almost forgot this pertains to Ubuntu 10.04lts since that method is for Grub2.. For previous grub the edit would be in the menu.lst for grub.

---


---
title: "Motionless mouse"
date: 2011-01-11
forum: General Help
---

### Post by aeh on 2011-01-11
I have just installed U 10.10 on a desktop machine. On startup, when the mouse pointer becomes visible, it doesn't react to mouse movements, nor is the red light under the mouse illuminated. After about 20-30 seconds, the mouse starts to work normally. Any ideas?

Cheers

BTW the machine has a Geforce 8800 card with proprietary drivers

---

### Post by dcstar on 2011-01-12
> **aeh said:**
> I have just installed U 10.10 on a desktop machine. On startup, when the mouse pointer becomes visible, it doesn't react to mouse movements, nor is the red light under the mouse illuminated. After about 20-30 seconds, the mouse starts to work normally. Any ideas?


Enable the USB mouse in the BIOS.

---

### Post by aeh on 2011-01-12
Thanks, but the legacy USB support was already on auto, I changed it to enable, no difference though

A

---

### Post by Tiit_Helimut on 2011-01-13
*Bump*

Having the same problem, only since I updated to the latest kernel (2.6.35-24) have I been getting this. I'm using 64-bit Ubuntu if that helps!


Any ideas would be appreciated!

---

### Post by aeh on 2011-01-14
I don't have this problem on my laptop or my other desktop machine....

---

### Post by Tiit_Helimut on 2011-01-14
It doesn't affect my laptop either so yeah, I assume it is a hardware problem/conflict. I'd post up my PC's hardware but I'm not sure how to generate a full list in Linux (due to being a newbie)...

Either the next update fixes it (which I'm hoping as it's irritating) or someone might pipe up and help us!

---

### Post by aeh on 2011-01-14
Tiit_Helimut, does your Rhythmbox music player work? Mine doesn't...

---

### Post by Tiit_Helimut on 2011-01-17
I'm afraid that my Rhythmbox does work and has done ever since I installed Ubuntu!

---

### Post by Tiit_Helimut on 2011-01-22
I appear to have fixed the problem. My motherboard has three sets of USB ports. It turns out that for some reason, Ubuntu initialises only _one_ set of USB ports on boot, then once it has loaded, after a while it loads the others. I'm not sure why it would do this but this is what's going on from what I can see.

I have plugged my mouse into the "first" set of USB ports and it now works at the login screen, so if you have the same trouble - try every port possible on bootup. If that doesn't work then I'm not sure what to try.

What puzzles me is why the latest update suddenly has this problem on a very small number of systems...

---

### Post by aeh on 2011-01-23
Well I have sort of resolved the problem: turn the power off (really off, power cord out) and then back on and the system boots normally, mouse works as well as Rhythmbox and Shotwell which do not grey out. It has everything to do with which USB device is connected to which port.
See thread [http://ubuntuforums.org/showthread.php?t=1610142](http://ubuntuforums.org/showthread.php?t=1610142)
A

---

### Post by aeh on 2011-02-02
It seems to have been a faulty USB card reader that caused the problem: new card reader and everything works.

---


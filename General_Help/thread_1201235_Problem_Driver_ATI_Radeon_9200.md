---
title: "Problem Driver ATI Radeon 9200"
date: 2009-06-30
forum: General Help
---

### Post by Mazerzinho on 2009-06-30
Hello people!
I have a problem, my ATI Radeon 9200 not install in Ubunto 9.04...
I don't know what to do for install this driver...
I am brazillian and the forums in Brazil nobody know say how install, for me this is a big problem, because, i used some programs for my work!
=(
I hope someone help me, or show me one solution!
Thanks!
Peace for all!
PS: Sorry by my english, not is the best, but you understand!
;)

---

### Post by mad_squirrel on 2009-06-30
Hello, Mazerzinho.
The first thing you should do is to check if xorg-driver-fglrx package is installed. To activate the driver go to **System->Administration->Hardware Drivers** and check if ATI driver is activated. if not, activate it and restart X server(log out - log in).
If this does not help, try following this HowTo:
[http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557)

Hope it helps,
Mike
P.S. Sorry for my English.

---

### Post by 3rdalbum on 2009-06-30
The ATI proprietary driver (fglrx) no longer supports the ATI Radeon 9200. You also cannot use an old version of the proprietary driver on Ubuntu 9.04.

As I understand it, there is open-source 3D acceleration support for this graphics card which should already be in use on your system.

What problems are you having that have led you to ask about the ATI proprietary driver?

---

### Post by linuxmagick on 2009-06-30
AMD/ATI has recently retired many of its graphics cards so the fglrx driver may not be available for your card any longer.  If that's the case, then you can follow the instructions in the following link to set up the open source drivers.  

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver")

The steps under the heading "Problem: Need to fully remove -fglrx and reinstall -ati from scratch" should work for you.

---

### Post by Mazerzinho on 2009-07-01
Inside of System->Administration->Hardware Drivers does not appear the option for my driver! For me this a problem, example, I installed Roller Coaster Tycoon Deluxe (Number 1 version) required 4mb of card video, but was how lag! Emulation by wine! I tried various methods and not the right!
Thank you!
Peace for All!

---

### Post by mad_squirrel on 2009-07-01
Maybe you should try open source drivers for your video card?
For example radeon(xserver-xorg-video-radeon)
P.S. You will have to install ati wrapper too(xserver-xorg-video-ati)

---


---
title: "failsafe terminal to install nVidia driver"
date: 2010-03-04
forum: General Help
---

### Post by danaur on 2010-03-04
Hi, 

my new laptop (ASUS N71Jv) refuses to install Ubuntu 9.10 - it just produces a black screen. I finally managed to get it on there somehow by installing it in safe graphics mode, so now I have to stare at 1024x768. NVIDIA has a new driver (195.36.08) available that may support my graphics card. When I try to install the executable nVidia driver from a terminal, it rightfully complains that X server is still active. Ctrl-alt-f1 or  sudo /etc/init.d/gdm stop produce a black screen and a frozen cursor, /sbin/init 3 does nothing. 

So what I want to do is simply install the nvidia driver while not being in gnome. 

I suspect that my xorg.conf file does not allow anything but 1024x768 (safe graphics mode). It's very frustrating. Any ideas how I can install the driver while being in simple failsafe command line mode or something? 

Thanks,
danaur

---

### Post by linuxman94 on 2010-03-04
1. Boot to recovery mode

2. Select "root" and press enter.

That will give you a root prompt.  Be careful because if you make a typo, you could screw up your computer.

---

### Post by danaur on 2010-03-04
Oh, I forgot, recovery mode stops eventually at a blank screen too. Anything I can enter in grub to force a basic command line mode? 

This new nvidia chipset is driving me bananas. Never had Ubuntu install problems like this before.

Thanks.

---

### Post by linuxman94 on 2010-03-04
Did you try an older kernal?

---


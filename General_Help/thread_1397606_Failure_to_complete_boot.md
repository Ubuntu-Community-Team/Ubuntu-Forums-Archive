---
title: "Failure to complete boot"
date: 2010-02-03
forum: General Help
---

### Post by sideaway on 2010-02-03
Hey there, whenever I try and boot the computer begins to load correctly, but after the scrolling ubuntu splash, I just get a black screen. Can anyone help?

64bit Ubuntu 9.10

Cheers,
Sideaway

---

### Post by n0dix on 2010-02-03
Which is the version of your kernel? what driver do you use? Give some specifications of hardware. Post your menu.lst, please.

---

### Post by sideaway on 2010-02-03
Harware is in sig.

e8400, gigabyte p35-DS3R, HD4870 with fglrx drivers will brb with kernel version (although I've got four backed up, and have used each one with same results) and will post menu.lst :) Is it different for Grub 2?

---

### Post by sideaway on 2010-02-03
Ok, kernel version is 2.6.31-17

---

### Post by sideaway on 2010-02-03
Aaaaand apparently Grub2 doesn't have a menu.lst?

---

### Post by sideaway on 2010-02-03
shamless bump! :)

---

### Post by sideaway on 2010-02-04
Ok, for some reason, it was the xorg.conf, but dpkg-reconfigure xserver-xorg wouldn't run, so in the interest of those in the same situation;
I booted a recovery kernel and dropped to a root console with networking, and installed VIM with apt-get install vim. No need for sudo as in a root shell.

I then edited the xorg.conf file with vim /etc/x11/xorg.conf

I changed the resolution from my native, to 800x600, so the value read "800x600_60.00" I then used the command ':w' to write to file. then ':qa' to quit vim. Then rebooted with reboot -n, and voila, It booted back to my desktop with the correct resolution and everything.

---


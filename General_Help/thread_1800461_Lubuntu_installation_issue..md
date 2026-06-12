---
title: "Lubuntu installation issue."
date: 2011-07-09
forum: General Help
---

### Post by vanity_and_veins on 2011-07-09
Please excuse me if this is posted on the wrong board or with the wrong prefix. 

I'm quite new to Linux in general, I've only been using it about a year, so I'm trying to teach myself. 

I'm trying to install Lubuntu on a desk top computer. I've downloaded the ISO file, burnt it to a CD and booted my computer back up with the installation disk and this is what comes up once the computer is booted with the disk:

ISOLINUX 4.02 debian-20101016 ETCD Copy right (C) 1994-2010 H. Peter Anvin et al

Unknown keywordin configuration file: --
No default or UI configuration directive found!

boot: _



I've never seen this screen before and I'm not sure where to go from here. 

Any help or insight is greatly appreciated! I thank you for your time.  :)

---

### Post by Rubi1200 on 2011-07-09
Hi and welcome to the forums :)

First check the integrity of the ISO:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the computer allows booting from a USB, use UNetbootin to create a bootable USB stick and try it that way:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

If not, then burn the image to CD at the lowest possible speed.

Make sure BIOS settings are okay (sometimes we forget ;))

Let me know if this helps.

---


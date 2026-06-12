---
title: "Hard drive failure + pendrive Linux"
date: 2012-07-24
forum: General Help
---

### Post by Insuffi on 2012-07-24
Hello there.

Today I got the dreaded IMMINENT HARD DRIVE FAILURE message on Windows. First, I thought perhaps it is some worm on my Windows(i'd been running anti virus less for some time), I'm sure you've heard of some like those running around proclaiming that the hard drive is going to fail, so you need to restart your computer.

I switched to Ubuntu and it showed the same thing. So, since I'm a poor college student and I pretty much need my pc more than I need to eat, I cannot replace the hard drive just yet, not to mention buying a new laptop.

So I thought I'd just install puppy linux on my 8gb usb drive and run it from there.(Quite the pleasant experience, actually; it's a lot faster than I thought). I'd be very grateful if somebody could help me out on this one - what are the implications of this, namely, me running linux on a pen drive while my hard drive is corrupted. It might sound like a silly question to some, but I just want to know whether my computer won't just become unusable if the hard drive does fail(even though I am technically? not using it for I/O)

Cheers.

---

### Post by dino99 on 2012-07-24
if you still have windows running:
- install and use ccleaner
- run your antivirus, or do an online detection
- defrag the system
- run chkdsk

from ubuntu:
- clean the system:
  - sudo apt-get clean
  - sudo apt-get autoclean
  - sudo apt-get autoremove
- run clamtk
- run fsck : [http://linuxpoison.blogspot.fr/2009/04/how-to-checkrepair-fsck-filesystem.html](http://linuxpoison.blogspot.fr/2009/04/how-to-checkrepair-fsck-filesystem.html)
- logout & reboot

but take care of your hardware:
- limit temperature:
  - fan have to blow
  - system not overclocked
  - system need fresh air : remove dust, and everything blocking breathing
  - run gparted to watch about warnings/errors in case

except the hdd warning you got, is hdd too hot ? noisy ? (sometimes hddtemp works badly and might be uninstalled)

---


---
title: "Installing distros after Ubuntu."
date: 2009-11-14
forum: General Help
---

### Post by Archbalt on 2009-11-14
Hi.

I have Ubuntu 9.10 installed as my main system, and a 10 gb partition that I wanna use just for testing others distros. But I'm afraid of messing up with the bootloader by doing this... 
So is it possible to do the installations and keep the Ubuntu's grub untouched? Or what is the best way of doing this? (I'm new to Linux and, just for curiosity, want to see how are all those systems and desktops enviroments :D)

---

### Post by jeb800e on 2009-11-14
Why don't you dual-boot?

---

### Post by unamanic on 2009-11-15
Most of the installers will ask where to install their version of grub (in some of them it may be an "advanced" option).  Just pick the partition you are installing to (i.e. sda2 vs. sda) and then chainload from ubuntu's grub to the other distro's.  I can't tell you how to do that with 9.10 since they use grub2, and I'm using my Fedora grub install to chainload from (just google grub2 chailload ubuntu and you should find instructions).

You will screw up your boot loader sometime in your experimenting, so it's best to learn how to fix it when you do.  I haven't yet with grub2, but there are plenty of tutorials out there.

---


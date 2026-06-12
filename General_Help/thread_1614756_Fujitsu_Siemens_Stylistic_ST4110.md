---
title: "Fujitsu Siemens Stylistic ST4110"
date: 2010-11-06
forum: General Help
---

### Post by binaryoutlaw on 2010-11-06
Ok so Ive been trying my best to install an OS onto a Fujitsu Siemens Stylistic ST4110 for 3 days now. The buttons on it will only work on the very first boot screen but not after that. Ive been using a USB keyboard for navigation. So far the screen will work in command line but not in a graphical environment. The vga port to my LCD monitor will work with a GE however but the screen flicker gives me a headache. Touch screen navigation only works in BIOS. I have tried Ubuntu 10.10 alternate, minimal and Xubuntu alternate all to the same effect. I got some success when I used Ubuntu 6.06 alternate, viewing on the screen worked but not touch, or buttons. I am using a USB external CD/DVD ROM for the distro installation.

I read post [http://ubuntuforums.org/showthread.php?t=589945](http://ubuntuforums.org/showthread.php?t=589945) and tried

```
sudo /etc/init.d/gdm stop
```but it stalls on Checking Battery State

Im out of ideas as what to do. Can I get some help?

---

### Post by binaryoutlaw on 2010-11-08
Still fiddling with it to no avail. I had an idea though, what if I just made a distro that only had the I810 driver on it? As to how to make a distro or add/remove things from it I am at a loss. Is there a way to switch out drivers in just CL? That way I wouldn't have to worry about stopping GDM and can configure it on up with ubuntu mini.

Update: Have now read post [http://ubuntuforums.org/showthread.php?t=582960&highlight=Fujitsu+ST4110](http://ubuntuforums.org/showthread.php?t=582960&highlight=Fujitsu+ST4110) and will be trying SUSE, I would prefer ubuntu though as I can build a lighter system using mini.

---


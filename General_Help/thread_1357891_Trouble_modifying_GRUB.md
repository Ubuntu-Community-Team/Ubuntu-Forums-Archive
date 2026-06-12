---
title: "Trouble modifying GRUB"
date: 2009-12-17
forum: General Help
---

### Post by chess19 on 2009-12-17
I'm trying to change GRUB in a few ways.  Right now, I've got my computer loaded with Windows XP, Windows 7, and Ubuntu.  When my computer boots up, it opens GRUB, and defaults to Ubuntu, then I have the option to select Windows 7, and only after selecting Windows 7 does another option come up which allows me to select Windows XP.   (All OSes are installed on the same HD)

I'd like to 1) Change the default OS to 7, and 2) Add Windows XP to the GRUB boot menu.  The problem is that all the information about editing GRUB tells me to modify /boot/grub/menu.lst, but, as far as I can see, that file doesn't exist.  Instead, the closest thing I could find was /boot/grub/grub.cfg, but that file is read-only.  

Can anyone tell me what to do, or even what file to modify to change GRUB settings?  (Or if there's a program that helps do it)

EDIT: I'm using Karmic, if that makes a difference

---

### Post by audiomick on 2009-12-17
Karmiic makes the difference. Ubuntu has changed from grub, now called grub legacy, to Grub2. The menu.lst file doesn't exist anymore.
You should find the instructions you need here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Leppie on 2009-12-17
win7 takes over the XP boot manager, hence the two will use one and the same boot manager after installing win7.
if you want all 3 systems to appear in the boot menu, best thing to do is use win7's boot manager and add ubuntu to it. a handy tool for editing the boot manager is [easybcd]("http://neosmart.net/dl.php?id=1").

---

### Post by n0glu3 on 2009-12-17
Type this in Terminal.

```
sudo apt-get install startupmanager
```It will be located to System >> Administration. That should allow you to fix your problem hopefully.

---

### Post by ajgreeny on 2009-12-17
> **n0glu3 said:**
> Type this in Terminal.

```
sudo apt-get install startupmanager
```It will be located to System >> Administration. That should allow you to fix your problem hopefully.
Not much use for grub2.  It will only allow you to change the default OS, I think, nothing more at the moment.

---


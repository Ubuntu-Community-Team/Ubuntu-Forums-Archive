---
title: "grub2 menu"
date: 2010-01-08
forum: General Help
---

### Post by linuxhippy on 2010-01-08
I like having a menu that after a couple seconds boots the first OS on the list.  This is what the now Grub Legacy did.  I looked at the new grub2 cfg file and saw that Ubuntu had several options for booting...like a safe mode and memory test.  I never see this boot menu when my pc starts-it just boots into Ubunto after flashing a grub line.

How can I see a menu with options when my pc boots?

---

### Post by Leppie on 2010-01-08
if you want to see the menu, open the grub defaults file:
```
gksudeo gedit /etc/default/grub
```
modify the following lines:
```
GRUB_HIDDEN_TIMEOUT=10 ##or any other number indicating the time in seconds you want the menu to show
GRUB_HIDDEN_TIMEOUT_QUIET=false  ##by default the menu hides when ubuntu is the only os installed, disabling the option will make the menu show at boot
```
the default boot entry is set here:
```
GRUB_DEFAULT=0  ##the first entry in the list
```

regenerate your grub.cfg:
```
sudo update-grub
```

---

### Post by linuxhippy on 2010-01-08
I did that with no errors but got no menu on reboot (I just saw numbers counting down).  Also, how would I add another menu entry to the grub menu (I see the options in grub.cfg but it says not to modify it)?

EDIT: I see, during the countdown press SHIFT

I'm still not sure how to add to that menu.

---

### Post by oldfred on 2010-01-08
more info here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Herman's pages on Grub2
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
GRUB 2: A Guide for Users 
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

You add entries to this
/etc/grub.d/40_custom
or a new file that will be first in the menu
gksudo gedit /etc/grub.d/06_custom
sudo chmod 755 /etc/grub.d/06_custom

Partitions now count from 1. sda1 = (hd0,1) 
Style has changed {} set & = are now required
# Chainload another bootloader
menuentry "Chainload partition 3" {
set root=(hd0,3)
chainloader +1
}

---

### Post by Leppie on 2010-01-08
if you want the menu to always show, edit the defaults file:
```
gksudo gedit /etc/default/grub
```
comment out the following line like this:
```
#GRUB_HIDDEN_TIMEOUT=10
```
update grub.cfg:
```
sudo update-grub
```

---


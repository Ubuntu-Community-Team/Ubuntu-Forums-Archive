---
title: "Boots directly to grub&gt;"
date: 2011-12-01
forum: General Help
---

### Post by Phil_Munck on 2011-12-01
I had Ubuntu 11.10 installed as a dual boot with Windows 7 on a Dell Inspiron 8600 with a single hard disk.  I started the unit this morning (12/1/2011) and booted into Windows where I did a Windows update and then rebooted into Ubuntu (which is the default boot selection).  I went to the Update Manager and selected all the available updates which downloaded and installed.  I then wanted to use a program in Windows and selected Restart from the shutdown menu.  When the computer restarted, it displayed the Dell flash screen and then displayed a terminal type screen headed by "GNU GRUB version 1.99-12ubuntu5" and displayed a "grub> " prompt.

I don't know how to get the system to move from this point.  There is apparently no 'man' page and help is very abbreviated. It's as though there is no operating system on it at all.  I desperately need that Windows installation because it has a device driver that is not available anywhere any more.:confused:

---

### Post by Phil_Munck on 2011-12-01
> **Phil_Munck said:**
> I had Ubuntu 11.10 installed as a dual boot with Windows 7 on a Dell Inspiron 8600 with a single hard disk.  I started the unit this morning (12/1/2011) and booted into Windows where I did a Windows update and then rebooted into Ubuntu (which is the default boot selection).  I went to the Update Manager and selected all the available updates which downloaded and installed.  I then wanted to use a program in Windows and selected Restart from the shutdown menu.  When the computer restarted, it displayed the Dell flash screen and then displayed a terminal type screen headed by "GNU GRUB version 1.99-12ubuntu5" and displayed a "grub> " prompt.

I don't know how to get the system to move from this point.  There is apparently no 'man' page and help is very abbreviated. It's as though there is no operating system on it at all.  I desperately need that Windows installation because it has a device driver that is not available anywhere any more.:confused:
I'm not sure why I am replying to my own message.

---

### Post by oldfred on 2011-12-01
You may be able to manually boot, installs are often sda5 or hd0,5 example is sdb1:

Adjust drive, partition to your install:
sh:grub>ls
#If on (hd1,1) or sdb1
sh:grub>ls (hd1,1)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd1,1)/vmlinuz root=/dev/sdb1
sh:grub>initrd (hd1,1)/initrd.img
sh:grub>boot

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

### Post by utnubuuser on 2011-12-01
there is a really clear How-To here:[http://sazeit.com/articles/boot-ubuntu-from-grub-prompt]("http://sazeit.com/articles/boot-ubuntu-from-grub-prompt")

Then, once you've booted Ubuntu, follow the instructions in this ( [http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair]("http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair") ) How-To to install Boot Repair and fix the MBR/Grub loader.

---


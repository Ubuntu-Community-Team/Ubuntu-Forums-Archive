---
title: "GRUB2 doesn't start in dual-boot machine"
date: 2009-10-31
forum: General Help
---

### Post by LordKelvan on 2009-10-31
Hi:

I wanted to set-up a dual-boot environment.  I first installed Windows 7 on the first partition of my hard drive, and then I installed Ubuntu 9.10 on the second partition.  However, when I start my computer, GRUB2 doesn't appear - it boots straight into Windows.  I tried re-installing GRUB2 onto /dev/sda (which is the drive which contains both OS's), but I still get the same behaviour.  

The only error I've seen with GRUB2 is when I call update-grub.  It gives me the error message "cannot find list of partitions!".  I believe this message comes from os-prober, and I'll assume its because it doesn't understand Windows 7's layout.  So I've added a custom entry to my GRUB2 for Windows (instead of having os-prober create one for me).

I'm using the default settings with regard to "hidden menu", and just to be sure I've re-checked the settings to make sure the menu isn't being hidden.  As well, I've tried pressing SHIFT/ESC when my computer boots (just in case the menu is hidden), but GRUB2 still doesn't show up.  Any ideas?

Cheers,
LK

---

### Post by LordKelvan on 2009-10-31
Some new developments.  I decided to re-install Ubuntu, but I still had the same problem.  Then I decided enter the BIOS boot menu (i.e., the menu you get by pressing F11 during boot-up).  The menu is as follows:

CD/DVD Drive
HDD1
HDD3
HDD2
HDD4

If I manually select HDD1, it loads GRUB2 with the correct entries.  This seems odd, because based on the above menu, I would have thought that it normally boots into HDD1.

---

### Post by mustafa2osman on 2009-10-31
[LEFT]Holla ... am not an ubuntu expert .. but lately I had problems with GRUB 

am using 9.04 version of Ubuntu 


try to follow those instructions :




1. Boot with Ubuntu Live CD
2. Open gnome-terminal
Give the commands:
3. sudo grub
then it shows grub> like this
grub>find /boot/grub/stage1
it’ll give a output like this (hd0,7)  7 is here for example, itÄºl be number of ur partition.
grub>root (hd0,7)
grub>setup (hd0)
grub>quit
[/LEFT]
 


hope I helped
BR  :)

---

### Post by LordKelvan on 2009-10-31
Thanks, but I'm using GRUB2, not GRUB.

---

### Post by LordKelvan on 2009-11-01
It was a really simple (and stupid) error.  I forgot that I had physically switched the order of my hard drives.  Thus, the BIOS boot order was trying to boot first from the drive which contains my Windows boot files (for some reason, the boot files are not located on the same drive as my actual Windows installation), and not /dev/sda.  This explains the behaviour I was seeing - normal booting would first boot to the drive with the boot files, and thus load Windows.  If I forced it to boot from /dev/sda, it would load GRUB2.

---


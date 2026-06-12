---
title: "dual boot problem"
date: 2012-03-18
forum: General Help
---

### Post by Aymandba on 2012-03-18
[CENTER][SIZE=3]i have windows 7 32 Bit
yesterday i installed ubuntu 10.11
but its boot directly to ubuntu and i want first boot to windows 7 directly
how i do that???


regards
thanx
[/SIZE][/CENTER]

---

### Post by Subidubi32 on 2012-03-18
Do you have multiple hard discs?

---

### Post by Aymandba on 2012-03-18
yes i have 3 hard disks 
win7 and ubunto on separated hard disk

---

### Post by Subidubi32 on 2012-03-18
And the Ubuntu comes up, when you start? So the boot disc in the bios is the ubuntu's disc.. than you have to configure the grub.

---

### Post by Aymandba on 2012-03-18
yes first boot is ubuntu and i want to make first boot is win7 
how do configure grub

---

### Post by Subidubi32 on 2012-03-18
Can you post the reply(terminal) for:
df -h

---

### Post by Helen McCall on 2012-03-18
Grub 2, which is the boot loader, will usually be set to boot the last booted system as the default.

If you want to set Win7 as the permanent default boot, you will find that the Grub 2 documentation is severely lacking in quick and easy workarounds.

There is some documentation at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) with some links to other documentation.

I am still going through all this to familiarise myself with Grub 2. I suspect from what I've been reading that you have to prepare a custom menu to make any particular system your default in multi-boot.

---

### Post by Mark Phelps on 2012-03-18
Use Grub-customizer.  It puts up a GUI that you can then use to set defaults:

[http://ubuntuforums.org/showthread.php?t=1664134&highlight=Grub+Customizer]("http://ubuntuforums.org/showthread.php?t=1664134&highlight=Grub+Customizer")

---


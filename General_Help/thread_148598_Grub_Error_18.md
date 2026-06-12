---
title: "Grub Error 18"
date: 2006-03-22
forum: General Help
---

### Post by Aulden on 2006-03-22
Hi all, 

I've looked up this error in the forum but didn't get anything to help me out of this problem. 

I have a IBM Thinkpad T41. I got XP installed, Suse 10, and I've managed to install Ubuntu on the third partition. The Suse Grub opens on start up and I can start into Windows and Suse but when trying to open Ubuntu it gives me Error 18. 

What to do!?

I've looked all over the internet and can't find anything that has helped. I've used Suse a fair bit but wanted to try Ubuntu along side. I can start Ubuntu if I load the SUSE install CD, and load into Ubuntu from there but that isn't very handy.

Please help! 

Any suggestions will be appreciated!

---

### Post by lha on 2006-03-22
You'll get better advice with this kind of issue of you post your menu.lst (from Suse, this time) and partition table(s) (sudo fdisk -l)...

[QUOTE=Grub manual]18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). [/QUOTE]

A bios update might do the trick. Otherwise, you have to put your Ubuntu's kernel somewhere near the beginning of your drive.

---

### Post by Aulden on 2006-03-23
Hey I've found the answer. 

For some reason I didn't see it the first search through the forum:

[http://ubuntuforums.org/showthread.php?t=33811](http://ubuntuforums.org/showthread.php?t=33811)

Thanks all!!!

YAY it works!

---


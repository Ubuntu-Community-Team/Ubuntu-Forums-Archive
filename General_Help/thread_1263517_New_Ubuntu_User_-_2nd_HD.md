---
title: "New Ubuntu User - 2nd HD"
date: 2009-09-11
forum: General Help
---

### Post by Quarkrad on 2009-09-11
A friend has asked me to 'give' him Ubuntu to try - at the moment he (and family) use winXP with 4 user profiles.  My plan is to take out his HD and replace it with one of my spare ones.  Install Ubuntu on that (sda1) and then put his original HD back in as a second HD (sdb) - it will have is original winXP environment on it.  I'm going to wait until the next Ubuntu October release that I understand will have Grub2.  My question is - I assume when I connect the 2nd HD I will be able to make Ubuntu recognise it by adding the relevant entries to the menu.lst file.

---

### Post by ankspo71 on 2009-09-11
Hi,
The Ubuntu CD will create the Windows entry for you if you wait to install Ubuntu after your hard drive is installed in the other computer. It automatcially detects other operating systems installed. Be sure to install grub on the first hard drive though, and be sure the boot priorities in the bios are correct. The drive with the grub needs to boot first.
Hope this helps.
James.

---

### Post by cak3 on 2009-09-11
yes, although the procedure is somewhat different with grub2. Grub2 uses a grub.cfg instead of menu.lst, and you don't want to edit that directly, since it uses scripts or predefined entries to generate that file.

That being said, you probably wont have to edit anything. If you simply run "grub-install --recheck /dev/sda" (or whichever drive you boot from) it should detect the disks and update the config accordingly. If not, it can still, of course, be specified manually.

---

### Post by islander_810 on 2009-09-11
Hello Quark,
alternatively, if his motherboard supports easy boot feature (like where you press F8 or something and a menu pops up from which you can select where to boot from) you can install Ubuntu to the 2nd Disk and use the easy boot menu to boot into Ubuntu/XP so that

1st HDD will contain solely Windows
2nd HDD will contain only Ubuntu 

Advantage here is that you won't have to configure GRUB, if windows reinstallation is required, re-configuring GRUB won't be needed.

---

### Post by Quarkrad on 2009-09-12
Thank you for all your comments  much appreciated. :)

---


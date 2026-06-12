---
title: "Yet another grub error! Grub error 17"
date: 2009-09-19
forum: General Help
---

### Post by bobleny on 2009-09-19
I'm trying to install System Rescue CD onto an external hard drive with an ext3 file system. The only issue I am having now is that the default boot loader for the SRCD doesn't work with ext3. I need to use grub!

After installing system rescue I used the following grub command to install grub on the external:
sudo grub-install --root-directory=/media/Boxy/ /dev/sdb1

The drive map is real simple.
Floppy
Internal
External

The computer doesn't have a floppy, but it is listed. The first hard drive is made of one ntfs partition (XP). The external is made of one ext3 partition (SRCD).

When you attempt to boot from the external you get a grub error 17 when the proper drive and partition is selected. Otherwise you get error 22, 21, or 15.

Any suggestions comments or ideas are welcomed.

Thanks!

---


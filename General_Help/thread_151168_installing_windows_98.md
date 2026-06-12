---
title: "installing windows 98"
date: 2006-03-27
forum: General Help
---

### Post by ubuntukid on 2006-03-27
I`ve got ubuntu running on my computer. I`m going to install windows 98 (only legal copy I have) on my main hd but I`m concerned how this will effect my ubuntu install. My ubuntu install is on my second hd. If I install windows will it automaticly boot into windows or will I still get the grub loader?

---

### Post by adie273 on 2006-03-27
It'll boot straight into Windows 98

---

### Post by b4t3m4n on 2006-03-27
Yeah, in these situations, its almost always better to install windows first, then linux after.  That way your bootloader will be on your MBR and then you can tell your bootloader where your windows install is at.  Windows doesn't really expect you to use anything other operating system other than theirs -.-

---

### Post by ajgreeny on 2006-03-27
Before you install windows, and assuming you have a floppy drive you could install grub to a floppy with *sudo grub-install /dev/fd0*.  If you get a message saying you can't do it because of something to do with bios, just make sure that the floppy is listed with a line in your /boot/grub/device.map as follows 
(fd0)   /dev/fd0
then try again.

Now when you've installed windows you can restore grub to the mbr after adding an entry for windows to the menu.list file in /boot/grub by doing *sudo grub-install /dev/hda* or *hdb* (where your mbr is)

My windows entry reads

# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

You may need to change the line starting "root" to wherever your windows partition is.  Remember that you just have to start all over if windows is not in the beginning of the hard drive. Microsoft requires its OS to be in the first few Gb, not necessarily the first partition (in my case it's the second).

Good luck

---


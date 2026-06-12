---
title: "setting the boot partition"
date: 2009-07-31
forum: General Help
---

### Post by graphicsxp on 2009-07-31
Hi,

How can I set the boot partititon from the command line ? I know how to do it in Gparted, but I need to be able to do it in terminal, after I boot from the live CD.

This is because I'm going to change the boot partition to another one (using GParted), and once this is done and I reboot, I need to be able to set it back to the current one.


Thanks
Sam

---

### Post by graphicsxp on 2009-07-31
Actually I searched a little bit and found that the command is 'parted'.

I give it a quick try before messing up, and when I type 

>parted -l

I get the followind error :

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label 

Any idea what I can do ? Because of that I can't set the boot partition either....

---

### Post by nothingspecial on 2009-07-31
Have you tried sudoing it?

---

### Post by treeingwalker on 2009-07-31
Assuming you are using the GRUB bootloader, I suggest thoroughly going through the man/info pages about GRUB. 

Without knowing exactly how you have your disk partitioned, and assuming you're using grub, go find the grub directory, and have a look at files like menu.lst.

You can, however, boot from a USB and then use gparted to work on the partitions on your disk, since most likely they won't get mounted.

---

### Post by graphicsxp on 2009-07-31
Hi guys,
Thanks for helping.

Actually I figured it out. It was my CDROM drive !  I had a cd inside, all I had to do was to unmount it.

then from parted, I've set my boot partition to number 2. Should be easy enough now to revert back to 1.

---


---
title: "Partition table wrong..installed twice"
date: 2010-07-09
forum: General Help
---

### Post by philbert1664 on 2010-07-09
Hi,
I rashly installed ubuntu twice on the same disk, I now have what I'm sure is a dangerous situation with my partition table:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9       18841   151271887+   7  HPFS/NTFS
/dev/sda3           18841       29787    87926785    5  Extended
/dev/sda4           29788       30393     4867695   db  CP/M / CTOS / ...
/dev/sda5           18841       19613     6201247+  83  Linux
/dev/sda6           29337       29787     3621888   82  Linux swap / Solaris
/dev/sda7           19613       28935    74875904   83  Linux
/dev/sda8           28935       29336     3225600   82  Linux swap / Solaris

The old Ubuntu install has been squeezed onto the ~6GB file system /dev/sda5

How can I sort this out!?

Is a repair possible or dump the extended partition and start again :o(  ?

Thoughts please.

---

### Post by audiomick on 2010-07-09
Hallo.
I think if you just delete the Linux and Swap that you don't want using gparted (from the live CD might be easier) and then expand the other one into the empty space, you will get what you want.

I suspect you will have to then do
```
sudo update-grub
```to get the boot loader sorted out, but I am not sure.

Grub2 help here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)


Make sure you know which Linux you want to keep.
I would suggest keeping the swap on sda6, as it is at the end of the extended partition. This will make your re-sizing operations less complicated.

---

### Post by john newbuntu on 2010-07-09
What makes you feel it to be dangerous?  From what I can see, there appear to be a few cylinder overlaps (between sda2 and sda3.  also sda5 and sda7 and between sda7 and sda 8 but it may not necessarily be sector or partition overlaps.  As far as I know Linux (and probably windows) use LBA to decide their boundaries.

You can check with 'sudo fdisk -lu' or 'sudo cfdisk -Ps /dev/sda' to see if any sectors overlap.
Note that you can share the swap partition between multiple installs of linux.

---


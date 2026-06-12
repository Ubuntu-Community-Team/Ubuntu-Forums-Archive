---
title: "External HDD boot"
date: 2012-06-05
forum: General Help
---

### Post by fillintheblank on 2012-06-05
I need to retrieve some files from a friends computer, which has a corrupted windows registry and wont boot. No problem with my handy dandy thumb drive with Ubuntu to boot up the computer. The problem is I forgot the thumb drive and cant get a new one for some time. All he has is an external HDD with files on it that wont be able to be removed from there. Is it possible to make a bootable partition on that external HDD without having to wipe it first?

---

### Post by tecs on 2012-06-05
Technically - yes.

You can resize (shrink) the existing partition on the external hard drive with gparted to create unallocated space at the end of the partition table, big enough to fit an Ubuntu installation.

But you will need an Ubuntu LiveCD to run gparted and install Ubuntu afterwards. I guess if you had one, you could use it to retrieve your friend's files, but that's not the case right?

EDIT:
Forgot to mention that after you are finished you can remove the Ubuntu partitions from the external HDD, resize the main partition back to fill the entire HDD space and remove grub from it.

---


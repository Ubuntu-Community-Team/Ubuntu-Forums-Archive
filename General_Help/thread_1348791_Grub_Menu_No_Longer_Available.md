---
title: "Grub Menu No Longer Available"
date: 2009-12-07
forum: General Help
---

### Post by Speedy328 on 2009-12-07
I have an HP desktop on which was installed Windows XP. Several months ago I installed Ubuntu 9.04 via Wubi onto a secondary disk. Since that time there have been no problems with the Wubi installation or dual booting via grub. I was even able to update to 9.10 within Wubi with no problem.

My problem began when I attempted to destroy a small, unused, partition on the XP disk and grow the Windows partition using gparted. The re-partitioning went okay but it appears to have screwed up the location of the master boot record. Upon power up the system now sees no boot image and never goes to the grub menu like it did before.

I can boot a Ubuntu LiveCD and mount both the Windows drive (dev/sda2) and the secondary drive (/dev/sdb1) with the Wubi installation so everything is there, just inaccessible for booting.

What is my best option for getting the grub menu back in place?

Thanks

---


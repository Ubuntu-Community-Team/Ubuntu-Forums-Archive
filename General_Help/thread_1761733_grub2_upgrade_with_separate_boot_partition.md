---
title: "grub2 upgrade with separate /boot partition"
date: 2011-05-18
forum: General Help
---

### Post by reader4 on 2011-05-18
I am upgrading from GRUB to GRUB2 according to the instructions here:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

but use a separate partition for /boot.  My question is: which to select in step 6?  I have the options of /dev/sda, /dev/sda1 (/boot), or /dev/sda2.  My guess was /dev/sda1, but I don't really want to guess on this one...

Thanks.

---

### Post by Quackers on 2011-05-18
Normally grub2 is installed to the MBR of the drive, not to a partition.
So that would be /dev/sda

---

### Post by reader4 on 2011-05-18
Ah, right.  Thanks.  Seems to have worked.

---

### Post by Quackers on 2011-05-18
That's good then :-)

---


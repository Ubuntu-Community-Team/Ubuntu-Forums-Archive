---
title: "Change Partition ID"
date: 2010-02-02
forum: General Help
---

### Post by nah40 on 2010-02-02
I have a hard drive with Ubuntu 9.10 that I was running via USB that I installed in my laptop, however it will not boot because the partitions are not named correctly.
Any advice on how to correct?

---

### Post by efflandt on 2010-02-02
That is why you should use UUID to identify partitions, since that is a unique ID for each partition that does not change (unless you alter partitions).  Or maybe you accidentally let the default installation put grub2 in the mbr of what was originally your laptop drive, instead of the mbr of the USB drive (**Advanced** button at installation summary).  So now that the USB drive "is" your main hard drive, grub2 mbr may be missing.

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

I installed 64-bit Ubuntu 9.10 on a USB hard drive with grub2 in the mbr of that drive.  It boots fine (booting from USB) whether it ends up as /dev/sdb on my laptop or /dev/sdf on my desktop, so I imagine it would boot fine as /dev/sda.

---


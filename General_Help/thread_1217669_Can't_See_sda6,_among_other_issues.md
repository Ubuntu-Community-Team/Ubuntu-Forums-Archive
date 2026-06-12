---
title: "Can't See sda6, among other issues"
date: 2009-07-19
forum: General Help
---

### Post by oaxacamatt1 on 2009-07-19
Hey All,
I recently put Ubuntu 9.04 on my Toshiba Satellite L300, (it was cheap, no snickers please).
[http://laptops.toshiba.com/laptops/satellite/L300/L305-S5921](http://laptops.toshiba.com/laptops/satellite/L300/L305-S5921)
It came with Vista which always crashed so I reformated and put 9.04 on.  I partitioned the HD so that sda1 is bootable, sda5 is swap and sda6 is for my muzak. I used reiserfs for sda1+6. The install went very well but when I rebooted I couldn't see sda6.  I have even used pysdm to make sure it is loaded on startup but no luck. One odd thing I noticed (maybe its nothing) when I looked over gparted info for the drives it says the DiskLabelType is msdos!?! but the file sys is reiserfs.  One more thing, I installed sda6 as /opt.  But that shouldn't matter, should it?

The other issues I describe later. One problem at a time.
Cheers

---

### Post by dlmarti on 2009-07-19
mount will tell you where (if at all) the partition was mounted

fdisk -l /dev/sda will output a list of the partitions on the drive

If the partition is there (and formatted, cause my guess is you didn't format it), then you should be able to mount it.

---


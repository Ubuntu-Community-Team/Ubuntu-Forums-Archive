---
title: "Aspire one won't boot"
date: 2010-07-25
forum: General Help
---

### Post by hongkongdonkey on 2010-07-25
I installed 10.04 netbook on an aspire one last year and everything has been working fine since.  switched it on yetserday and I get the message

mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found.  Try passing init=bootarg

Does anyone have any ideas on how to fix this?

Thanks

---

### Post by choochoousmc on 2010-07-25
> **hongkongdonkey said:**
> I installed 10.04 netbook on an aspire one last year and everything has been working fine since.  switched it on yetserday and I get the message

mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found.  Try passing init=bootarg

Does anyone have any ideas on how to fix this?

Thanks
Ok, I'm a new comer here, but based on your info I would say the root section of the hard drive has been corrupted somehow.
My guess is you will have to reinstall / repair the current installation.
One very good reason keep ALL your data on a separate partition or hard drive and backed up.

---

### Post by hongkongdonkey on 2010-07-25
I've tried reinstalling but get an 'Input/output error during write on /dev/sda' message.  If I hit retry I get 'Error fsyncing/closing /dev/sda: Input/output error'

I then get the message 'The ext4 file system creation in partition #1 of SCSI2 (0,0,0)(sda) failed before the installatiion stops.

---


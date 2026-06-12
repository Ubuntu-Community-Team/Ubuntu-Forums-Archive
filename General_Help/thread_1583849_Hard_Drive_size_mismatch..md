---
title: "Hard Drive size mismatch."
date: 2010-09-28
forum: General Help
---

### Post by garlicsalt2 on 2010-09-28
Hello, I have an odd problem. I am trying to recover some data for a friend from a 2.5" SATA hard drive. The label on the top of the drive identifies it as a Western Digital 250 GB Hard drive. I have verified with my friend that this is the correct size. However, every linux distro I try, including Ubuntu 10.4, and 9.10, SystemRescueCD, etc. as well as Windows XP, Windows 7 and Mac OS X, all think that the drive is 2 TB in size.

The partition table is coming up blank (ie, no partitions defined). The total drive size is listed as 2 TB, but this is apparently wrong!! Also, dmesg lists a bunch of access out of bounds messages, referencing the device.

Sorry, I can't be more specific at the moment, as I don't have the drive in front of me.

Is there a way to override the LBA data of a hard drive in linux?? The LBA info is listed on the sticker on the top of the drive, as a 6 or 7 digit number, i think... Again, I don't have it directly in front of me.

---

### Post by CharlesA on 2010-09-28
Make sure that the drive is being detected correctly by the BIOS.

---

### Post by srs5694 on 2010-09-28
It sounds like the drive's electronics are going south. It's conceivable you can find a workaround long enough to rescue some data, but we'll need to see the output of "sudo fdisk -lu /dev/sdb" on the drive. (Change "/dev/sdb" to whatever the drive's identifier is.) Please post the results between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string for legibility.

---

### Post by PRC09 on 2010-09-28
If you have access to a windows machine the following link may be of interest.I did use it once and it worked just fine,my hd was seen as 20gb when it was actually 160gb....



[http://blog.atola.com/restoring-factory-hard-drive-capacity/](http://blog.atola.com/restoring-factory-hard-drive-capacity/)

---


---
title: "Clonezilla and extracting files from Windows"
date: 2011-04-22
forum: General Help
---

### Post by Victor43 on 2011-04-22
I have a backup of a Windows OS done by Clonezilla but would like to know if its possible to extract the files from a Windows computer from the backup CD where the backup was saved .

Can this be done and what software will be able to help

Thanks in advance

---

### Post by wilee-nilee on 2011-04-22
I found this.
[http://ubuntuforums.org/showthread.php?t=872832](http://ubuntuforums.org/showthread.php?t=872832)

---

### Post by Victor43 on 2011-04-23
Thanks for the reply. Victor.

I ran the commands as suggested by the author but got the following errors when running mount. The hint that is given in the error is correct the image is of an entire drive and not just a partition. Does anyone have any ideas ? Thanks again.

Failed to read last sector (80276741): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/loop0': Invalid argument
The device '/dev/loop0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---


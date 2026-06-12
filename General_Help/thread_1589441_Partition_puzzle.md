---
title: "Partition puzzle"
date: 2010-10-06
forum: General Help
---

### Post by berman56 on 2010-10-06
I just completed an installation of latest 10.10.  I am dual booting Ubutnu 64-bit and Vista, each with its own drive.  

When I run disk utility, my Ubuntu drive has "Partition Type" as HPFS/NTFS and the "Type" as "Ext4 (version 1.0)"

Is there any problem with setup?

Thanks for the help.

---

### Post by oldfred on 2010-10-06
Are you sure your partition type is not msdos or MBR? That is standard and gpt is the new for Macs and drives over 2GB.

---

### Post by srs5694 on 2010-10-06
I recommend you post a screen shot so we can all see precisely what the utility is reporting.

---

### Post by berman56 on 2010-10-07
See attached for a screenshot of of the disk utility.

---

### Post by Morbius1 on 2010-10-07
I've got to ask .....

What does the following command say it is:
```
sudo blkid -c /dev/null
```

---

### Post by srs5694 on 2010-10-07
I'm not extremely familiar with Ubuntu's Disk Utility; however, it looks to me as if it's saying that the partition is flagged in the partition table as type 0x07 (HPFS/NTFS), but contains an ext4 filesystem. Linux is fine with this inconsistency, since it ignores partition type codes for most purposes (installation is one notable exception). Nonetheless, it's probably best to fix this so that it doesn't cause problems down the road if you use a utility or OS that does care about the partition type codes. To do this, follow these steps:


[list=1]
[*]Launch a text-mode shell (terminal window).
[*]Type "sudo fdisk -u /dev/sda".
[*]At the fdisk prompt, type "p" to view the partition table. It should show one partition with "07" under the "Id" column.
[*]Type "t" to change the type code. You'll be prompted for a new code. Type "83" and hit the Enter key.
[*]Type "p" again to verify that the change is correct.
[*]Type "w" to save your changes.
[/list]


Thereafter, Disk Utility should show something more consistent.

---


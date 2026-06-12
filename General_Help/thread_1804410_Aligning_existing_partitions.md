---
title: "Aligning existing partitions"
date: 2011-07-14
forum: General Help
---

### Post by kyselejsyrecek on 2011-07-14
Hi,

When I was installing Ubuntu onto my laptop, I probably did a mistake partitioning the hard drive by selecting align to: nothing, because I didn't want to have unallocated spaces between partitions.

However, this resulted in partitions' misalignment as no one partition in the extended one (including the one that is extended) doesn't start on a physical sector boundary.

As I already have much data on the HDD and I don't have another one that big, it is impossible for me to erase existing partitions and then copy the data back. So, is there please a way to get the partitions aligned properly without deleting them?

Here is output from fdisk -lu:

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd58c6e9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    36706303    18352128   83  Linux
/dev/sda4        36708350  1465149167   714220409    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5        36710398   372254717   167772160   83  Linux
Partition 5 does not start on physical sector boundary.
/dev/sda6       372256766  1341569023   484656129   83  Linux
Partition 6 does not start on physical sector boundary.
/dev/sda7      1439986338  1465144064    12578863+  82  Linux swap / Solaris
Partition 7 does not start on physical sector boundary.

Thanks,
Luká&#353; Chmela

---

### Post by srs5694 on 2011-07-14
First, the below comments are based on the assumption that you've got an Advanced Format disk. Since you haven't said what brand or model disk you've got, I can't verify this assumption. Many, but not all, current hard disks are Advanced Format models. If yours is not one of these, you shouldn't mess with your partitions, since doing so is riskier than leaving them alone. If there's any doubt in your mind about your disk's type, check with the manufacturer.

Your best bet is to use a live CD with GParted to resize your partitions, but this time be sure the "align to 1 MiB boundaries" option (or whatever its exact wording) is checked. My recommendations for specific partitions:


[list]
[*]For /dev/sda5 and /dev/sda6, shrink them by the smallest amount possible from the start. (Don't worry about the ends unless GParted complains that it can't satisfy all constraints. If that happens, shrink the ends a bit, too.)
[*]Don't worry about /dev/sda4 (your extended partition), since its alignment is irrelevant.
[*]/dev/sda1 is already properly aligned, so don't touch it.
[*]Personally, I'd delete /dev/sda7 (your swap partition) and re-create it, since swap space doesn't hold important data; however, this will change its UUID value, so doing this will require editing /etc/fstab. If this scares you, you could try resizing /dev/sda7.
[/list]


Note that you may need to explicitly disable swap space (via "sudo swapoff -a" or an option in GParted), particularly if you use the Ubuntu installer in its live CD mode, since some emergency systems search for and activate swap space if it's available.

Be aware that resizing partitions, particularly from their start points, is both time-consuming and risky. If you can't back up /dev/sda5 and /dev/sda6, I strongly recommend that you purchase adequate backup storage before you proceed. For that matter, having adequate backup is important even if you *didn't* need to do this -- hard disks can and do fail, human error can cause data loss, bugs can cause data loss, computers can be stolen, and so on. Going without backup for your valuable data means you don't put much value on your data.

---

### Post by kyselejsyrecek on 2011-07-15
Hi,

Thank you for the response.

Sorry for forgetting mention what HDD I have, it is WDC WD7500BPVT-2 and it shall use Advanced Format already learned from Western Digital site.

However, the problem in alignment is exactly using Gparted as it doesn't show any unallocated space before the partitions (except the swap partition that of course may be removed and recreated later, no problem).

As the partitions other than /dev/sda1 could be safely unmounted, I have tried it previously from the system running from /dev/sda1, but the only thing I can do with the partitions is moving rightwards (and I have to move /dev/sda6 first as there's no space between /dev/sda6 and /dev/sda5, nor /dev/sda4). So I have tried to do it from LiveCD but I got exactly the same result.

Maybe I have not understand to what exactly should I do to align the partitions properly?

I attach screenshot of Gparted (sorry for the localization, I was not able to make it run in english).

Thank you again!

---

### Post by srs5694 on 2011-07-15
> **kyselejsyrecek said:**
> However, the problem in alignment is exactly using Gparted as it doesn't show any unallocated space before the partitions (except the swap partition that of course may be removed and recreated later, no problem).

That's why I specified *shrinking* the partitions by the smallest amount possible.

---

### Post by kyselejsyrecek on 2011-07-15
Uhm, sorry then.

So does it mean *resizing* them to the smallest size possible and then resizing them back? It will help align the /dev/sda5 partition properly from its beginning?

Sorry for the questions, that's not my cup of tee. :-)

Thanks

---

### Post by srs5694 on 2011-07-15
No, just resize by the smallest possible amount -- with any luck less than 1 MiB. With the "align to 1 MiB" option set, that will force the start of the partition to align on a 1 MiB boundary, whatever size you set. There's no point in doing it twice, and in fact doing so is highly inadvisable, since doing it twice greatly increases the odds of losing data in what is an inherently risky operation.

---

### Post by kyselejsyrecek on 2011-07-15
Ah, thank you very much. I will try that.

---


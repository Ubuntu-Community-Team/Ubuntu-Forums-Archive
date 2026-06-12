---
title: "Hard Drive &quot;busy&quot; error"
date: 2009-10-30
forum: General Help
---

### Post by LAKOSWOLF on 2009-10-30
Greetings all,

As I've said in a previous post, I have upgraded my PC to 9.10 and with the exception of a few issues it has been uneventful. However when attempting to reformat one of my ext3 drives ( the file system was corrupted somehow during instillation even though this drive was NOT the target of the install) the disk utility application refused to complete the operation, stopping with a "device busy" error. I attempted to format using Gparted but was stopped again with the same issue.

Here's where it gets interesting

I booted into Intrepid Ibex off a live CD and was able to use Gparted to format BOTH partitions, however when booting back into Karmic only one was available. I also noticed that the now "working" drive seems to be listed as " /dev/mapper/pdc_caejidgdcg1 " ( the drive is really sdd1 however) Furthermore Gparted reports that it can't read the file system on sdd1.

Does anyone anywhere have any ideas? I can't seem to make heads or tails of this.

Thank You!

---

### Post by P4man on 2009-10-30
have a look at your fstab perhaps? try commenting out the references to those partitions, reboot and see if you can formet them?

---

### Post by LAKOSWOLF on 2009-10-30
No such luck unfortunately, it would not appear that the drive is even listed in my fstab:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=9cf25673-014f-4ccf-bcbd-abf28ed3eed7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a3ee6225-5789-4d33-8ee8-a0715042b7cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


and if it helps here is the output of fdisk -l:

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a97aab8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29838   239673703+  83  Linux
/dev/sda2           29839       30401     4522297+   5  Extended
/dev/sda5           29839       30401     4522266   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbefcbef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe950e950

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321   83  Linux

I've also provided a screen shot of drives as they show up in Gparted

The drive highlighted in orange is the drive I am able to mount, but seems to show up in two places at once. The information window with the warning is from /dev/sdb. /dev/mapper/pdc_... seems to act like a normal partition. (it does not show up in Ibex as /dev/mapper/pdc...)

The drive highlighted in green is the one which I am unable to do anything with. It behaves fine in Ibex, but shows up as busy in Karmic.

[IMG]http://i64.photobucket.com/albums/h198/lakoswolf/scrn.png[/IMG]

any other thoughts?

---

### Post by P4man on 2009-10-30
Can you delete the partition, and then recreate it ?

---

### Post by LAKOSWOLF on 2009-10-30
Nope, I've tried that multiple times, every time I do Gparted says it can't read the file system and /or the drive is busy.

---


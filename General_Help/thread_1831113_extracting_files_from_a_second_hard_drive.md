---
title: "extracting files from a second hard drive"
date: 2011-08-22
forum: General Help
---

### Post by pauln60 on 2011-08-22
Hi all,

I have a system with a single IDE master, and I've added a drive from another system that I need to extract some files from... so it's showing up as /dev/hdb, and I need to mount it - I suspect this pretty straightforward for someone who knows what they're doing.  Can anyone point me to a description of how this is done?

Many thanks,
Paul

---

### Post by garvinrick4 on 2011-08-22
You have to mount the partition. You mount the partition on the drive not the drive. 
```
sudo fdisk -l
``` (lower case L)
Now if partition is sdb1 or whatever it is on that drive use yours.
```
sudo mkdir /media/sdb1
``````
sudo mount /dev/sdb1 /media/sdb1
```#should now be on desktop to open:
If did not mount on desktop look in Nautilus or in /media of file system to open.

Unmount when done with.
```
sudo umount /media/sdb1 
```

---

### Post by pauln60 on 2011-08-23
Thanks!  Unfortunately it turns out to be a bit more involved.  The second disc is part of an old SME server, and it can't be mounted as ext3. 

-------------------------------------------------------------
> sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9375    75304656   83  Linux
/dev/hda2            9376        9729     2843505    5  Extended
/dev/hda5            9376        9729     2843473+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   fd  Linux raid autodetect
/dev/hdb2              14        9729    78043770   fd  Linux raid autodetect
-----------------------------------------------------------

So it has to be mounted as a member of a RAID, apparently:

------------------------------------------------------------
> sudo mdadm -E /dev/hdb2
/dev/hdb2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e6c0c01b:62baa263:898ab1af:f0c1006a
  Creation Time : Tue Apr 29 14:17:01 2008
     Raid Level : raid1
  Used Dev Size : 78043648 (74.43 GiB 79.92 GB)
     Array Size : 78043648 (74.43 GiB 79.92 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 2

    Update Time : Wed Aug  3 21:35:23 2011
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 8f6cf86 - correct
         Events : 8788473


      Number   Major   Minor   RaidDevice State
this     0       3        2        0      active sync   /dev/hda2

   0     0       3        2        0      active sync   /dev/hda2
   1     1       0        0        1      faulty removed

--------------------------------------------------------------

So I tried to mount it as per
[http://wiki.contribs.org/Recovering_SME_Server_with_lvm_drives](http://wiki.contribs.org/Recovering_SME_Server_with_lvm_drives)

But the system doesn't have any md devices:

---------------------------------------------------------
> sudo mdadm --assemble --scan
mdadm: unexpected failure opening /dev/md127
mdadm: No arrays found in config file or automatically

----------------------------------------------------------

So I'm stuck.  Any suggestions?

Many thanks,
Paul

---

### Post by garvinrick4 on 2011-08-23
No, never had a raid setup so am at a loss, this will bump it up to front looking for a raid user. Hope you get straitened out.

---


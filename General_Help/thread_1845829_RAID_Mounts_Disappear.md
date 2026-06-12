---
title: "RAID Mounts Disappear"
date: 2011-09-17
forum: General Help
---

### Post by scambro on 2011-09-17
Hello,

I've had Ubuntu running for a few years on one of my home servers and have this issue every few weeks.  I have two RAIDs (running off of a Promise SATA card).  I mount both of them to /media/ via fstab.  Occasionally one (or both) of the mount points will disappear.  What I mean by that is that if I ls /media/FourFive/ I get input/output error, etc.  

I try to sudo mount -a, but then get:

```

mount: special device UUID=887b0f65-c91e-44b4-840b-2a3af21cc019 does not exist
mount: special device UUID=0843ae0d-8855-4879-bbe9-ac882763a9da does not exist

```

My fstab file looks like:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=787830f2-646a-4188-8ca3-d72791982682 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d1566bb3-2937-491a-9c6a-776360af1d7d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# should be 4.5 TB device
UUID=887b0f65-c91e-44b4-840b-2a3af21cc019 /media/FourFive auto    defaults,errors=remount-ro  0  0
#should be 1.5 TB device
UUID=0843ae0d-8855-4879-bbe9-ac882763a9da /media/OneFive  auto    defaults,errors=remount-ro  0  0

```

When I run fdisk -l right now, I'm not seeing the two RAID devices:

```

$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002a034

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38539   309564486   83  Linux
/dev/sda2           38540       38913     3004155    5  Extended
/dev/sda5           38540       38913     3004123+  82  Linux swap / Solaris

```

I can fix this problem 100% of the time by rebooting, but I don't want to have to reboot the server to remount my drives.  First off, how can I make these drives 're-appear' without rebooting?  And secondly, why do they disappear in the first place?

Thanks!

---

### Post by scambro on 2011-09-18
In this case, I'm actually remote, so I can't reboot the pc until I return.  Any suggestions/ troubleshooting appreciated.  Thanks!

---


---
title: "Can't mount addition drive"
date: 2011-09-13
forum: General Help
---

### Post by Mazman on 2011-09-13
Hi

Just started using ubuntu 11.04 but I seem to be having a problem with mounting all my internal hard disks.

These drives have moved from a Windows 7 installation so are all NTFS, but there is always one drive that won't mount.

I have 4 in total, the system drive and 3 additional data drives.

Here is what shows up in fdisk

```
Disk /dev/sda: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xca41ca41

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312567353    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a384c70

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdd: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004128f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38392   308375552   83  Linux
/dev/sdd2           38392       38914     4192257    5  Extended
/dev/sdd5           38392       38914     4192256   82  Linux swap / Solaris

```

I have also attached a screenshot of my disc utility screen showing the message that I get when I try to mount that drive.


I have tried swapping around the drives to different sata ports but then it's a different drive that doesn't want to mount, it seems there is always one drive it can't mount.

I'm still kind of new to ubuntu/linux so I don't quite understand all the stuff in fdisk list, so it may be just something that I don't know about.

Thanks

---

### Post by Pariah819 on 2011-09-13
You said when you swapped the hard drives and sata ports the problem moved to a different drive, can you verify that its not a sata port on your motherboard?  If the drive that can't mount is always plugged into the same sata port that would point to a faulty port.

---

### Post by seawolf167 on 2011-09-13
First thing to do is to ensure that the SATA port on your motherboard isn't faulty. To check this, simply try each port individually and see [if] one of them doesn't allow you to recognize any of your drives. 

If no ports are faulty, please post the output of the following commands

```
cat /etc/fstab
sudo blkid
mount
```

---

### Post by Mazman on 2011-09-13
After much frustration and switching on and off I finally found a way to have all drives mounted.

It looks like it didn't like it when a drive was on the same controller as the boot drive, or at least that's what I think the issue is. I don't get how this wasn't a problem in Windows, does ubuntu have problems with certain controllers?

Thanks for the help:)

---

### Post by Pariah819 on 2011-09-13
Okay, sounds like you are all set then.  Please mark the thread as solved if you don't have any further issues.

---


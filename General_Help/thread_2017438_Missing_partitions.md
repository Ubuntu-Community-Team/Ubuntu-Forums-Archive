---
title: "Missing partitions"
date: 2012-07-05
forum: General Help
---

### Post by celebrimbor on 2012-07-05
I have installed Ubuntu on one of my partition and Crunchbang on the other partition. As I wanted to make some continuous space, I moved Crunchbang partition and then checked fdisk output which looks like this
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc7996dfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63       80324       40131   de  Dell Utility
/dev/sda4           81918   625139711   312528897    f  W95 Ext'd (LBA)
/dev/sda5           81920   211816447   105867264   83  Linux
/dev/sda6       299100160   341043199    20971520   83  Linux
/dev/sda7       341045248   625139711   142047232    7  HPFS/NTFS/exFAT
```

I cannot see sda2 and sda3 partitions. Can anyone tell me how to find them?

---

### Post by matt_symes on 2012-07-05
Hi

You did make a backup before you did this ? Just in case ?
[FONT=monospace]
[/FONT]> /dev/sda5           81920   **211816447**   105867264   83  Linux 
/dev/sda6       **299100160**   341043199    20971520   83  Linuxsda5 and sda6 look like your Linux partitions.

What did you have on sda2 and sda3 ?

It may just be a case the gparted has moved you partitions around.

You have unallocated space between sda5 and sda6, by the looks of it, as i highlighted above

Kind regards

---

### Post by jim_24601 on 2012-07-05
You probably don't have them.

Your standard MBR partition table has 4 slots available for ("primary") partitions, but there's no law that says all of them have to be used or that they have to be in the same order in the partition table as they are on disc.

If you want more than 4 partitions, you have to make one of the primary partitions an "extended" partition, which is just a container for "logical" partitions. Linux always numbers logical partitions starting from 5, regardless of how many primary partitions are used.

Your computer is set up with the Dell "utility" partition (probably some proprietary thing to do with system restore) as primary and everything else as logical under /dev/sda4. Primary slots 2 and 3 aren't used, so fdisk isn't showing them. I don't know why Dell decided to put the extended partition in slot 4 instead of slot 2, but there's no reason why they shouldn't. (But if they had put it in slot 2, the logical partitions would still be numbered starting from 5, so you'd appear to be missing 3 and 4.)

So you've got 2 Linux partitions, presumably Ubuntu and Crunchbang, and one Windows. Which sounds to me like exactly what you should have. I take it all the data you expect to be there is there?

---

### Post by jim_24601 on 2012-07-05
> **matt_symes said:**
> You have unallocated space between sda5 and sda6, by the looks of it, as i highlighted above

My guess is that's the space the OP freed up by moving crunchbang. It can't be the "missing" partitions 2 and 3, since it's inside the extended partition 4.

---

### Post by celebrimbor on 2012-07-05
Thanks for help @Matt and @Jim :) I don't have a backup, but I have kept my important data on /dev/sda7 and left that partition untouched. As Jim poited out, /dev/sda5 holds Ubuntu and /dev/sda6 holds Crunchbang.

I have kept that space unallocated to install ROS.

When I ran fdisk from live CD, it did show information about /dev/sda3 and /dev/sda4 and both were 0 MB in size. How can I remove them?

I tried to open cfdisk but it gives Bad Logical Partition error. Can this cause any further trouble?

Should I wipe out Dell Utility and Make Ubuntu partition primary to fix this?

---

### Post by jim_24601 on 2012-07-05
> **celebrimbor said:**
> When I ran fdisk from live CD, it did show information about /dev/sda3 and /dev/sda4 and both were 0 MB in size. How can I remove them?

This may sound silly, but are you sure it's referring to the same physical disc? The partition layout of a given disc shouldn't change between boots, but the assignment of devices to physical discs might, particularly if you've got different media attached.

> I tried to open cfdisk but it gives Bad Logical Partition error. Can this cause any further trouble?

It sounds dodgy, but it might just be a [bug in cfdisk]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=464377"). Which partition is it complaining about?

> Should I wipe out Dell Utility and Make Ubuntu partition primary to fix this?

I shouldn't recommend it, unless you're planning to blow Windows away completely and just use Linux. As I said, I'm not sure that you have anything to "fix".

---

### Post by matt_symes on 2012-07-05
Hi

> I shouldn't recommend it, unless you're planning to blow Windows away completely and just use Linux. As I said, I'm not sure that you have anything to "fix".I would agree with this. 

I have seen nothing to suggest you have any problems at all with your setup especially if you created the free space between sda5 and sda6 yourself and if the installers created the extended and logical partitions and you did not create them or move existing partitions around.

I think you are fine to go.

I would also keep the Dell Utility partition.

Kind regards

---

### Post by celebrimbor on 2012-07-06
> This may sound silly, but are you sure it's referring to the same physical disc? The partition layout of a given disc shouldn't change between boots, but the assignment of devices to physical discs might, particularly if you've got different media attached.

Yes. I was referring to same physical disk. I guess it got messed up because I have resized and moved many partitions for trying new distros.
> It sounds dodgy, but it might just be a bug in cfdisk. Which partition is it complaining about?
Exactly! cfdisk was showing error as because that exact same reason and I could get rid of it by fdisk /dev/sda followed by -f flag.

Thanks a ton to both @Jim and @Matt for assuring me and helping about Dell Recovery partition. I was very worried about it. :)

---


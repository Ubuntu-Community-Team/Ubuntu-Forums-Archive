---
title: "Gparted error: Can't have a partition outside the disk!"
date: 2011-06-29
forum: General Help
---

### Post by dayzman on 2011-06-29
Hi,

I was upgrading Ubuntu to Natty last night, but it crashed just before completion. Then, I couldn't mount the drive so I'm now booting it from the live disc. I go into gparted, but it gives me an error saying:

Can't have a partition outside the disk!

I have /root and /home in separate partitions, so I must find a way so that /home can survive. I've run testdisk and this is what I get:

```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
>* FAT16 >32M               0   1  1    14 254 63     240912 [DellUtility]
 P FAT32 LBA               15   0  1  4192 254 63   67119570 [NO NAME]
 P FAT32 LBA             8360   1  1 12183 254 62   61432496
 L Linux                14068   1  1 18939 254 62   78268616
 L Linux Swap           18940   1  1 19129 254 40    3052264
 L FAT32 LBA            19130 218 33 19457  21 20    5240832 [MEDIADIRECT]

```

There are only 2 Linux partitions, Linux and Swap, so it seems that my /home has disappeared! Is there a way to recover it? Also, how do I fix Gparted's complaint?

Any help will be much appreciated.

Cheers

---

### Post by oldfred on 2011-06-29
I have not used testdisk enough to know. But it should show your /home partition. Do you know where it was on disk? Was it where it is showing FAT partitions. You do have to be careful not to create overlapping partitions, I do not think it lets you but you need to understand your partition layout before to be able to recover it best.

I would do this first just to have a current backup of current partition table layout.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

I think it is testdisk that sometimes makes the extended partition end larger than the drive. Fixparts will usually solve the partition table issue. Fixparts will not find missing partitions.

Fixparts - Repair broken partition tables (not overlapping issues)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by srs5694 on 2011-06-29
*Don't* use TestDisk yet! Instead, type the following diagnostic command:

```

sudo fdisk -lu

```

Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags or the results will be difficult to read.

---

### Post by dayzman on 2011-06-29
> **srs5694 said:**
> *Don't* use TestDisk yet! Instead, type the following diagnostic command:

```

sudo fdisk -lu

```

Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags or the results will be difficult to read.

I get

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      240974      120456    6  FAT16
/dev/sda2       226002483   304271098    39134308   83  Linux
/dev/sda3       304271163   307323426     1526132   82  Linux swap / Solaris
/dev/sda4       307323450   312592769     2634660    f  W95 Ext'd (LBA)
/dev/sda5       307337216   312578047     2620416    c  W95 FAT32 (LBA)

Disk /dev/sdb: 3997 MB, 3997695488 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7807999 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007c96d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7807967     3903952+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(486, 5, 63)

```

If I do deep search in testdisk, I see the /home partition, but I can't write change the partition table because it complains about an invalid structure.

---

### Post by dayzman on 2011-06-29
> **oldfred said:**
> 
I think it is testdisk that sometimes makes the extended partition end larger than the drive. Fixparts will usually solve the partition table issue. Fixparts will not find missing partitions.

Fixparts - Repair broken partition tables (not overlapping issues)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I see. I think I should try recovering the missing partition first. Testdisk can find it, but it can't write to the table... :(

---

### Post by oldfred on 2011-06-29
srs5694 should comment as fixparts is his program. Many programs will not write new partition tables with errors as they are not sure then what is correct and do not want to compound error.

The error that makes your table invalid is that this is the size of your drive.
total 312581808 sectors
But sda4 says it ends as 312592769 which is too large.
/dev/sda4       307323450   312592769     2634660    f  W95 Ext'd (LBA)

But you also have the missing partition. You have used all 4 primary partitions with one of those as the extended. But sda1 FAT16 and sda5  FAT32 are smaller partitions. Were these ones you created? You have to have a primary partition or expand the extended to hold the /home to comply with partition standards.

---

### Post by srs5694 on 2011-06-29
Oldfred's analysis is correct; /dev/sda4 is too large for your hard disk, which is what's giving GParted fits. I recommend you begin this way:


[list=1]
[*]Back up your partition table with sfdisk, as described in the "Pre-Launch Procedures" section of the [FixParts Web page.](http://www.rodsbooks.com/fixparts/)
[*]Use FixParts to fix the bad extended partition. Typically, just launching FixParts on the disk and then saving the table back with "w" will fix the sort of problem you've got; however, it's always wise to verify that it's working with the right partitions by using "p" before you write the partition table back. Alternatively, follow the sfdisk procedure described [here](http://www.rodsbooks.com/missing-parts/index.html) (under "Fixing the Problem the Hard Way"). This has the advantage of leaving the extended partition's start point unchanged; FixParts will probably move the start of the extended partition, which may require you to resize it later if you have to use the more difficult recovery option (described shortly).
[*]Back up your partition table *again* with sfdisk. Keep both copies. (You want to maintain a trail of possible restore points in case something goes wrong that you can trace to a particular step.)
[/list]


At this point, you have at least three options:


[list]
[*]Try TestDisk again and see if it can recover your /home partition.
[*]Use GParted's partition-recovery feature. (I think it's Device->Attempt Data Rescue, but I'm not positive of that.) I've never used this feature, but I do recall one case posted here a month or two ago in which GParted succeeded in rescuing a partition when TestDisk failed.
[*]Try creating a "new" partition in the empty space using fdisk. The trouble is that this is very much a hit-or-miss proposition, and it's even harder today because you can't be sure whether 1 MiB alignment or cylinder alignment is appropriate. (Based on your extended and swap partitions, I'm guessing cylinder alignment, but that might be incorrect.) I'd recommend this step only if both TestDisk and GParted fail. If you do try this method, you should do it from a live CD with swap space turned off. You should then create the partition, attempt to mount it, and if it doesn't mount, *do not attempt to repair it;* go back into fdisk, delete the partition you just created, and optionally try again with different settings. The key is that you can write partition table data structures with relative impunity, but you should *not* attempt to write to the space in which that partition used to reside, since any write operation is likely to damage the filesystem or the files it contains. Note also that if you used FixParts for recovery, you'll probably have to resize your extended partition to cover the space in which the missing partition resides before you try to create your partitions. You'll have to use GParted for this. I recommend telling it to not attempt to align partitions or to align them to cylinder boundaries (not to 1 MiB boundaries), and make sure that the extended partition begins on sector 307,323,450 (where it does now) or earlier before you begin your recovery effort.
[/list]


Good luck!

---

### Post by dayzman on 2011-06-30
Thank you both. I've run FixParts and now GParted can see the partitions! However, 107GB is regarded as unallocated space and the /home partition isn't recognised. Testdisk still can't recover /home due to "bad structure".

I can't seem to find the recovery function in gparted though...

Thanks a lot

---

### Post by dayzman on 2011-06-30
This is what Testdisk deep search finds:

```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
 * FAT16 >32M               0   1  1    14 254 63     240912 [DellUtility]
 D FAT32 LBA               15   0  1  4192 254 63   67119570 [NO NAME]
 D HPFS - NTFS             15  10 60  1320 117 13   20971520 [RECOVERY]
 D HPFS - NTFS           1320 117 14  5144 117  6   61432553
 D HPFS - NTFS           1321   0  1  7056 254 56   92148833
 D HPFS - NTFS           1321   0  8  7056 254 63   92148833
 D FAT32 LBA             7057   2  1 10243 254 62   51199028
>D FAT32 LBA             8360   1  1 12183 254 62   61432496
 D Linux                10244   1  1 14067 254 62   61432496
 P Linux                14068   1  1 18939 254 62   78268616
 P Linux Swap           18940   1  1 19129 254 40    3052264
 L FAT32 LBA            19130 218 33 19457  21 20    5240832 [MEDIADIRECT]

```

---

### Post by dayzman on 2011-06-30
> **oldfred said:**
> 

But you also have the missing partition. You have used all 4 primary partitions with one of those as the extended. But sda1 FAT16 and sda5  FAT32 are smaller partitions. Were these ones you created? You have to have a primary partition or expand the extended to hold the /home to comply with partition standards.

No, I didn't create the FAT16 and FAT32 smaller partitions -- one is DellUtility and the other is MediaDirect. Should I expand /dev/sda2 to hold /home?

---

### Post by oldfred on 2011-06-30
You still have an issue with complying with the rules of partitions. I do not understand where your /home could have been?

You can have 4 primary partitions. One (and only one) of the primary partitions can be an extended partition that can hold many logical partitions. But each of the 4 partitions must be contiguous or the extended cannot have a primary in the middle of it.

So where was your /home. You have no more primary partitions and your extended is at the end with swap (sda3 primary) in front of it. So based on that you cannot add to the extended partition to include any more space and you cannot add another primary.

Did you create other new partitions or how did you have a separate partition for /home?

---

### Post by dayzman on 2011-06-30
> **oldfred said:**
> You still have an issue with complying with the rules of partitions. I do not understand where your /home could have been?

You can have 4 primary partitions. One (and only one) of the primary partitions can be an extended partition that can hold many logical partitions. But each of the 4 partitions must be contiguous or the extended cannot have a primary in the middle of it.

So where was your /home. You have no more primary partitions and your extended is at the end with swap (sda3 primary) in front of it. So based on that you cannot add to the extended partition to include any more space and you cannot add another primary.

Did you create other new partitions or how did you have a separate partition for /home?

I don't think I created new partitions after the fault. I believe the /home partition should have been a primary partition. Do you know how I can fix the situation? Since Testdisk can list the files, does that mean the partition is still there and intact?

Thanks

---

### Post by oldfred on 2011-06-30
You have to delete a primary to make room if it was a primary. I would suggest deleting swap (sda3). Then testdisk may be able to recover /home to the primary sda3 that then is available.

But you will have to move things around a little after your recovery if it works and make space so you can expand the extended partition and put a new swap into the extended. You will also have to update fstab with the new UUID of swap as it will keep trying to load the old one. You should be able to boot with warning messages and then edit fstab. If not then use liveCD to edit.

---

### Post by dayzman on 2011-06-30
> **oldfred said:**
> You have to delete a primary to make room if it was a primary. I would suggest deleting swap (sda3). Then testdisk may be able to recover /home to the primary sda3 that then is available.

But you will have to move things around a little after your recovery if it works and make space so you can expand the extended partition and put a new swap into the extended. You will also have to update fstab with the new UUID of swap as it will keep trying to load the old one. You should be able to boot with warning messages and then edit fstab. If not then use liveCD to edit.

I tried deleting swap in gparted, but I get an error saying ""Error about informing the kernel about modifications to partition.. Failed to add partition 5 (Device or resource busy)". I can't see swap in gparted anymore, but it's still there in Testdisk. Do you know how I can thoroughly delete swap here?

Thanks

---

### Post by dayzman on 2011-06-30
Great! I've recovered it. I had to use Testdisk to properly delete swap.

Thanks a lot!

---

### Post by srs5694 on 2011-06-30
My suspicion is that some of your partitions got converted from logical to primary form. The Windows XP installer is known to do this under some circumstances, and other programs might do the same thing. In fact, TestDisk is likely to do that with some recovery operations.

This brings up another point: TestDisk is an emergency recovery tool. You should *not* be using it for normal partitioning operations, including deleting swap space. TestDisk has known bugs, one of which may have created the problem with GParted being unable to see the partitions on the disk. (To be sure, GParted's limitation is partly to fault here, but GParted is at least just being a stickler for a correct partition table; something else, like TestDisk, *created* an improper partition table to begin with.)

An inability to delete swap space in GParted usually means that the swap space was in use at the time. (GParted refuses to operated on partitions that are in use.) Such partitions are marked with a key icon in GParted, IIRC. You can get around this problem by disabling swap space before deleting it. You can even do this in GParted by right-clicking the swap space and selecting an option to turn it off. In some cases you might need to boot from a recovery disc so that you can unmount all the partitions in an extended partition to be able to work on any of them. Another option in such cases would be to use fdisk; it's quite happy to work on in-use partitions, but your changes won't be seen by the kernel until you reboot, which can be dangerous if you want to start creating new filesystems or whatnot right away.

Finally, although it's too late to do this, you could probably have used FixParts to convert both of your Linux partitions (/dev/sda2 and /dev/sda3) into logical partitions. Whether this would have worked would depend on the details of the size of the recovered /home partition, though.

Now that you've got everything working, of course, you needn't be concerned with these might-have-beens; however, I do urge you to not reach for TestDisk quite so quickly in the future. It's a useful tool, to be sure, but so is a chainsaw. That doesn't mean you should be using one to trim your fingernails!

---


---
title: "Already have 3 Primary + 1 Extended How to install ubunut?"
date: 2011-01-03
forum: General Help
---

### Post by udinnet on 2011-01-03
Hi there,
I want to know what is the possible approach to solve the below problem.

I have a HP DV6 pc with 
* 200MB system partition (Primary)
* 395GB C: (Primary,NTFS, Win 7 X64)
* 200MB HP_TOOLS Partition (Primary,FAT32)
* 200GB E: (NTFS,Extended and logical drive)

This is my partition layout and these partitions are very important.

When I check these partitions from Ubuntu 10.10 Setup It shows sda1,sda2,sda4,sda5
But no SDA3!!!

So juzt selected install with alongside OS option and when it comes to that partition size adjusting window for dual boot is named that the new partition about to create is SDA3!!!(By dividing sda2 Win 7 Partition) .

Then I juzt exit that setup and not continued. So nothing changed. So I want to know that what will happen If i installed Ubuntu in sda3(Auto generated) With dual boot partitioning option? Will I lost my logical drive (200GB)?

Or is it ok?        :popcorn:

---

### Post by PapaNerd on 2011-01-03
Auto-anything on a file system containing data you want to keep is scary.

If it were me, I would fully back up the partition the installer wants to divide, and then use fdisk or another partitioning tool to manually change the partition table.  Once that is complete, re-store your backed up data onto the (now smaller) ntfs partition and then perform the ubuntu installation on the new (probably ext4) partition.

---

### Post by oldfred on 2011-01-03
You cannot have two extended partitions and the automatic install trys to shrink the largest partition and insert a primary and put swap in a logical. In your case, you will have to manually partition. You can shrink c: and create sda3 for / (root) and shrink sda5 and add swap as sda6 inside the extended. 

Most new system use all 4 partitions as primary and then you have to delete one. Many create the backup DVDs from the vendor partition and if possible create a repair CD. Then that partition is obsolete. Some also delete the utilities and either not use them or reinstall into a logical partition. You still should create the DVD & CD for recovery & repair, just in case you ever need them.

Be sure to back up all you important data before making any system changes. Software is pretty reliable but we all have clicked on the wrong thing and said delete all, oops I did not mean to do that.

You will have to use manual install. If you are using D: sda5 as a shared data partition, you may not be storing as much data into /home which also has all your user settings in hidden files & folders.


For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended.

---

### Post by udinnet on 2011-01-03
> **oldfred said:**
> You cannot have two extended partitions and the automatic install trys to shrink the largest partition and insert a primary and put swap in a logical. In your case, you will have to manually partition. You can shrink c: and create sda3 for / (root) and shrink sda5 and add swap as sda6 inside the extended. 

Most new system use all 4 partitions as primary and then you have to delete one. Many create the backup DVDs from the vendor partition and if possible create a repair CD. Then that partition is obsolete. Some also delete the utilities and either not use them or reinstall into a logical partition. You still should create the DVD & CD for recovery & repair, just in case you ever need them.

Be sure to back up all you important data before making any system changes. Software is pretty reliable but we all have clicked on the wrong thing and said delete all, oops I did not mean to do that.

You will have to use manual install. If you are using D: sda5 as a shared data partition, you may not be storing as much data into /home which also has all your user settings in hidden files & folders.


For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended.


Thank you friend.... But windows 7 don't let me create any more partition by shrinking volumes. If somehow I shrink c: and create some room for root(/) will it be assigned as primary partition (ext4). But when it happens it will brake the current limitation! Now there are 4 primary and 1 extended!

??

---

### Post by deserthowler on 2011-01-03
> **udinnet said:**
> Hi there,
I want to know what is the possible approach to solve the below problem.

I have a HP DV6 pc with 
* 200MB system partition (Primary)
* 395GB C: (Primary,NTFS, Win 7 X64)
* 200MB HP_TOOLS Partition (Primary,FAT32)
* 200GB E: (NTFS,Extended and logical drive)

This is my partition layout and these partitions are very important.

When I check these partitions from Ubuntu 10.10 Setup It shows sda1,sda2,sda4,sda5
But no SDA3!!!

So juzt selected install with alongside OS option and when it comes to that partition size adjusting window for dual boot is named that the new partition about to create is SDA3!!!(By dividing sda2 Win 7 Partition) .

Then I juzt exit that setup and not continued. So nothing changed. So I want to know that what will happen If i installed Ubuntu in sda3(Auto generated) With dual boot partitioning option? Will I lost my logical drive (200GB)?

Or is it ok?        :popcorn:

sda1 and sda2 should be your primary partitions.  sda4 should be extended.  sda5 should be logical.  You can create more logical partitions in sda4.
Earl

Earl

---

### Post by udinnet on 2011-01-03
> **deserthowler said:**
> sda1 and sda2 should be your primary partitions.  sda4 should be extended.  sda5 should be logical.  You can create more logical partitions in sda4.
Earl

Earl

Nope dude sda4 is a primary... and sda5 is extended... waiting for a reply for post #4 :confused:

---

### Post by perspectoff on 2011-01-03
Leave the first three (primary) partitions alone. You only need to work with the 200 Gb extended partition.

You indicate that within that 200 Gb extended partition you have one logical NTFS partition. That one needs to be shrunk so that there is free space created within the extended partition (to be used by the Ubuntu installer in order to create both a swap partition and the Ubuntu OS partition, both of which will be logical partitions).

You can use GParted (found on the Ubuntu LiveCD) to shrink the NTFS logical partition that resides within the extended partition, freeing up space. (You can use GParted to shrink an NTFS partition as long as there isn't a Windows OS residing within that NTFS partition. An NTFS partition residing within an extended partition almost never has a Windows OS residing on it.) You should make at least 20-30 Gb free within the extended partition (or as much as you want to devote to Ubuntu).

After that, the Ubuntu installer can install automatically to the free space you created.

Alternatively, you can manually create the logical partitions to be used for Ubuntu yourself, if you choose. In the free space you made available within the extended partition, create a 2 Gb "linux swap" logical partition within the extended partition, and an ext4 logical partition within the extended partition that uses the remainder of the free space (preferably at least 20-30 Gb). (This latter partition will be used for the / (root) of the Ubuntu installation).

Note that the extended partition gets a designation (such as /dev/sda4) but that it is not explicitly available for use as a partition. It is only there to be subdivided into logical partitions, each of which will also receive a designation (/dev/sda5, /dev/sda6, /dev/sda7, etc.).

(In your case, I suspect the extended partition is third on the hard drive instead of fourth, hence it is designated /dev/sda3 instead of /dev/sda4.)

Believe me, this is easier than it used to be. HP used to create 4 primary partitions on its hard drives. Now they create 3 primary partitions and 1 extended partition. That is a step in the right direction. If they could only leave some free space in the extended partition to begin with, it would save a step in installing Ubuntu.

---

### Post by perspectoff on 2011-01-03
> **oldfred said:**
> You cannot have two extended partitions and the automatic install trys to shrink the largest partition and insert a primary and put swap in a logical. 

Really? I've never seen it do that. It doesn't make any sense, either.

It would have to shrink one primary partition (risky business if it is the Windows primary partition that is being shrunk) and create a second primary, an extended partition, and a logical partition within that extended partition to accomplish this. That is fraught with obstacles and arbitrary decisions about a user's hard drive configuration that I would be surprised to see even the Debian/Ubuntu MOTUs making.

---

### Post by psusi on 2011-01-03
Post the output of sudo fdisk -lu

---

### Post by oldfred on 2011-01-03
+1 psusi's recommendation as then we can see your exact layout.

You do not want to create partitions with windows as it may try to convert to SFS which is a one way conversion and not compatible with anything. But you do want to use windows tools to shrink the windows partition.

You can create all the Linux partitions in the extended partition, but will have to manually expand the extended partition into the free space and may have to move other partitions around which can be a slow process.

---

### Post by udinnet on 2011-01-03
Thanks Guys. I installed ubuntu with no problem. Used 2 Logical Drive for swap and root.

This is my disk layout.:guitar:


Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x30ae6f9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          409600   704786023   352188212    7  HPFS/NTFS
/dev/sda3       704786430  1250050047   272631809    f  W95 Ext'd (LBA)
/dev/sda4      1250050048  1250261679      105816    c  W95 FAT32 (LBA)
/dev/sda5       830619648  1239564287   204472320    7  HPFS/NTFS
/dev/sda6      1239566336  1250050047     5241856   82  Linux swap / Solaris
/dev/sda7       704786432   830617599    62915584   83  Linux

---


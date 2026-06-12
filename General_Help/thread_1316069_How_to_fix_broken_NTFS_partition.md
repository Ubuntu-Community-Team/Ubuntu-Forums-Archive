---
title: "How to fix broken NTFS partition"
date: 2009-11-05
forum: General Help
---

### Post by RLZIII on 2009-11-05
EDIT: Problem solved.  Read the last post for the answer.

Okay, here's the rundown.  I have a 80GB drive that was split into three parts: a very small unallocated space portion in the front of the drive, about 60GB of space as a Windows XP NTFS partition, and a Windows 7 NTFS partition that was about 14GB at the end of the drive.  I deleted the Windows 7 partition with the intentions of growing the 60GB partition to take up the whole drive (as I didn't need any other partitions).

My drive has a few KB of bad sectors on it.  Always has.  So in order to resize the partitions, I needed to use ntfsresize and fdisk.  So, I did the fdisk part first, as it's what I understand you need to do before using ntfsresize if you are growing a partitions (not shrinking one).  I did the following with fdisk (a very basic setup):

```
suubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 9729.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): d
Selected partition 1

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-9729, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-9729, default 9729): 
Using default value 9729

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 07 
Changed system type of partition 1 to 7 (HPFS/NTFS)

Command (m for help): a
Partition number (1-4): 1

Command (m for help): p

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dc770

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

```As you can see, checking at the end of that with "p" shows the system is NTFS.  However, now when I go to use ntfsresize or GParted, it says the disk is not NTFS.  GParted shows it as reiserfs, which fdisk doesn't.

I tried using testdisk to see if I could figure something out, but I'm not familiar with the program, and didn't get very far.  It does show the partition as NTFS, but when I go to list the files, it says that the file system seems broken.

So, I ask the Linux gurus...what should I do to recover the partition and/or finish my original task (growing the partition)?

---

### Post by RLZIII on 2009-11-05
Just wanted to bump with a few updates.  Now when doing anything with ntfsresize, I get this response:

```
subuntu@ubuntu:~$ sudo ntfsresize -i /dev/sda1
ntfsresize v2.0.0 (libntfs 10:0:0)
$MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
Failed to startup volume: Input/output error.
ERROR(5): Opening '/dev/sda1' as NTFS failed: Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.

```

It used to just say that it wasn't an NTFS partition.  Now it seems like there may be a problem with the MFT, perhaps caused by my wrongdoings in testdisk?  As far as I know, there shouldn't have been any data loss throughout this process, as it seems like the problem is purely with the partition table, caused by whatever I did wrong in fdisk.  So if someone could please help, I'd greatly appreciate it.  I'd hate to have to lose all of my data and format when, in theory, it's all there an untouched/unharmed.

---

### Post by hal10000 on 2009-11-05
Well, i don't know what you are doing there.

You say you want to resize the Windows 7 partition, but what you are doing is to erase all your partitions and create a new one, taking the whole free space for it.

So, you don't have to resize anything. You just need to reboot after exiting fdisk, then your partition will be correct.

But, why do you use linux programs for these tasks? You can do this all during the normal windows-installation process.

> As far as I know, there shouldn't have been any data loss throughout this process,
Partitioning is **always **dangerous for your data, especially if you want to resize partitions.

> I'd hate to have to lose all of my data and format when, in theory, it's all there an untouched/unharmed
I suppose it's too late now to save your data. As far as i understood your posting, you have already deleted your partitions.

---

### Post by RLZIII on 2009-11-05
What I want to do is resize the Windows XP partition, the only one on the drive.  The setup before I used fdisk was a very small amount of unallocated space in the first (a few KB, not sure why), the partition I wanted to take up the whole drive, and then more unallocated space at the end.  I haven't used GParted or ntfsresize for anything yet, I've only used fdisk.

And I want to keep the middle partition without losing data, as I already have Windows XP on side partition.  There is no Windows installing taking place.

After using fdisk and rebooting, I get an error that says there's no OS found.

Hopefully that clears up some stuff.

---

### Post by hal10000 on 2009-11-05
Let's go back to your fdisk listing and see what you did:

```
Command (m for help): d
Selected partition 1


```
----> you deleted partition 1

```
Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1

```
----> you created a new primary partition

```

First cylinder (1-9729, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-9729, default 9729): 
Using default value 9729

```
----> you choose the **whole ** disk space (from the first cylinder No. 1 up to the last cylinder No. 9729 for this new partition

```

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 07 
Changed system type of partition 1 to 7 (HPFS/NTFS)

```
----> you choose NTFS as filesystem

```

Command (m for help): p

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dc770

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

```
----> you print out your partition table and as you can see, it contains only one partition, particularly the one you created with the upper commands.

Any data previously stored on your harddisk is **lost**
With a little luck (if you did'nt write anything to your new partition) you can get your partitions back with the [COLOR="Red"]testdisk [/COLOR] utility.

btw., you can't resize a pertition with fdisk, you'll need parted (or gparted, which has a nice gui) to do this. Don't use fdisk at all, it's a buggy program that does fuzzy things, parted is much better.

[EDIT] After using fdisk you still have to format your new partition with ntfs:
```

sudo mkfs.ntfs /dev/sda1

```

---

### Post by RLZIII on 2009-11-05
All the documentation I read about ntfsresize said that, in order to resize a partition, I needed to go through said steps with fdisk.  I've only been running Ubuntu through a USB drive, so the partitions/hard drive shouldn't have been touched.  Would you mind telling me how to go about restoring the partitions through testdisk?

EDIT: Even [here](http://man.linux-ntfs.org/ntfsresize.8.html) (under the Enlargement section), it says that I must first use fdisk to delete the partition and then enlarge it before enlarging the filesystem (via ntfsresize).  Is there maybe just a step that I missed?  Will using the "mkfs.ntfs" command for sure wipe the data on said partition?  Or is that perhaps the extra step I need to perform in order to use ntfsresize?

---

### Post by RLZIII on 2009-11-05
Well, I have found and solved the problem.  When I deleted the partition with fdisk, I started it at the first cylinder, which apparently was incorrect when dealing with Windows XP.

In fdisk, typing the command "u" will change the  reliable sector unit from the default cylinder one.  This showed me that I was starting the new partition at 63, when it should be started at 2048.

For archive purposes:

```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 9729.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): u
Changing display/entry units to sectors

Command (m for help): d
Selected partition 1

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First sector (63-156301487, default 63): 1
Value out of range.
First sector (63-156301487, default 63): 2048
Last sector, +sectors or +size{K,M,G} (2048-156301487, default 156301487): 
Using default value 156301487

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 7
Changed system type of partition 1 to 7 (HPFS/NTFS)

Command (m for help): a
Partition number (1-4): 1

Command (m for help): p

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000dc770

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   156301487    78149720    7  HPFS/NTFS

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

```

EDIT: Alright, now after rebooting and simply running "sudo ntfsresize -b -f /dev/sda1" through the terminal, I have everything up and running.  I guess I should have payed more attention at the starting cylinder to begin with.

---

### Post by hal10000 on 2009-11-05
I use fdisk only to print a partition table, which does no changes on the harddisk. For partitioning, formatting, resizing and similar tasks i always use gparted (or parted if i only have a command line). Both programs use ntfsresize as a backend and you don't have to first delete and then recreate the partitions. gparted does this all in one step, you just need to relocate the space with your mouse button.

If you want to restore your partitions with testdisk, then you better **don't perform** [COLOR="Red"]mkfs.ntfs[/COLOR]

testdisk is a very powerful tool to restore partitions and files, but i'm a little bit afraid of using it on my system when i don' really have to do such tasks, because a little mistake could make my system unusable. And the last time i used it was some months ago, so i can't remember all the stept you would have to perform.

But you can find a very detailed documentation for testdisk here: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I hope this can help you out.

Good luck

---


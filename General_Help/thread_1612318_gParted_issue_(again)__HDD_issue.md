---
title: "gParted issue (again) / HDD issue"
date: 2010-11-03
forum: General Help
---

### Post by iCHRYST on 2010-11-03
Hello again everyone.

As per my previous [thread]("http://ubuntuforums.org/showthread.php?t=1610503") I'm still having troubles with gParted.

I was converting the last 300GB of my drive to ext4 when a sudden power outage occurred. Upon the power comming back on, I quickly checked my system and discovered that the entire drive was converted to ext4 - when I knew that it wasn't. So upon checking Disk Utlity and the properties of the drive I discovered that the drive is only 916.9GB in size (I thought the drive would at least be 950GB) and that there is a folder lost+found located on the drive which is locked and I have no access to. The folder itself contains 46.8GB of data which I cannot access.

I have tried reformatting the drive to ext4 (after backing up the bare essentials of what I needed to a measly DVD). However, even after reformatting the drive and restarting multiple times the folder is still there.

I have tried to open gParted to see if there is any unallocated space on the drive, but during the startup process (when it checks for all media on the system) it suddenly closes with no warning nor prompts.

What I want to ask is - have a bricked my hdd/system? Is there anything I can do to fix the problem I have gotten myself into?

Kind regards,
iCHRYST.

*EDIT: I am not sure if this is of any help, however, I still need to manually mount the drive every time I restart the computer. My initial train of thought (which was probably wrong) was if I had an ext4 hdd I wouldn't need to mount the drive every time I turn the computer and could instantly access my music via Rhythmbox.

---

### Post by TNT1 on 2010-11-03
use gparted and create a new partition table. That will for sure delete the folder you speak of. It will delete everything, and then you can format to ext4

---

### Post by iCHRYST on 2010-11-03
> **TNT1 said:**
> use gparted and create a new partition table. That will for sure delete the folder you speak of. It will delete everything, and then you can format to ext4

I can't boot gParted however. It starts to scan for devices/media/hdd's and closes instantly without any form of warning.

---

### Post by TNT1 on 2010-11-03
> **iCHRYST said:**
> I can't boot gParted however. It starts to scan for devices/media/hdd's and closes instantly without any form of warning.

Oh. Boot a livecd and use gparted from there?

---

### Post by Quackers on 2010-11-03
You could try booting from the live cd, then installing and then running testdisk. People have had a lot of success recovering partitions with it.

---

### Post by iCHRYST on 2010-11-03
> **Quackers said:**
> You could try booting from the live cd, then installing and then running testdisk. People have had a lot of success recovering partitions with it.

I booted up the live disk, and it said that all the partitions were there and that it was 1TB in size. I installed testdisk and I'm running scans now. However it's not really finding anything.

When I formated the disk to FAT the folder was gone, yet when I formatted back to ext4 the file has returned.

---

### Post by srs5694 on 2010-11-03
> **iCHRYST said:**
> So upon checking Disk Utlity and the properties of the drive I discovered that the drive is only 916.9GB in size (I thought the drive would at least be 950GB)

This is probably an effect of the 5% of disk space that's reserved by ext2/3/4 by default, or possibly an effect of a confusion of [gigabytes vs. gibibytes.](http://physics.nist.gov/cuu/Units/binary.html) More precision in reporting is necessary to be sure. If you need help, post the output of the following commands, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility:

```

df
fdisk -lu

```

> and that there is a folder lost+found located on the drive which is locked and I have no access to. The folder itself contains 46.8GB of data which I cannot access.

The lost+found directory is a standard feature of the ext2/3/4 filesystems; it will *always* be present on such a filesystem. It's normally empty, but it will contain files recovered by fsck if that utility finds "lost" files when it's run.

You report using various extreme measures to get rid of lost+found, but you don't say if any of these measures reduced the amount of data it contained, or for that matter how you've determined that it's holding 46.8 GB of data. If this directory is now empty, you shouldn't worry about it; or if you're deeply offended by the presence of this directory, switch to another filesystem; IIRC, ReiserFS, JFS, and XFS all don't use this directory. If you've still got 46.8 GB of data in lost+found, please specify how you're making that determination.

Also, partition-level maintenance (that is, deleting and re-creating an entire partition or partition table) is overkill for dealing with filesystem-level problems. Filesystems reside within partitions, and any filesystem-level problem *can* be dealt with by filesystem-level tools (fsck, mkfs, etc.). Deleting and re-creating a partition often forces use of such tools to make the disk usable again, but otherwise does nothing useful. Partition-level maintenance is necessary if there are partition problems (partitions are too big or too small, you need to add new partitions, etc.).

> *EDIT: I am not sure if this is of any help, however, I still need to manually mount the drive every time I restart the computer. My initial train of thought (which was probably wrong) was if I had an ext4 hdd I wouldn't need to mount the drive every time I turn the computer and could instantly access my music via Rhythmbox.

To have a partition mount whenever you boot the computer, you need to create an /etc/fstab entry, like this:

```

UUID=07ed5fde-41eb-4f69-b431-a64b8ffb6c28  /mnt/extra  ext4  defaults  1 2

```

You need to adjust the UUID value (which you can obtain by typing "sudo blkid /dev/sdb1", substituting the appropriate device file for "/dev/sdb1"), set the mount point (/mnt/extra here) to whatever you like, and create a suitable mount point (/mnt/extra here).

The GNOME desktop environment normally auto-mounts partitions, but if you're using another desktop environment that won't work. It also won't work if you don't log in at the console but instead want to run the computer as a file server or the like.

---

### Post by ezsit on 2010-11-03
Whenever you format a drive with ext2, ext3, and ext4 (and probably other unix style filesystems) you get a Lost+Found folder that is for root use only. When I format drives I always get a Lost+Found folder but it is usually empty, taking only several kb of space.

---

### Post by iCHRYST on 2010-11-03
> **Quackers said:**
> You could try booting from the live cd, then  installing and then running testdisk. People have had a lot of success  recovering partitions with it.

I ran testdisk, it found 2 partions (when there should only be one) - however, when I try searching for files it says that the partion is damaged. I can't find any clear option to recover it.


@srs5694; I run the commands as you said I've copied and pasted the details below between code BBCode. I don't know how to make the data more presentable to you as I am unsure of what I am looking at, sorry.

```

Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sda1            465605320   4367696 437586248   1% /
none                   1919392       220   1919172   1% /dev
none                   1927492       160   1927332   1% /dev/shm
none                   1927492       212   1927280   1% /var/run
none                   1927492         0   1927492   0% /var/lock
none                 465605320   4367696 437586248   1% /var/lib/ureadahead/debugfs
/home/joshua/.Private
                     465605320   4367696 437586248   1% /home/joshua
/dev/sdb1            961432072    204436 912389636   1% /media/ZION


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000179df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   946057215   473027584   83  Linux
/dev/sda2       946059262   976771071    15355905    5  Extended
/dev/sda5       946059264   976771071    15355904   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007e643

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001   83  Linux

```

> **srs5694 said:**
> 
You report using various extreme measures to get rid of lost+found, but you don't say if any of these measures reduced the amount of data it contained, or for that matter how you've determined that it's holding 46.8 GB of data. If this directory is now empty, you shouldn't worry about it; or if you're deeply offended by the presence of this directory, switch to another filesystem; IIRC, ReiserFS, JFS, and XFS all don't use this directory. If you've still got 46.8 GB of data in lost+found, please specify how you're making that determination.

Nothing I have tried to do has increased, or decreased the size of the lost+found folder. I come to the assumption that it has data in it when I look at the properties of the drive (Right click > properties). It claims that there is used space on the drive.

I have attached a screenshot in this post incase it can give you more information than I can.

> **srs5694 said:**
> 
Also, partition-level maintenance (that is, deleting and re-creating an entire partition or partition table) is overkill for dealing with filesystem-level problems. Filesystems reside within partitions, and any filesystem-level problem *can* be dealt with by filesystem-level tools (fsck, mkfs, etc.). Deleting and re-creating a partition often forces use of such tools to make the disk usable again, but otherwise does nothing useful. Partition-level maintenance is necessary if there are partition problems (partitions are too big or too small, you need to add new partitions, etc.).

You learn something new every day. I didn't know that. I just thought creating new partitions just fixed it. Luckily I don't fix computers for a living. Haha!

Unfortunately I'm a linux noob. beside basic apt-get commands I don't know much about the terminal. However, I am very greatful for you assistance.

> **srs5694 said:**
> 
To have a partition mount whenever you boot the computer, you need to create an /etc/fstab entry, like this:

```

UUID=07ed5fde-41eb-4f69-b431-a64b8ffb6c28  /mnt/extra  ext4  defaults  1 2

```You need to adjust the UUID value (which you can obtain by typing "sudo blkid /dev/sdb1", substituting the appropriate device file for "/dev/sdb1"), set the mount point (/mnt/extra here) to whatever you like, and create a suitable mount point (/mnt/extra here).

Oh excellent! Thank you very much! I'll consider attempting this when I manage to restore my hdd slightly.

---

### Post by iCHRYST on 2010-11-04
I'm not trying to look impatient but I'm just bumping this thread to see if I could get some more advice. Thanks.

---

### Post by srs5694 on 2010-11-06
I don't think you've got 46 GB in lost+found; I think that 46 GB is actually just the 5% space that ext2/3/4 reserves for use by root. I'm not sure how Nautilus (if that's what produced the screen shot you attached) computes these things, though, so I could be wrong. If I'm right, the following command will reduce the reserved space to 0% (or you could change the percentage to something else):

```

sudo tune2fs -m 0 /dev/sdb1

```

---

### Post by alphaamanitin on 2010-11-06
Zero you drive out with the dd command and then reformat.  
```
sudo dd if=/dev/zero of=/dev/sdX bs=16M
```

X should be replaced with your drive, so something like sda.  That will fill the entire drive with zeros.  Everything will be gone, everything.  The if stands for input file, the of, output file, don't get them mixed up, and make sure you use the right drive ID if you have a dual boot or multiple hard drive.  You won't get any indication it is working besides a blinking cursor.  To check it follow the instructions found here:

[http://linuxcommando.blogspot.com/2008/06/show-progress-during-dd-copy.html](http://linuxcommando.blogspot.com/2008/06/show-progress-during-dd-copy.html)

Then redo the partitions from there.  Oh, use a liveCD to do the dd command, and the partitions.

AlphaA

---

### Post by srs5694 on 2010-11-06
I don't think zeroing out the drive as alphaamanitin suggests is necessary or desirable at this point. Unless I've overlooked something (which is a distinct possibility), the only outstanding problem iCHRYST is having is the difference between the allocated and available space. As I wrote, that's almost certainly just an issue of the 5% reserved space in ext2/3/4. Zeroing the drive will take a lot of time and will have *no* effect on this issue; only using tune2fs or changing the percentage when creating a new filesystem with mke2fs (or some other utility) will do anything about this issue.

---

### Post by iCHRYST on 2010-11-13
Sorry for the late reply everyone. I decided to cut my losses and just mount the drive at /home and went ahead and hid the lost+found folder by adding a period before it.

Thank you very much for all the support and generous help. :)

---

### Post by zaphod777 on 2010-11-14
> **iCHRYST said:**
> Sorry for the late reply everyone. I decided to cut my losses and just mount the drive at /home and went ahead and hid the lost+found folder by adding a period before it.

Thank you very much for all the support and generous help. :)

Not sure but adding the "." may cause problems since the FS doesn't expect it to be there. You would be better creating a folder called "home" on the drive and mounting that to your home folder. then you won't see that folder. 

even your primary HDD has this folder it is just on /

---


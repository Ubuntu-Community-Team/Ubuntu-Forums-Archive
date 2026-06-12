---
title: "Linux changed NTFS drive to RAW"
date: 2009-10-16
forum: General Help
---

### Post by dreamweaverdreams on 2009-10-16
The drive was NTFS and after backing up all my files to it I couldn't access it in Win 7. I used EXTfsd which reported that the drive filesystem had been changed to RAW. I can still access the drive in Linux but not windows. Any ideas why it changed to RAW and how I can make it accessible in Windows and is the data safe?

---

### Post by phillw on 2009-10-16
> **dreamweaverdreams said:**
> The drive was NTFS and after backing up all my files to it I couldn't access it in Win 7. I used EXTfsd which reported that the drive filesystem had been changed to RAW. I can still access the drive in Linux but not windows. Any ideas why it changed to RAW and how I can make it accessible in Windows and is the data safe?

You don't say what you were backing up and where you said to back it up.

Were you backing up windows or ubuntu ?

which partition did you tell it to back up to

which partitions do you have, and what was stored on them ?

Phill.

---

### Post by dreamweaverdreams on 2009-10-16
I was backing up pictures, documents software etc, no system files from an old 500gb external HD to a 500gb partition on a esata 1.5 tb drive using Ubuntu. I also put some music files on a second 500gb partition. There are three partitions only two have data on them. Windows can read the second partition with the music on it and the drive with nothing on it.

---

### Post by krieg5521 on 2009-10-16
first of all,i think ubuntu is the most vague useless software ever created....WINDOWS rules!!it has a much better gui than poor ubuntu....not only that,in ubuntu,every damn thing is controlled by the dumb terminal.....but in windows,each part of the software is divided into subsections....plus windows provideds more user friendly options rathere than the gibberish ubuntu offers!!!using ubuntu is so much more complicated than windows that even a donkey would tell that....all in all,UBUNTU SUCKS!!!SO LONG LOSERS!

---

### Post by zzzBrett on 2009-10-16
> **krieg5521 said:**
> first of all,i think ubuntu is the most vague useless software ever created....WINDOWS rules!!it has a much better gui than poor ubuntu....not only that,in ubuntu,every damn thing is controlled by the dumb terminal.....but in windows,each part of the software is divided into subsections....plus windows provideds more user friendly options rathere than the gibberish ubuntu offers!!!using ubuntu is so much more complicated than windows that even a donkey would tell that....all in all,UBUNTU SUCKS!!!SO LONG LOSERS!


...wow.

You will not be missed.

---

### Post by StuartN on 2009-10-16
> **krieg5521 said:**
> even a donkey would tell that

Someone called?

Anyways, **dreamweaverdreams**, how was the partition mounted when you backed up to it, and what command did you use to back up?

It might also help to post the output (with this partition mounted) from the commands **mount**, **df** and **sudo fdisk -l** and point out which partition is the one you are having trouble with.

---

### Post by dreamweaverdreams on 2009-10-16
Sorry if I get this wrong am quite new to Linux. I was using Nautilus filemanager. I shift/dragged and dropped the files from the Ext drive to the partition on the esata drive.
This is the output from mount
dreamweaver@Sentinel:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dreamweaver/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dreamweaver)
/dev/sdc1 on /media/Lacie 250 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1 on /media/New Volume type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd2 on /media/New Volume_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd3 on /media/New Volume__ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
This is the output from df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            467928144 118579792 325578984  27% /
tmpfs                  4034172         0   4034172   0% /lib/init/rw
varrun                 4034172       108   4034064   1% /var/run
varlock                4034172         0   4034172   0% /var/lock
udev                   4034172       216   4033956   1% /dev
tmpfs                  4034172       120   4034052   1% /dev/shm
lrm                    4034172      2560   4031612   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sdc1            244196000     97216 244098784   1% /media/Lacie 250
/dev/sdd1            511999996 145558356 366441640  29% /media/New Volume
/dev/sdd2            511999996  44184628 467815368   9% /media/New Volume_
/dev/sdd3            441135100 339079540 102055560  77% /media/New Volume__
This is the output from sudo fdisk -l
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1136a2a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       59917   481177600    7  HPFS/NTFS
/dev/sda3           59918      121601   495476730    5  Extended
/dev/sda5           59918      119100   475387416   83  Linux
/dev/sda6          119101      121601    20089251   82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801   83  Linux

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5a0c3165

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       63742   512000000    7  HPFS/NTFS
/dev/sdd2           63742      127483   512000000    7  HPFS/NTFS
/dev/sdd3          127483      182402   441135104    7  HPFS/NTFS

The partition I'm having trouble with is sdd1. Here it says that it's HPFS/NTFS but when I looked at it from windows using ext2FSD it said the filesystem was RAW but the other two partitions were HPFS/NTFS.

---

### Post by StuartN on 2009-10-16
> **dreamweaverdreams said:**
> 
/dev/sdd1            511999996 145558356 366441640  29% /media/New Volume
/dev/sdd2            511999996  44184628 467815368   9% /media/New Volume_
/dev/sdd3            441135100 339079540 102055560  77% /media/New Volume__

So these are a 511 GB (29% free), 511 GB (9% free) and 441 GB (77% free), all labelled New Volume. The problem you have in Windows is with the first 511 GB (29% free) drive.

I can see nothing wrong with any of these. You could run Gparted, unmount the drives (you can do that inside Gparted), and run the disk check. You could also change the labels while you are in there.
Gparted is at the System->Administration->Partition editor.

Why are you using EXTfsd? If these partitions are NTFS, then Windows should be able to read them natively.

---

### Post by dreamweaverdreams on 2009-10-16
I must have made a mistake there sorry. The problem I am having is with the drive with only 9% free space so sdd2.
I formatted an external hdd drive earlier with gparted as ext3 but now I can't access it  because it says I don't have permission. Is that something that could happen if I run a disk check?
I was using EXTfsd to try and read the drive while in windows. Windows reads the other two drives with no problem which I was I am so bemused.

---

### Post by StuartN on 2009-10-16
> **dreamweaverdreams said:**
> I must have made a mistake there sorry. The problem I am having is with the drive with only 9% free space so sdd2.

I would label those partitions something other than New Volume so that you can tell them apart. As for the inability of Windows to read the partition, it seems hard to fix it with Ubuntu if you can't find any problem in Ubuntu.

---

### Post by dreamweaverdreams on 2009-10-16
Unfortunately, Gparted won't let me rename them. It says 'unable to read the contents of this file system. Because of this some operations may be unavailable.'
I agree it seems odd that it does this especially as it will read the other two drives and why does EXTfsd see it as RAW. The other program, I think it was ext2ifs, won't read them at all in windows.
So if this is a windows problem I can't see me actually being able to solve it.
If I could format and still access the drives using ext3 I would do that but as I can't access the drive after I 've formatted it I seem to be scuppered both ways.

---

### Post by StuartN on 2009-10-16
> **dreamweaverdreams said:**
> Unfortunately, Gparted won't let me rename them. It says 'unable to read the contents of this file system. Because of this some operations may be unavailable.'

I guess that includes disk checking? If so, then install ntfsprogs and you should be able to both check and relabel the NTFS partitions with Gparted.

---

### Post by dreamweaverdreams on 2009-10-29
Thanks very much for the info Stuart, that worked perfectly.

---


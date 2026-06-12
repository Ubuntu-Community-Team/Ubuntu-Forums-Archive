---
title: "Help Ubuntu can't mount my hard drive"
date: 2012-08-08
forum: General Help
---

### Post by fantasygirl on 2012-08-08
Hi I registered on this forum because I need some help with backing up my hard drive with Ubuntu.

I am using Ubuntu 10.04 (burnt onto cd) and it's all working fine, but it doesn't show my hard drive in Places/Computer so I can't get a back up of my hard drive. My hard drive does show up in Disk Utility and Gparted though.

Moreover, I can't seem to mount my hard drive using the commands. I have tried different commands, all with no success. I think it's because my hard drive is partitionless but I'm not sure, I'm really a novice at this which is why I need help. NB: The reason why I need to back up my hard drive with Ubuntu is because I can't boot my computer into WIndows (I can't access my files, data, start menu, programs, etc). 

So, my question is, can somebody help me? Has anyone had the same problems like mine and what did you do to solve it? If you need more info, please feel free to contact me or reply. Thank you in advance!
Below I have pasted what I've been doing in Terminal (I'm sorry. it's really long..) and I have also included a screenshot of the Disk Utility:

ubuntu@ubuntu:~$ sudo /bin/bash
root@ubuntu:~# mkdir /media/disk
root@ubuntu:~# mount -t ntfs-3g mkdir /media/disk /media/disk -o force
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
root@ubuntu:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1275       31055   239210496    7  HPFS/NTFS
/dev/sda2           31055       60802   238941184    7  HPFS/NTFS
/dev/sda3   ?      168620      364326  1572012319   3e  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?      194663      194663           0   66  Unknown
Partition 4 does not end on cylinder boundary.
root@ubuntu:~# mount -t ntfs-3g /dev/sda1 /media/disk -o force
ntfs-3g: Failed to access volume '/dev/sda1': No such file or directory

ntfs-3g 2010.3.6 external FUSE 28 - Third Generation NTFS Driver
        Configuration type 1, XATTRS are on, POSIX ACLS are off

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2010 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)
root@ubuntu:~# ntfs-3g /dev/sda1 /mnt/windows
ntfs-3g: Failed to access volume '/dev/sda1': No such file or directory

ntfs-3g 2010.3.6 external FUSE 28 - Third Generation NTFS Driver
        Configuration type 1, XATTRS are on, POSIX ACLS are off

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2010 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)
root@ubuntu:~# sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1275       31055   239210496    7  HPFS/NTFS
/dev/sda2           31055       60802   238941184    7  HPFS/NTFS
/dev/sda3   ?      168620      364326  1572012319   3e  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?      194663      194663           0   66  Unknown
Partition 4 does not end on cylinder boundary.
root@ubuntu:~# fsck.ext4 -f /dev/sda

e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@ubuntu:~# 
root@ubuntu:~# e2fsck
Usage: e2fsck [-panyrcdfvtDFV] [-b superblock] [-B blocksize]
        [-I inode_buffer_blocks] [-P process_inode_size]
        [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
        [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
root@ubuntu:~# n
n: command not found
root@ubuntu:~# -n
-n: command not found
root@ubuntu:~# e2fsck
Usage: e2fsck [-panyrcdfvtDFV] [-b superblock] [-B blocksize]
        [-I inode_buffer_blocks] [-P process_inode_size]
        [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
        [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
root@ubuntu:~# -n
-n: command not found
root@ubuntu:~# -f
-f: command not found
root@ubuntu:~# f
f: command not found
root@ubuntu:~# e2fsck -n
Usage: e2fsck [-panyrcdfvtDFV] [-b superblock] [-B blocksize]
        [-I inode_buffer_blocks] [-P process_inode_size]
        [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
        [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
root@ubuntu:~# e2fsck n
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: No such file or directory while trying to open n

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@ubuntu:~# resize2fs
resize2fs 1.41.11 (14-Mar-2010)
Usage: resize2fs [-d debug_flags] [-f] [-F] [-M] [-P] [-p] device [new_size]

root@ubuntu:~# fsck.ext4 -f /dev/sda
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@ubuntu:~# sudo e2fsck /dev/sdax
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: No such file or directory while trying to open /dev/sdax

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@ubuntu:~# sudo e2fsck /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: No such file or directory while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@ubuntu:~# sudo e2fsck /dev/sda2
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@ubuntu:~# sudo mount /dev/sda /media/openSpaceI
mount: mount point /media/openSpaceI does not exist
root@ubuntu:~# sudo mount /dev/sda1 /media/openSpaceI
mount: mount point /media/openSpaceI does not exist
root@ubuntu:~# sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1275       31055   239210496    7  HPFS/NTFS
/dev/sda2           31055       60802   238941184    7  HPFS/NTFS
/dev/sda3   ?      168620      364326  1572012319   3e  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?      194663      194663           0   66  Unknown
Partition 4 does not end on cylinder boundary.
root@ubuntu:~# sudo mkdir /media/newhd
root@ubuntu:~# sudo mount /dev/sdb1 /media/newhd
mount: special device /dev/sdb1 does not exist
root@ubuntu:~# df -H
Filesystem             Size   Used  Avail Use% Mounted on
aufs                   1.1G    38M   1.1G   4% /
none                   1.1G   320k   1.1G   1% /dev
/dev/sr0               729M   729M      0 100% /cdrom
/dev/loop0             700M   700M      0 100% /rofs
none                   1.1G   103k   1.1G   1% /dev/shm
tmpfs                  1.1G    33k   1.1G   1% /tmp
none                   1.1G    82k   1.1G   1% /var/run
none                   1.1G   4.1k   1.1G   1% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
root@ubuntu:~# sudo mkdir -p /media/c
root@ubuntu:~# sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1275       31055   239210496    7  HPFS/NTFS
/dev/sda2           31055       60802   238941184    7  HPFS/NTFS
/dev/sda3   ?      168620      364326  1572012319   3e  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?      194663      194663           0   66  Unknown
Partition 4 does not end on cylinder boundary.
root@ubuntu:~# sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda1 /media/c
ntfs-3g: Failed to access volume '/dev/sda1': No such file or directory

ntfs-3g 2010.3.6 external FUSE 28 - Third Generation NTFS Driver
        Configuration type 1, XATTRS are on, POSIX ACLS are off

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2010 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)
root@ubuntu:~# sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda /media/c
NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
root@ubuntu:~# sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda2 /media/c
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
root@ubuntu:~# sudo mkdir /media/newhd
mkdir: cannot create directory `/media/newhd': File exists
root@ubuntu:~# sudo mount /dev/sda 
mount: can't find /dev/sda in /etc/fstab or /etc/mtab
root@ubuntu:~# sudo mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
root@ubuntu:~# sudo mount /dev/sda1 /media/newhd
mount: special device /dev/sda1 does not exist

---

### Post by Mark Phelps on 2012-08-08
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of GetDataBack for NTFS from Runtime Software in MS Windows.
5) Run GetDataBack and select the option to find Deleted files.
6) When done, browse the filesystem in the app to see if your directories and files were found.  If so, view some to confirm the contents are intact.
7) If they are, you will have to purchase GetDataBack to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

### Post by rukiaEnix on 2012-08-08
You don't just simply mkdir over a mount on the same dir:

> 
root@ubuntu:~# mount -t ntfs-3g mkdir /media/disk /media/disk -o force
First check your disk like this as root or with sudo: 

```

fdisk -l

```Now you know your /dev/disk, might be something like sda1 or hda1, hda[n]. For explaining the commands I'll use as example that your disk is the sda1

Then try this as root or with sudo:

```

mount -t ntfs /dev/sda1 /media/disk

```

---

### Post by fantasygirl on 2012-08-08
THank you for your reply Rukia, but I have already tried that. THis is what I get:

ubuntu@ubuntu:~$ sudo /bin/bash
root@ubuntu:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1275       31055   239210496    7  HPFS/NTFS
/dev/sda2           31055       60802   238941184    7  HPFS/NTFS
/dev/sda3   ?      168620      364326  1572012319   3e  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?      194663      194663           0   66  Unknown
Partition 4 does not end on cylinder boundary.
root@ubuntu:~# sudo mount -t ntfs /dev/sda1 /media/disk
ntfs-3g: Failed to access volume '/dev/sda1': No such file or directory

ntfs-3g 2010.3.6 external FUSE 28 - Third Generation NTFS Driver
        Configuration type 1, XATTRS are on, POSIX ACLS are off

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2010 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)
root@ubuntu:~# sudo mount -t ntfs /dev/sda /media/disk
NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---

### Post by rukiaEnix on 2012-08-08
I'm starting to thik you DO have something wrong with your disk -.-

Try testdisk and analyze your disk with it. ([http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download))

---

### Post by fantasygirl on 2012-08-08
THank you for your reply Mark,

I tried connecting my hard drive to another computer, but when I started up the computer, there was only a black screen with ''Invalid partition table''. WHen I entered BIOS the boot device options didn't show my hard drive. I'm not sure where it went wrong because they were both Acer computers with the same kind of hard drives. 

Do you btw mean that my hard drive can't be accessed with ubuntu and that there is no other inexpensive way ?

---

### Post by rukiaEnix on 2012-08-08
Why don't you try testdisk? -.-

---

### Post by fantasygirl on 2012-08-08
Hi RUkia,
I'm sorry, I spent the last hour trying to figure out why it wouldn't let me run testdisk but it's all fine now.
I ran the test and I have included a few screenshots of the test. It appears that the filesystem of one partition is damaged (see screenshot of partition 2?). I put a question mark there because I don't know if it's actually called the second partition or not, but it was the second on the list in the quicksearch,

I'm now running the deeper search. I will get back to you when it's finished cause this will take a while.

---

### Post by fantasygirl on 2012-08-09
IN the deeper search I found that the second, fourth and seventh partitions had damaged filesystems. I'm supposed to change the status of the partitions now but I don't know which one I should change to which status. Can somebody explain this to me?

---

### Post by fantasygirl on 2012-08-09
Oops, I forgot to include the screenshot of the deeper search.

---

### Post by fantasygirl on 2012-08-09
I made screenshots of the list of files that I get of the partitions in deeper search. Any help is greatly appreciated :) Am I supposed to change all D statusses to L statusses before I write the partition structure? What am I supposed to do?

---

### Post by fantasygirl on 2012-08-09
Screenshots of the last two partitions.

---

### Post by rukiaEnix on 2012-08-09
OK, I see you can recover your files with photorec, I recommend you to recover your files with this utility and then try changing the status of the partitions. What more damage can happen if it's already damage? -.-...

---

### Post by fantasygirl on 2012-08-09
Hi  Rukia,

DO you mean I don't continue with testdisk before I've used photorec first? SO I stop after the deeper search without changing the partitions?

---

### Post by rukiaEnix on 2012-08-09
Yes, better to stop the change of partitions. First recover your data. What if something worst happens? 

Recover it first and then you continue with the changing.

---

### Post by fantasygirl on 2012-08-09
Alright thanks. I'll give it a go tonight and let you know how it goes.

---

### Post by fantasygirl on 2012-08-09
I think I restored my files with photorec! Am I supposed to change the statusses of the partitions in testdisk  (after the deeper search) now? How should I change them? Am I supposed to change all D statusses to L statusses? Thanks so much for your help.

---

### Post by fantasygirl on 2012-08-09
(I want to be able to boot into WIndows and access my files)

---

### Post by rukiaEnix on 2012-08-10
Where did you backup your files?

Also I've been thinking if it would be better to format those partitions so your Windows system partition doesn't take any damage.

---

### Post by fantasygirl on 2012-08-10
HI Rukia,

I backed up the files on my 16 GB memory card. But if I format them won't I lose all of my files?

---

### Post by rukiaEnix on 2012-08-13
Just format the partitions that are damaged. If you have already backup your data you should not have problem, it will be lose from the partitions but now you have it all in your memory card.

But just the damaged partitions. Be careful with your Windows partition that's still working.

---


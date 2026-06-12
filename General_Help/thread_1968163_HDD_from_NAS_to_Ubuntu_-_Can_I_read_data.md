---
title: "HDD from NAS to Ubuntu - Can I read data?"
date: 2012-04-28
forum: General Help
---

### Post by GFM on 2012-04-28
Hello,

I have read many threads about this topic and saw that somebody succeeded, However, I replicated the actions and failed.

Here is the point: I extracted one of two HDDs from a NAS and I now want to access it through Ubuntu. The drive shows in "Computer" as an array, but when trying to access it, an error message appears: Unable to mount location --> Can't mount file. 

The command: sudo fdisk -l, produces the following result:

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x83162b86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  3907026943  1953512448    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83162bfd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   125042687    62417920    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  3907029167  1953514583+  ee  GPT

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5ed77bc2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   625137344   312568641    7  HPFS/NTFS/exFAT


The HDD I am trying to access appears to be the sdc one in the list above. Note that this message may be important (whatever it means) :WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


This solution looked the most promising: **sudo mount -t xfs -o ro /dev/sdc/mnt**, but it only produced this:

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

Note that I do not know what I am doing as I only installed Ubuntu today, with ZERO previous exposure to it. Hence, I write code that means nothing to me and therefore may well be trying bad solutions...

Any idea on how to access data on this drive?

Thanks,
GFM

---

### Post by GFM on 2012-04-30
So, no takers for this one, I guess...

GF

---

### Post by steeldriver on 2012-04-30
looks like you're trying to mount the whole device, can you use parted to look at the actual partitions / fs types?

[COLOR=Blue]_[How to mount a partition on a disk that has an EFI GPT partition table in Debian GNU/Linux]("http://www.pjc.me.uk/efi-gpt/index.html")_[/COLOR]

also there's a typo in your mount command, you're missing a space between  your block device and mount point i.e. /dev/sdcX /mnt not /dev/sdcX/mnt

---

### Post by GFM on 2012-05-01
> **steeldriver said:**
> looks like you're trying to mount the whole device, can you use parted to look at the actual partitions / fs types?

[COLOR=Blue]_[How to mount a partition on a disk that has an EFI GPT partition table in Debian GNU/Linux]("http://www.pjc.me.uk/efi-gpt/index.html")_[/COLOR]

also there's a typo in your mount command, you're missing a space between  your block device and mount point i.e. /dev/sdcX /mnt not /dev/sdcX/mnt


Thank you for the tips. The correct syntax produces the following:

ubuntu@ubuntu:~$ sudo mount -t xfs -o ro /dev/sdc /mnt
mount: /dev/sdc already mounted or /mnt busy

As for the partition mounting, I am going to try...

Thanks again
GF

---

### Post by GFM on 2012-05-01
Fist attempt: [B]sudo mount -t xfs -o ro /dev/sdc /mnt
[/B]Result:[B] mount: Structure needs cleaning
----------------------------------------------------------------------
[/B]
Second attempt: sudo mount -t xfs /dev/sdc3 /mnt 
 Result:[B]mount: Structure needs cleaning
-----------------------------------------------------------------------

[/B]The command:** sudo parted /dev/sdc print **produced the following result:

Model: WDC WD20 EADS-00S2B0 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      16.0MB  2064MB  2048MB  ext3                  raid
 2      2064MB  2576MB  512MB   linux-swap(v1)        raid
 3      2576MB  2000GB  1998GB                        raid
-----------------------------------------------------------------------------

The command: **sudo mount -t ext3 /dev/sdc1 /mnt**

Produces an empty line (i.e. it seems to work).

Repeating the command: [B]sudo mount -t ext3 /dev/sdc1 /mnt
[/B]
Produces: 
mount: /dev/sdc1 already mounted or /mnt busy
mount: according to mtab, /dev/sdc1 is already mounted on /mnt
---------------------------------------------------------------------------------------------------------

So, what type of partition is #3, given the the map does not specify it? How should I mount parition 3?

Thanks,
GF

---

### Post by steeldriver on 2012-05-01
OK so you pulled this from a _raid_ nas? I don't think that was clear from your original post

in that case you *may* be able to do it (I have never tried personally) - it's going to be a fair bit of work though, maybe a lot of work if you have LVM on top of the raid volume as well

let's hope someone more knowledgeable chimes in - if not you might want to start here ("Recovery of RAID and LVM2 Volumes"):

[http://www.linuxjournal.com/article/8874](http://www.linuxjournal.com/article/8874)

this is all assuming it is linux s/w raid - if it's some kind of proprietary h/w raid you may be sol

---

### Post by GFM on 2012-05-02
> **steeldriver said:**
> OK so you pulled this from a _raid_ nas? I don't think that was clear from your original post 
 
I don't know - The NAS I use has 2 identical HDDs in it and there is no redundacy setup. The HDDs are 2TB each and the NAS is called eTrayz ([HERE]("http://www.xtreamer.net/etrayz/features.aspx")). From the feature list it seems that it is indeed a RAID NAS (whatever that means)...
 
GF

---

### Post by steeldriver on 2012-05-02
ok that sounds a lot like the Netgear box that I have (ReadyNas), which is supplied with a single HDD but 'automagically' mirrors it (i.e. goes into RAID-1) if you throw a drive in the second bay

if you still have access to the original box you *may* have better luck rebuilding the array there - otherwise afaik you will have to bite the bullet and follow the steps in the article I linked (with a bit of luck you *won't* have the same issues with conflicting LVM volume names)

if you google 'linux software raid data recovery' or 'linux software raid rebuild' you may find some better how-tos

good luck

---

### Post by GFM on 2012-05-02
> **steeldriver said:**
> ok that sounds a lot like the Netgear box that I have (ReadyNas), which is supplied with a single HDD but 'automagically' mirrors it (i.e. goes into RAID-1) if you throw a drive in the second bay
 
if you still have access to the original box you *may* have better luck rebuilding the array there - otherwise afaik you will have to bite the bullet and follow the steps in the article I linked (with a bit of luck you *won't* have the same issues with conflicting LVM volume names)
 
if you google 'linux software raid data recovery' or 'linux software raid rebuild' you may find some better how-tos
 
good luck
 
NOTE: the 2 drives are NOT mirrored. Each of them contains different data. In other words, the total capacity is the sum of the two drives.
 
As for the NAS, I do have access to it - but how do I rebuild from there? Can I write command lines somewhere??
 
Thank you,
GF

---

### Post by GFM on 2012-05-02
Would this solution be any good: [http://www.caldigit.com/RemoveGPT.asp](http://www.caldigit.com/RemoveGPT.asp) ?
 
GF

---

### Post by steeldriver on 2012-05-02
I don't think the GPT partition table is your problem (the original warning from fdisk is normal in this case), I would ignore that. You aren't trying to make the drive bootable, and parted read it just fine.

I honestly don't feel comfortable trying to advise you further (bad advice is worse than no advice imo) - it *may* be as simple as making sure you have the mdadm package (and possibly lvm2) installed and rebooting and seeing if it automatically detects the raid volume and going from there - I hope I've at least given you some keywords to search for

---

### Post by GFM on 2012-05-02
> **steeldriver said:**
> I don't think the GPT partition table is your problem (the original warning from fdisk is normal in this case), I would ignore that. You aren't trying to make the drive bootable, and parted read it just fine.
 
I honestly don't feel comfortable trying to advise you further (bad advice is worse than no advice imo) - it *may* be as simple as making sure you have the mdadm package (and possibly lvm2) installed and rebooting and seeing if it automatically detects the raid volume and going from there - I hope I've at least given you some keywords to search for
 
Understood - thank you VERY MUCH for your help.
 
GF

---


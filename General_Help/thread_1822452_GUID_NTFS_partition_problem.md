---
title: "GUID NTFS partition problem"
date: 2011-08-10
forum: General Help
---

### Post by gefthebest on 2011-08-10
Hi,

I have just lost a huge NTFS partition from an external RAID0 hard drive array and am trying to recover it.
I believe the problem might have occured when I left the drive connected when I booted in Windows 7, since the hard drive is 8TB and the partition 4TB there might have been some weird MBR protective thing, I am not very good with that. 
Anyways, the partition is marked unknown in ubuntu 11.04 Disk utility and I am unable to delete it too! (I was going to delete it and recover the data after)...: [http://mobiparty.net/img/DriveProb.png](http://mobiparty.net/img/DriveProb.png)

What can I do if I want to ultimately get the data on there (about 3TB of stuff...)

Thank you

---

### Post by oldfred on 2011-08-10
I thought Windows 7 correctly read gpt drives. Or did you boot from a MBR Windows 7 and it then was confused.

Paragrah below is not correct, It is type 7 in MBR, in gpt they do not have unique types, I believe.

It says it is Linux type. If you are sure it is NTFS, you could just try changing the type to 07 for NTFS with disk utility (not format). I do not know how to change in RAID if you have to use other tools to change those types of things. Both partition table has to have the type 7 and the boot sector has to be NTFS, otherwise it gets confused.

---

### Post by oldfred on 2011-08-10
Type is the same, I just created a NTFS partition and it is 0700:

```
fred@fred-MavericDT:~$ sudo parted -l
[sudo] password for fred: 
Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdd: 16.1GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name          Flags
 1      1049kB  2097kB  1049kB               KingstonData  bios_grub
 2      2097kB  7552MB  7550MB  ext4
 3      7552MB  15.0GB  7464MB  ext4
 4      15.0GB  16.1GB  1048MB  ntfs
```

```
fred@fred-MavericDT:~$ sudo gdisk -l /dev/sdd
GPT fdisk (gdisk) version 0.7.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdd: 31375360 sectors, 15.0 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): ECD862C9-27C6-44EF-846C-5272FE5A465F
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 31375326
Partitions will be aligned on 2048-sector boundaries
Total free space is 4029 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            4095   1024.0 KiB  EF02  KingstonData
   2            4096        14749695   7.0 GiB     0700  
   3        14749696        29327359   7.0 GiB     0700  
   4        29327360        31373311   999.0 MiB   0700  
fred@fred-MavericDT:~$ 
```

---

### Post by srs5694 on 2011-08-10
First, concerning type codes: Unfortunately, Linux has been using the same partition type code GUID (EBD0A0A2-B9E5-4433-87C0-68B6B72699C7) for its filesystem partitions as Windows has been using for its filesystem partitions for some time now. In gdisk, this type code shows up as "0700" under the "Code" column. In Palimpsest Disk Utility, it's reported as "Linux Basic Data Partition." In parted and GParted, the type code isn't reported at all; these tools look inside the partition and try to identify the filesystem it contains rather than report partition type codes.

Fortunately, this is changing. There's a new type code (0FC63DAF-8483-4772-8E79-3D69D8477DE4) for Linux filesystem partitions. This code is already available in gdisk 0.7.2, as type "8300". (I'm the author of gdisk, and I initiated the push to create this new type code.) It's not yet been added to libparted, but it should be soon. The patch I submitted for this has been tentatively accepted and will cause the parted utility to show Linux partitions with the new type code normally but will show partitions with the Windows type code as having the "msftdata flag" set. This is a bit awkward because of the design of libparted and the desire of the libparted developers to preserve the ability to set this type code on Linux partitions in case there are compatibility problems with other software. Given the various development delays, the soonest this change might make it to standard Ubuntu builds of libparted-based tools is with Ubuntu 11.10, but probably not until 12.04 or even later.

That said, I don't believe the type code is at the root of gefthebest's problem. The Palimpsest Disk Utility screen shot seems to indicate that the problem partition has a correct type code set but that the filesystem can't be recognized. I recommend the following procedure:


[list=1]
[*]Do a low-level backup of the partition, as in "sudo dd if=/dev/sdb1 of=/backup/file.img". This will, unfortunately, require a huge amount of disk space. Compressing the backup as it's done might help, depending on what's stored on the disk. If you lack sufficient disk space for a backup, then you can proceed without it, but that increases the risk of your losing some or all of the data on the disk.
[*]Reboot into Windows Vista or later and run CHKDSK (or its GUI equivalent) on the disk. Windows Vista and 7 can handle GPT just fine on non-boot disks. When you're done, reboot correctly; *do not* simply hit the power button on the computer, and *do not* unplug the disk without properly unmounting it.
[*]If you continue to have problems, repeat the previous step another time or two and/or look for more advanced Windows filesystem recovery tools.
[*]If you still have no luck, try using [PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) in Linux to recover individual files. There are Windows tools to do the same thing, but I don't know their names or reputations. Be aware that this will be a very tedious task, since you're likely to get files with incorrect filenames and perhaps no directory structure. I've seen claims that some Windows recovery tools can recover filenames.
[*]If you want to delete the partition, try using [GPT fdisk (gdisk);](http://www.rodsbooks.com/gdisk/) it should do the job with no problem.
[/list]

---

### Post by gefthebest on 2011-08-11
Thank you very much for those replies!

However, regarding this:

> **srs5694 said:**
> Reboot into Windows Vista or later and run CHKDSK (or its GUI equivalent) on the disk. Windows Vista and 7 can handle GPT just fine on non-boot disks. When you're done, reboot correctly; *do not* simply hit the power button on the computer, and *do not* unplug the disk without properly unmounting it.

The reason for my recent change to Ubuntu as main OS for my PC is because Windows 7 did not seem to like at all partitioning of my 8TB drive and reseted it in a sense at each reboot: I created partitions, copied over files but each time I rebooted the partitions were seen as unformated in Windows, so I changed to Ubuntu....

So I am not sure whether the CHKDSK will work as planned when trying the procedure suggested...

Thank you

---

### Post by gefthebest on 2011-08-11
> **oldfred said:**
> 
```
fred@fred-MavericDT:~$ sudo parted -l
``````
fred@fred-MavericDT:~$ sudo gdisk -l /dev/sdd
GPT fdisk (gdisk) version 0.7.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdd: 31375360 sectors, 15.0 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): ECD862C9-27C6-44EF-846C-5272FE5A465F
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 31375326
Partitions will be aligned on 2048-sector boundaries
Total free space is 4029 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            4095   1024.0 KiB  EF02  KingstonData
   2            4096        14749695   7.0 GiB     0700  
   3        14749696        29327359   7.0 GiB     0700  
   4        29327360        31373311   999.0 MiB   0700  
fred@fred-MavericDT:~$ 
```

Concerning that, I get several errors:

```
sudo parted -l
(...)
Error: The backup GPT table is not at the end of the disk, as it should be.
This might mean that another operating system believes the disk is smaller.
Fix, by moving the backup to the end (and removing the old backup)?

```

And it does not even find any of my external drive's partitions...

```

gefthebest@Jeff-PC:~$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Warning! Secondary partition table overlaps the last partition by
12884901225 blocks!
Try reducing the partition table size by 51539604900 entries.
(Use the 's' item on the experts' menu.)
Disk /dev/sdb: 15628116664 sectors, 7.3 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): FE533E9B-BC69-472A-ADB0-4FD155DB6E55
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 2743214742
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      8589936639   4.0 TiB     0700  
   2      8589936640     10737420287   1024.0 GiB  0700  
   3     10737420288     15628115967   2.3 TiB     0700 

```

Which is weird actually because I used to have GPT: damaged

Thank you

---

### Post by srs5694 on 2011-08-11
The GUID Partition Table (GPT) stores its main partition data at the start of the disk and it places a backup of that data at the end of the disk. Part of the trouble seems to be that something has moved the backup data from its correct position at the end of the disk to a point considerably earlier, at about 1.28 TiB. You can fix this problem in parted by answering "y" to the prompt you posted, or in gdisk by using the "e" item on the experts' menu. (Launch gdisk, then type "x", then type "e", then type "w" to save the change and exit.)

As a side note, it's conceivable that this corruption of the GPT data is what's damaged the filesystem on /dev/sdb1. The reason is that the 1.28 TiB mark is within /dev/sdb1, so moving the backup GPT data could have overwritten critical data structures in the filesystem, thus damaging it. I can't be positive that this is what happened, though; I don't know enough about NTFS, much less the precise layout of your specific filesystem.

Given what you've said about Windows damaging the disk, it's possible that Windows is seeing the disk as smaller than it is -- perhaps it's "seeing" the individual disks in the RAID array, or maybe you've got a driver in the chain that's got a 32-bit limitation and so is dropping binary digits from the disk's size, which would result in an apparent size of less than 2 TiB. You might be able to fix this problem by upgrading a driver on the Windows side. I recommend you check with the hardware's manufacturer; they may have some updated drivers or a procedure to follow under Windows to overcome this problem. Was the disk sold as a unit that was advertised with an over-2TiB size, or was this an empty enclosure to which you added your own disks? If the latter, it could be the design is old enough that the manufacturer didn't consider the possibility that it would exceed 2 TiB when it was initially released.

If you can't seem to resolve that issue, then the best suggestion I have is to do a dd backup of the partition from Linux (as in step #1 of my previous post) onto some medium that Windows can read. You should then be able to recover *that* from Windows. I realize you probably don't have the necessary hardware for this, but that really is my best suggestion. Failing that, you'll have to fall back to step #4 in my previous post, since tools to recover NTFS in Linux are essentially nonexistent.

Another comment: If you can't use the disk in Windows, it's a bit dangerous to use NTFS on it, for reasons that you've now discovered first-hand: You can't recover from problems. Thus, in the long run, if this disk will remain for use under Linux only, you should convert all of its NTFS partitions to ext4, XFS, or some other Linux-native filesystem. That way you'll at least have adequate recovery tools should problems recur.

---

### Post by gefthebest on 2011-08-11
Thanks alot for the responses, I feel much more knowledgeable about all this now (:

I also have wondered why I chose to format it in NTFS but I thought that maybe then computers other than mine could read it under windows or smth but that was a bad decision...

I will see what I can do, I have another large drive in my hometown but definitely not 4.4TB (the original size of the partition)... so I might I'l just overwrite it and format it in ext4, to at least be prepared for future crashes...

Thank you for the help

PS: It was just an enclosure but it was also sold with up to 12TB of storage (4x 3TB drives) and it is a new model so it definitely supports 8TB and it advertises that it supports windows...

---


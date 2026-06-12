---
title: "Errors when mounting external HD"
date: 2011-11-08
forum: General Help
---

### Post by altjx on 2011-11-08
Is there a particular format other than NTFS that I'm supposed to format my external HD to? I can pass it to my Windows 7 VM with no issues and it detect fine... The minute I turn it on and have it detect by Ubuntu 11.10, this is the two error messages that pop up

```
Error mounting: mount exited with exit code 12: NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

```
Error mounting: mount exited with exit code 12: NTFS signature is missing.
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

Any idea how to solve this without having to format the external HD almost every few days that I turn it on for certain purposes?

---

### Post by efflandt on 2011-11-08
What does **sudo fdisk -l** (small L) show for that drive.  Is it maybe a Windows volume instead of regular primary partition(s)?

---

### Post by diablostallion on 2011-11-16
I am having a very similar problem. I get the exact same error except for
> Error mounting: mount exited with exit code 12:

> root@user-desktop:/home/user# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1fa39405

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24457   196449280   83  Linux
/dev/sda2           24458       60800   291924673    f  W95 Ext'd (LBA)
/dev/sda5           25497       60800   283579380    7  HPFS/NTFS
/dev/sda6           24458       25496     8344576   82  Linux swap / Solaris

Partition table entries are not in disk order

I have been trying the line;

> mount /dev/sda5 /media/c/ -t ntfs -o nls=utf8,umask=0222

---

### Post by efflandt on 2011-11-16
diablostallion how did you create/format those partitions that they ended up out of order (sda5 after sda6 on the drive)?  Other people may favor other tools, but I would use **sudo fdisk /dev/sda** from Ubuntu install CD or bootable USB to remove sda5 and sda6 and recreate them as:

sda5, start           24458, end       25496, type   82  (Linux swap / Solaris)
sda6, start           25497, end       60800, type    7 (HPFS/NTFS)

Removing and recreating partitions should not remove or corrupt any data as long as they are recreated with the same general type (primary or logical) with same exact start, end, and file system type, since that just edits the partition table not data in the partitions.

Then create a directory to mount /dev/sda2 and go to etc on that partition and edit fstab to change swap to /dev/sda5 (unless it uses UUID in which case you should not have to do anything).  My PC does not use swap since it has 8 GB RAM and I do not hibernate, so I am not sure how swap is shown in /etc/fstab.

Just curious if you get an error if you click on that NTFS partition under Devices in the File/Folder viewer in Ubuntu.  That is how I would usually mount my Win7 partition (which HP labeled "OS") or Maverick partition (running 11.10 from SSD). If a partition has no label the file/folder viewer may just show it by size.

---

### Post by Mark Phelps on 2011-11-17
If you're going to mount manually, or using fstab, then don't use "ntfs"; instead, use "ntfs-3g".  It is more robust than "ntfs" and does a better job mounting and handling NTFS filesystems.

Also, do you simply turn off the drive and THEN disconnect it when removing it?  Or, do you do a Safe Removal (clicking the tray icon in Win7 and waiting for the popup telling you it's safe to remove)?

If you do the first, that risks leaving the partition in an "unclean" state -- which can then prevent Ubuntu from mounting it.

If you do the second, then it should mount OK in Ubuntu.

---


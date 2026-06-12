---
title: "Cannot move file to trash"
date: 2011-05-13
forum: General Help
---

### Post by gdonwallace on 2011-05-13
This started happening last week.  Whenever I try to delete a file that is not in my /home directory I get the message:

**Cannot move file to trash, do you want to delete immediately.**

I have found a couple threads in the forums about this issue, but it has always been associated with windows or samba shares.

This is happening on my computer, not on a shared folder or through samba.  Its a little frustrating to say the least.

Any ideas??

---

### Post by seawolf167 on 2011-05-13
It sounds like you are attempting to delete a file from an NTFS formatted drive. This is normal and will always happen when using an NTFS drive.

You can check the format of the location by either opening up GParted (System -> Administration -> GParted) and read the format type or by entering the following command in a terminal

```
sudo fdisk -l
```

and finding the partition in question

---

### Post by gdonwallace on 2011-05-13
When I execute the fdisk -l command I get the following:

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008b5d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9466    76027904   83  Linux
/dev/sda2            9466        9726     2094081    5  Extended
/dev/sda5            9466        9726     2094080   82  Linux swap / Solaris

Disk /dev/dm-0: 2144 MB, 2144337920 bytes
255 heads, 63 sectors/track, 260 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83d3dbcf

Disk /dev/dm-0 doesn't contain a valid partition table

That last line is a bit bothersome, but I don't know if it should be there or not.  When I am deleting files, it is on /dev/sda1.  I don't have an NTFS partition on this hard drive.  Everything is EXT4 formatted.

---


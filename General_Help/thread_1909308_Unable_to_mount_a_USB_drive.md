---
title: "Unable to mount a USB drive"
date: 2012-01-15
forum: General Help
---

### Post by mavenuparker on 2012-01-15
I have a 16 GB USB drive, formatting it with KDE partition manager returns errors. I'm attaching a screenshot of it.

After clicking OK on the shown window, I'm able to mount the pen drive and dump files into it. But the files disappear after i unmount and mount it back again.

Please help. I need the usb disk very badly.

---

### Post by Paddy Landau on 2012-01-15
I think you need to click on the line with the error and press the "Details" button, otherwise we cannot see what the error is.

---

### Post by mavenuparker on 2012-01-16
The Details tab had all this:

```
Delete partition &#8216;/dev/sdb1&#8217; (15.99 GiB, unknown) 
Job: Delete file system on &#8216;/dev/sdb1&#8217; 
Delete file system on &#8216;/dev/sdb1&#8217;: Success

Job: Delete the partition &#8216;/dev/sdb1&#8217; 
Delete the partition &#8216;/dev/sdb1&#8217;: Success
Delete partition &#8216;/dev/sdb1&#8217; (15.99 GiB, unknown): Success

Create a new partition (15.99 GiB, fat32) on &#8216;/dev/sdb&#8217; 
Job: Create new partition on device &#8216;/dev/sdb&#8217; 
Create new partition &#8216;/dev/sdb1&#8217;: Success

Job: Create file system fat32 on partition &#8216;/dev/sdb1&#8217; 
Command: mkfs.msdos -F32 -v /dev/sdb1 
mkfs.msdos 3.0.9 (31 Jan 2010)
/dev/sdb1 has 255 heads and 63 sectors per track,
logical sector size is 512,
using 0xf8 media descriptor, with 33543657 sectors;
file system has 2 32-bit FATs and 16 sectors per cluster.
FAT size is 16368 sectors, and provides 2094430 clusters.
There are 32 reserved sectors.
Volume ID is db6ec42e, no volume label. 
Create file system fat32 on partition &#8216;/dev/sdb1&#8217;: Success

Job: Set the file system label on partition &#8216;/dev/sdb1&#8217; to "" 
File system on partition &#8216;/dev/sdb1&#8217; does not support setting labels. Job ignored. 
Set the file system label on partition &#8216;/dev/sdb1&#8217; to "": Success

Job: Check file system on partition &#8216;/dev/sdb1&#8217; 
Command: fsck.msdos -a -w -v /dev/sdb1 
dosfsck 3.0.9 (31 Jan 2010)
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
Checking we can access the last sector of the filesystem
Boot sector contents:
System ID "mkdosfs"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
      8192 bytes per cluster
        32 reserved sectors
First FAT starts at byte 16384 (sector 32)
         2 FATs, 32 bit entries
   8380416 bytes per FAT (= 16368 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 16777216 (sector 32768)
   2094430 data clusters (17157570560 bytes)
63 sectors/track, 255 heads
         0 hidden sectors
  33543657 sectors total
FATs differ - using first FAT.
Reclaiming unconnected clusters.
Checking free cluster summary.
Performing changes.
/dev/sdb1: 0 files, 1/2094430 clusters 
Check file system on partition &#8216;/dev/sdb1&#8217;: Error
Create a new partition (15.99 GiB, fat32) on &#8216;/dev/sdb&#8217;: Error

```

Hope you find what stops that from formatting.

---

### Post by Paddy Landau on 2012-01-16
Hmm, that is most puzzling. It could be that the USB has a faulty sector.

Try this:

Open Disk Utility. Choose your USB disk on the left-hand panel under *Peripheral Devices*. From there, unmount your USB (if mounted) but do not choose Safe Removal. Click on Format Drive near the top and partition. Then click on Format Volume near the bottom and format as FAT.

Let us know what happens.

---


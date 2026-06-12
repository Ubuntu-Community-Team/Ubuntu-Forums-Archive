---
title: "partition is mounted, but not recognized by fdisk, gparted or testdisk"
date: 2010-02-01
forum: General Help
---

### Post by Dan42 on 2010-02-01
I have this weird problem where I can mount my /dev/sdb partition correctly (unless ubuntu did a fsck on startup), but it isn't recognized by any of the system utilities I've tried. In **gparted** the disk just shows up as unallocated space. **testdisk** fails to detect the partition with either the "quick search" or "deeper search". And **fdisk -l /dev/sdb** just produces this:
```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe96ce96c

   Device Boot      Start         End      Blocks   Id  System
```

While searching for solutions I found a lot of posts where gparted shows the device as unallocated space but none where even *fdisk* fails to detect it. And yet I can mount it, read & write files. Any idea what's going on? How to diagnose it? Should I worry about the disk dying? It's not *that* old or heavily used... :-(

---

### Post by niteshifter on 2010-02-01
Hi,

It sounds like the disk is not partitioned. Yes, I know: you can read and write files to it - it's possible (just not commonly done) to create a file system on a non-partitioned disk. It does mean that some things aren't going to work:

Tools that look for a partition table are not going to work, there is no partition table.

You can't resize, create or delete partitions. Because ... there are none.

If you attempt to partition it, you'll kill the file system that is there and most likely lose all or part your files.

---

### Post by lidex on 2010-02-01
Do you have an nvidia chipset? What is on sdb and how many partitions? Has it been formatted? Is it accessible from another OS?

---

### Post by louieb on 2010-02-01
niteshifter might be right - I've never seen it but .. just out of curiosity - use testdisk and run a deep scan and see what shows up.

---

### Post by Dan42 on 2010-02-01
Thank you for your comments; they helped to put me on the right track. As niteshifter guessed, this disk is not partitioned; it just contains one big ext3 filesystem. I always thought of it as a "single-partition" disk, but by putting myself in the "no partition" frame of mind it changed the way I used testdisk: when prompted to choose the partition type, instead of selecting "Intel/PC partition" I went with "Non partitioned media" and then testdisk was able to see the filesystem.

As lidex suggested, I tried accessing the disk with a slightly different OS. I booted from a 9.04 disk and tried fdisk and gparted again, but with the same results.

The thing is, I could **swear** that gparted used to be able to see the filesystem on that disk. So I'm not sure that showing up as "unallocated space" is the normal behavior for a healthy disk. Not to mention that a few times it failed to mount at all on startup. 

lidex: I have an nvidia chipset but when I created the filesystem I had an ati chipset (my motherboard fried some months ago)

---


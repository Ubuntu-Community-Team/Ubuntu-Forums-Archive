---
title: "I think I need to use fsck...I have a few questions"
date: 2010-05-13
forum: General Help
---

### Post by Copperline on 2010-05-13
Hi,
I interrupted GParted during a partition resize and of course have now damaged my (ext3) file-system so Ubuntu won't load.

I know I can repair this (possibly) with fsck but I have a few questions:

1. Is fsck the correct way to go on this? As I can access my files with a Live CD then I could just re-install the OS if it is an easier course of action.

2. Is there any way to run fsck with some form of progress indication? I've been reading around and apparently fsck takes a very long time and I'd like to be able to see what it's up to if possible.

3. Is there any other option available for file system repair other than fsck? Any other utilities (even Windows ones) that will repair an ext3 file-system?

4. Should this process take an incredibly long time...I've read of somebody taking 60 hours...

Very many thanks.

---

### Post by mikewhatever on 2010-05-13
Have you checked that the partition table is intact? How about booting from a live cd and posting the output of *sudo fdisk -l*.

---

### Post by Copperline on 2010-05-13
Apologies...I should have said...I have indeed checked and the partition table seems to be fine.

> 
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0e026c03

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5123    41150466    7  HPFS/NTFS
/dev/sdb2            5124       19457   115137855    5  Extended
/dev/sdb5            5124       19323   114061468+  83  Linux
/dev/sdb6           19324       19457     1076323+  82  Linux swap / Solaris




unfortunately this is all crashed together and I don't know how to get it to display as I want it to!
Hope it's enough.

---

### Post by sandyd on 2010-05-13
> **Copperline said:**
> Hi,
I interrupted GParted during a partition resize and of course have now damaged my (ext3) file-system so Ubuntu won't load.

I know I can repair this (possibly) with fsck but I have a few questions:

1. Is fsck the correct way to go on this? As I can access my files with a Live CD then I could just re-install the OS if it is an easier course of action.

2. Is there any way to run fsck with some form of progress indication? I've been reading around and apparently fsck takes a very long time and I'd like to be able to see what it's up to if possible.

3. Is there any other option available for file system repair other than fsck? Any other utilities (even Windows ones) that will repair an ext3 file-system?

4. Should this process take an incredibly long time...I've read of somebody taking 60 hours...

Very many thanks.

> **Copperline said:**
> Apologies...I should have said...I have indeed checked and the partition table seems to be fine.



unfortunately this is all crashed together and I don't know how to get it to display as I want it to!
Hope it's enough.
good, its intact. No warning of overlapping partitions either.
1. you can  use testdisk, but it will take even longer than fsck
2. Not that I know of
3.testdisk
4. Not really, and it depends on the severity of the damage. Since all the partition tables are intact, boot up to a livecd, and run
```

sudo fsck -y /dev/sdb5
```

---

### Post by mikewhatever on 2010-05-13
The output looks fine, and partitions are there. Try running the following:
```
sudo fsck -yv /dev/sda5
```

-y -- autofix errors
-v -- be verbose, though don't think it shows progress.

You are gonna be checking the 100GB partition, I can't tell how long it's going to take, probably about 20 minutes.

---

### Post by Copperline on 2010-05-13
Thank you both very much...that's excellent. I'll set it off now, go to bed, and see what greets me in the morning! With a bit of luck...it should be fixed.

Cheers
Copperline

---


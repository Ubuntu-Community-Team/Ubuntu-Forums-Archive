---
title: "Can't partition whole SATA disk?"
date: 2006-04-09
forum: General Help
---

### Post by FullyFunctnlPhil on 2006-04-09
Running Ubuntu 5.10 on amd64 for the first time, have no idea what I'm doing, etc.

I have a 160gb SATA drive (/dev/sda) as my primary and a 320gb SATA (/dev/sdb) as my secondary disk.  I thought I had successfully partitioned and formatted the 320 to be used for media storage, mapped to /media/sdb4

However, when I browse the folder it says that only 133 gigs are free, even though the drive is currently empty.  Under the Ubuntu Disks Manager, it is shown as a 298.09gb drive with a 186.27gb partition (/dev/sdb4), but under size says "free space not available".  Pressing "enable" doesn't seem to do anything.  This leaves 111.82gb of free space which is also inaccessible.  What did I do wrong?  I want to be able to access the entire drive, preferably under one massive partition.

fdisk yields the following:
```
Disk /dev/sdb4: 200.0 GB, 200005876224 bytes
255 heads, 63 sectors/track, 24315 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

     Device Boot      Start         End      Blocks   Id  System

```

I'm lost.  Help?

---

### Post by Sutekh on 2006-04-09
[QUOTE=FullyFunctnlPhil]I thought I had successfully partitioned and formatted the 320 to be used for media storage, mapped to /media/sdb4[/QUOTE]

What did you use to partition the disc?  

It might help to step through the process you used too. 

Worst comes to worst, you can try format the disc again.

---

### Post by FullyFunctnlPhil on 2006-04-10
I used fdisk a while ago to make the partition.  I just tried it again and the partitioning worked, but when i tried to format it I get:

```
$ mkfs ext3 /dev/sdb4
mke2fs 1.38 (30-Jun-2005)
mkfs.ext2: invalid blocks count - /dev/sdb4

```

No change in disks-admin.

---

### Post by Sutekh on 2006-04-10
Hmm, I don't know very much about mkfs.  I thought you specified the filesystem like
```
mke2fs -j /dev/sdb4
```or
```
mkfs.ext3 /dev/sdb4
```

Does this result in the same error?

---

### Post by FullyFunctnlPhil on 2006-04-10
I tried that and it appeared to work:

```
sudo mke2fs -j -c /dev/sdb4

```

```
Checking for bad blocks (read-only test): done                        559
Writing inode tables: done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 26 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

```

But I ran fdisk again and the partition table is still empty:

```
Disk /dev/sdb4: 200.0 GB, 200005876224 bytes
255 heads, 63 sectors/track, 24315 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

     Device Boot      Start         End      Blocks   Id  System

```

---

### Post by Celerex on 2006-04-10
make sure you're running 'fdisk /dev/sdb' not 'fdisk /dev/sdb4' (fdisk works on disks not partitions).

I have a feeling that sdb4 is actually an extended partition and not a primary. Anyway, try that and repost. Also, could you post your hdparm? 'hdparm /dev/sdb'.

---

### Post by FullyFunctnlPhil on 2006-04-10
Ah, thanks.

fdisk /dev/sdb yields:

```
Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb4               1       24316   195318238+  83  Linux

```

hdparm:

```
/dev/sdb:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 38913/255/63, sectors = 625142448, start = 0

```

---

### Post by Celerex on 2006-04-10
well, whilst in fdisk, can you delete this partition and then recreate it?

```

fdisk /dev/sdb
...fdisk loads...
Command (m for help): <push d>
Partition number (1-4): <push 4> <-- This line MAY not happen (fdisk is smart like that)
Command (m for help): <push p> <-- You'll notice empty table now (don't worry, the partition isn't gone until you write the table to the disk)
Command (m for help): <push n>
Command action
   e   extended
   p   primary partition (1-4)
<push p>
Partition number (1-4): <push 1>
First cylinder (1-177869, default 1): <push enter>
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-38913, default 38913): <push enter> <-- Defaults to the whole disc, that value 38913 is what your disc SHOULD be

Using default value 38913

Command (m for help): <push p>

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End         Blocks   Id  System
/dev/sdb1               1       38913  312568672+  83  Linux

```

If your output looks like that.. then you're good. push W on the next command line and it will write and you should be golden.

---

### Post by FullyFunctnlPhil on 2006-04-10
Hey, it works!

I tried the same thing last night to no avail, but I see 278.5gb free now.  I'm not really sure what happened, but thanks!

---


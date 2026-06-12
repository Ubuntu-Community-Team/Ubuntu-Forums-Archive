---
title: "Whole hard drive gone"
date: 2010-01-30
forum: General Help
---

### Post by ubuntüser on 2010-01-30
My whole hard drive shows up as gone! 
I have a OS drive, and then a 2x1TB raid drives in raid 1 configuration using MDADM.

Now, I booted up and that drive shows up as blank.
The output from cat /proc/mdstat is:

Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[1] sda1[0]
      976759936 blocks [2/2] [UU]
      
unused devices: <none>


What happened to my drives???

Please help!
Thanks

EDIT: I am trying testdisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) to find my partition.

If anyone can help, would the default partition map be Intel or EFI GPT under ubuntu?

---

### Post by tgalati4 on 2010-01-30
If you can boot, then look in /var/log and examine the log files.  Also:

dmesg | more

Look for mount errors that might be helpful to troubleshoot.

---

### Post by falconindy on 2010-01-30
Uhhh... the output you posted shows that there's 2 drives in use as the **active** device md0. It shows no **un**used devices. That's a good thing... What makes you think your hard drives are gone?

---

### Post by ubuntüser on 2010-01-30
Im cutting a ton out from the dmesg thing, but I think you can help me by looking at this: (*** means cut out stuff in betw)

```


*** (cut out stuff)
[    2.531574] raid1: raid set md0 active with 2 out of 2 mirrors
*** (cut out stuff)
[ 1289.436212] EXT3 FS on md0, internal journal
[ 1289.436224] EXT3-fs: mounted filesystem with writeback data mode.
*** (cut out stuff)


```

Right now, while running testdisk, I've found that suddenly my partition is accessible somehow. I can see all the data, access it, etc.
But I don't want to stop testdisk now.

---

### Post by ubuntüser on 2010-01-30
> **falconindy said:**
> Uhhh... the output you posted shows that there's 2 drives in use as the **active** device md0. It shows no **un**used devices. That's a good thing... What makes you think your hard drives are gone?

My hard drives are fine, the partion table's gone.

Testdisk is showing some problems, but it seems to be going good.

Even with raid1 it takes a ton of time to go through every cylinder of a 1TB raid array. :p

Well, recovery *seems* to be going well, don't know how much testdisk is gonna do.

But at least I know I can access my 500GB+ of data now.

---

### Post by falconindy on 2010-01-30
Hard to tell that you're having problems when the only things you post are "all systems normal" messages.

---

### Post by ubuntüser on 2010-01-30
> **falconindy said:**
> Hard to tell that you're having problems when the only things you post are "all systems normal" messages.

That's what I'm having problems with. It's reporting all system s normal now, but it was not accessible at boot.
And I think its only accessible right now that testdisk is running...

Is there any good way to recover a partition table?

---

### Post by falconindy on 2010-01-30
testdisk...

---

### Post by ubuntüser on 2010-01-30
> **falconindy said:**
> testdisk...

Haha, OK. But its output currently contains many things. I only had one partition that was ext3.

Its saying:

```

Disk /dev/md0 - 1000 GB / 931 GiB - CHS 244189984 2 4
Analyse cylinder 63400000/244189983: 26%

And then it has lots of things like

HPFS - NTFS     [lots of numbers here]
FAT12     [lots of numbers here]
HFS     [lots of numbers here]
HFS     [lots of numbers here]
HFS     [lots of numbers here]
HFS     [lots of numbers here]
HFS     [lots of numbers here]
check_FAT: Unusual, only one FAT
check_FAT: Bad number of entries in root dir
check_FAT: Unusual, only one FAT
check_FAT: Bad number of entries in root dir
check_FAT: Bad jump in FAT partition
HFS     [lots of numbers here]

```

What is up with the FAT partitions? I only had one ext3 partition.

---

### Post by ubuntüser on 2010-01-31
OK, so my data is accessible, but fdisk still says that the device md0 does not contain a valid partition table. My partition type was ext3, and just one big partition. Is there any way to fix this without losing data?

---

### Post by falconindy on 2010-01-31
Again, that's normal behavior for fdisk. Taken from my server which runs 3 mdadm arrays...

```
Disk /dev/md0: 98 MB, 98566144 bytes
2 heads, 4 sectors/track, 24064 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 2006 MB, 2006712320 bytes
2 heads, 4 sectors/track, 489920 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 65536 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md2: 998.0 GB, 998005932032 bytes
2 heads, 4 sectors/track, 243653792 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 65536 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table
```
Wouldn't you know it? The thing boots/runs fine ><

---

### Post by ubuntüser on 2010-01-31
OK, I think I've fixed it by rewriting the MBR. But I need someone to do something for me. Can someone with a raid1 array give me their output of fdisk -l? In particular, I'm trying to find out if it matches this:

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ce25e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001d320

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/md0: 1000.2 GB, 1000202174464 bytes
2 heads, 4 sectors/track, 244189984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

    Device Boot      Start         End      Blocks   Id  System

```

BTW, sda and sdb are the two drives that make up the raid array. So now, I can access my data. But under /dev/md00, it doesn't show any partitions. I want to know if that is normal.

---


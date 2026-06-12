---
title: "Nuked Linux FS...?"
date: 2011-03-17
forum: General Help
---

### Post by Moulinoski on 2011-03-17
In one of my not-so-brilliant moments, I accidentally booted Windows XP Recovery partition from Grub instead of Windows 7 Loader when I went to do something in my Windows partition and well... Win XP Recovery ate my Grub2 and much, much worse, my Linux partitions.

Since then, I installed a temporary Linux partition where the Win Xp Recovery partition used to be (how do you like that), after being unable to fix the problem via Google.

I had tried to use reiser as well as other things, and well... I'm pretty sure my Linux partition is beyond all hope, but I decided to at least post this here, and maybe someone out there might actually have a solution. I'm quite ready to just kill it off, though. I've made my piece with all of the stuff I hadn't backed up yet.

Anyways, sda4 is the now-defunct Linux partition. fdisk doesn't recognize the filesystem, so it displays it as unknown. And I can't, and couldn't, get a superblock magic number to recover it either. :/

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc0bf6260

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13698   110024702+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           18815       19452     5124735   83  Linux
/dev/sda3           19453       19457       40162+  82  Linux swap / Solaris
/dev/sda4           13698       18814    41097217   15  Unknown
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdb: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders
Units = cylinders of 5916 * 512 = 3028992 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1323     3910640    b  W95 FAT32
ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sda4 | grep superblock
dumpe2fs 1.41.12 (17-May-2010)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sda4
Couldn't find valid filesystem superblock.

```

---

### Post by pqwoerituytrueiwoq on 2011-03-17
[testDisk]("http://www.cgsecurity.org/wiki/TestDisk") may work
worth a try

---

### Post by Moulinoski on 2011-03-17
What have I done. >.<

```
ubuntu@ubuntu:~/Downloads$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc0bf6260

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19458   156290903+  ee  GPT

```BTW, that happened after I used testdisk. I thought "hey, I can change it back from Unknown to Linux! Haha!"

And to no one's surprise, not even Grub2 loads now. woot.

Well, at least I can still mount my Windows 7 partition, whatever good that does me.

---

### Post by pqwoerituytrueiwoq on 2011-03-17
gparted screen shot?
something here may be of use
[http://ubuntuforums.org/showthread.php?t=1704894](http://ubuntuforums.org/showthread.php?t=1704894)

---

### Post by Moulinoski on 2011-03-17
I tried everything in your post link, unfortunately. Thank you for helping me, though. My header file is dead, so I'm just going to format the whole netbook into Ubuntu Netbook Edition (I don't have anything on my Windows partition).

Now, how do I label this thread? It's not entirely Solved per se... Hmm...

---

### Post by pqwoerituytrueiwoq on 2011-03-17
if you messed something up with test disk it may be able to undo it 
no harm in trying at this point
rock and hard place scenario

---

### Post by srs5694 on 2011-03-18
I'm not intimately familiar with TestDisk's capabilities, but I do know that it asks you about the partition table type when you first launch it. I suppose it's conceivable that if you told it you had a GPT disk, it would find your MBR partitions and convert them to GPT form. If so, your partitions may still be completely intact; you'd just need to use GParted, GNU Parted, GPT fdisk (gdisk), or some other GPT-aware utility to view them, rather than Linux fdisk, which can't handle GPT. The Linux kernel is perfectly GPT-aware, so if this hypothesis is correct, you should see Linux device nodes (/dev/sda1, etc.) for your partitions. There's even a modest chance that you could restore Linux to bootability on that disk as it is now, although Windows won't boot from GPT on a BIOS-based computer.

Even if I'm wrong about this, you should still be able to use TestDisk to recover your partitions, assuming their filesystems haven't been damaged so much that TestDisk can't find them. You might need to delete the GPT data first, though. [GPT fdisk](http://www.rodsbooks.com/gdisk/) is probably the best way to do this, if it becomes necessary:

```

sudo sgdisk --zap-all /dev/sda

```

Be *very* careful with that command, though; you don't want to issue it on your other disk! Also, in case anybody's reading this in the future, *don't* apply that command unless you *fully* understand what your problem is and what that command does! (I've seen a few too many cases lately of people applying advice that can help cure one problem to a problem that seems superficially similar but is really very different, thus causing even worse problems. Using sgdisk as I've just specified, but with a different problem, is one way to double the depth of the hole you're in.)

One more point: You might want to consider backing up the entire /dev/sda to another disk. That will enable you to try potentially very destructive commands on either the original or the backup, with confidence that you've got the ability to get back to where you are now. You can use dd to perform such a backup, as in:

```

sudo dd if=/dev/sda of=/dev/sdb

```

That command backs up /dev/sda to /dev/sdb. (The if= option specifies the input file, and of= specifies the output file.) Be sure to verify which disk is which and quadruple-check the command before you enter it; if you reverse the if= and of= options, you'll overwrite the data you want to save with whatever's on the backup disk!

So to sum up:


[list=1]
[*]Do a low-level backup.
[*]Check for Linux device nodes for partition (/dev/sda1, etc.) and/or examine the partition table with GParted, gdisk, or a similar tool. If partitions are present, try to access them.
[*]If the GPT data are garbage, use sgdisk to delete the GPT structures.
[*]If the GPT data are garbage, or if the partitions defined in GPT are incomplete, use TestDisk to try to recover your partitions.
[/list]

---


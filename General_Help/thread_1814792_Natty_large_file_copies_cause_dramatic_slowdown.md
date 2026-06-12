---
title: "Natty large file copies cause dramatic slowdown"
date: 2011-07-30
forum: General Help
---

### Post by Odipides on 2011-07-30
**The problem:**
If I initiate a file copy of more than a couple of GiB, the PC goes into a dramatic slowdown. Even selecting a different subdirectory through Nautilus can take 30+ seconds.

Now, whilst I appreciate that file copying puts a load on the bus, DMA and, to a certain extent, the CPU, it seems unconscionable that it makes the PC effectively unusable until the copy has completed.

Is there any way to (practically) lower the priority, or similar, of the copy process so that one can continue to use the platform during large file copies? Right now, I end up using a laptop adjacent to the PC whenever I have to copy a large file. This, for a mainstream operating system is, frankly, ludicrous.

I'm aware that I could run Nautilus 'nicely' but I don't want to make changes which would compromise other aspects of the system. It would also be pleasant, for a change, not to have to read a couple of telephone directories of technical documentation in order to resolve the problem myself. This must be a general problem and, in my view, something which seriously compromises the usefulness of Ubuntu given the sizes of contemporary drives and files.

The i7 I'm using at the moment has 8 cores non of which go over 15% usage while the copy is progressing despite the OS being effectively frozen for long periods.

**Environment:**[FONT=Courier New]
[/FONT][INDENT][FONT=Courier New]Intel Core i7-2600 @ 3.40GHz; 16GB RAM; Natty (11.04) fully updated as at 29th July 2011; Kernel 2.6.38-10-generic, GNOME 2.32.1.; Primary drive has 563.9GiB free space, [/FONT]

[FONT=Courier New]Running in Ubuntu 'Classic' (no effects) mode[/FONT]

[FONT=Courier New]Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes[/FONT]
[FONT=Courier New]255 heads, 63 sectors/track, 243201 cylinders[/FONT]
[FONT=Courier New]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT]
[FONT=Courier New]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=Courier New]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=Courier New]Disk identifier: 0x00000000[/FONT]

[FONT=Courier New]Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=Courier New]/dev/sdc1               1      243202  1953514583   ee  GPT[/FONT]
[/INDENT]**Various links to others with the issue, with no definitive solution just a lot of 'try this...'** (as far as I can see)
   [http://ubuntuforums.org/showthread.php?t=1382161](http://ubuntuforums.org/showthread.php?t=1382161)
   [https://bbs.archlinux.org/viewtopic.php?pid=877748](https://bbs.archlinux.org/viewtopic.php?pid=877748)
   [http://ubuntuforums.org/showthread.php?t=1172932](http://ubuntuforums.org/showthread.php?t=1172932)
   [http://ubuntuforums.org/showthread.php?t=951229](http://ubuntuforums.org/showthread.php?t=951229)
   [http://ubuntuforums.org/showthread.php?t=1513236](http://ubuntuforums.org/showthread.php?t=1513236)

---

### Post by hakermania on 2011-07-30
+1 I can confirm this!
I am copying a 23Gb movie (OMG, yes it is 1080p ;)) to an external hard drive and my PC has slowed down too much!
Plus the speed has dropped from 28Mb/s to only 13 :/

---

### Post by Odipides on 2011-07-30
How is the external drive formatted?

If it's NTFS or FAT (particularly FAT) there's a dramatic slowdown after the first 500MB is copied. I generally format my external drives as ext3/4 and then the copy speed stays pretty much the same all through the copy.

Still hangs the PC while it's copying though.

Exhibit A:
Copy to an external USB drive, NTFS format. started at 50MB/sec and ends up at 5.
[IMG]http://dl.dropbox.com/u/1166899/slowUSB.png[/IMG]

---


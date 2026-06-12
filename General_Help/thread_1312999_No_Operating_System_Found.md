---
title: "No Operating System Found"
date: 2009-11-03
forum: General Help
---

### Post by kogger on 2009-11-03
I run a laptop dual-booted between Ubuntu and Windows 7. I recently upgraded to Karmic, and with that upgraded from an ext3 to an ext4 filesystem. With the change to ext4 I found that the program I used to read my linux filesystem (Ext2Fsd, if anyone is curious) no longer worked. In an effort to get it to work I tried changing a couple settings, and then I rebooted my computer.

To put it simply, Grub2 is destroyed. It boots into a grub rescue> prompt that doesn't recognize 'boot' or even 'help' as valid commands. I booted from a LiveCD, and GParted says there are no operating systems on my computer. When I run sudo fdisk -l from a LiveCD, though, here's my output:

```
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

Device      Boot     Start        End       Blocks    Id   System
/dev/sda1    *           1       9135     73376856    85   Linux extended
/dev/sda2             9136      17620     68155762+    7   HPFS/NTFS
/dev/sda3            17621      36302    150063165     7   HPFS/NTFS
/dev/sda4            36303      38913     20972857    82   Linux swap / Solaris
```

/dev/sda1 is my linux partition, sda2 and 3 are my windows and data partitions, and sda4 is my swap. According to fdisk, everything is there, but according to GParted and Grub, nothing is.

One more thing I forgot to add: I can mount and enter my windows partition just fine, but attempting to mount my linux partition gives me an error.

Can anyone help me out?

---

### Post by kogger on 2009-11-03
bump

---

### Post by wildweathel on 2009-11-03
Okay, relax and take a deep breath.  Try to not change anything without thinking about it first.

First, I'm pretty sure your Windows partition is okay.  If you get a working bootloader, you should be able to boot Windows, and all your files will be there.

The part I'm concerned about is your Linux partition.  "Linux Extended" means a partition that contains other partitions: /dev/sda5 and higher.  However, I'm not seeing those.  

Something changed your partition table.  I'm wondering of Windows, or especially Ext2Fsd did that.  
There are two possibilities I can think of.  First, /dev/sda1 was actually your Ubuntu root partition.  Something decided to call it an extended partition and now Linux is confused.  

Second, /dev/sda5 was actually your Ubuntu root partition.  The extended partition table is missing or damaged, because Windows/Ext2Fsd barfed on it.  

Additionally, it seems strange that you have a 10G swap partition.  Is that really how you set it up?

So, here's the first question: Do you have data you want to keep on your Ubuntu partition?  If not, we can just delete those two partitions (1 and 4), not touch the Windows ones (2 and 3), and try to re-install.  Hopefully, Ubuntu will detect Windows on 1 and 4 and all will be happy.

But, that doesn't sound like the case.  So, I think we should try harder to see what's in those partitions.

```
sudo file -s /dev/sda1
``` will do a read-only identification of what's in sda1.  If we're lucky, it'll identify an ext4 filesystem.  My root filesystem looks like this:

```

wildweathel@basilisk-reloaded:~$ sudo file -s /dev/sda5
/dev/sda5: Linux rev 1.0 ext4 filesystem data, UUID=[redacted]
(needs journal recovery) (extents) (large files) (huge files)

```In that case, it'll be a simple matter of setting the filesystem flag to the correct value and re-installing grub.  If not, we need to do some more digging.  Can you live-cd boot it, run these two commands and post the output here?

```

sudo file -s /dev/sda1
sudo file -s /dev sda4

```

---

### Post by kogger on 2009-11-03
I'm pretty sure I know what I did wrong now. /dev/sda1 is my Linux root partition, and since I didn't really know what I was doing I used Ext2Fsd to re-label it as a Linux extended. So your first possibility is what happened. Linux is confused.

After some messing around with fsck and fdisk, GParted now shows all my partitions, although /dev/sda1 (linux) is shown as unallocated, and I think that's because of the messed-up label.

Anyway, my output for file -s /dev/sda1:
```
/dev/sda1: x86 boot sector, code offset 0x0
```

...and /dev/sda4:
```
/dev/sda4: Linux/i386 swap file (new style), version 1 (4K pages), size 5243213 pages, no label, UUID=[long UUID number that I don't feel like typing out]
```

And yes, I did set up a swap partition that big. I could make it smaller and be fine, but I haven't come close to running out of space anyway, so I haven't bothered.

At this point I would rather not delete my Ubuntu partition, but I am willing to. I just did a fresh install recently, so I'll be able to recover pretty well, but it'd still be a pain in the ***.

---

### Post by wildweathel on 2009-11-03
Okay, so that's three out of four partitions known to be good.  (Awful big for a swapfile.  I don't think 32 bit can even use swap that big.  But, at least we don't have to worry about it...)

That leaves the issue of sda1.  Ext2Fsd has overwritten the beginning of the partition, which unfortunately contains the "superblock"--the very first place that ext4 driver or fsck is going to look.  But, the ext family of filesystems have multiple superblocks.  With any luck, only the beginning of your filesystem has been changed.

First, I want to confirm that you made a fresh Karmic install with ext4.  You didn't upgrade an existing ext3 partition.  

The next step is to try

```

sudo [fsck.ext4]("http://vmlinux.org/cgi-bin/dwww/usr/share/man/man8/fsck.ext4.8.gz?type=man") -n /dev/sda1

```

The -n switch will make it run in read-only mode.  It will probably fail because it can't find the superblock.  But, you can add the option "-b *block-number*" to look somewhere else.   Try 
32768
16384
8193

If those don't work, 
```

sudo -k
sudo mke2fs -n /dev/sda1

```
will show you where the backup copies are supposed to be.  *Warning: be sure there's an '-n' with that command.  Otherwise it will really format the partition.*

Good luck.

---

### Post by kogger on 2009-11-03
The fsck.ext4 commands give me an "Invalid argument while trying to open /dev/sda1" error.

And the results of mke2fs:

```
mke2fs 1.41.9 (22-Aug-2009)
mke2fs: inode_size (128) * inodes_count (0) too big for a filesystem with 0 blocks, specify higher inode_ratio (-i) or lower inode count (-N).
```

---

### Post by kogger on 2009-11-03
I got it! =)

After some searching online, I found [this page](http://www.mohdshakir.net/2008/01/03/recover-lost-partition-table-using-ubuntu-live-cd-gpart) which fixed my problem.

Thanks for your help.

---

### Post by wildweathel on 2009-11-03
Yay!   Awesome!  [Mark thread solved]("http://ubuntuforums.org/showthread.php?t=524404&highlight=mark+as+solved")!

---


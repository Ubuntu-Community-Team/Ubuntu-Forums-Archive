---
title: "resizing USB ext hdd for linux format"
date: 2011-04-04
forum: General Help
---

### Post by emonti on 2011-04-04
I have an external 3TB hdd which is all NTFS formatted. I want to claim a portion of the drive for an ext2 partition.

I was hoping to resize my NTFS partition ... but it seems GParted on Lucid (even cd boot), doesn't list my external usb device at all.

Any idea why that might be? I read somewhere that the device should be  unmounted before it can be detected but it makes no difference - even  after a device list-refresh in GParted.

(I tried running the install/setup Windows software which came with the ext drive but there is no option for resizing it)

Any help would be much appreciated.

---

### Post by TeoBigusGeekus on 2011-04-04
Does the device show with 
```
lsusb
```
?

---

### Post by tredegar on 2011-04-04
A 3TB drive is BIG.

It is likely to have a GPT partition table, which some older tools may not understand or handle correctly.

See [here]("http://ubuntuforums.org/showthread.php?t=1705325") for some more information.

---

### Post by emonti on 2011-04-06
TeoBigusGeekus,

'lsusb' gives the following output:

```

...
Bus 001 Device 014: ID 0bc2:5071 Seagate RSS LLC 
...

```

So, yes, the device seems to be showing.

---

### Post by srs5694 on 2011-04-06
Try the following diagnostic commands:

```

ls -l /dev/sd?
dmesg | grep sdb

```

Change "sdb" in the second command to whatever the device name is or should be -- "sdb" is most probably correct if you've got just one other disk device, but it could be "sdc" or something else if you've got two internal disks or other external disks (including USB flash drives) attached.

The first command will show what disk devices the kernel has recognized. (The lsusb output shows that the device is recognized, but perhaps not as a disk device.) The second command will show kernel messages related to the device, which may include error messages about problems the kernel could not overcome.

---

### Post by emonti on 2011-05-23
Hey srs5694,

Thanks for the response. Here's the output I get from your second cmd:

```
[    6.435444] sd 2:0:0:0: [sdb] 732566645 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[    6.435935] sd 2:0:0:0: [sdb] Write Protect is off
[    6.435940] sd 2:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[    6.435945] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.436691] sd 2:0:0:0: [sdb] 732566645 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[    6.437189] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.437195]  sdb: sdb1
[    6.452884] sd 2:0:0:0: [sdb] 732566645 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[    6.453436] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.453442] sd 2:0:0:0: [sdb] Attached SCSI disk

```

There don't appear to be any error messages.

---

### Post by srs5694 on 2011-05-23
It looks as if your disk is being detected, so my guess at this point is that it's something about libparted that's causing problems. Try these two commands, and post their output:

```

sudo fdisk -l /dev/sdb
sudo parted /dev/sdb print

```

These are both for diagnostic purposes.

Also, please tell us what version of Ubuntu you're using.

---

### Post by tredegar on 2011-05-23
It is attached as /dev/sdb

What is the output of the following command```
sudo gdisk /dev/sdb
```?
Note that is **[COLOR="Red"]g[/COLOR]disk** not **fdisk**

---

### Post by emonti on 2011-05-24
srs5694,

Here is my output:

```
emonti@leanmachine:~$ sudo fdisk -l /dev/sdb
[sudo] password for emonti: 
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 3000.6 GB, 3000592977920 bytes
1 heads, 7 sectors/track, 104652377 cylinders
Units = cylinders of 7 * 4096 = 28672 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2   104652001  2930256000    7  HPFS/NTFS
Partition 1 does not start on physical sector boundary.
```... and ...

```
emonti@leanmachine:~$ sudo parted /dev/sdb print
Warning: Device /dev/sdb has a logical sector size of 4096.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

Model: Seagate FA GoFlex Desk (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 4096B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      28.7kB  3001GB  3001GB  primary


```

Ubuntu 10.4 (Lucid), kernel: 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 i686 GNU/Linux

Thanks

---

### Post by emonti on 2011-05-24
tredegar,

I installed gdisk and ran your cmd and got the following output:

```
emonti@leanmachine:~$ sudo gdisk /dev/sdb
GPT fdisk (gdisk) version 0.5.1

WARNING! Sector size is not 512 bytes! This program is likely to misbehave!
Proceed at your own risk!

Partition table scan:
WARNING! Sector size is not 512 bytes! This program is likely to misbehave!
Proceed at your own risk!

  MBR: MBR only
  BSD: not present
Unable to seek to secondary GPT header at sector 5860533159!
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
THIS OPERATON IS POTENTIALLY DESTRUCTIVE! Exit by typing 'q' if
you don't want to convert your MBR partitions to GPT format!
***************************************************************
```

That looks a little scary. What do you suggest?

---

### Post by tredegar on 2011-05-24
> That looks a little scary. What do you suggest?
I hope you pressed **q** !

The disk has MBR not GPT.
But the sectors are 4096 bytes, not the 512 linux is expecting.

It's difficult to know what to advise.....
I'd probably backup the files on the disk, then re-partition and re-format it with linux tools, then restore the files.

Wait a while, because the other readers  of / subscribers to this thread may have better advice.

---

### Post by coldraven on 2011-05-24
I know that this is stating the obvious, but did you select the drive from the drop down in the top right corner of the Gparted window?

---

### Post by srs5694 on 2011-05-24
The problem is, as pointed out by tredegar, that the disk has 4096-byte sectors rather than the more common 512-byte sectors. *Linux* handles this just fine; but *libparted* does not, as the GNU Parted output warns:

[quote=edmonti]
```
Warning: Device /dev/sdb has a logical sector size of 4096.  Not all parts of GNU
Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

```
[/quote]

I have two suggestions:


[list]
[*]**Upgrade libparted/GParted** -- Ubuntu 10.04 is now a year old, and there have been a lot of changes in libparted and GParted in that time. It's possible that a newer version will handle a disk with 4096-byte sectors better than the version you've got, although I've not looked into this issue in detail and so can't promise any improvement. Thus, you could try using a newer version. This will require installing it all from source, finding an upgraded package for your version of Ubuntu, or running it from a separate boot disc (say, an Ubuntu 11.04 install disc or [PartedMagic](http://partedmagic.com/doku.php)). I can't guarantee this will work.
[*]**Use a combination of other tools** -- You should be able to use the Windows partitioning tool to shrink the existing NTFS partition and then use a combination of Linux text-mode tools (fdisk and mkfs) to create a suitable Linux partition on the disk. There are other ways to accomplish the same effect, too, using various other tools. This is almost certain to work, but if you're unfamiliar with these tools, it'll take a bit of learning to figure out how to do it.
[/list]


I'd like to emphasize again that the problem is restricted to libparted, which is used by GParted, GNU Parted, and several other Linux partitioning tools. (The version of gdisk you tried is not based on libparted, but has similar restrictions. Since 0.6.0, gdisk has supported such disks and so has no such problems.) The Linux kernel, which is what parses partitions for normal use when you're *not* modifying partitions, has long supported disks with 4096-byte sectors, so once the disk is properly partitioned, you shouldn't have problems except with partitioning tools based on libparted (or anything else with a similar limitation).

---

### Post by tredegar on 2011-05-24
@ srs5694
A useful and informative post. Thank you, I have learnt a bit more.

---

### Post by coldraven on 2011-05-24
@srs5694
I bow before your superior knowledge :) and learnt something!

---

### Post by emonti on 2011-05-26
Coldraven,

Yes, I did check the top righthand dropdown list but sdb is not listed.

'Thank-you's to tredegar  and srs5694 for your insights. ( yes I pressed 'q' ;-) )

I think I will try upgrading **libparted** first. I have utilites on my ultimate boot cd but I'm not too familiar with them.

Thank-you, again for your help.

I'll update this thread with feedback as I make progress.

---


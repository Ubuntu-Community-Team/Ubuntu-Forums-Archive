---
title: "Mount old harddisk (wrong fstype/superblock invalid?)"
date: 2011-10-29
forum: General Help
---

### Post by ThomasV on 2011-10-29
Hey everyone.

Recently my old computer died and I have bought a new one. In order to access the data on my old hard drive I bought a SATA to USB cable on Amazon. I removed the harddrive from my old dead computer and connected it to my new computer. After running

sudo mount /dev/sdb /media/old

I was able to acces my old harddisk at /media/old. Whee! Much easier than I'd expected. Now to the problem:

I was not smart enough to actually backup the content from my old computer to the new one right away. I figured that I had solved the problem now and could do it later.  Second time I tried it was not as easy (I have upgraded to 11.10 in between, maybe thats the reason? ). Now running the same command gives:

mount: you must specify the filesystem type

Trying to specify:

sudo mount -t ext2 ext/dev/sdb /media/old

gives this:

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

To be honest I'm not quite sure of the filesystem type on the old harddrive, but ext3 and ext4 gives the same result. Is there any way to find out?

If I try to run 

sudo fsck /dev/sdb

I get 

fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb
 
Is the problem that my superblock is invalid (whatever that means). Can anyone help me recover my old data?

On beforehand thanks

Vass

---

### Post by Shazaam on 2011-10-29
With the drive connected what does 
```
sudo fdisk -lu
```
print out?

---

### Post by ThomasV on 2011-10-29
sudo fdisk -lu   gives this (only for /dev/sdb):

Disk /dev/sdb: 160.0 GB, 160041884672 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581806 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006669a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   300292095   150145024   83  Linux
/dev/sdb2       300294142   312580095     6142977    5  Extended
/dev/sdb5       300294144   312580095     6142976   82  Linux swap / Solaris

---

### Post by Shazaam on 2011-10-29
Try this...
```
sudo mount /dev/sdb1 /media
```

---

### Post by ThomasV on 2011-10-29
> **Shazaam said:**
> Try this...
```
sudo mount /dev/sdb1 /media
```


I suppose you mean: sudo mount /dev/sdb1 /media/old?

In any case I already tried that. No matter which number I put in they all give me

mount: you must specify the filesystem type

---

### Post by Shazaam on 2011-10-29
This might help if I have to leave...
In terminal-
```
man mount
```
Many ways to mount a partition; by device, type, label, etc.

ext, ext2, ext3, ext4? Which one was it formatted too?
```
sudo mount -t ext2 /dev/sdb1 /media/old
sudo mount -t ext3 /dev/sdb1 /media/old
sudo mount -t ext3 /dev/sdb1 /media/old 

```


Here is something to look at later...
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)

---


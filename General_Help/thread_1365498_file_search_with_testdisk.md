---
title: "file search with testdisk"
date: 2009-12-27
forum: General Help
---

### Post by bandito40 on 2009-12-27
Hi,

I was wondering if anyone knows how to do a file search with testdisk? My hard drive broke a while ago and I was able to get all of my important files off it but it has been a while and I want to get more files off but don't remember where there are in the directory tree.

Thanks,

---

### Post by TopEnder on 2009-12-31
bandito40.  Have a look at the files in /usr/share/doc/testdisk , there maybe able to help you.  I don't have the experience in telling you howto as I have just install testdisk today and I was able to recover a 8Gb SD card (Platimum II 60x) that would only allow access to 4GB, most ot it was trial & error. Let the forum know how you went as it could help others, TopEnder

---

### Post by bandito40 on 2010-01-02
I tried to copy different ways.  Testdisk lets me navigate through the directory tree but there is no file search.  I tried running a log but it only works until a certain point then it only logs drive errors instead of directory contents.  I also tried ddrecue but I was never able to mount the image properly.  I was hoping that maybe there was a way that php or java could be used to communicate with testdisk and allow a file search that way.  I also tried photorec but that didn't seam to really do the trick.

Thanks.

---

### Post by TopEnder on 2010-01-03
Bandito40, Have a look at the following link it maybe of help to you with your file search,  TopEnder

[http://www.cgsecurity.org/wiki/TestDisk#Documentation](http://www.cgsecurity.org/wiki/TestDisk#Documentation)

---

### Post by bandito40 on 2010-01-07
ok

I have gotten this far. I have managed to copy an image of the entire drive but can't seams to go any farther.

I cannot mount it. Tried this [http://ubuntuforums.org/showthread.php?t=711773](http://ubuntuforums.org/showthread.php?t=711773) but testdisk doesn't give me the partition offset here is the output:

> Disk image - 40 GB / 37 GiB - CHS 4864 255 63
Analyse cylinder  4864/4863: 100%
Read error at 4863/254/63 (lba=78140159)

  ext3                     0   1  1  4723 254 58   75890992
  Linux SWAP 2          4724   1  1  4863 254 42    2249016




I tried to get the offset with fdisk -l -u and get this output.

> 
Disk image: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders, total 0 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdf7acfa1

Disk image doesn't contain a valid partition table

So I tried to fix the partition with fsdk.ext3 and get this output:

> fsck.ext3: Superblock invalid, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /home/bandito/image

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

I haven't tried e2fsck because I am not sure what alternate superblock I should use.

Can anyone shed any light on the issue?

Thanks in advanced!

---


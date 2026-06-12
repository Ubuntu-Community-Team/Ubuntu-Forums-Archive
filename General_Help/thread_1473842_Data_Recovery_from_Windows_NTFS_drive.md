---
title: "Data Recovery from Windows NTFS drive"
date: 2010-05-05
forum: General Help
---

### Post by Crazydog115 on 2010-05-05
Hey everyone.

The other day one of my hard drives on my windows system decided to stop working. Not entirely sure what happened, but it seemed that it just erased its partition header, although I wasn't able to recover it.

Anyway, I successfully got an image of the drive using GNU_ddrescue (yay!), and I'm currently salvaging what CAN be salvaged with foremost.

So, can anyone suggest a way to get EVERYTHING off of the drive? I mean, it seems that it's all intact (since foremost is finding so much stuff).

I've tried mounting the partition, but as you can see:

```
backup1@ubuntu:/media/backup$ mmls image -b
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

     Slot    Start        End          Length       Size    Description
00:  Meta    0000000000   0000000000   0000000001   0512B   Primary Table (#0)
01:  -----   0000000000   0000000062   0000000063   0031K   Unallocated
02:  00:00   0000000063   0156280319   0156280257   0074G   NTFS (0x07)
03:  -----   0156280320   0156301487   0000021168   0010M   Unallocated
backup1@ubuntu:/media/backup$ sudo mount -t ntfs -o r,force,loop,offset=32256 image mnt
[sudo] password for backup1: 
ntfs_mst_post_read_fixup: magic: 0x43425355  size: 1024  usa_ofs: 34912  usa_count: 1525: Invalid argument
Record 0 has no FILE magic (0x43425355)
Failed to load $MFT: Input/output error
Failed to mount '/dev/loop1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
backup1@ubuntu:/media/backup$ 

```

It's not working. Any suggestions?

---

### Post by mb_webguy on 2010-05-05
Have you tried using testdisk to rebuild the partition table?

---

### Post by Crazydog115 on 2010-05-05
I have at one point, but I can't try anymore. The drive is basically dead. I can hear the read head just flopping around, and the OS will only see that the drive is connected for about 30 seconds.

And just now, it seems it won't spin up anymore. 

When I tried it before, it didn't work, but I can't recall what it told me.

---

### Post by Loves SSH on 2010-05-05
If you get another drive at least the size of the drive you imaged, you can 'dd' the image to the new drive. You should at that point be able to boot from it like the drive never died and get your data.

EDIT: Or if that isn't an option, you can mount the image as a local drive. Take a look at [this]("http://ubuntuforums.org/showthread.php?t=711773") for reference.

---

### Post by Crazydog115 on 2010-05-05
It's not a bootable drive. It just stored stuff, and anyway I don't have a spare drive lying around. :P

Also, I've TRIED mounting it, as stated in the OP, but it didn't work.

---


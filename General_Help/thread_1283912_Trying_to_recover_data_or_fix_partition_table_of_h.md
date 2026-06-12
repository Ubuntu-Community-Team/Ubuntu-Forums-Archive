---
title: "Trying to recover data or fix partition table of hard drive"
date: 2009-10-06
forum: General Help
---

### Post by dodle on 2009-10-06
I little while back my power supply went out, taking with it two hard disks.  One was formatted to NTFS, the other Ext2.  I ordered new logic boards for both drives.  The NTFS drive worked instantly after I replaces the logic board, but I am having much more trouble with the Ext2 drive.  Partition editors seem to recognize the drive, but I cannot mount it.  I am worried about formatting because I don't want to lose the data on the disk.  I don't even know if I can format it if the disk is physically damaged.  

Here is the readout when I try to mount it:
```
ubuntu@ubuntu:~$ sudo mount -t ext2 /dev/sdb /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I've tried using the fsck command:
```
ubuntu@ubuntu:~$ sudo fsck /dev/sdb
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb
Could this be a zero-length partition?
```

I am hopeful that the only problem is that the partition table is messed up, but I don't know how to repair it.

**Edit:** I also tried mounting the hard drive in Windows and using R-Linux and PhotoRec with no success.

---

### Post by bogdan.veringioiu on 2009-10-06
Hi.

You are trying to mount the drive, not the partition:
Try:
sudo mount -t ext2 **/dev/sdb1** /mnt
The same goes for fsck:
e2fsck -cy **/dev/sdb1**

Try to view your partitions with (if you are not sure):
fdisk -l /dev/sdb

Bogdan

---

### Post by dodle on 2009-10-12
Sorry, no luck with those.

I have gone to extremes and tried switching out the discs (the physical cd shaped part of the hard drive) but now am getting a "primary slave failure" at startup.  The two drives are identical, so I would think that putting the old drive's disc in the new drive's casing would work.

---

### Post by zer0x on 2009-10-12
You physically swapped the platters over!? Do you have your own cleanroom!?

If its still possible, what does 'sudo fdisk -l' output?

---

### Post by dodle on 2009-10-14
I haven't been able to try out that command because the OS won't load with the drive installed.  I suppose I could set the BIOS to bypass any disk failures.

"Platters"!  That's the word I was looking for, yes I switched the platters.

---

### Post by zer0x on 2009-10-14
Hi,

I was afraid of that! Switching the logic board is no problem, but physically dis-assembling the disk and swapping the platters is an incredibly risky move and should only be performed as _the_ last resort!

If your BIOS is now reporting drive failure, I am afraid you are probably out of luck. The only thing I could suggest would be try a data-recovery company, but that is likely to cost a lot of money and may still be unsuccessful.

If at any point you could get the disk back to being recognized in the OS, I would suggest using dd|ddrescue|gddrescue to create an image of the disk to another drive. You can then attempt data recovery from that image file without risking further damage to the original disk.

Good luck!

zer0x

---

### Post by dodle on 2009-10-14
Thanks, if I can get the drive to be recognized again I will try those commands.  I am trying to avoid going to a data recovery company as I cannot afford to pay $1700 dollars because the drive is formatted for Linux.  Event if it were formatted to NTFS, it would cost around $400.

---

### Post by bodhi.zazen on 2009-10-14
First, you should probably do this from a live CD. Better image the hard drive and work on the image.

Try testdisk and photorec, they are in the repositories

```
sudo apt-get install testdisk
```

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---


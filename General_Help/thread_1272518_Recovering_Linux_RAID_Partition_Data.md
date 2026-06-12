---
title: "Recovering Linux RAID Partition Data"
date: 2009-09-22
forum: General Help
---

### Post by CarlosinFL on 2009-09-22
I found my old drive which was previously in a RAID 1 mirror. The machine and 2nd drive used for the mirror are no longer available so I would like to know if it's possible to boot from Live CD and recover the data that is on the Linux RAID partition? I used Ubuntu 9.04 to boot into a live environment and was able to see my S-ATA disk with the Linux RAID partition table however I have no idea if it's possible to mount and copy  the data straight off  the disk. I need many important files that I believe to be on the partition table.

Can anyone please help me?

---

### Post by moody_mark on 2009-09-22
I would have assumed as long as the file system is readable by Linux (i.e. ext3 or FAT) then theres no reason it shouldnt be. Ive used the Live CD to boot loads of different machines and never had any problems mounting discs that had a OS on them or not. Give it a try, you wont hurt it as your booting from the CD. Id be interested to know what your results are as Im about to setup a File Server at work with Linux and two mirrored discs.

What package did you use to control the 2-disc RAID array by the way?

---

### Post by hambone79 on 2009-09-22
You should be able to mount it like a normal disk since it is most likely formatted to a regular Linux file system.

Can you post the output of this command so we can be sure:
```
sudo fdisk -l
```

---

### Post by CarlosinFL on 2009-09-22
It should have an ext3 or ext4 partition table. When I try to mount it and view the files I get the following:

```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001fd14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   fd  Linux raid autodetect

root@ubuntu:~# mount /dev/sda1 /recov/
mount: unknown filesystem type 'linux_raid_member'

root@ubuntu:~# cd /recov/

root@ubuntu:/recov# ls -l
total 0
```

---

### Post by hambone79 on 2009-09-22
Try this:

```
mount -t ext3 /dev/sda1 /recov
```

That should force it to mount ext3.

---


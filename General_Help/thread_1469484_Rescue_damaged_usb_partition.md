---
title: "Rescue damaged usb partition"
date: 2010-05-02
forum: General Help
---

### Post by Loetje on 2010-05-02
Hi,

I was copying some data from a 4GiB USB drive that had 2 partitions, 512M ext2 and 3.something GiB FAT32. I was copying from the FAT32 partition when it suddenly gave me an error message (file xx not accesible).

After that the usb drive is shown by gparted as 4GiB of unallocated space.

sudo fdisk -l gives me
```
Disk /dev/sdf: 3898 MB, 3898142208 bytes
120 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 7440 * 512 = 3809280 bytes
Disk identifier: 0x00000000

Disk /dev/sdf doesn't contain a valid partition table

```

I tried this tuturial: [http://ubuntuforums.org/showthread.php?t=308821]("http://ubuntuforums.org/showthread.php?t=308821")

Which worked fine up untill I tried fsck. It gave me this response
```
sudo fsck -y /home/niels/rescue.img 
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /home/niels/rescue.img

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

I tried e2fsck -b 8193 <device> with the same result:

```
sudo e2fsck -b 8193 /home/niels/rescue.img 
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Bad magic number in super-block while trying to open /home/niels/rescue.img

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

CAn anyone tell me how to recover the data on the usb drive? I am mainly interested in the stuff that was on the FAT32 partition..

---


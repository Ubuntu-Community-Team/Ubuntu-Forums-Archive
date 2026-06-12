---
title: "Cannot mount drive"
date: 2010-03-22
forum: General Help
---

### Post by boatman1 on 2010-03-22
I've been trying to mount a USB drive, this is what I've done so far

sudo fdisk -l

```
Disk /dev/sdb: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdca51e9c
```

sudo pmount /dev/sdb (I've tried all commands with /dev/sdb1 too)

```
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

ntfs-config (enabled NTFS capabilities)
Tried to mount again, same problem.

Tried mounting to mount point:

sudo mkdir /media/external

sudo mount -t vfat /dev/sdb /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I'm not sure what else to try. My other USB drives don't have this problem, in fact, this one has worked fine so far.

(I have about 2gb of photos stored on it, so I can't wipe it. Yeah it was stupid not backing it up.)

---

### Post by prodigy_ on 2010-03-22
Err. Why are you trying to mount a **physical device** (/dev/sdb)? You should only mount **partitions** (e.g. /dev/sdb1), exactly like mount command output hinted.

And your "fdisk -l" output looks incomplete, because there are no partitions listed. Are you 100% sure that the disk is working properly? I'd suggest to try to access it from another PC, if possible.

---

### Post by boatman1 on 2010-03-22
> **prodigy_ said:**
> Err. Why are you trying to mount a **physical device** (/dev/sdb)? You should mount only **partitions** (e.g. /dev/sdb1), exactly like mount command output hinted.

And your "fdisk -l" output looks incomplete, because there are no partitions listed. Are you sure that the disk is alright?

I said I tried all commands with /dev/sdb1 as well, made no difference.

Full output:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00860085

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18702   150223783+  83  Linux
/dev/sda2           18703       19457     6064537+   5  Extended
/dev/sda5           18703       19457     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdca51e9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         491     3943926   83  Linux

```

---

### Post by prodigy_ on 2010-03-22
Well, that's even more interesting. Your /dev/sdb1 is neither NTFS nor VFAT. According to fdisk it's type 0x083/Linux which means it's formatted with either ext2/ext3 or ext4. Try: ```
sudo mount -t ext4 /dev/sdb1 /media/external
```

---

### Post by prodigy_ on 2010-03-22
[Edit: sorry, double post]

---

### Post by boatman1 on 2010-03-22
> **prodigy_ said:**
> Well, that's even more interesting. Your /dev/sdb1 is neither NTFS nor VFAT. According to fdisk it's type 0x083/Linux which means it's formatted with either ext2/ext3 or ext4. Try: ```
sudo mount -t ext4 /dev/sdb1 /media/external
```

```

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

By the way, I have encrypted stuff on it (I used true crypt) but I don't think that would make any difference, it hasn't in the past.

---

### Post by prodigy_ on 2010-03-22
Hmm. Try ```
e2fsck -C /dev/sdb1
``` (This command won't do anything if the filesystem isn't really ext. If you're 100% sure this disk is, for example, VFAT-formatted you'd better use Windows chkdsk utility to check it.)

---

### Post by boatman1 on 2010-03-22
Hmm this is strange. I can 'mount' it using TrueCrypt. Turns out the whole thing was encrypted.

I've managed to copy the files so they're safe now, but I still can't do anything with it without TrueCrypt. I've tried partitioning it but it won't let (in GParted).

Thank you btw prodigy. It says 'unknown' for format...

---

### Post by miegiel on 2010-03-22
> **boatman1 said:**
> Hmm this is strange. I can 'mount' it using TrueCrypt. Turns out the whole thing was encrypted.

I've managed to copy the files so they're safe now, but I still can't do anything with it without TrueCrypt. I've tried partitioning it but it won't let (in GParted).

Thank you btw prodigy. It says 'unknown' for format...

Making partitions and file systems in a terminal :
```
sudo fdisk /dev/sdb1
sudo mkdosfs /dev/sdb1
or
sudo mkfs.ntfs --help (pick your options ;)
```
Making file systems (mkfs) is called formatting in windows speak.

Also, flash memory doesn't live for ever. I had a USB stick that had become to senile to remember what a file allocation table looks like.

---

### Post by gordintoronto on 2010-03-22
Don't put a swap file on a flash drive, it will have a very short life.

---


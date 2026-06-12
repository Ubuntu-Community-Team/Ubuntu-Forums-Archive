---
title: "How to mount USB flash drive"
date: 2009-10-30
forum: General Help
---

### Post by emigrant on 2009-10-30
hi,
if i plug in USB pen from one user, it is not available for the other user.
how to mount it in such a way that it is available for all the users.

thank you very much.

---

### Post by Giblet5 on 2009-10-30
You need to tweak [HAL]("http://www.linuxfromscratch.org/blfs/view/svn/general/hal.html").

It would be nice if there were a GUI interface to HAL configuration, but I don't know of one...

---

### Post by Gatemaze on 2009-10-30
if you could only mount it belonging to a particular group with rwx permissions and where the users are members of...

---

### Post by emigrant on 2009-10-30
> **Gatemaze said:**
> if you could only mount it belonging to a particular group with rwx permissions and where the users are members of...
how? :(

---

### Post by Giblet5 on 2009-10-30
> **Gatemaze said:**
> if you could only mount it belonging to a particular group with rwx permissions and where the users are members of...

Hacker. ;)

---

### Post by Giblet5 on 2009-10-30
> **emigrant said:**
> how? :(

Pick a directory or make one. Change its ownership so that a group that you're both members of can write to it.

Use the mount command to mount it there.

Example: Users bob and mike would like to access an external USB disk drive.

Open a terminal window and enter the following commands:
```
sudo mkdir /media/FatDrive
sudo groupadd mikebob
sudo usermod -a -G mikebob bob
sudo usermod -a -G mikebob mike
sudo chown bob:mikebob /media/FatDrive
sudo chmod 770 /media/FatDrive
```

Now you're ready to mount the drive.
```
sudo fdisk -l | grep FAT32
##
## Which drive is the external disk?
## Let's assume it's /dev/sdc1
sudo umount /dev/sdc1
sudo mount /dev/sdc1 /media/FatDrive -o noatime,user -tvfat
```

Your best bet is still to modify the HAL configuration.

---

### Post by Gatemaze on 2009-10-30
giblet has given you the exact commands above... only they have to be done all the time (well the umount, mount ones). adding a script still pain... or maybe fstab may have smth to do with it... like adding the line

```

/dev/sdc1 /media/FatDrive -o noatime,user -tvfat

```

bear in mind that even if this works... it will fail if you plug in another usb pen beforahand... unless.... you replace /dev/sdc1 with the disk number maybe...

otherwise as giblet also said editing the hal configuration is the way...

---

### Post by emigrant on 2009-10-30
@ Giblet5,
my 4GB pendrive looks confusing :(
is it ok if i just mount **sdb**?

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03550354

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51200000    7  HPFS/NTFS
/dev/sda2            6375       11474    40960000    7  HPFS/NTFS
/dev/sda3           11475       11499      200812+  82  Linux swap / Solaris
/dev/sda4           11500       19457    63922635    5  Extended
/dev/sda5           11500       19170    61617276   83  Linux
/dev/sda6           19437       19457      168651   82  Linux swap / Solaris
/dev/sda7           19171       19436     2136613+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4022 MB, 4022337536 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x83f5fd0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         460     3694918+   b  W95 FAT32
/dev/sdb2             461         489      232942+   5  Extended
/dev/sdb5             461         489      232911   82  Linux swap / Solaris
```

---

### Post by Gatemaze on 2009-10-30
that should be sdb1... but it will fail if next time you mount a usb pen before this one... (it will be sdc1)... maybe you can use the uuid... when mounted do
```

ls -l /dev/disk/by-uuid/

```

you also need to have a look on what the fstab lines mean, in order to set the correct group, masks, etc... there is plenty of info in the forum about this...

this might be of information help
[http://liquidat.wordpress.com/2007/10/15/short-tip-get-uuid-of-hard-disks/](http://liquidat.wordpress.com/2007/10/15/short-tip-get-uuid-of-hard-disks/)

---

### Post by emigrant on 2009-10-30
[Gatemaze]("http://ubuntuforums.org/member.php?u=406538"), thank you very much for the help,
i will look at the link you gave. :)

---

### Post by Giblet5 on 2009-10-30
> **emigrant said:**
> @ Giblet5,
my 4GB pendrive looks confusing :(
is it ok if i just mount **sdb**?

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03550354

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51200000    7  HPFS/NTFS
/dev/sda2            6375       11474    40960000    7  HPFS/NTFS
/dev/sda3           11475       11499      200812+  82  Linux swap / Solaris
/dev/sda4           11500       19457    63922635    5  Extended
/dev/sda5           11500       19170    61617276   83  Linux
/dev/sda6           19437       19457      168651   82  Linux swap / Solaris
/dev/sda7           19171       19436     2136613+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4022 MB, 4022337536 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x83f5fd0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         460     3694918+   b  W95 FAT32
/dev/sdb2             461         489      232942+   5  Extended
/dev/sdb5             461         489      232911   82  Linux swap / Solaris
```


You can't mount a physical IDE (SATA/PATA) disk. You have to mount a partition.

USB sticks appear as an IDE type disk.

You have two partitions defined and one filesystem. You can mount the FAT32 filesystem only.

The second partition (sdb5) is swap space (not mountable).

Adding an entry for the UUID of /dev/sdb1 in /etc/fstab will allow you to mount that where you want (eg, /media/FatDrive) whenever the stick is inserted and regardless of what other sticks have been inserted.

Tech Note: Don't rely too heavily on flash memory. It's a great technology, but it degrades with every write cycle and *will* eventually fail.


Editing the HAL config is still the best option.

---

### Post by emigrant on 2009-10-30
Thank u. Il first give a try to this and go for HAL editing. Bcz at the first impression it looks like more complex :D

---


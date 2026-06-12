---
title: "What are my options for mounting a HD when..."
date: 2010-03-13
forum: General Help
---

### Post by nuclearj on 2010-03-13
the system is empty.

I got a computer from a friend and want to get access to the music that is on either or both of the HDs.  Access worked through win xp (should have transfered them then)  I installed Karmic on a diff HD, Ubuntu can see them but cannot open them.  Any ideas?

partial output of 'sudo fdisk -l'
```
Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82580b4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    0  Empty

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82580b4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14593   117218241    0  Empty

```

---

### Post by srs5694 on 2010-03-13
There's something very strange about those disks: A partition type code ("Id" column in the output) of 0 refers to an empty partition, and it's not normally used. That said, Linux should still be able to mount those partitions (I just tested), although I did so using the text-mode "mount" command, not a GUI. I don't know what GUI you're using (if you're using one) or how it would react.

Thus, I recommend you either open a terminal/xterm and mount the partitions manually or change the type codes to something appropriate -- probably 0x07 (NTFS) or perhaps 0x0c (FAT-32).

---

### Post by nuclearj on 2010-03-13
> **srs5694 said:**
> There's something very strange about those disks: A partition type code ("Id" column in the output) of 0 refers to an empty partition, and it's not normally used. That said, Linux should still be able to mount those partitions (I just tested), although I did so using the text-mode "mount" command, not a GUI. I don't know what GUI you're using (if you're using one) or how it would react.

Thus, I recommend you either open a terminal/xterm and mount the partitions manually or change the type codes to something appropriate -- probably 0x07 (NTFS) or perhaps 0x0c (FAT-32).

i am using the terminal and I tried to mount it with 

```
sudo mount /dev/sdb /media/Storage/
```

and I got this back
```
nuclearj@nuclearj-office:/$ sudo mount /dev/sdb /media/Storage/
[sudo] password for nuclearj: 
mount: you must specify the filesystem type
```

then i tried this

```
sudo mount dos /dev/sdb /media/Storage/
```

and then it gave me the manual... I'm very much an amateur still

How would I go about changing the types?

---

### Post by nuclearj on 2010-03-13
so i tried changing the type in the Palimpest Disk Utility, and it would not take.  how would it look in the command line?

---

### Post by srs5694 on 2010-03-13
You need to mount the *partition,* not the *whole disk:*

```

mount /dev/sdb1 /media/Storage

```

Note /dev/sdb1, not /dev/sdb.

To change a partition type code using fdisk, you use the 't' option:

```

$ sudo fdisk /dev/sdc
Password: 

The number of cylinders for this disk is set to 1965.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sdc: 16.2 GB, 16166944768 bytes
255 heads, 63 sectors/track, 1965 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003d423

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         260     2088418+  83  Linux
/dev/sdc2            1325        1965     5148832+  83  Linux

Command (m for help): t
Partition number (1-4): 1
Hex code (type L to list codes): 07
Changed system type of partition 1 to 7 (HPFS/NTFS)

Command (m for help): p

Disk /dev/sdc: 16.2 GB, 16166944768 bytes
255 heads, 63 sectors/track, 1965 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003d423

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         260     2088418+   7  HPFS/NTFS
/dev/sdc2            1325        1965     5148832+  83  Linux

Command (m for help): 

```

---

### Post by nuclearj on 2010-03-13
Okay so I did change the system type and got these errors when I tried to mount the partitions:

```
nuclearj@nuclearj-office:~$ sudo mount -t ntfs /dev/sdc1 /media/Storage
NTFS signature is missing.
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

and then I chanced it to a FAT-32 and got this when trying to mount

```
nuclearj@nuclearj-office:~$ sudo fdisk /dev/sdc

The number of cylinders for this disk is set to 14593.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): c
Changed system type of partition 1 to c (W95 FAT32 (LBA))

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: If you have created or modified any DOS 6.x
partitions, please see the fdisk manual page for additional
information.
Syncing disks.
nuclearj@nuclearj-office:~$ sudo mount -t vfat /dev/sdc1 /media/Storage
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Is there a way to find out the exact fs type?

---

### Post by srs5694 on 2010-03-13
You can try "mount" without specifying a filesystem type ("-t ntfs" or "-t vfat") and the kernel should autodetect the filesystem type; however, FAT and NTFS are the only likely candidates for a Windows system, so it seems unlikely that this would work. It *might* still work if the Windows system had unusual filesystem drivers -- say, for HFS+ (OS X).

---


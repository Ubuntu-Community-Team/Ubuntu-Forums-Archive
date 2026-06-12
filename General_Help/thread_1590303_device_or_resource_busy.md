---
title: "device or resource busy"
date: 2010-10-07
forum: General Help
---

### Post by revtds on 2010-10-07
I had an internal drive that I used for miscellaneous data, besides my bootable main drive, with Vista/Ubuntu 10.04 dual boot.

I recently pulled all of the data off of it to make it an internal backup, so I could use cron to schedule daily or weekly backups at night.

I deleted the two partitions on it, which were a trial install of Lucid. I then made one new partition, and formatted it to NTFS, so I could access it from Windows as well as Linux.

It won't mount now.

Every time I try to mount it, it says it couldn't because the resource or device is busy.  It shows a 69 Meg usage area on it, so when I tried to have GParted fix it, which it tried to do by resizing it, it said another OS was using it at the same time so it could do nothing so data integrity would not be compromised.

Below are the results of several commands I have tried from reading the forums:

tom@ubuntu910:~$ sudo blkid
/dev/sda1: UUID="C8A6FA38A6FA271A" TYPE="ntfs" 
/dev/sda6: LABEL="root" UUID="5f06e19e-06c9-4d75-ab2d-052e1090d4a2" TYPE="ext3" 
/dev/sda7: LABEL="home" UUID="7f9cd98b-861a-4983-8b4b-9cf29c4cb48d" TYPE="ext3" 
/dev/sdb1: UUID="13F9DEA83F27A53F" TYPE="ntfs" 
/dev/sdc1: LABEL="My Book" UUID="A2E8CC08E8CBD925" TYPE="ntfs" 
/dev/mapper/cryptswap1: UUID="3e6d335a-f871-4cca-a0c6-72739871fe2c" TYPE="swap" 
/dev/mapper/cryptswap2: UUID="be08cae0-a019-41ef-9447-07c23e8cadd4" TYPE="swap" 

tom@ubuntu910:~$ ntfsfix /dev/sdb1
Mounting volume... Error opening partition device: Permission denied.
Failed to startup volume: Permission denied.
FAILED
Attempting to correct errors... Error opening partition device: Permission denied.
FAILED
Failed to startup volume: Permission denied.
Volume is corrupt. You should run chkdsk.

tom@ubuntu910:~$ sudo fuser -m /dev/sdb1
tom@ubuntu910:~$

tom@ubuntu910:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000776ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12494   100352000    7  HPFS/NTFS
/dev/sda2           12495       38373   207867962+   5  Extended
/dev/sda5           12495       13513     8185086   82  Linux swap / Solaris
/dev/sda6   *       13514       17337    30716248+  83  Linux
/dev/sda7           17338       25496    65534976   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a24b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdc: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000564d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121516   976075744    7  HPFS/NTFS

tom@ubuntu910:~$ sudo mount -a
fuse: mount failed: Device or resource busy
tom@ubuntu910:~$ 

tom@ubuntu910:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/InternalBackup -o force
fuse: mount failed: Device or resource busy
tom@ubuntu910:~$ 

tom@ubuntu910:~$ cat /etc/fstab
proc            /proc           proc    defaults        0       0
UUID=5f06e19e-06c9-4d75-ab2d-052e1090d4a2 /               ext3    errors=remount-ro 0       1
UUID=7f9cd98b-861a-4983-8b4b-9cf29c4cb48d /home           ext3 defaults 0 2
UUID=13F9DEA83F27A53F /media/InternalBackup	ntfs	defaults 0 2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/mapper/cryptswap2 none swap sw 0 0

---

### Post by andrewthomas on 2010-10-07
maybe this is a silly question, but is it already mounted?
 
If you go to media in nautilus do you see it?
 
What happens if you try to unmount it?

---

### Post by revtds on 2010-10-07
tom@ubuntu910:~$ sudo umount /dev/sdb1
[sudo] password for tom: 
umount: /dev/sdb1: not mounted

It can be seen in "Places", It shows up everywhere, but will not mount or unmount, and always returns that it is busy.

---

### Post by revtds on 2010-10-07
When I try to mount it from "Places" it says:

"Unable to mount 160 Gb Filesystem - One or more block devices are holding /dev/sdb1"

---

### Post by andrewthomas on 2010-10-07
What about if you take it out of your fstab and reboot.

---

### Post by revtds on 2010-10-08
There must have been a fschk running, although I could not identify anything in the system monitor.

Next morning, and it boots fine, "mount" returns no errors and it is listed.  

The only thing I don't understand, being the noob that I am is that it is listed as:

/dev/sdb1 on /media/InternalBackup type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

What is fuseblk, and does it matter?

Time for some research again, I guess.

---


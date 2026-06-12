---
title: "Can't mount previous ubuntu installation to access files"
date: 2012-08-22
forum: General Help
---

### Post by desertrocks on 2012-08-22
Hi Guys,

Long story. I recently installed Ubuntu Server 12.04. It was working great until a friend of mine wanted to copy some movies from my server. I plugged in the thumb drive... it was detected but couldn't be mounted. After reading around I found that I could mount it by editing the fstab file. I can't recall what changes I made specifically but when I rebooted the server could no longer mount the ubuntu partition.

I searched around but found that it was just easier for me to load up my other HD with a fresh install. Once I had that completed I hooked up my old HD to recover some files but, like the thumb drive, it can be seen but not mounted.

I've searched around but haven't come across anything describing this specific issue. Some similar issues describe editing the fstab and whatnot but after my last experience with editing fstab I'd be more comfortable having the more experienced assess the issue.

tl;dr
Can't mount old Ubuntu drive to recover files.

I have two identical 750gb Hard Drives.

```
andrew@Proliant:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000ec8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1465147391   732322817    5  Extended
/dev/sda5          501760  1465147391   732322816   8e  Linux LVM

Disk /dev/mapper/Proliant-root: 741.3 GB, 741305483264 bytes
255 heads, 63 sectors/track, 90125 cylinders, total 1447862272 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/Proliant-root doesn't contain a valid partition table

Disk /dev/mapper/Proliant-swap_1: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/Proliant-swap_1 doesn't contain a valid partition table

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00060dfe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      499711      248832   83  Linux
/dev/sdc2          501758  1465147391   732322817    5  Extended
/dev/sdc5          501760  1465147391   732322816   8e  Linux LVM

```

You can see /dev/mapper/Proliant-swap_1 has 0x00000000 as an identifier... which is concerning.

How should I proceed?

---

### Post by steeldriver on 2012-08-22
fdisk reports Disk identifier: 0x00000000 for all my lvm2 volumes as well - I don't think that's necessarily an issue

I assume you're trying to mount the LVM? if so I'd start by running

```
sudo lvdisplay
```If the volume is listed as 'NOT available' you can try to change its status to 'available' using

```
sudo lvchange -ay /dev/*vgname*/*lvname*
```where *vgname *and *lvname* are your volume group and logical volume names. If that works you should be able to mount the filesystem normally as

```
sudo mount /dev/mapper/*vgname*-*lvname mountpoint*
```where *mountpoint*  is your chosen filesystem mount point e.g. /mnt/oldsys (which you'll have to create first with sudo mkdir /mnt/oldsys).

You *may* need to specify a filesystem type explicitly with -t but let's try without first. Obviously if lvdisplay shows it as available already then you can skip straight to mounting. You may want to add -o ro if you don't want to risk modifying any existing data.

---

### Post by desertrocks on 2012-08-22
**lvdisplay**
```
  /dev/dm-0: read failed after 0 of 4096 at 0: Input/output error
  /dev/dm-1: read failed after 0 of 4096 at 0: Input/output error
  --- Logical volume ---
  LV Name                /dev/ProLiant/root
  VG Name                ProLiant
  LV UUID                d0Zfff-Stm0-8eim-jNdM-TXxI-d7O6-sZBBJ4
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                690.39 GiB
  Current LE             176741
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0

  --- Logical volume ---
  LV Name                /dev/ProLiant/swap_1
  VG Name                ProLiant
  LV UUID                a9VewH-RYC2-PUX2-dlkp-gciz-7zma-59FpP8
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                8.00 GiB
  Current LE             2048
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

  --- Logical volume ---
  LV Name                /dev/Proliant/root
  VG Name                Proliant
  LV UUID                iWcUbv-1ft4-1pRy-jw4D-KhPB-PNjg-c01itE
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                690.39 GiB
  Current LE             176741
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2

  --- Logical volume ---
  LV Name                /dev/Proliant/swap_1
  VG Name                Proliant
  LV UUID                qv0Mro-T4tg-ahmn-DcZZ-RqBO-2FKs-ev2jIv
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                8.00 GiB
  Current LE             2048
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3

```

Looks like it's available. Thankfully I made a typo when naming the server this time around. The old system was named ProLiant whereas now it is Proliant (note the capitol L). If it weren't for that, I wouldn't know how to tell these apart. 

So I ran
**sudo mount /dev/mapper/ProLiant-root Samba Share**
```
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

:confused: I'm pretty sure the vgname and lvname are probably wrong. Sorry... I'm still a newbie. What would you do from here?

---

### Post by steeldriver on 2012-08-22
Hmm... I wasn't aware you could mount to a samba share like that? are you sure that's even possible?

Personally I would go old school and try something like

```
sudo mkdir -p /mnt/oldsys
sudo mount /dev/mapper/ProLiant-root /mnt/oldsys

```However this worries me:

> /dev/dm-0: read failed after 0 of 4096 at 0: Input/output error
/dev/dm-1: read failed after 0 of 4096 at 0: Input/output error

---

### Post by desertrocks on 2012-08-22
Samba Share is a folder in my Home directory. I planned on sharing it later. For now I'll follow your lead and mount it in /mnt/oldsys.

```
sudo mount /dev/mapper/ProLiant-root /mnt/oldsys
mount: you must specify the filesystem type

```

So I tried these things:
```
andrew@Proliant:~$ sudo mount -t auto /dev/mapper/ProLiant-root /mnt/oldsys
mount: you must specify the filesystem type

andrew@Proliant:~$ sudo mount -t ext4 /dev/mapper/ProLiant-root /mnt/oldsys
mount: wrong fs type, bad option, bad superblock on /dev/mapper/ProLiant-root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

andrew@Proliant:~$ sudo mount -t ext3 /dev/mapper/ProLiant-root /mnt/oldsys
mount: wrong fs type, bad option, bad superblock on /dev/mapper/ProLiant-root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by steeldriver on 2012-08-22
OK in that case let's try to probe the fs type; either

```
sudo file -sL /dev/mapper/ProLiant-root

```
or

```
sudo parted /dev/mapper/ProLiant-root print

```
should tell you - then you can repeat the mout command adding -t *fstype *where *fstype *is whatever you get from above

---

### Post by desertrocks on 2012-08-22
```
andrew@Proliant:~$ sudo file -sL /dev/mapper/ProLiant-root
/dev/mapper/ProLiant-root: ERROR: cannot read `/dev/mapper/ProLiant-root' (Input/output error)
andrew@Proliant:~$ sudo parted /dev/mapper/ProLiant-root print
Error: /dev/mapper/ProLiant-root: unrecognised disk label
```

Input/output error? I have a hard time believing the drive went bad as soon as I changed the fstab file...

---


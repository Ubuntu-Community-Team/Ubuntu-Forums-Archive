---
title: "Cannot mount NTFS partition"
date: 2010-01-03
forum: General Help
---

### Post by Wouter N on 2010-01-03
Hi,

I'm trying to mount an NTFS partition, to access my files stored on this partition. However, the disk gets detected by fdisk:
*sudo fdisk -l*
```

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x852eb261

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?           1        5100    40960000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            5100       13672    68857852    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           13673       14946    10233405    5  Extended
/dev/sda5           13673       14946    10233373+  83  Linux

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x211d7cc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2432    19535008+  83  Linux
/dev/sdb2            2433        2918     3903795    5  Extended
/dev/sdb5            2433        2918     3903763+  82  Linux swap / Solaris

```

When I try:
```

sudo mount -t ntfs /dev/sda1 /media/windows

```
I get the following error:
```

ntfs-3g: Failed to access volume '/dev/sda1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.

```
How do i solve this? It is being detected right? But the mount commands says otherwise...?

---

### Post by DeMus on 2010-01-03
Try this:

Auto mount Windows disks
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

---

### Post by Wouter N on 2010-01-03
The NTFS Configuration tool only spawns a box with 2 options (Enable write support for internal/external device), it does not allow me to choose drives I want to be automounted :(

---

### Post by Leppie on 2010-01-03
Is the partition encrypted?

---

### Post by mhh91 on 2010-01-03
> **Wouter N said:**
> The NTFS Configuration tool only spawns a box with 2 options (Enable write support for internal/external device), it does not allow me to choose drives I want to be automounted :(

edit the file /etc/fstab


you'll find your partitions listed in the file,probably with the flag "noauto",which means that they won't be automounted when the system boots,change that flag to "auto"

---

### Post by Wouter N on 2010-01-04
> **Leppie said:**
> Is the partition encrypted?
No, it isn't encrypted with bitlocker or anything else afaik...

> **mhh91 said:**
> edit the file /etc/fstab


you'll find your partitions listed in the file,probably with the flag "noauto",which means that they won't be automounted when the system boots,change that flag to "auto"
I added the following line to my /etc/fstab file(/dev/sda1 wasn't mentioned yet):
```

/dev/sda1 /media/windows ntfs-3g defaults 0 0

```
But no effect...

---

### Post by K.J. on 2010-01-04
Try
sudo mount -t ntfs /dev/sda1 /media/windows -o force

Also, boot from an XP disc and run checkdisk.

---


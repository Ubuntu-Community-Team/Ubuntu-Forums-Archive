---
title: "Ubuntu 10.4 Hard Drive Missing"
date: 2010-05-24
forum: General Help
---

### Post by pobri19 on 2010-05-24
Hi guys, I'm having trouble locating my second hard disk on my fresh Ubuntu 10.4 install. 

It's a terabyte drive that I cannot seem to find in Ubuntu. It's formatted in NTFS and is over 90% full of data. 

If I boot into Windows 7 the drive appears fine and the data is all there and Windows disk scan doesn't report any problems.

The drive: WDC WD10EADS-00L5B1 ATA Device (as listed on Windows 7)
Disk 1 (According to Windows 7)

Here is my fstab, fdisk and uname:

```
linux@nix:/dev$ uname -a
Linux nix 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
```

```
linux@nix:/dev$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

```
linux@nix:/dev$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5eb6f2c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          51      402432    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              51       11241    89884672    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           11241      108853   784071680    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4          108853      121602   102400001    f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5          108853      121602   102400000   83  Linux

```

As you can see from the above, my other drive is detected fine (the one with the Windows installation and Ubuntu installation on it)

Any help would be greatly appreciated! Thanks.

EDIT: On a side not, I don't have a floppy drive installed, so I'm not sure why fd0 is listed (perhaps it's irrelevant - I'm new to the Linux world so I wouldn't know)

---

### Post by pobri19 on 2010-05-24
Bump, anyone? This is quite urgent :(

---

### Post by pobri19 on 2010-05-25
And here's lsscsi output:

~$ sudo lsscsi
[8:0:0:0]    cd/dvd  HL-DT-ST BDDVDRW CH08LS10 2.00  /dev/sr0
[9:0:0:0]    disk    ATA      WDC WD1001FALS-0 05.0  /dev/sda

---

### Post by pobri19 on 2010-05-25
Someone please help :(

I also just realized I have ANOTHER drive that isn't being detected in Ubuntu, but is being detected in Windows. The reason I didn't realize because it wasn't formatted in Windows (so I didn't see it) but when I booted into the BIOS I confirmed the existence of it (and remembered I put it in there :P). 

So obviously there's something weird going on with Ubuntu if 2 drives won't show for no reason... I booted into the BIOS and they appear fine:

Channel 5, Slave: WDC WD1001 FALS (Windows/Ubuntu drive - the working one)
Channel 6, Master: WDC WD2500 AAKS (The 250GB drive that I didn't notice I had - is also not appearing)
Channel 7, Master: WDC WD10EADS (The second 1TB drive that isn't showing... The one this thread was initially about)

The BIOS is also up to date, so it's not that. Surely a problem with Ubuntu, no idea WHAT the problem is though.

---

### Post by pobri19 on 2010-05-25
I figured out the problem. Turns out Ubuntu doesn't want to detect disks plugged into SATA 3.0 ports... It's a new motherboard with SATA 3.0 support.

Does anyone know how I can get SATA 3.0 support on my Ubuntu installation? Perhaps there's a kernel module or driver for this?

---


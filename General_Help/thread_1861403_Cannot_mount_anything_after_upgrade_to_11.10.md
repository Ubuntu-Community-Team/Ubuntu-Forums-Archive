---
title: "Cannot mount anything after upgrade to 11.10"
date: 2011-10-15
forum: General Help
---

### Post by aquamaster on 2011-10-15
I can't mount anything, Cant mount partitions on the same hard drive or any usb flash drives. My PC is dual-booted with windows 7. Another problem is I can't shut down, if I click shut down it just logs me off, i have to do "sudo halt" for it to turn off.

---

### Post by aquamaster on 2011-10-15
jack@jack-Satellite-L355:~$ sudo fdisk -l
[sudo] password for jack: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x31b16e49

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   104857599    52427776    7  HPFS/NTFS/exFAT
/dev/sda2       452454713   488395847    17970567+   7  HPFS/NTFS/exFAT
/dev/sda3       104857600   452452351   173797376   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 2006 MB, 2006974464 bytes
16 heads, 32 sectors/track, 7656 cylinders, total 3919872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8064     3919871     1955904    e  W95 FAT16 (LBA)
jack@jack-Satellite-L355:~$ 

jack@jack-Satellite-L355:~$ groups
jack adm dialout fax cdrom floppy tape audio dip video plugdev fuse netdev lpadmin admin sambashare vboxusers

---

### Post by aquamaster on 2011-10-15
Bump...really need to get this fixed

---

### Post by effenberg0x0 on 2011-10-15
Try this:

Save your work first, your session will be restarted.
```
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo service lightdm restart

```Please report back.

Effenberg

---


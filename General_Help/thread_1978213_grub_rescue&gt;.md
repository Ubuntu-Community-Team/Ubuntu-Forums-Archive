---
title: "grub rescue&gt;"
date: 2012-05-11
forum: General Help
---

### Post by ico170 on 2012-05-11
i just instaled ubuntu over my windows xp and wanted to have a dual boot but when i restarted this appear on mz screen:

Error: no such device: 84fe8f44-8392-4d5d-ba3f-d9541746b25a
grub rescue>

this is mz 
sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00091ae0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488375999   244187968+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb5981567

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16126   198064127    99024001    f  W95 Ext'd (LBA)
/dev/sdb2   *   198064128   312580095    57257984   83  Linux
/dev/sdb5           16128   193871495    96927684    7  HPFS/NTFS/exFAT
/dev/sdb6       193871872   198064127     2096128   82  Linux swap / Solaris

and
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="DA74BDBB74BD9B29" TYPE="ntfs" 
/dev/sdb2: UUID="f21150ae-3782-4d67-ae37-7e0ed5f28045" TYPE="ext4" 
/dev/sdb5: LABEL="stari" UUID="300472030471CBFA" TYPE="ntfs" 
/dev/sr0: LABEL="Ubuntu 12.04 LTS i386" TYPE="iso9660"

---

### Post by kc1di on 2012-05-11
in ubuntu install boot repair or use it from a cd.
it should fix it for you 
you can get it here: 

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---


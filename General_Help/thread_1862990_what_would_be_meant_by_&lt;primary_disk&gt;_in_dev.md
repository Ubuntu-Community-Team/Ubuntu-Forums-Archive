---
title: "what would be meant by &lt;primary_disk&gt; in /dev/&lt;primary_disk&gt; ?"
date: 2011-10-17
forum: General Help
---

### Post by Helen84 on 2011-10-17
im trying to follow the instructions @ [http://lfscript.org/docs/installing.htm](http://lfscript.org/docs/installing.htm)

i get to #7 

**Then set up Grub in the chroot environment:     ****chroot ./rootfs grub-install /dev/<primary_dis**k>

what is <primary_disk>? 

this is my partition layout?

```
helen@scruffy-ubunntu:~# fdisk -ls

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8cdd4106

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25190   202334278    7  HPFS/NTFS
/dev/sda2   *       25190       25203      102400    7  HPFS/NTFS
/dev/sda3           25203      121602   774322177    5  Extended
/dev/sda5           25203       49691   196701773    7  HPFS/NTFS
/dev/sda6           49691       75188   204800000   83  Linux
/dev/sda7           75188       76208     8192000   82  Linux swap / Solaris
/dev/sda8           76208       77483    10240000   83  Linux
/dev/sda9           77483       77610     1024000   82  Linux swap / Solaris
/dev/sda10          77610       80160    20480000   83  Linux
/dev/sda11          80160       80670     4096000   82  Linux swap / Solaris
helen@scruffy-ubunntu:~#


```

/dev/sda2  is win7 & /dev/sda6 is ubuntu10.10

---

### Post by Is Mise on 2011-10-17
Your primary disk is /dev/sda

---


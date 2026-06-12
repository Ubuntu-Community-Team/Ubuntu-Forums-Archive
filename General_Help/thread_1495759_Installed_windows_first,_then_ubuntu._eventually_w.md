---
title: "Installed windows first, then ubuntu. eventually windows not accessible... [="
date: 2010-05-28
forum: General Help
---

### Post by emigrant on 2010-05-28
following is my fdisk:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xed73ed73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12110    97272552    f  W95 Ext'd (LBA)
/dev/sda2   *       12111       19458    59016192   83  Linux
/dev/sda5             244        4462    33886749    7  HPFS/NTFS
/dev/sda6            4463        8286    30716248+   7  HPFS/NTFS
/dev/sda7            8287       12110    30716248+   7  HPFS/NTFS
/dev/sda8               1         244     1951744   82  Linux swap / Solaris

Partition table entries are not in disk order
```


sda5 is the windows partion.

please help to restore the grub.

thanks a lot.

---

### Post by dino99 on 2010-05-28
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

more into links below

---

### Post by emigrant on 2010-05-28
hi,
thanks for the reply,
but it seems too difficilut for me.
im bit naive in handling this issue.
please suggest a simpler way.
thanks.

---

### Post by emigrant on 2010-05-28
im ready to format both win and linux, except the following:

/dev/sda6            4463        8286    30716248+   7  HPFS/NTFS
/dev/sda7            8287       12110    30716248+   7  HPFS/NTFS


please suggest the right way to install both win and lin.
i failed twice trying to install win first and lin then.

thanks.

---


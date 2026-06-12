---
title: "Delete windows"
date: 2010-02-23
forum: General Help
---

### Post by DJ . on 2010-02-23
I have a partition set up for windows and Linux. Windows died. I know about fdisk, so I posted the outcome of fdisk -l:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16351635

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7935    63737856    7  HPFS/NTFS
/dev/sda2            7936        7936        8032+   f  W95 Ext'd (LBA)
```

what I can't find out, is is sda1 windows or sda2? How do I know which one to delete?

---

### Post by mikewhatever on 2010-02-24
Well, since sda2 is only about 8MB and can't possibly hold a Windows installation, I'd say it has to be sda1.

---

### Post by shihkster1015 on 2010-02-24
Same, I'd say it's sda1. It's the right filesystem and the size of sda2's impossible. 
I'm not sure about windows if it uses another smaller partition to store the boot data, but it's flagged to boot from sda1, so i'm pretty sure it's sda1.

---

### Post by cong06 on 2010-02-24
Do you have multiple drives? how did you get Ubuntu installed on 8MB?

---


---
title: "Boot menu doesn't show Vista"
date: 2010-10-17
forum: General Help
---

### Post by Ningamer on 2010-10-17
Hey guys,

I just installed Ubuntu on my laptop, which also has Vista installed. HOWEVER... On boot I only get five options: Ubuntu, Ubuntu (Recovery), both MemTests and a Windows Recovery. Where's my Vista gone? I left it's partition completely alone during installation, and I can find all the Windows files in Ubuntu, but I can't boot it. Halp please?

Thanks!

---

### Post by Quackers on 2010-10-17
It may sound strange but reboot and then select the Windows recovery option and hit enter. It may just be labelled wrongly. If it actually starts the recovery environment just exit and reboot into Ubuntu.

---

### Post by Ningamer on 2010-10-17
Wow, that's really weird. Well, it seems to be working now, thanks a lot! :D

---

### Post by Quackers on 2010-10-17
My Windows entries are the wrong way round in grub too.
I'm surprised you didn't have 2 entries though (Windows Recovery (loader) and Windows Vista (loader)).
But so long as it boots Vista it doesn't matter :-)

---

### Post by wilee-nilee on 2010-10-17
If you run the bootscript in my signature you will probably find that the recovery partition is the booting partition, hence the name.

---

### Post by Quackers on 2010-10-17
It doesn't seem to be that way in mine
```
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   170,846,207   167,772,160   7 HPFS/NTFS
/dev/sda3         170,846,208   488,388,607   317,542,400   f W95 Ext d (LBA)
Empty Partition
```

It isn't really important, but I would like to understand it.

---


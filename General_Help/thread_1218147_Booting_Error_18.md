---
title: "Booting Error 18 ?"
date: 2009-07-20
forum: General Help
---

### Post by JannuBl22t on 2009-07-20
Well.. Hey there!

Today I received my copy of Unbuntu 9.04. I installed it.. but um I get some kind of Error 18 when I try to boot it.. I'm a Windows person so I don't know anything about Unbuntu or Linux things :D 
Please help me ^^

Regards,
Jaan

---

### Post by prshah on 2009-07-20
> **JannuBl22t said:**
> I get some kind of Error 18 when I try to boot 


The [GRUB Wiki at linuxquestions]("http://wiki.linuxquestions.org/wiki/GRUB#Error_18") will give you lots of details on why this occurs and how to fix it.

Essentially, you have probably created your Linux partitions at the very end of your hard disk. You need to create them nearer to the beginning (this is a very very very simplified explanation). To confirm this, boot off the Ubuntu (live) CD, and open the terminal (Applications-Accessories-Terminal) and post back the output of the following commands```
sudo fdisk -l
``` (That's a small "L", not the numeral "1").

Read above link, and post back if you have more questions.

---

### Post by JannuBl22t on 2009-07-20
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x37883dd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           3      117844    59392000    7  HPFS/NTFS
/dev/sda2          121907      614984   248510808    7  HPFS/NTFS
/dev/sda3          614985      620181     2619288    5  Extended
/dev/sda5          614985      619830     2442352+  83  Linux
/dev/sda6          619831      620181      176872+  82  Linux swap / Solaris
```

Well.. this is it..

---


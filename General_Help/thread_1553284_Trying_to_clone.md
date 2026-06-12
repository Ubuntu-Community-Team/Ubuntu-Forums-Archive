---
title: "Trying to clone"
date: 2010-08-14
forum: General Help
---

### Post by MooPi on 2010-08-14
I'm using dd to clone a Windows Vista hard drive and recovery partition with zero luck. I duplicated the partitions with gparted then used dd to copy each partition and then the master boot record. Nothing............. no boot.
```
dd if=/dev/sdb1 of=/dev/sda1
``````
dd if=/dev/sdb2 of=/dev/sda2
``````
dd if=/dev/sdb of=/sda bs=512 count=1
```

---

### Post by brokenromeo on 2010-08-14
Use clonezilla to do this...you can boot to the clonezilla disk and create an image of your hardrive to an external usb drive...

---

### Post by ahallubuntu on 2010-08-14
> **MooPi said:**
> I'm using dd to clone a Windows Vista hard drive and recovery partition with zero luck. I duplicated the partitions with gparted then used dd to copy each partition and then the master boot record. Nothing............. no boot.
```
dd if=/dev/sdb1 of=/dev/sda1
``````
dd if=/dev/sdb2 of=/dev/sda2
``````
dd if=/dev/sdb of=/sda bs=512 count=1
```

If either of your drives is a WD or Seagate drive, you might try using their free disk utilities, downloadable from the respective websites.  WD and perhaps Seagate include a free stripped-down version of Acronis True Image, which you may be able to boot off of a CD.  (I have a licensed Windows version and I still wind up booting the rescue CD, which is a highly functional version of True Image.)  True Image definitely handles Linux partitions - or ext3 at least, not sure about others.

---

### Post by C.S.Cameron on 2010-08-15
If you are trying to clone the entire bootable disk sda to sdb try ```
dd if=/dev/sda of=/dev/sdb
```
sdb needs to be larger than sda though.

---


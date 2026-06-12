---
title: "pendrive kingston 8 gb"
date: 2010-06-17
forum: General Help
---

### Post by croccio on 2010-06-17
bro i do a mistake with gparted and now windows and ubuntu don't show my pen! and g parted donesn't recognize my pen! how can i do???

---

### Post by croccio on 2010-06-17
ubuntu doesn't recognize my pen, windows says that a pen connect to the computer doesn't work propely =( please =(

---

### Post by wilee-nilee on 2010-06-17
You might need a partition bootable cd this is one that I use when gparted on the live cd or in Ubuntu doesn't work.
[http://partedmagic.com/download.html](http://partedmagic.com/download.html)
Can you describe the mistake you made, and have you tried rebooting the computer, with the thumb plugged in and not plugged in.

Partedmagic uses gparted but some times a bootable specialized cd is what is needed.

There is also this one which is a ntfs live cd.
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

There is also the gparted live bootable cd.
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Can you right click and format the thumb in windows, this will wipe it do you have stuff on it your trying to save?

---

### Post by croccio on 2010-06-17
parted magic dosn't recognize my pen and in windows it show me that message but it dowsn't show me

---

### Post by croccio on 2010-06-17
i war crating 4 partition on my pen then my computer rebboot and the pen is KO

---

### Post by croccio on 2010-06-17
ubuntu doesn't recognize my pen if i do sudo fdisk -l i've this:
```
Disco /dev/sda: 251.0 GB, 251000193024 byte
240 testine, 63 settori/tracce, 32422 cilindri
Unità = cilindri di 15120 * 512 = 7741440 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x00040004

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4063    30716248+   7  HPFS/NTFS
/dev/sda2            4064       32421   214386480    f  W95 Esteso (LBA)
/dev/sda5            4064       32421   214386448+   7  HPFS/NTFS

Disco /dev/sdb: 203.9 GB, 203928109056 byte
255 testine, 63 settori/tracce, 24792 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x00028e20

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7649    61440561   83  Linux
/dev/sdb2           24517       24793     2222081    5  Esteso
/dev/sdb3            7650       24516   135484177+   7  HPFS/NTFS
/dev/sdb5           24517       24793     2222080   82  Linux swap / Solaris

Le voci nella tabella delle partizioni non sono nello stesso ordine del disco

```

---

### Post by croccio on 2010-06-17
windows doesn't show me it

---

### Post by wilee-nilee on 2010-06-17
It looks like fdisk sees it so if it was me I would wipe the thumb from the command line I just don't know the command though. It may not be the thumb though it might be that something happened in the shutdown. Take the thumb to another computer and see if you get the same results. 

Your answers don't give enough information so it is difficult to see whats really going on. If this is a language barrier then use a translator on the web to get a more inclusive description posted if that helps.

---

### Post by croccio on 2010-06-18
> **wilee-nilee said:**
> It looks like fdisk sees it so if it was me I would wipe the thumb from the command line I just don't know the command though. It may not be the thumb though it might be that something happened in the shutdown. Take the thumb to another computer and see if you get the same results. 

Your answers don't give enough information so it is difficult to see whats really going on. If this is a language barrier then use a translator on the web to get a more inclusive description posted if that helps.

i made 4 partition on mz pen so: personal - 3zears - 4zears - other  so i applz this change. then gparted give me error. and mz monitor crash! so i reboot mz pc and at start up in gparted there isnßt mz pen! i trz knoppix and it doesnßt recogniye it =(

---

### Post by warfacegod on 2010-06-18
[http://www.freetranslation.com/]("http://www.freetranslation.com/")

---

### Post by croccio on 2010-06-19
i was creating 4 divisions on the pen usb. then my monitor went in crash, I have open another discussion for this argument, and I have rEBOOT the computer. then gparted pointed out the pen, however with gparted I did not succeed to create the divisions, so I detached it and then I reattached it and does not find it

---

### Post by croccio on 2010-06-20
up

---

### Post by warfacegod on 2010-06-20
See if Palimpset can see it. System> Admin.> Disk Utility

If so, mount it then open Gparted again.

---

### Post by croccio on 2010-06-20
it doesn't see my pen i can't mount it

---

### Post by warfacegod on 2010-06-20
Does the computer see other pen drives?

---

### Post by croccio on 2010-06-20
yes it does

---

### Post by warfacegod on 2010-06-20
Sounds like you broke the drive.

---

### Post by croccio on 2010-06-20
is there any way to program it?

---

### Post by warfacegod on 2010-06-20
Try plugging it into other computers. If you can get one to recognize it, reformat it.

---


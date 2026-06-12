---
title: "Problem Installing Sata Card on Ubuntu 10.04"
date: 2010-05-02
forum: General Help
---

### Post by joelandsonja on 2010-05-02
I purchased a new Sata Card today so I can install multiple harddrives on my system, but it appears as though I am missing the drivers for the card, because it is simply not recognizing it. 

Does anyone know how to obtain drivers for these cards and install them?

Please keep in mind that I am a Newbie when it comes to Ubuntu jargon, so I would appreciate it if someone could walk through the process with me. 

Thanks!

Edit - Just in case you were wondering, the Sata Card is Generic, and I have no idea who the manufacturer is. It literally says 'Sata Card' on the box and has no company information, but I did buy it at a reputable business, so I have no doubt that it should work fine. It is most likely this card: [http://www.newegg.com/product/product.aspx?Item=N82E16815124020](http://www.newegg.com/product/product.aspx?Item=N82E16815124020)

---

### Post by joelandsonja on 2010-05-03
Any thoughts from the Graveyard shift?

---

### Post by joelandsonja on 2010-05-03
[B]Sigh ...

Alright, I'll try to give a bit more info on the subject.

I typed in 'sudo fdisk -l' and this is what happened:[/B]

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c04f8
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38162   306531328   83  Linux
/dev/sda2           38162       38914     6037505    5  Extended
/dev/sda5           38162       38914     6037504   82  Linux swap /  Solaris
 
Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc01c0062
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      182401  1465136001    7  HPFS/NTFS
 
Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
1 heads, 63 sectors/track, 46512336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0460b790
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           2    46512256  1465136032+   7  HPFS/NTFS
 
Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x602f93f8
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001    7  HPFS/NTFS
 
Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7f90dba9
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30401   244196001    7  HPFS/NTFS
 
 [B]Any thoughts folks? 

I really need some help on this one.
[/B]

---


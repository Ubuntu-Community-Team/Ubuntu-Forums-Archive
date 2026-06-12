---
title: "Help 4 GB Pendrive bcame 750MB after trying to install ubuntu to pendrive"
date: 2010-03-19
forum: General Help
---

### Post by ranjithnair on 2010-03-19
**I did the below steps to install ubuntu to pendrive and now the pendrive is just 750MB...How can i bring back it to its previous state**

sudo fdisk /dev/sdb

This will give you the fdisk prompt. Look to what you have on the drive. Check if you have to backup the data you have on it. 'p' will print the content of /dev/sdb. If you have partitions on it remove them ('d', 'partition number').

Make partition 1:

1. 'n' for new partition

2. 'p' to make it a primary partition

3. '1' to call it partition number 1

4. Then just press enter to accept the proposed starting cylinder

5. '+750M' to make its size 750 MB

6. Then 'a' to make it the active partition

Set the file system of partition 1 to FAT:

1. 't'

2. then '1'

3. then '6'


Make partition 2:

1. 'n' for new partition

2. 'p' to make it a primary partition

3. '2' to call it partition 2

4. then just press enter to accept the proposed starting cylinder

5. then press enter to accept the proposed ending cylinder

6. Save and quit fdisk with 'w' to write the new settings.

---

### Post by Psumi on 2010-03-19
So you expected Ubuntu to take up less than 1 GB? :|

---

### Post by DawieS on 2010-03-20
Install **gparted** with **Synaptic Package Manager** (if you don't have it already). Now use **gparted** to delete partitions and format the pendrive. This will bring it back to the "new" condition (also remove any labels eg. boot, LBA).

If you want to install Ubuntu on the pendrive, rather use **System - Administration - USB Startup Disk Creator**.
:grin:

---

### Post by darolu on 2010-03-20
With the instructions you followed, your pendrive has 2 partitions,one with 750MB (step 5. '+750M' to make its size 750 MB) and the other one should be ~3,2GB.

You didn't specify what file system you chose; you have to set a file system to your second partition in order to use it (repeat the "t" step); remember that FAT16 supports file volumes up to 2GB only, FAT32 is what you may want to choose (as it is compatible with most OS's).

The easiest way to "fix it" or repartition it, is via Gparted as DawieS told you, just remember, choose FAT32, you can format with Ext2/3/4 if you like also, but keep in mind that Windows won't be able to read it.

---


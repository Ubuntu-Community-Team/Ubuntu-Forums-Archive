---
title: "usb device wont format"
date: 2010-12-25
forum: General Help
---

### Post by Supersonicmonk on 2010-12-25
I tried to make a startup disk using an 8gb usb drive and set 4gb of space to save documents however it looked like the installation froze so I cancelled it and deleted the partition in the disk utility however now it shows up as unknown in ubuntu and RAW in vista. I only got it today so it would be nice if I could fix it

---

### Post by tango_ninja on 2010-12-25
Have you tried using paritition manager to view the unallocated space? 

Just stick the drive in the port and open the program via Applications > System Tools > Gnome Partition Manager.  

You can create/remove/modify partitions from here.

---

### Post by C.S.Cameron on 2010-12-25
Never try to format a flash drive with multiple partitions in windows.
In Ubuntu right click and select Format.
Or use gparted.

Format it FAT32 if you plan in using it in Windows..

---

### Post by efflandt on 2010-12-26
If you deleted the partition, there is nothing to format.  You need to create a partition to format.  Or if you accidentally formatted the entire drive (like /dev/sdb) instead of a partition (like /dev/sdb1), you may need to create an msdos partition table first before you can make a partition (which should be FAT32 for Startup Disk Creator).  But your device may be some other device if you have a second hard drive and/or built-in multi-memory card reader.

I would use gparted (which you may need to install) because I do not fully understand the default Disk Utility.  Once when I "thought" I was marking a partition as a boot partition with Disk Utility, it started churning my drive endlessly and I do not know what it was trying to do.  Fortunately it did not damage anything when I stopped it.

---


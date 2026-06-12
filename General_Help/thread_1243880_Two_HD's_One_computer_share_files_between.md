---
title: "Two HD's One computer share files between?"
date: 2009-08-18
forum: General Help
---

### Post by RCRedneck on 2009-08-18
Got two HD's on this box. 9.04 and windows XP. Anyway to share files between the two HD's? IE: I'm booted into 9.04 and I download some MP3's. Want to copy these to the XP drive too.....

Gracias Amigos....

---

### Post by BDNiner on 2009-08-18
You would have to create a FAT32 partition on one of the drives. It would be easiest in ubuntu because you can use gparted to resize the windows partition and use the extra space to create the FAT32 partition. 

If you wanted to use the ubuntu disk for the extra partition then you would need a live CD and resize the partition using gparted.

---

### Post by Wiebelhaus on 2009-08-18
Mount the ntfs drive my simply clicking on it , provide permissions and then copy to the location you want to.

---


---
title: "WD 2TB harddisk"
date: 2010-11-10
forum: General Help
---

### Post by RastaManPower on 2010-11-10
i just bought a wd 2tb hdd for my media files and documents, what format should it be? ntfs or ext 4?

---

### Post by cipherboy_loc on 2010-11-10
If you want to use it only on GNU/Linux, use ext4. If you want to use it on Windows, use NTFS. You will have to format it as fat32 from GNU/Linux if you want to use it on both. The reason being, Windows cannot format drives greater than 4GB to Fat32 (Vfat). 


Cipherboy

---

### Post by srs5694 on 2010-11-10
FAT32 is often a poor choice, since it can't support files bigger than 4 MiB. I therefore recommend it only if you're sure you won't want to store such big files on it. (Video files and system backup files can easily exceed this size.) The NTFS-3g drivers give Linux pretty good NTFS read/write support, so that can be a good choice for cross-platform support. There are also ext3fs (but not ext4fs) drivers for Windows, although I know less about how well they work. (I've seen conflicting reports on this score.)

---

### Post by RastaManPower on 2010-11-11
i will make it ext4. if i will need to use any of the files on windows i will just move them into a ntfs pendrive and boot in win.thanx

---


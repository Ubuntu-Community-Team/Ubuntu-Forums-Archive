---
title: "File system for dual OS use"
date: 2006-05-18
forum: General Help
---

### Post by Calle on 2006-05-18
Which file system is the best to use on a 250 GB HD when I want to be able to read & write from both Linux and Windoze XP? 
I have tried FAT32 earlier, but after converting the partition (originally NTFS) the disk wouldn't keep all of my files, and it made me wonder if FAT32 is taking up more "space" than NTFS, is this right?

---

### Post by frodon on 2006-05-18
The only FS which offers write/read support for both OS is FAT32 but it has some disadvantages, it doen't support unix rights and it doen't support files > 4Go.
The the best solution is to know which OS you will use the most, if you know that you can choose a better way than all in FAT32.

---

### Post by cadr on 2006-05-18
I think so, yes. FAT32 isn't a very efficient filesystem. It is possible (and actually quite easy) to get read/write access to an NTFS partition from Ubuntu, but you have to install ntfsmount, which uses the FUSE userspace filesystem module for Linux. Write access is safe, but it's not technically complete yet, apparently (you might occasionally get situations where you won't be able to write to the partition). IIRC, there is also experimental NTFS write support directly in the kernel, but you would have to recompile to get that, and I think it's still experimental (and quite dangerous).

---

### Post by cadr on 2006-05-18
Oh, and see [http://wiki.linux-ntfs.org.nyud.net:8080/doku.php?id=ntfsmount?coral-no-redirect]("http://wiki.linux-ntfs.org.nyud.net:8080/doku.php?id=ntfsmount?coral-no-redirect") for some useful info on ntfsmount.

---

### Post by Harleen on 2006-05-18
Instead of writing to NTFS from Linux I'd prefer the other way round. Install a file system driver for ext2 on windows and to read and write your Linux partition. In contrast to NTFS the ext2 file system is well documented and the file system driver can be considered as stable.
You can get such a driver here: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---


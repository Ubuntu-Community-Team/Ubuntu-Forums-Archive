---
title: "How do you repair drivers in Ubuntu 10.04"
date: 2010-05-23
forum: General Help
---

### Post by alexpwnsn00b2 on 2010-05-23
Hi everyone I was messing around with USB SDmini  and decided I wanted to rename them. I installed Gparted and everything seemed fine I was able to rename them, but when I took one out to rename a different one Ubuntu no longer recognized the SD mini. Thinking it might be a bad SD mini I inserted the SD mini i had just renamed, but that didnt show up either. Regular USB drives work fine its just the SD card slot that is messing up. [U]Is there a way to repair drivers in Ubuntu 10.04?

[/U]P.S. I love Ubuntu :)

---

### Post by alexpwnsn00b2 on 2010-05-28
I used the sudo fdisk -l command and it seems that Ubuntu does not recognize my SD micro. Here is what I got after running the command

 Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x493a622b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10485760   27  Unknown
/dev/sda2   *        1306       29915   229805056   83  Linux
/dev/sda3           29915       30402     3906560   82  Linux swap / Solaris

---

### Post by wilee-nilee on 2010-05-28
You might try another partition tool like this one to get the device setup correctly. This uses gparted, but I have found it to recognize setups that even gparted on a live cd wont see.
[http://partedmagic.com/](http://partedmagic.com/)

There are a lot of different partition programs, here is a wiki on blanking the device if it can be recognized. I would look in the disc management and see if it shows there.
[https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

---


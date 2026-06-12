---
title: "how to install os with grub4dos or  just grub ..i dont know :)"
date: 2011-11-30
forum: General Help
---

### Post by Marko90 on 2011-11-30
hi, need some help with installing windows 7, 
i have ubuntu 11.10 installed on this laptop, but i need windows7 installed alongside, so i will not loos data from ubuntu. i tried to install windows but when i got to chose on which partition to install it, i could not see any of my partitions.
this problem exist probably because all partitions have been converted to linux partitions that cannot be seen by windows. so my question is how can i format them so i can install windows,
i ve also heard about program called grub4dos which i can use to install windows directly from hdd 
any advice is appreciated ..
thanks in advance

---

### Post by oldfred on 2011-11-30
Windows needs a primary NTFS formated partition with the boot flag. Or you have to have unallocated space and a free primary partition, but Windows has been known to not rewrite logical partitions correctly, so best to just create NTFS partition. Some have reported that a gparted NTFS partition does not always work, so you may have to use Windows to reformat again. Windows 7 normally installs to two partitions, a hidden 100MB boot/repair partition. But if you have created the partition in advance it will install to just one.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---


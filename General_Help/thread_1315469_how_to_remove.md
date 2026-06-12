---
title: "how to remove?"
date: 2009-11-05
forum: General Help
---

### Post by kasrawiz on 2009-11-05
i have just bought a laptop and now i want to keep it for ubuntu in my desktop computer i want to keep windows Xp now in desktop PC i have both ubuntu and XP installed now i want to remove Ubuntu from it and only keep XP how to remove ubuntu safely and get ubuntu drive as free space or fat32 partition in my xp i don't want my xp to be damage its bootloader 


thanks

---

### Post by wildweathel on 2009-11-05
[http://ubuntuforums.org/showthread.php?t=245959](http://ubuntuforums.org/showthread.php?t=245959)

---

### Post by alphaniner on 2009-11-05
On your desktop PC, you need to restore the Windows bootloader with a Windows install disc.  Then you can use Disk Management (Start -> Run -> diskmgmt.msc) in Windows to re-format the Ubuntu partitions for use by Windows.

---

### Post by praveenthivari on 2009-11-05
> **kasrawiz said:**
> i have just bought a laptop and now i want to keep it for ubuntu in my desktop computer i want to keep windows Xp now in desktop PC i have both ubuntu and XP installed now i want to remove Ubuntu from it and only keep XP how to remove ubuntu safely and get ubuntu drive as free space or fat32 partition in my xp i don't want my xp to be damage its bootloader 


thanks

Ah! with no punctuation in ur statements, I really find difficult to get the meaning. But If I am right, ur desktop has two OS and u want to remove ubuntu from that.

If that is wat u meant, just go [http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm) and download the free version. The user interface is clean and there would be no difficulty to u to delete the partition. Read it's manual if required.
Before this I think u would need to install the XP boot loader back. So download and install EasyBCD. Use it to install the boot loader.

I think that would be enough for u to delete the partition and format that back to FAT file system:D

---


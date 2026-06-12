---
title: "how to remove grub"
date: 2011-05-31
forum: General Help
---

### Post by aarsalankhalid on 2011-05-31
I had a dual boot of Ubuntu 11.04 with Windows XP SP3. I formatted the ext4 partition of Ubuntu. Now when I start my pc, it says "Unknown Filesystem" and then gives me a grub command line. How can I get rid of that and just continue using my Windows?

---

### Post by noah++ on 2011-05-31
Restore the MBR from Repair Mode on the Windows CD, or do [this]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/") from an Ubuntu CD.

---

### Post by oldfred on 2011-05-31
You still have the grub bootloader in the MBR of the drive. Since you deleted the rest of the grub code that is in the Ubuntu partition, grub will not boot.

You need to install a windows boot loader to the MBR. If your XP install works then, it will boot XP.

You need the fixMBR command:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by aarsalankhalid on 2011-05-31
Thnx for the help, guys!
I was able to get my old windows back by what OldFred suggested. I used the Windows installation CD to 'repair' boot files. Plain as that...now I can log into windows and everything is working alright :)

Thnx again

---


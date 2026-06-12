---
title: "Testdisk Not Restoring my reformatted Ext4 partition"
date: 2011-09-24
forum: General Help
---

### Post by Z3ro3X on 2011-09-24
I attempted to reformat a flash drive as Fat32 and inadvertently clicked the icon for my 500 GB hard drive.  "I wasn't paying attention"  It was taking a long time being that I thought I was formatting my 8 GB flash drive and noticed it said 500 GB.  Out of panic I clicked cancel.  I went into gparted and delete the corrupted fat32 file system that never finished formatting.  I tried to use testdisk to restore it.  The initial Quick Search shows it as FAT32.  I hit enter and do a Deeper Search.  It finds one labeled "Linux" so I hit Stop, highlight the partition labeled Linux and hit the right arrow key to change the D to * for Primary bootable and it turns green.  I hit Write .  When I'm all done it tells me to reboot.  So I do but when I log back in and run gparted it shows it as FAT32.  What's the deal?  I'm on Ubuntu 11.04.  Also, this is a spare hard drive I was using before buying a 1 TB drive that I now have Win 7 and Ubuntu with /home sitting on.  I started using the 500 GB to store random stuff I downloaded.  Half the drive is full and I don't remember everything I put on there.  I haven't written anything to that disc so the data is still there.  All I did was reformat it, though not completely.  I should be able to restore the original partition tables.

---


---
title: "getting rid of Windows"
date: 2010-03-22
forum: General Help
---

### Post by jmsgz on 2010-03-22
hi folks
can i get rid of the ntfs partition without messing up grub?
what does the flag "Boot" mean in the gparted window in the ntfs partition?
I see there is a grub directory in etc/boot/ ....is that where the boot loader is located or in ntfs partition? Justd trying to make sure before i get rid of the last remnants of M$ on my computer.

thanks in advance
:-)

---

### Post by blueridgedog on 2010-03-22
I would wager that the boot loader is in the MBR of the disk and the first partition can go.  If it were me, I would do a clean install with only two partitions, one for swap and one for / - in the long run it would be cleaner than having your OS reside on an extended partition.

Alternatively, there is no harm in keeping it around for dual booting.

---

### Post by 2hot6ft2 on 2010-03-22
Windows set the flag as boot. I agree with blueridgedog. A nice clean install setting the drive up the way you want it all in one fail swoop beats creating deleting and moving partitions around and will save you some headaches.

---

### Post by jmsgz on 2010-03-22
so, if i understand you guys just remove it all and reinstall desired os's?

thanks
:-)

---

### Post by 2hot6ft2 on 2010-03-22
> **jmsgz said:**
> so, if i understand you guys just remove it all and reinstall desired os's?

thanks
:-)
Pretty much. When running the installer just delete all the existing partitions and start from a blank disk then set up the partitions for the way you want it to all be. I mean you'll just have 2 or 3 partitions from the sound of things Ubuntu, swap, and maybe a storage partition. Or another OS since you said OS's just now.

Give some thought as to how you want it to be before hand then you wont need to make any more partition changes in the near future. A ubuntu install only takes a little while and compared to how long it takes to move or resize a partition you could same some time, effort and risk.

---


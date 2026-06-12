---
title: "Grub error: no such disk"
date: 2011-10-16
forum: General Help
---

### Post by sansa dude on 2011-10-16
Hi, 

I am having a problem with the boot on my PC. My setup has 3 separate hard drives, one with Ubuntu 11.10 (sda1), Windows 7 (sdb1), and Windows XP (sdc1). I can boot into ubuntu with no issue but I am having problems with both of the Windows drives.

When I run the grub-update command all of the drives are detected and added to the grub menu but the windows drives are not bootable and give me the  error: no such disk, error: no such partition.

All three drives will boot on their own when I change the boot order in the BIOS.

any suggestions? when I googled the problem I came up with something that had to do with "set root (hd0,0)" in the grub.cfg file.

could this have anything to do with the problem?

Thanks :)

---


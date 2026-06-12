---
title: "How the whole thing about MBR work"
date: 2010-10-17
forum: General Help
---

### Post by SkyerSK on 2010-10-17
Hello,
I spent last two days trying to figure out how exactly the "searching for operating systems" and MBR things work, and I don't think I clearly got it.

Please, correct me if something is wrong:
(grub related)
1. In the MBR sector, there is "the first link" for loading more complex boot loader, grub in my case.
2. Then, "the link" points to GRUB files (like menu, etc.) somewhere on the disk, some partition.
3. Grub loads

My question is:
1. Installation steps (grub legacy) "setup" and "root" are meant to install grub into MBR and some disk-partition? Does that mean I can install grub into MBR of first disk, and point it to another disk? (for sake of this post)
2. Sometimes, it happens, that after selecting another OS (with another GRUB), it own grub menu appears. Why does it happen? Does grub redirect itself and try to start operating system, while another grub interrupts it, and start itself?

Thanks.
And sorry for my English, I'm not speaking it nationally.

---


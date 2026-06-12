---
title: "Mounted windows 7 partition. Now windows 7 won't boot."
date: 2010-01-24
forum: General Help
---

### Post by afbase on 2010-01-24
Hello,

I'm using Karmic Koala 9.10 (amd64) on /dev/sdb6 and windows 7 on /dev/sda2.  I mounted my windows 7 partition in Nautilus.  I copied some files and made some folders from Nautilus onto my windows 7 partition.  I tried booting into windows 7 but it failed on loading Windows 7.  It then gave me a blue screen flashes and then restarted.  The blue screen flashes so quickly i cannot determine the exact issue.  I tried booting into windows 7 in Safe mode.  It fails to load and gives what i believe is the same blue screen.

  Would anyone know why this is?   I used to be able to read and write files onto my old XP and Vista partitions.  Now with windows 7,  I seems that I can't.

---

### Post by afbase on 2010-01-26
> **afbase said:**
> Hello,

I'm using Karmic Koala 9.10 (amd64) on /dev/sdb6 and windows 7 on /dev/sda2.  I mounted my windows 7 partition in Nautilus.  I copied some files and made some folders from Nautilus onto my windows 7 partition.  I tried booting into windows 7 but it failed on loading Windows 7.  It then gave me a blue screen flashes and then restarted.  The blue screen flashes so quickly i cannot determine the exact issue.  I tried booting into windows 7 in Safe mode.  It fails to load and gives what i believe is the same blue screen.

  Would anyone know why this is?   I used to be able to read and write files onto my old XP and Vista partitions.  Now with windows 7,  I seems that I can't.

I solved it.  I have an Alienware m17x.  After an exhaustive search, I realized Nvidia chipset/Sata drivers for 64-bit windows OS'es tend to have a some issues.  I reverted back to the old Microsoft drivers by booting into safe mode with Command Line > restart> then go into safe mode (regular) > Control Panel > Device Manager > IDE/ATA hard drives > NVidia SATA driver > right click > properties> driver tab > roll back driver.

---


---
title: "boot problem"
date: 2010-06-05
forum: General Help
---

### Post by bjx2 on 2010-06-05
I installed ubuntu 10.04 on my HDD and it made changes to win7 on another HDD, which wasn't what I wanted. I was able to fix the problem (rewriting MBR and track 0) because I had a backup of the win7 partition, but when I try to boot from the ubuntu HDD the system hangs (reeboot by ctrl alt del works). What I want is to be able to boot from eihter HDD using the BIOS based boot manager without interference with the other HDD. Obviously you should make some changes to the MBR and/or track 0 of the ubuntu HDD (ext4 (primary) and swap (logical) partitions + a NTFS logical partition) but since I am not familiar with linux I would be grateful for an explanation of the necessary procedure. The only way I can enter ubuntu now is through the 'try ubuntu without making any changes to your computer' interface on the live CD. Btw, is it possible to make the changes through this interface? In Acronis disk director (win program) the ext4 partition is marked as bootable.

regards
bb

---


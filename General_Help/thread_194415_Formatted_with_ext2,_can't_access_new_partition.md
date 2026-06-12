---
title: "Formatted with ext2, can't access new partition"
date: 2006-06-11
forum: General Help
---

### Post by Koori23 on 2006-06-11
6.06 Dapper OS. I formatted the logical drive via the "Disks" menu within the Administration dropdown menu. It's recognized path is /dev/hda5 and I can open it but I can't move or copy anything into it. It's probably a rights issue. 

My Ubuntu installation is /dev/hda3 and it's access path is / (This makes sense, it is the bootable drive.) Swap is /dev/hda7 and both of those are working properly. When I go to click "Enable" on hda5 partition, it does nothing. What do I need to modify to give myself read/write access so I can move stuff to it?

I am very ignorant when it comes to Linux partitioning, Windows with FDISK, I'm fine with.. So, any help would be amazing. I've tried the Help Files as well as Google Searches, either I'm just confused and doing it wrong or I'm missing something..

---

### Post by gerbman on 2006-06-12
[QUOTE=Koori23]6.06 Dapper OS. I formatted the logical drive via the "Disks" menu within the Administration dropdown menu. It's recognized path is /dev/hda5 and I can open it but I can't move or copy anything into it. It's probably a rights issue. 

My Ubuntu installation is /dev/hda3 and it's access path is / (This makes sense, it is the bootable drive.) Swap is /dev/hda7 and both of those are working properly. When I go to click "Enable" on hda5 partition, it does nothing. What do I need to modify to give myself read/write access so I can move stuff to it?

I am very ignorant when it comes to Linux partitioning, Windows with FDISK, I'm fine with.. So, any help would be amazing. I've tried the Help Files as well as Google Searches, either I'm just confused and doing it wrong or I'm missing something..[/QUOTE]What does your /etc/fstab file look like?

---


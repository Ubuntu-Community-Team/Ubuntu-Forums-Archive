---
title: "ubuntu seems to have disappeared after W7 installation"
date: 2011-03-07
forum: General Help
---

### Post by soraxd on 2011-03-07
i have a 234GB ext4 partition for ubuntu. i have a 60 gb NTFS partition, i installed windows 7, when prompted as to where to install w7, i chose the 60gb partition. windows 7 installed fine. when i went to reset, i wasnt asked which os to boot, so i installed EasyBCD and "added new entry" selecting the defaults 
Type: GRUB (Legacy)
Name: NeoSmart Linux
Device: Partition 1 (Linux - 234 Gib)
and did not check "[ ] GRUB isnt installed to MBR/bootsector"

when i restart im offered windows 7, or neosmart linux, i select neosmart linux, and it just sits there with a black screen and a curser.. the partition is still there, when i view my computer in windows it only shows 60 gb available, because it cant read the 234 ext4.. how do i get my ubuntu back?

---

### Post by TeoBigusGeekus on 2011-03-07
Try to reinstall grub2 using [this]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html") guide.

---

### Post by soraxd on 2011-03-07
will this erase my ubuntu? all my install programs and settings?

---

### Post by FoxEWolf on 2011-03-07
This may have been caused because you set that partition to be a primary boot partition.

reinstall grub2 with the guide that TeoBigusGeekus posted previously.

as to what will happen to your current settings in ubuntu, I couldn't tell you because Ive never been in that situation.

---

### Post by Verbeck on 2011-03-07
> **soraxd said:**
> will this erase my ubuntu? all my install programs and settings?
no, it wont

---

### Post by YesWeCan on 2011-03-07
> **soraxd said:**
> i have a 234GB ext4 partition for ubuntu. i have a 60 gb NTFS partition, i installed windows 7, when prompted as to where to install w7, i chose the 60gb partition. windows 7 installed fine. when i went to reset, i wasnt asked which os to boot, so i installed EasyBCD and "added new entry" selecting the defaults 
Type: GRUB (Legacy)
Name: NeoSmart Linux
Device: Partition 1 (Linux - 234 Gib)
and did not check "[ ] GRUB isnt installed to MBR/bootsector"

when i restart im offered windows 7, or neosmart linux, i select neosmart linux, and it just sits there with a black screen and a curser.. the partition is still there, when i view my computer in windows it only shows 60 gb available, because it cant read the 234 ext4.. how do i get my ubuntu back?
The thing is that I think(?) you need Grub installed in the Ubuntu partition for EasyBCD to work (you probably had it installed to the MBR before). Best to update to Grub2 too.

---


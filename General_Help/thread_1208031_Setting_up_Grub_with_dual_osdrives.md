---
title: "Setting up Grub with dual os/drives"
date: 2009-07-08
forum: General Help
---

### Post by latteguy on 2009-07-08
I successfully loaded Ubuntu on sdb and have all my partitions on the same drive. On sdc, are my windows vista/7 installs. When using CD to install Ubuntu, I changed the default setting of Grub's location to sdb (mbr?) and change the bios to boot that drive first. When booting, I get the menu screen pops up and gives me bunch of Ubuntu choices and lastly, Windows Vista bootloader. Loading to Ubuntu is no problem but when I choose Vista, I get the error 22. Currently, to get into vista/widows 7, I have to change to the bios to boot sdc first. From searching, I think I'm supposed to edit the grub menu.lst to make this work, however, I'm not sure how to get there (finding the grub menu.lst, accessing it, etc) since I have been reading and using Ubuntu for 2 days. Can someone please point me in the right direction???Thanks!

---

### Post by Sub101 on 2009-07-08
Could you post your menu.lst please. Its in /boot/grub. Thanks

---


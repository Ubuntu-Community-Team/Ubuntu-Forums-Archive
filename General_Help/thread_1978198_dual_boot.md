---
title: "dual boot"
date: 2012-05-11
forum: General Help
---

### Post by Lechmy on 2012-05-11
Hi,i have dual boot Windows XP and Ubuntu 9.10(instaled from USB,newest was 11 but i had problem starting instalation) but now i cant start Ubuntu,i tryed it when it was instaled but when i restarted PC i couldnt start Ubuntu,i dont have option to select what OS i want to start at the BIOS start and i now dont have Ubuntu on my USB because i had to format it,if some one can help me,i looked on net and found some text about it but i couldnt do anything

---

### Post by wilee-nilee on 2012-05-11
9.10 is end of release and not supported basically, install 10.04.1.

You need to have a disc available or thumb, it will be about the best tool you can have.

---

### Post by SuaSwe on 2012-05-11
Hi Lechmy,

It's not clear from your post if you had ever used the Ubuntu install (e.g. it had been tested and worked, and contains data you wish to keep) or if it failed after the first attempt at installing. In either case you ideally need a LiveUSB or LiveCD to work with.

---

### Post by Lechmy on 2012-05-11
i'll try again with some other version all over again,but basicly SuaSwe i instaled Ubuntu,everything worked ok but i cant boot it,partition is taken so its there...i guess

---

### Post by Lechmy on 2012-05-11
i did some more digging and asked some friends that had Ubuntu before,i maybe have to enter some code in MBR but im stuck there, [https://help.ubuntu.com/community/WindowsDualBoot#Master_Boot_Record_and_Boot_Managerif](https://help.ubuntu.com/community/WindowsDualBoot#Master_Boot_Record_and_Boot_Managerif) Master Boot Record and Boot Manager part is probably where im stuck,if some one could help me with this.

---

### Post by oldfred on 2012-05-12
Ubuntu 9.10 was the first to use grub2. So follow the grub2 repair commands if you want to boot Ubuntu or the fixMBR if you just want to boot Windows.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---


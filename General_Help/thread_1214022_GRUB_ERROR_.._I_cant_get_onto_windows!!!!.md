---
title: "GRUB ERROR .. I cant get onto windows!!!!"
date: 2009-07-15
forum: General Help
---

### Post by bsta520 on 2009-07-15
i had dual boot ubuntu/vista...and i just deleted the partition that ubuntu was on to free up some space...and when i shut down the computer and turned it back on ... grub loads and says ERROR 22  and stays there....now i cant sign onto my vista... im not sure what to do can someone help me bypass grub please....thank you

---

### Post by cariboo on 2009-07-15
To repair the problem boot from you Vista install disk, and select the repair option. I you only have a restore disk, you may need to go [here ]("http:///neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and download and burn the correct iso for your version of Vista.

---

### Post by bsta520 on 2009-07-15
i did that and the only other option besides restoring the system is to restore from a restore point...but when i do that it just restarts the computer and GRUB still comes up...is there anyway to disable grub if i cant get onto an os. ?

---

### Post by philcamlin on 2009-07-15
did you try reinstalling grub?

---

### Post by b.a.w on 2009-07-15
By deleting the partition you probably deleted /boot where your grub files are at. The MBR tries to read these files and it is gone so you have this error. An easy way to do it if you don't want to do system recovery with vista install cd or you don't have one would be to reinstall ubuntu. After the reinstall, grub should work again and you can access vista. Search for EasyBCD. This configures Vistas bootloader and it allows you to reinstall it to the MBR. From here you can delete the Ubuntu partition from Vista. This has worked for me before. Good luck.

---


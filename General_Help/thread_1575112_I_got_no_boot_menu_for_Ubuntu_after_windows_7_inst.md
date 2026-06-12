---
title: "I got no boot menu for Ubuntu after windows 7 install"
date: 2010-09-15
forum: General Help
---

### Post by elidoperezmd on 2010-09-15
Hi all...

I double boot Ubuntu/Vista, yesterday i replaced vista with 7...and after installation was finished i dont get a boot screen as i used to...it just goes into windows 7 sraight...when i hit f12 to enter the boot menu, the only OS that is available is 7. In the windows 7 partition i only have the gbs assigned to that certain partition, meaning that the 100 and something assigned to ubuntu are somewhere out there....

did i explain myself? 

thanks for the help/time/replies

---

### Post by MooPi on 2010-09-15
When you installed Windows 7, it wrote over the Master Boot Record(MBR). You will need to reinstall grub to get the boot loader back. These two links offer help info to restore grub.
[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+sticky](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+sticky)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by elidoperezmd on 2010-09-15
> **MooPi said:**
> When you installed Windows 7, it wrote over the Master Boot Record(MBR). You will need to reinstall grub to get the boot loader back. These two links offer help info to restore grub.
[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+sticky](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+sticky)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Ill give a try right now, thanks

---


---
title: "Window 7 and Ubuntu"
date: 2011-04-16
forum: General Help
---

### Post by Silverdogz on 2011-04-16
Hi everyone,
I have a Windows 7 OS installed on a SATA drive, A few days ago I  installed Ubuntu 10.10 on an IDE drive. So far the only way is to switch  the HDD drives in BIOS to boot up the one I want. Can anyone help me  here.

---

### Post by Ad@m on 2011-04-16
I suggest you make the IDE Ubuntu drive the 1st boot device, then update your grub menu.

Running the command sudo update-grub should detect and add your Windows drive to the grub loader.

---


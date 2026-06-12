---
title: "Uninstalling Fedora16 and installing Ubuntu 11.10"
date: 2012-02-27
forum: General Help
---

### Post by ttsdinesh on 2012-02-27
My samsung notebook came with Windows 7 pre loaded. I installed Fedora 16 in that along with windows 7. Now I dont want Fedora and like to install Ubuntu 11.10. How can I uninstall/overwrite Fedora with out affecting Windows 7? As fedora is installed after windows I doubt it would have changed boot loader and it might cause trouble when ubuntu overwrites it. Pls help.

Thanks in advance.

---

### Post by nothingspecial on 2012-02-27
During the install process, when it asks how you want to install Ubuntu? choose the option "Something Else"

Make sure you choose the Fedora partition, give it a mountpoint of /, choose to format it and use it as an ext4 journaling file system.

Do not touch the windows partition. The installer will take care of grub (the bootloader).

---

### Post by ttsdinesh on 2012-02-27
> **nothingspecial said:**
> During the install process, when it asks how you want to install Ubuntu? choose the option "Something Else"

Make sure you choose the Fedora partition, give it a mountpoint of /, choose to format it and use it as an ext4 journaling file system.

Do not touch the windows partition. The installer will take care of grub (the bootloader).
Thanks.

---


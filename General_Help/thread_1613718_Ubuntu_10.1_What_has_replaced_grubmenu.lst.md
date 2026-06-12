---
title: "Ubuntu 10.1: What has replaced grub/menu.lst?"
date: 2010-11-04
forum: General Help
---

### Post by nsivin on 2010-11-04
I am using Ubuntu 10.10 (freshly installed, no Wubi) on a PC, dual-booting with WinXP. In the last couple of versions, I used the file /boot/grub/menu.lst for two important functions: One was to set the startup delay for the boot menu; the default is 10 seconds, but I find 1 second is enough. The second is to set the default OS. This file does not exist in v. 10.10. Where do I set those variables now?

---

### Post by nsivin on 2010-11-04
I am using Ubuntu 10.10 (freshly installed, no Wubi) on a PC, dual-booting with WinXP. In the last couple of versions, I used the file /boot/grub/menu.lst for two important functions: One was to set the startup delay for the boot menu; the default is 10 seconds, but I find 1 second is enough. The second is to set the default OS. This file does not exist in v. 10.10. Where do I set those variables now?

---

### Post by drs305 on 2010-11-04
Grub legacy has been replaced with Grub 2. The configuration file is /boot/grub/grub.cfg but you don't edit it directly. Rather you edit the scripts that create it.

Take a look at the links in my signature line. "G2 Basics" is the main introductory thread.  Setting the default: Use either StartUp-Manager or take a look at "G2-Tasks".

Note: I combined your posts.

---

### Post by pqwoerituytrueiwoq on 2010-11-04
and should you need to revert to the old grub
[https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy](https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy)

you may need to change root to uuid on the chan-load to grub 2 entry

---

### Post by nsivin on 2010-11-07
Thanks for the answers. I found the full instructions at
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---


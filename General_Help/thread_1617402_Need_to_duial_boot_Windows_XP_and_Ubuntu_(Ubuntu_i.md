---
title: "Need to duial boot Windows XP and Ubuntu (Ubuntu is already installed)"
date: 2010-11-09
forum: General Help
---

### Post by apoorvumang on 2010-11-09
I need to dual boot between Ubuntu 10.10 and Windows XP.
I have Ubuntu installed on my hard drive currently, and I want to install XP as well. However, I've heard that installing Windows removes GRUB and its not possible to boot Ubuntu. Is there any workaround? Thanks in advance.

---

### Post by oldfred on 2010-11-09
It is not difficult if you can install another operating system you can easily reinstall grub to the MBR.

Windows automatically installs its boot loader to the MBR. You just have to reinstall grub2 and after rebooting Ubuntu run sudo update-grub to find the windows install and you have dual boot.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
chroot version:
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

Older but discusses the issues, reinstall grub2, not other alternatives:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

You need to have a primary partition formated to NTFS with the boot flag. Then XP should install to that partition without issue.

---


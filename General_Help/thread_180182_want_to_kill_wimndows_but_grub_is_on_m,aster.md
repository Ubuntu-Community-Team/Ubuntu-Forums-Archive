---
title: "want to kill wimndows but grub is on m,aster"
date: 2006-05-21
forum: General Help
---

### Post by LORD_PoLvO on 2006-05-21
hey i want to be ab;le to change my machine from duel boot to just ubuntu but i dont want o have to go through alll i have been all over again is there a way to put grub of the master drive so i can safely formatt is without losing the ability to boot into ubuntu?

---

### Post by aysiu on 2006-05-21
If Grub isn't on the MBR, how are you dual-booting?

Did you somehow manage to get Ubuntu into Windows' boot.ini file?

Well, if you do want to restore Grub to the MBR, follow [these directions](http://ubuntuforums.org/showthread.php?t=24113). That won't delete Windows, though. You'd need to unmount Windows' partition and then delete it with GParted or QTParted.

---

### Post by ????? on 2006-05-21
He means that he wants to remove Windows from his computer and go back to single-boot with Ubuntu. (In other words, uninstall Windows and just use Ubuntu)

---

### Post by aysiu on 2006-05-21
[QUOTE=?????]He means that he wants to remove Windows from his computer and go back to single-boot with Ubuntu. (In other words, uninstall Windows and just use Ubuntu)[/QUOTE] I understand that, which is why I'm asking what Grub has to do with it.

If Grub is already on the MBR, you don't need to mess with Grub or reinstall it in order to remove Windows.

On the other hand, if (for some peculiar reason) Windows is in charge of the boot loader, then, yes, one would have to reinstall Grub to the MBR.

---

### Post by LORD_PoLvO on 2006-05-22
yes whenever i have formated the windows drive before i restart and it comes up with a grub bootloader error how are u supposed ti install grub gruab again after the format

---

### Post by aysiu on 2006-05-22
[QUOTE=LORD_PoLvO]yes whenever i have formated the windows drive before i restart and it comes up with a grub bootloader error how are u supposed ti install grub gruab again after the format[/QUOTE] [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---


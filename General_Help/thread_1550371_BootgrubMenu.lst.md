---
title: "/Boot/grub/Menu.lst"
date: 2010-08-11
forum: General Help
---

### Post by ajack38 on 2010-08-11
Hi, I am trying to dual-boot windows xp with Ubuntu Lucid Lynx (Ubuntu installed first) and I'm following a tutorial ([http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=2](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=2)) and it has said for me to back up /Boot/grub/Menu.lst but when I go to back it up using sudo gedit /boot/grub/menu.lst. in the terminal, it opens the file but when it opens fully but it doesn't show anything at all but in the tutorial it shows that there should be something there ([http://apcmag.com/images/apcapc/howto/Dualboot_-_XP___Ubuntu__Ubuntu_first__images/media_1208839938127.jpg](http://apcmag.com/images/apcapc/howto/Dualboot_-_XP___Ubuntu__Ubuntu_first__images/media_1208839938127.jpg)).

Does anyone know why it isn't there?

Thanks.

---

### Post by linux18 on 2010-08-11
its /boot/grub/grub.cfg now that we are in the grub 2 era.

---

### Post by wilee-nilee on 2010-08-11
Per the 2nd post run in the terminal
```
sudo grub-install -v
```

If it answers grub 1.97 or beyond use this link with a live cd to reinstall grub2. It is a wiki I have it defaulting to the live cd install portion.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---


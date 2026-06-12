---
title: "Can't get rid of boot menu and access BIOS"
date: 2011-04-30
forum: General Help
---

### Post by Xepter on 2011-04-30
Hi,
So I installed Ubuntu 8.04 with Wubi a while ago on my Toshiba Satellite A500/02j and recently uninstalled it (with Wubi). For whatever reason, Windows will not get rid of its bootloader and I cannot access my BIOS settings. I've tried spamming every function key that I have when it boots up but nothing happens (if I press ESCAPE when I'm at the boot menu it restarts). Any idea on how to get rid of it and get me my bios back?
Thanks,
Xepter

---

### Post by Rubi1200 on 2011-04-30
> In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi  line. For Vista, you can use EasyBCD to edit the boot menu.  Alternatively you can modify the boot menu via Control Panel > System  > Advanced > Startup and Recovery and pressing "Edit". For  Windows 98 you have to edit C:\config.sys and remove the Wubi block. [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

Hope this helps.

---


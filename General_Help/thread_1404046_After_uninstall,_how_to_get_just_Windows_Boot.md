---
title: "After uninstall, how to get just Windows Boot"
date: 2010-02-11
forum: General Help
---

### Post by donmor on 2010-02-11
Uninstalled Wubi version of Ubuntu 9.04 and at start up the boot still comes up with Ubuntu and Windows for 20 seconds then starts in Windows.
How do I get it back to just booting Windows as before?
Thanks
Don

---

### Post by bcbc on 2010-02-11
Depends on version of Windows:
In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line. For Vista, you can use EasyBCD to edit the boot menu. Alternatively you can modify the boot menu via Control Panel > System > Advanced > Startup and Recovery and pressing "Edit". For Windows 98 you have to edit C:\config.sys and remove the Wubi block.

See [https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?") for more info.

---

### Post by donmor on 2010-02-11
Many thanks.

Don

---


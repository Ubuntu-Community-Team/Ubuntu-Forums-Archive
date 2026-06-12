---
title: "America's Army"
date: 2010-01-11
forum: General Help
---

### Post by phoenixfire900 on 2010-01-11
Where can I install the latest version of America's Army for Ubuntu 9.10?

---

### Post by running_rabbit07 on 2010-01-11
[http://www.americasarmy.com/](http://www.americasarmy.com/) Their web site?

---

### Post by cascade9 on 2010-01-11
Americas Army dropped support for linux ages ago, your only chance is to play under *nix is via WINE...

---

### Post by hawthornso23 on 2010-01-11
> **cascade9 said:**
> Americas Army dropped support for linux ages ago, your only chance is to play under *nix is via WINE...

Possibly true of the latest version.  However the previous version is still supported and runs on linux just fine.  Be aware that it needs libstdc++.so.5 in /usr/lib32 . This 32 bit library was inexplicably dropped from 64 bit Karmic. To get it to run you'll need to manually install this library.

---

### Post by phoenixfire900 on 2010-01-11
what is the previous version, where can I download it and where can I find and install this library?

---

### Post by khelben1979 on 2010-01-11
[Try this one]("http://americasarmy.filefront.com/file/AASF_Direct_Action_v25_Linux_Full_Install;49654").

---

### Post by phoenixfire900 on 2010-01-11
after I install this how do I run it?

---

### Post by hawthornso23 on 2010-01-12
Look for armyops in the applications menu. It is integrated into the gnome desktop.

---

### Post by hwttdz on 2010-01-12
And my solution for installing libstdc++5 was to readd one of the jaunty sources that had it.

---


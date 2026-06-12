---
title: "wubi gone from uninstall options and upgrading from iso"
date: 2011-05-25
forum: General Help
---

### Post by Kronos454 on 2011-05-25
i want to upgrade to ubuntu 11.04 and i downloaded the iso but it didn't detect my previous installation of ubuntu 10.10
so i thought of going to programs and features and doing a complete  uninstall but ubuntu wasn't listed in there even though i installed  using WUBI in C drive
now what am i supposed to do?
delete all ubuntu files manually?

plz reply HURRIEDLY!!!!:confused::confused::frown::frown:

[http://ubuntuforums.org/attachment.php?attachmentid=193131&stc=1&thumb=1&d=1306335129](http://ubuntuforums.org/attachment.php?attachmentid=193131&stc=1&thumb=1&d=1306335129)

[http://ubuntuforums.org/attachment.php?attachmentid=193132&stc=1&thumb=1&d=1306335129](http://ubuntuforums.org/attachment.php?attachmentid=193132&stc=1&thumb=1&d=1306335129)

[http://ubuntuforums.org/attachment.php?attachmentid=193133&stc=1&thumb=1&d=1306335129](http://ubuntuforums.org/attachment.php?attachmentid=193133&stc=1&thumb=1&d=1306335129)

---

### Post by bcbc on 2011-05-25
See the Wubi guide for how to uninstall: [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

(Should be a program in the \ubuntu directory called something like uninstall-ubuntu.exe)

It's possible to upgrade, but not from Windows. And it takes much longer than reinstalling - so unless you want to preserve your existing install then not much point. Note that the upgrade can fail, so take backups of the root.disk (and C:\wubildr) beforehand if you want to be able to roll back to the state prior to upgrading.

---


---
title: "mouse and keyboard"
date: 2009-09-26
forum: General Help
---

### Post by rukqoa on 2009-09-26
This is not exactly a hardware problem.
Because of an issue with hal that would cause ubuntu to hang when it boots, I started messing around with update-rc.d 
now, it's broken. when i go into recovery mode and start dbus and hal manually and then resume boot, my keyboard and mouse work just fine. but, my mouse/keyboard does not work in normal boot.
i've tried reinstalling dbus and hal already, and it doesn't work.
any suggestions? thanks in advance.

---

### Post by jerrrys on 2009-09-28
go to **System->Administration->Services** and make sure that **System Communication Bus (dbus) **is checked

---


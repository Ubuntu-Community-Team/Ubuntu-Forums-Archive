---
title: "Gnome-Do Won't Appear above other windows"
date: 2010-01-09
forum: General Help
---

### Post by FatalChaos on 2010-01-09
I just installed gnome-do on Kubuntu because I could not get launchy to function, but I can't get gnome-do to consistently appear above other windows even after applying the workaround on the gnome-do wiki for kde users. Any ideas?

---

### Post by nortexoid on 2010-01-10
When I installed kubuntu-desktop in Ubuntu and then logged into the KDE desktop, gnome-do worked and take focus, but there was some visual corruption using Kwin as the window manager.

I'd recommend using krunner which functions pretty much as gnome-do but is better integrated with KDE (e.g. with nepomuk).

---

### Post by FatalChaos on 2010-01-10
I like krunner, but I can't get it to detect some applications, and I can't get krunner to open up folders and files like gnome do can, although in theory it should be able to open up folders like gnome-do.

---

### Post by FatalChaos on 2010-01-10
Figured out that setting "focus stealing prevention level" to none under System Settings -> Window Behavior -> Window behavior fixes these issues.

---


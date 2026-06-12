---
title: "Gnome menu edit doesn't work"
date: 2010-04-12
forum: General Help
---

### Post by deusdies on 2010-04-12
Hi,

For some reason, right click on gnome menu in the panel and clicking "edit menus" doesn't work (nothing happens).

Does anyone know a command in terminal that should bring the dialog up, so I can see if any errors take place?

Thanks!

---

### Post by wojox on 2010-04-12
What does System > Preferences > Main Menu yield?

---

### Post by kurp on 2010-04-12
Use command...
```
alacarte
```
...in terminal in order to open mentioned window.

---

### Post by deusdies on 2010-04-12
Thanks, I've found the problem - apparently, there's a bug in Python when using Serbian localization.

---


---
title: "lyx main menu doesn't show in global menu"
date: 2010-10-14
forum: General Help
---

### Post by jctots on 2010-10-14
hello,

i am using the global menu applet on ubuntu desktop edition. almost all of the apps shows its main menu on the global menu applet, but lyx doesn't. am i the only one experiencing this problem? i am using updated maverick.

thanks for the help

---

### Post by earlycj5 on 2010-11-22
You're not the only one.

I just discovered this too.

Anyone had any fixes?

---

### Post by evgeny12 on 2011-01-07
Good advices are in [http://askubuntu.com/questions/6784/is-it-possible-to-make-indicator-appmenu-ignore-a-specific-application](http://askubuntu.com/questions/6784/is-it-possible-to-make-indicator-appmenu-ignore-a-specific-application)
Unfortunately, for me not everything works (Ubuntu 10.10 lyx menu problem), but you may try it. I found solution there in comment.

Right click on Main Menu -> Edit Menus->Lyx properties
There it is written: lyx %F
I added text to make it as: env QT_X11_NO_NATIVE_MENUBAR=1 lyx %F
For users of Avant window manager: don't forget delete lyx and then add again
fixed lyx launcher (drag and drop).

---


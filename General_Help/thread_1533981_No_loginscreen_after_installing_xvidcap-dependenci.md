---
title: "No loginscreen after installing xvidcap-dependencies"
date: 2010-07-18
forum: General Help
---

### Post by funsseelen on 2010-07-18
Hello,
 
In order to install "xvidcap" I had to install a couple of dependencies first. But while installing cairo, gtk+-2.0 and atk a.o. something went wrong. I guess it was after atk-1.28 (which wasn't even satisfiable) unpacking *tar.gz-files didn't work anymore with archive manager, nor with "tar -x *tar.gz". It even crashed my terminal. After rebooting the login screen didn't show up anymore. It shows my background though and I can hear the ubuntu-login-screen-sound.
 
What I did after:
 
- rebooting with <shift> to select kernel (recovery)
- <ctl><alt><F1> brought me to the command line to:
- update and upgrade.
 
It still doesn't work. Does anyone know what the problem is and how to fix it?
 
For example typing
$ gedit
outputs:
(gedit:4244): Gtk-WARNING **: cannot open display:
 
Thank you for reading!
 
Funs
(ubuntu 10.04)

---

### Post by funsseelen on 2010-07-18
This is what I get after the damage was done
 
```
 
$ pkg-config --modversion glib-2.0
2.24.1
$ pkg-config --modversion pango
1.28.1
$ pkg-config --modversion cairo
1.8.10
$ pkg-config --modversion gtk+-2.0
2.20.1
$ pkg-config --modversion atk
1.28.0

```

---


---
title: "¿Where are my programs?"
date: 2009-11-15
forum: General Help
---

### Post by astaroth_j on 2009-11-15
Hello, I'm new in Linux-Xubuntu and I need help with my programs. I just installed Mercury Messenger distribution for Ubuntu.Devian but I can't found where the program was installed. Help!

And apologizes for my bad English xD

---

### Post by Brandon Williams on 2009-11-15
After installing a deb package to your system, you can find out what files were installed by running 'dpkg -L <packagename>' in a terminal. For example:
```
dpkg -L mercury-messenger
```

Typically, the executable program to run will be installed in /usr/bin/. In this case, it is /usr/bin/mercury, so you can run 'mercury' at the command prompt or with the Alt+F2 run dialog.

You will have to make sure that you have also installed sun-java6-jre on your system, since the mercury-messenger deb does not correctly specify this dependency.

---

### Post by MaxIBoy on 2009-11-15
[s]Also, once you have found a command that works to launch murcury, you can add it to the menu. Right click on the menus, click "edit menus," find the right place where you want to add it, and click "New Item." Give it a name and the right command.[/s]

Ignore what I said, that's for Ubuntu not Xubuntu. Sorry. To add to menus in Xubuntu, do this: [http://www.xfce.org/documentation/4.2/manuals/xfdesktop#xfdesktop-menu](http://www.xfce.org/documentation/4.2/manuals/xfdesktop#xfdesktop-menu)

---

### Post by ctult on 2009-11-15
Log out and then log back in. It works for me. :)

---

### Post by Brandon Williams on 2009-11-15
> **MaxIBoy said:**
> Ignore what I said, that's for Ubuntu not Xubuntu. Sorry. To add to menus in Xubuntu, do this: [http://www.xfce.org/documentation/4.2/manuals/xfdesktop#xfdesktop-menu](http://www.xfce.org/documentation/4.2/manuals/xfdesktop#xfdesktop-menu)

Since the switch to XDG menus, xfce no longer has a graphical menu editor. To edit menus in Xubuntu, you have to create the necessary files individually.

---

### Post by MaxIBoy on 2009-11-15
> **Brandon Williams said:**
> Since the switch to XDG menus, xfce no longer has a graphical menu editor. To edit menus in Xubuntu, you have to create the necessary files individually.So alacarte should work then (same as in Gnome?)

```
sudo apt-get install alacarte
alacarte
```

---

### Post by Brandon Williams on 2009-11-16
Nope. You might be able to make new menu entries with it (I'm not sure sure), but alacarte doesn't work to edit the menu structure (adding and reorganizing submenus). This is because alacarte won't let you work on an arbitrary .menu file. It assumes you're using applications.menu and system.menu. Also, alacarte uses some merging functionality that XFCE doesn't yet support.

---


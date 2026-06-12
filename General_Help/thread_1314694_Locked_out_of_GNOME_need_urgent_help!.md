---
title: "Locked out of GNOME need urgent help!"
date: 2009-11-04
forum: General Help
---

### Post by redscorpion69 on 2009-11-04
I was trying to turn of ports/services in system/administration/services and i managed to turn off a service which threw me out of gnome, and now i just log in to cli. Does anyone know what service i managed to kill and how do i turn it back on from cli?

THANK YOU

---

### Post by fooman on 2009-11-04
what version of ubuntu are you using?

after logging in cli...have you tried typing:

```
startx
```

then pressing enter?  ...post back with any errors you see.

if that does not work,  when booting up....at the grub menu,  try recovery mode.  once there...try the "xfix" option if it is there.  when that completes, continue with normal boot....see if that works.

---

### Post by BQAggie2006 on 2009-11-04
You may have deactivated what is listed in the Services menu as the Graphical Login Manager, which is GDM or the Gnome Display Manager. All you have to do is login on the command line, run the command:

```
sudo /etc/init.d/gdm start
```Then go back and re-enable the service.

---

### Post by redscorpion69 on 2009-11-04
startx wouldn't work, that's why i posted,
but sudo /etc/init.d/gdm start did!

thanks alot everyone

---


---
title: "how to change default desktop ?"
date: 2010-10-27
forum: General Help
---

### Post by freeaks on 2010-10-27
hi there,
i would like to know how i can change my default destop environement..
i don't use gdm at all, i don't want to. i prefer startx (i boot into terminal mode)
also, i would like a global setting. not ~/.xinitrc 

for example in fedora the default desktop is setup in this file: /etc/sysconfig/desktop
so i can change the default desktop for all users just by modifying this file.
how can this be done in ubuntu ?

thanks

---

### Post by pqwoerituytrueiwoq on 2010-10-27
i have not tryed this but this may be what you want
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by aeiah on 2010-10-27
have you tried messing with /etc/X11/xinit/xinitrc ? i believe it's the global .xinitrc file. i dont know a great deal about it though tbh

---

### Post by freeaks on 2010-10-29
> **pqwoerituytrueiwoq said:**
> i have not tryed this but this may be what you want
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)


that's exactly what i said i *do not want*
i don't use no display manager at all. no xdm, gdm, kdm ..


rather, i would like to find out where the default desktop to run from startx command is setup. in what file ? (global setting file.. not per user.)

i would like to be able to switch at will between all my installed desktop environment and window manager ..globally. for all users.
i use fvwm, amiwm, lxde, gnome and kde. i need to find where i can change which one is about to run when i use startx command.

tnx

---

### Post by freeaks on 2010-11-01
*bump*

so what are my options ?
~/.xinitrc or gdm are the only way on ubuntu ?

---

### Post by HiImTye on 2010-11-01
/etc/X11/xinit/ has both xinitrc and xserverrc

man page for startx
[http://www.manpagez.com/man/1/startx/](http://www.manpagez.com/man/1/startx/)

edit: just replace the xinit directory with the one above

---


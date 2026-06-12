---
title: "Where are new application installed"
date: 2006-03-05
forum: General Help
---

### Post by wpshooter on 2006-03-05
I attempted to install a 3d chess game BUT where does it put this application.  I have looked on about every menu on the desktop and I do NOT see it.

Thanks.

---

### Post by CallsignBaron on 2006-03-05
Sometimes depending on how you install a program it doesn't get installed into the applications menu. When this happens, see if you can start the application with it's command from a shell. (for example, the command for Epiphany, the Gnome web browser, is simply "epiphany") If you can run the program from the terminal then you will have to create an entry in the Applications menu yourself for the program simply by right clicking the menu and selecting "Edit Menus".
Hope this helps! :)

---

### Post by wpshooter on 2006-03-05
When I type in 3dchess at the terminal nothing happens.

Do I have to be the admin/root user to do this ?

Also when I right click on the games menu, I don't see an edit menus selection.

Thanks.

---

### Post by halfvolle melk on 2006-03-05
It's probably in /usr/share.

Try:
```
locate chess
```
in a terminal. Maybe it pops up.

edit: it's called 3Dc and it's in "/usr/games".

---


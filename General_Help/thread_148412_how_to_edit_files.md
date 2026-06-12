---
title: "how to edit files"
date: 2006-03-22
forum: General Help
---

### Post by vigorsky on 2006-03-22
i have installed kubuntu and normaly i use the file manager in the root modus to edit an file. I have an installed an application and wil edited the configuration file but i cant find an filemanager konqueror shows me no way to start in root or sudo modus how can i edit an file and save this file i have no write rights.

---

### Post by MrDan on 2006-03-22
[QUOTE=vigorsky]i have installed kubuntu and normaly i use the file manager in the root modus to edit an file. I have an installed an application and wil edited the configuration file but i cant find an filemanager konqueror shows me no way to start in root or sudo modus how can i edit an file and save this file i have no write rights.[/QUOTE]


sudo gedit /path/filename

---

### Post by eriefisher on 2006-03-22
I think in (k)ubuntu it's: sudo kwrite(or kate) /path/file name

eriefisher

---

### Post by Jucato on 2006-03-22
more correctly, it's
```
kdesu kate /path/filename
```
or
```
kdesu kwrite /path/filename
```
There's an option in Konqueror (even when you run it as a regular user) when you right click a text file that belongs to root to edit it as root. This will launch kdesu kwrite, too.

---


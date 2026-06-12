---
title: "Location of Gedit configuration files."
date: 2010-01-27
forum: General Help
---

### Post by zozza on 2010-01-27
Does anyone know where the Gedit configuration file/s are located?

I know that the ~/.cache/  contains some information and deleting it removes the most recent documents list in the File menu.

However, if I wanted to remove the most recent Find and Replace information which appears in the drop-down box when you choose Find or Replace, what file would I need to remove or edit.

Thanks

---

### Post by ghostborg on 2010-01-27
/usr/share/gedit-2

---

### Post by zozza on 2010-01-28
> /usr/share/gedit-2

These directories have not been updated for some time and do not contain active configuration files.

I want to know how to modify the find / replace drop-down boxes for example.  There must be a configuration directory somewhere?

---

### Post by redmail on 2010-08-08
terminal: gconf-editor 
open     / - apps - gnome settings - gedit - history-gedit2 ...

---

### Post by generic_user on 2010-08-21
I think this is the file you are looking for
~/.gconf/apps/gnome-settings/gedit/%gconf.xml

---


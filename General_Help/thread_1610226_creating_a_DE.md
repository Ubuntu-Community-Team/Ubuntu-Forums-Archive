---
title: "creating a DE"
date: 2010-10-31
forum: General Help
---

### Post by Kingcheese26 on 2010-10-31
hi,

i've just been trying to create my own very basic lightweight desktop environment. I followed a tutorial i found online which says to save the .desktop file to /usr/share/xsessions. However, when i tried to save it to that location, it said i didn't have the permissions necessary to do it. any ideas as to what to do???:confused:

---

### Post by kaldor on 2010-10-31
> **Kingcheese26 said:**
> hi,

i've just been trying to create my own very basic lightweight desktop environment. I followed a tutorial i found online which says to save the .desktop file to /usr/share/xsessions. However, when i tried to save it to that location, it said i didn't have the permissions necessary to do it. any ideas as to what to do???:confused:

You need superuser privileges. When copying, use the sudo command in front of cp. Example:

*sudo cp yourfile /usr/share/xsessions*
or..
*gksudo nautilus*

The former grants you superuser rights and lets you copy your files to restricted directories.

The latter opens up the file manager with full read/write access if you prefer a GUI.

---


---
title: "Lock Dialog"
date: 2010-04-30
forum: General Help
---

### Post by RedSingularity on 2010-04-30
Anyone else having a problem setting a custom lock dialog theme in 10.4?

---

### Post by RedSingularity on 2010-05-02
Bump

---

### Post by plopp37 on 2010-05-02
Sure, none of downloadable themes use the same file format -- .ui instead of Karmic .xml or .glade or what was the actual one...

---

### Post by Nandox7 on 2010-06-08
You can convert the .glade files to the .ui format.

e.g.:
 gtk-builder-convert -w theme.glade theme.ui

And place all the files after inside the /usr/share/gnome-screensaver folder
not inside a sub-folder.

---


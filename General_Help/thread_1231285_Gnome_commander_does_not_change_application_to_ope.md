---
title: "Gnome commander does not change application to open file type"
date: 2009-08-04
forum: General Help
---

### Post by DrScum on 2009-08-04
using Gnome Commander under 8.04 i can't change the default app for a given file type by using rickt click > properties. Nothing happens after clicking the "change" button. It works fine when using the default file browser but the changes are not effective in Gnome Commander. What am I missing?

---

### Post by krypel on 2009-08-27
Ye ye, I just figured exactly the same thing..

---

### Post by kriukov on 2010-08-28
Same question. Bump.

---

### Post by oszkar00 on 2010-11-13
Here is the solution:

[http://www.nongnu.org/gcmd/doc.html](http://www.nongnu.org/gcmd/doc.html)

You must edit the file: ~/.local/share/applications/defaults.list

An example: if you want to open a .csv (comma separeted values) file with Geany, you need to add a new line: text/csv=geany.desktop . Then save the file, and it just works! :-D

---


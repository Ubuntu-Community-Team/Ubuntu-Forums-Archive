---
title: "default icons"
date: 2009-09-10
forum: General Help
---

### Post by The Mishanator on 2009-09-10
hello. i was wondering if there is a way to change default icons in ubuntu. i mean, when i create, say an empty folder, i want the icon that i chose out of my icon pack to be the icon that is assigned to it by default.

---

### Post by CatKiller on 2009-09-10
Icons for a given file type are theme-dependent. Put an appropriately named/sized image in <theme>/<size>/mimetypes (where theme is /usr/share/icons/*themename* for system-wide icon themes or ~/.icons/*themename* for single-user themes), and that is the image that will be used.

---

### Post by Screwdriver0815 on 2009-09-10
when you want to change just a single icon for a particular folder or the like, you can right-click on it, choose "properties" and then you can click on the symbol in the context menu. From there you can change the icon by navigating to the file you want.

But note: this icon-file has to stay in the folder where you have selected it. And: if you ever change your entire icon theme, this icon will always have the one you have choosen with this method (above)

---


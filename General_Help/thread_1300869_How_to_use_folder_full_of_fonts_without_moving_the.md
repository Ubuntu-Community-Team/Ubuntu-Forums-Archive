---
title: "How to use folder full of fonts without moving them"
date: 2009-10-25
forum: General Help
---

### Post by joey-elijah on 2009-10-25
IS there anyway to use a folder full of fonts on a shared partition without moving them into the home .fonts folder?

---

### Post by macaholic on 2009-10-25
Do you want to JUST use the fonts inside that folder and none else? If that's the case you could just make your local .fonts folder a link to the fonts folder on the shared partition.
EDIT: The code for doing so would be something like:```
mv ~.fonts fonts-backup #omit if you don't want to backup your current font directory
ln -s /path/to/sharedfonts ~/.fonts
```
Alternatively you could make a link to every font file in the shared folder within the .fonts folder.

---


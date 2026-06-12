---
title: "Using a script to open a file.  How do I target said file?"
date: 2009-07-27
forum: General Help
---

### Post by Dirjel on 2009-07-27
I've decided to use a bash script whenever I open an image file rather than just the standard Eye of Gnome program.  I'm trying to keep random pictures from showing up in the "Recent Documents" folder thing, so I can have easy access to *work*, instead of random pictures I'm always opening.  Here's the script I'm using:
```
#! /bin/sh

mv ~/.recently-used.xbel ~/.recently-used_OLD.xbel
eog
mv -f ~/.recently-used_OLD.xbel ~/.recently-used.xbel
```
Now, when I tell nautilus to use this script when I double-click an image file, it opens Eye of Gnome, and blocks the Recent Documents menu from picking it up.  However, Eye of Gnome does not open the image I chose.  How can I change that?

---

### Post by Baelus on 2009-07-27
Add $1 after eog:

```
#! /bin/sh

mv ~/.recently-used.xbel ~/.recently-used_OLD.xbel
eog $1
mv -f ~/.recently-used_OLD.xbel ~/.recently-used.xbel
```

---

### Post by Dirjel on 2009-07-27
Alright, that works.  Thanks a lot!

---

### Post by Dirjel on 2009-07-30
Alright, new problem.  Whenever I click on something with spaces anywhere in the file/folder hierarchy, Eye of Gnome opens with an error message, and no image loaded.  What do I have to change to fix that?

---

### Post by Dirjel on 2009-07-30
Got it figured out.

```
#! /bin/sh

mv ~/.recently-used.xbel ~/.recently-used_OLD.xbel
eog "$@"
mv -f ~/.recently-used_OLD.xbel ~/.recently-used.xbel
```
Works perfectly.

---


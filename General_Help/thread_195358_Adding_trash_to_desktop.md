---
title: "Adding trash to desktop"
date: 2006-06-12
forum: General Help
---

### Post by kyoushu on 2006-06-12
How do I add a trash Icon onto the desktop?

---

### Post by johnc4510 on 2006-06-12
To make the Trash icon appear on the desktop, go to Applications->System Tools->Config Editor Gconf
In Gconf, go to Apps->Nautilus->Desktop, and check the trash-icon-visible

---

### Post by MellonCollie on 2006-06-12
Open Configuration Editor and navigate to **apps/nautilus/desktop**, on the right pane put a tick next to **trash_icon_visible**.

---

### Post by Azurlune on 2006-06-12
Run gconf-editor and navigate to /apps/nautilus/desktop. You should find an option there to enable it.

---

### Post by glitch13 on 2006-06-21
I did this, and it worked, but something odd must be happening.  The trash icon is now a bitmap image and not a vector graphic.  The icon style I'm using (human, the default one) is vector based, but the Computer and Trash icons I've put on my desktop by enabling them in gconf-editor are bitmaps (of the human themed icons).  If I "stretch" them, they get horrible looking....

What gives?

---

### Post by mduran on 2006-06-21
Other with console
> 
$ gconftool-2 --type boolean --set /apps/nautilus/desktop/trash_icon_visible true

to deactivate 
> 
$ gconftool-2 --type boolean --set /apps/nautilus/desktop/trash_icon_visible false


---

### Post by lukemack on 2008-05-05
Anyone know how to do this on Hardy Herron (8.0.4) Desktop? Using gconf-editor has no effect.

---

### Post by charlemagne86 on 2008-05-24
I did that on hardy using gconf-editor...works fine

i mean the using th gui.....bt i had t first give a string name to the icon.

---

### Post by charlemagne86 on 2008-05-24
I gave the name at just below/above the place where i have to check the display rule...

---


---
title: "technical"
date: 2010-08-09
forum: General Help
---

### Post by dwilds on 2010-08-09
what do you do not to overwrite files

---

### Post by dino99 on 2010-08-09
give a new file name if you need the original one (save as, when you right click or use the menu)

---

### Post by ajgreeny on 2010-08-09
If it's something as simple as config txt files, you can set the preferences of gedit to save a backup when you edit and save a file.  That way you will always have a backup of the previous file on the disk.

If you use nano in terminal to do the edit I don't think there is an equivalent way to ensure a backup, you just have to do it manually.

---

### Post by The Cog on 2010-08-09
> chmod -w filename
will remove the writable flag, leaving it readonly.

Right-click ->Properties -> Permissions to do this in the GUI.

---


---
title: "Why won't file browser let me delete files?"
date: 2006-06-24
forum: General Help
---

### Post by nameiwantistaken on 2006-06-24
I want to delete files.  I don't want to have to pop open a command prompt to do it.  Is it just me or is this basic desktop functionality.  Is there a way for me to easily change this?

---

### Post by lamego on 2006-06-24
You can delete files with file browser as long you own or have write permission on the files. For your own protection you don't have such permissions on system files.
If you do which to delete system files are your own risk use:
```
sudo nautilus
```
That will open a file manager with admin privileges.

---

### Post by vigleik on 2006-06-24
[QUOTE=nameiwantistaken]I want to delete files.  I don't want to have to pop open a command prompt to do it.  Is it just me or is this basic desktop functionality.  Is there a way for me to easily change this?[/QUOTE]

edit->preferences->behavior and check the box that says "Include a Delete command that bypasses Trash".

Vigleik

---

### Post by aysiu on 2006-06-24
Just check the proper preferences and you won't be prompted.

By the way, if you want to browse as root, the proper command is ```
gksudo nautilus
```

---


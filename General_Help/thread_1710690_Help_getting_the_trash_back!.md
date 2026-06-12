---
title: "Help getting the trash back!"
date: 2011-03-20
forum: General Help
---

### Post by speedruntrainer on 2011-03-20
Hello.

I wanted to delete files in the trash but I accidently clicked 'Remove from panel'
Now my Recycle bin is gone, how to get it back?
I tried everything, panel is removed too, help!

---

### Post by Mikux on 2011-03-20
I'm not on my Ubuntu install, but I'm 99.9% sure you can add a desktop shortcut through gconf-editor.  

ALT+F2 > gconf-editor

apps > nautilus > desktop - enable trash icon

To empty your trash from terminal:
```
rm -rf ~/.Trash/*
```

---

### Post by Script Warlock on 2011-03-20
right click to the panel and choose "add to panel" now type trash and add.

---

### Post by roger_1960 on 2011-03-20
Hi

If your panel is missing, first try > ALT-F2 to get a way of inputting a command

then in the entry line

> gnome-panel to restore a panel

---

### Post by Script Warlock on 2011-03-20
restore panel

gconftool --recursive-unset /apps/panel && killall gnome-panel

---


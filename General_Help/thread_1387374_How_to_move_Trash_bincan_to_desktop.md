---
title: "How to move Trash bin/can to desktop ?"
date: 2010-01-21
forum: General Help
---

### Post by retro_killa on 2010-01-21
I would like to know how I can move the trash bin / trash can to the desk top & not have it in the status bar. Is there away to do this ?

---

### Post by sisco311 on 2010-01-21
Press Alt+F2 and run:
```
gconf-editor
```

go to /apps/nautilus/desktop and select the *trash_icon_visible* checkbox

---

### Post by ..::| Dave89 |::.. on 2010-01-21
[FONT=Times New Roman, serif]Hit Alt+F2 & type in [/FONT][FONT=Times New Roman, serif]gconf-editor and navigate to  [/FONT][FONT=Times New Roman, serif]apps > nautilus > desktop.  Check trash_icon_visible, and you're done.[/FONT]

---

### Post by retro_killa on 2010-01-21
thx worked great A++ help guys

---


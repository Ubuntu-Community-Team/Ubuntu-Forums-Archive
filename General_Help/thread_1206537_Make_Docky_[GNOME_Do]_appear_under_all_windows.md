---
title: "Make Docky [GNOME Do] appear under all windows?"
date: 2009-07-07
forum: General Help
---

### Post by SerenityKill3r on 2009-07-07
Hey Guys,

It's annoying me that I can't get Docky to appear under all Windows, so maximised windows get the entire screen.

Anyone know how to do this without hiding Docky?

Thanks

---

### Post by damis648 on 2009-07-07
Open gconf-editor via the run dialog (Alt+F2) and navigate to /apps/gnome-do/preferences/Docky/Utilities/DockPreferences and check the key "AllowWindowOverlap". Now close that window and restart Docky. Notice now that maximised windows pass beyond Docky, but Docky is always in front. If you are using compiz, you can fix this by opening CCSM and setting a window rule for 'below' of
```
(class=Do) & type=Dock
```

Cheers!

---

### Post by SerenityKill3r on 2009-07-07
I solved it, upgraded to latest PPA, and set to Intellihide.

---

### Post by damis648 on 2009-07-07
Ah okay.

---


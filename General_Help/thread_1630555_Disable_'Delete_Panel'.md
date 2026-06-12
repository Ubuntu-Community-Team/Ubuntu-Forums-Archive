---
title: "Disable 'Delete Panel'"
date: 2010-11-25
forum: General Help
---

### Post by cpressland on 2010-11-25
Hey guys,

I'm rolling out Ubuntu in our call center at the moment and I'd like to disable the 'Delete Panel' functionality, I wana keep things as default as possible.

Any ideas guys?

Chris

---

### Post by WorMzy on 2010-11-25
Open gconf-editor (Alt+F2, gconf-editor, run) and browse to /apps/panel/global/locked_down, set it to true and restart gnome-panel. That will work for one user. To make it the default setting, right-click on the gconf entry and choose "Set as Default", enter your sudoers password and authenticate, then right-click it again and choose "Set as Mandatory". That should make it a global key which users have no option to change.

---

### Post by cpressland on 2010-11-25
Thankyou :)

Much appreciated.

---


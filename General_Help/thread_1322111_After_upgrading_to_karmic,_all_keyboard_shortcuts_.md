---
title: "After upgrading to karmic, all keyboard shortcuts are capitalized"
date: 2009-11-10
forum: General Help
---

### Post by Ozeuss on 2009-11-10
Just upgraded to karmic, and i noticed that all my keyboard shortcuts have to be capital letter-
Ctrl+A (meaning it's really Ctrl+Shift+A). another weird thing is that when i press Ctrl in terminal, it uses my alternate language (in my case, hebrew).
Anyone know how to fix this?

---

### Post by Ozeuss on 2009-11-11
anyone?

---

### Post by Ozeuss on 2009-11-21
i solved it by changing the setting in gconf-editor,
desktop->gnome-> peripherals->*computername*->0
and changed the order of the input languages (making US first).

---


---
title: "Oh Dear - Themes"
date: 2009-11-09
forum: General Help
---

### Post by Quarkrad on 2009-11-09
9.10 - I installed a few themes to see what they were like.  OK, but I now want to back to default.  If I go System/Preferences/Appearance and select any of the themes I have a problem. No matter what sort of window opens (nautilus, thunderbird, firefox, etc) I do not have the normal three icons top right of the window - hide, resize, quit.  I cannot resize any windows - I can only quit them by File/Quit.  Any ideas how I can get my icons back?

---

### Post by P4man on 2009-11-09
select your theme, then click  customise e then go to window border and pick one that works. That is assuming you have windows borders at all. If you dont try alt F2 and run

```
metacity --replace
```

---

### Post by _khAttAm_ on 2009-11-09
I guess it is a compiz issue. You may try 
compiz --replace
in the run dialog that comes up when you press Alt+F2

---

### Post by Quarkrad on 2009-11-09
Many many thanks - metacity --replace did it.

---

### Post by P4man on 2009-11-09
To make sure it keeps working, open compiz settings manager (assuming you installed that) and check if the *windows decoration plugin* is enabled  (its in effects).

---


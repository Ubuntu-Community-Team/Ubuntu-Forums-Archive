---
title: "Disabling password when resume from hibernation. . ."
date: 2009-09-11
forum: General Help
---

### Post by Clove7 on 2009-09-11
How do I remove that password, the one that comes up when you move the mouse/press a key and your computer comes out of hibernation? I can't seem to find it.

---

### Post by P4man on 2009-09-11
open ```
gconf-editor
``` and navigate to:
/apps/gnome-power-manager/lock/hibernate

turn it off there.

---


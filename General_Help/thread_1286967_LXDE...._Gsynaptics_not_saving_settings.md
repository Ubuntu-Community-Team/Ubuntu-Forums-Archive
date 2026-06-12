---
title: "LXDE.... Gsynaptics not saving settings?"
date: 2009-10-09
forum: General Help
---

### Post by asianette on 2009-10-09
Everytime I reboot/log in to a new session, I have to run gsynaptics to turn off the scrolling and such. Is there a reason why my settings are being reset?

---

### Post by kerry_s on 2009-10-09
in your startup you need:
**gsynaptics-init --sm-disable**

---

### Post by asianette on 2009-10-09
> **kerry_s said:**
> in your startup you need:
**gsynaptics-init --sm-disable**

Ok, I made a shell script for it... what exactly is --sm-disable?

---

### Post by kerry_s on 2009-10-10
> **asianette said:**
> Ok, I made a shell script for it... what exactly is --sm-disable?

"--sm-disable" i think is so theres only 1 instance, but i'm not sure. thats the way it is in my startup when i installed it, i didn't have to manually add it, but then i'm using gnome, not lxde.

---


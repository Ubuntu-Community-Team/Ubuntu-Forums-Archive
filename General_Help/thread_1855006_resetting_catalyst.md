---
title: "resetting catalyst?"
date: 2011-10-05
forum: General Help
---

### Post by Someone uk on 2011-10-05
when i start my computer i have problems with gnome and it happened after a bad configuration to catalyst

is there a way to reset catalyst to the default settings in the terminal?

---

### Post by khelben1979 on 2011-10-05
You can try:
```
sudo aticonfig -f --initial
``` to see if it helps. And if uncertain, make backups first.

---


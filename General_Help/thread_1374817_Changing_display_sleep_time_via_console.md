---
title: "Changing display sleep time via console?"
date: 2010-01-07
forum: General Help
---

### Post by itmozart on 2010-01-07
Is it possible to change the sleep time via console?

Sometimes it'd be helpful to change it (to 1 minute, or to never sleep) via console.

Thanks!
Saverio

---

### Post by chewearn on 2010-01-07
The relevant settings you are looking for can be found in:
gconf > apps > gnome-power-manager > timeout

Use gconftool-2 to manipulate gconf in terminal or a bash script.

```
man gconftool-2
```

---


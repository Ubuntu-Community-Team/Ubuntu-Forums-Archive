---
title: "fglrxconfig and mouse settings"
date: 2006-05-28
forum: General Help
---

### Post by jvandecar on 2006-05-28
This isn't a how, more of a why.

Why does the mouse have to configured when FGLRXCONFIG is run?

---

### Post by tkjacobsen on 2006-05-29
in the new ati-drivers you should use aticonfig instead of fglrx config:
```
sudo aticonfig --inintial
```

This will modify your existing xorg.conf istead of creating a new.

---


---
title: "2 many xorg.conf."
date: 2010-09-12
forum: General Help
---

### Post by soryu on 2010-09-12
how do i remove all those xorg.conf files i have. there are like 12 of them and 11 xorg.conf backup files.
could these be messing up my nvidia settings?
im getting errors.
how can i get a new default xorg.conf file?

---

### Post by soryu on 2010-09-12
or which one am i currently using?
i want to get rid of the others.

---

### Post by AlphaLexman on 2010-09-12
You are using /etc/X11/xorg.conf you should keep the xorg.conf.failsafe the others should be ok to delete, providing your graphics are in working order.

---

### Post by WorMzy on 2010-09-12
The only one you're using is xorg.conf. You can remove the others by using sudo rm <filename> on them, or by running nautilus in gksu mode.

```
gksu nautilus /etc/X11
```

---

### Post by soryu on 2010-09-12
Done & Done.

thanks

---


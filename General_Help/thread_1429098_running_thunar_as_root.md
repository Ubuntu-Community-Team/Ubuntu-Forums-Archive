---
title: "running thunar as root"
date: 2010-03-13
forum: General Help
---

### Post by ubunterooster on 2010-03-13
I need to have root permissions to move files onto a said device. How do I run thunar with such permissions?

---

### Post by themarker0 on 2010-03-13
Sudo Thunar? Then just copy and paste what else you/want need.

---

### Post by ubunterooster on 2010-03-13
sudo thunar opens thunar but the media player still shows all files as read only

---

### Post by spcwingo on 2010-03-13
You can try:

```
gksu thunar
```

followed by adjusting the permissions [in the right click context menu under properties (or something worded similarly)].

---

### Post by ajgreeny on 2010-03-13
Should really be ```
gksudo thunar
```, but if ```
sudo thunar
``` opened thunar without problems, it may not make any difference.

Are the files in question copied from a CD?  If so they may well be read only and you will need to change their permissions.

---

### Post by ubunterooster on 2010-03-13
I really should have thought ahead.
 Right now, I'm unable to use my computer [written via nintendo DSi] but when I get a chance, I'll try the above.

---


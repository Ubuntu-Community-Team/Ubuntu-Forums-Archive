---
title: "how can i get my old panel back?"
date: 2010-07-31
forum: General Help
---

### Post by nobody850 on 2010-07-31
i was trying to explore the OS when i deleted the original panel.
how can i get it back.
thank you

---

### Post by sgage on 2010-07-31
Boot to recovery mode, then:

apt-get install gnome-panel

---

### Post by WorMzy on 2010-07-31
> **sgage said:**
> Boot to recovery mode, then:

apt-get install gnome-panel

What.


Run the following commands to completely reset your panel:

```
rm -fr ~/.gconf/apps/panel
```then
```
gconftool-2 --shutdown
```finally
```
pkill gnome-panel
```

---

### Post by nobody850 on 2010-07-31
thank you, i will try it today.

---

### Post by nobody850 on 2010-07-31
thank you, works great now.

---


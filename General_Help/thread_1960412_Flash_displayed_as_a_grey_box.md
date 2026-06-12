---
title: "Flash displayed as a grey box"
date: 2012-04-17
forum: General Help
---

### Post by layers on 2012-04-17
I messed with the Gnome colour chooser (RGBvalues) and then I removed it. Ever since then, my youtube videos are funny and other more important flash material is displayed as a grey box.

if I really need it, I do ```
export XLIB_SKIP_ARGB_VISUALS=1 && firefox
```which I found in a thread, but how can I make it permanent?

---

### Post by layers on 2012-04-17
bump?

---

### Post by lovinglinux on 2012-04-19
I would try to revert the initial changes that caused the problem, because adding such workaround globally could interfere with other applications.

---


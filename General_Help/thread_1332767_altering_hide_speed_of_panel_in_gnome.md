---
title: "altering hide speed of panel in gnome"
date: 2009-11-20
forum: General Help
---

### Post by richardy on 2009-11-20
Hi,
Is it possible to alter the raise and hide speed of the panel - i want to make it immediate (like in Xubuntu). I tried to use gconf-editor and found some alterable values, defaults were 500ms for hide and 300ms for raise. I changed these values to 100ms for both (as a test) but this had no effect.

Any help is much appreciated.

Cheers.

---

### Post by richardy on 2009-11-20
Anybody?

---

### Post by kerry_s on 2009-11-20
in gconf-editor the 1's you want to change is "toplevels", you change them to 0 to be fast like on xfce4. you want to do the hide & un_hide.

---


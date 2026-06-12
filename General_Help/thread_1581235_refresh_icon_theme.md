---
title: "refresh icon theme"
date: 2010-09-24
forum: General Help
---

### Post by behzadsh on 2010-09-24
hi,
I edited or changed some icons in /usr/share/icons/ but nothing changed :confused:
I think they are cached. what should I do to refresh them?

---

### Post by sikander3786 on 2010-09-24
Salam Brother.

What you really wan't to achieve? Install some new icon themes? I don't think you need to change or add icons manually in /usr/share/icons directory.

---

### Post by behzadsh on 2010-09-26
> **sikander3786 said:**
> Salam Brother.

What you really wan't to achieve? Install some new icon themes? I don't think you need to change or add icons manually in /usr/share/icons directory.

I installed an icon theme, then I change some of svg (scalable) and png file... but no change happened.

e.g. I edit and changed firefox-3.5 icon but its icon is still what it was!!

---

### Post by VCoolio on 2010-09-26
Try: gtk-update-icon-cache ICONSET NAME  to reload icon theme (delete .cache file inside theme folder first if it's there) or change icon theme in appearance properties and change it back.

---

### Post by Ultra_Man on 2010-09-26
Just log out and log back in for the changes to take effect.

---


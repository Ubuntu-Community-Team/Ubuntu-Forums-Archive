---
title: "openGL Direct Render only works from bash?"
date: 2006-06-16
forum: General Help
---

### Post by Trab on 2006-06-16
I have the oddest error, ive tried many things to fix it, and posted before, but i figured something out.

if i edit my /etc/X11/xorg.conf and change device from nvidia to nvida and ctrl+alt+backspace (force kill X) it obviously fails...
then i ctrl+F1 and vi the xorg.conf and fix it to say nvidia...
then i type startx
and direct rendering then works.

why doesnt it just work off the first boot? this is VERY inconvenient, and just plain annoying...

thanks,
Trab

---


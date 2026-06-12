---
title: "D4x problems"
date: 2006-02-04
forum: General Help
---

### Post by clov on 2006-02-04
I can't run D4X. I used to do it, but not anymore... I get:
> 
(d4x:11030): Gdk-CRITICAL **: gdk_gc_set_clip_rectangle: assertion `GDK_IS_GC (gc)' failed

(d4x:11030): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:11030): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:11030): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:11030): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:11030): Gdk-CRITICAL **: gdk_gc_set_clip_rectangle: assertion `GDK_IS_GC (gc)' failed
Segmentation fault


---

### Post by bonzodog on 2006-02-04
have you upgraded the package or gnome, or any libraries associated with D4X?
Those look like errors caused by gtk.

---


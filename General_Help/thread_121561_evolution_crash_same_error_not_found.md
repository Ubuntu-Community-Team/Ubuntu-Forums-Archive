---
title: "evolution crash: same error not found"
date: 2006-01-25
forum: General Help
---

### Post by chz on 2006-01-25
when i run evolution everything works fine, but when i exit i get this message:
$ evolution
adding hook target 'source'

(evolution:9276): camel-WARNING **: camel_exception_get_id called with NULL parameter.

(evolution:9276): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:9276): GnomeCanvas-CRITICAL **: gnome_canvas_request_redraw: assertion `GNOME_IS_CANVAS (canvas)' failed

camel-ERROR **: file camel-object.c: line 242 (cobject_finalise): assertion failed: (o->ref_count == 0)
aborting...
=================================

i don't know what could be wrong, i tried reinstalling anything that resembled evolution camel and gdk. anybody else encounter this issue..or have some idea of wut could be wrong..?

---


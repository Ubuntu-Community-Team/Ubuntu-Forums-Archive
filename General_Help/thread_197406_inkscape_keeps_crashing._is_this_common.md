---
title: "inkscape keeps crashing. is this common?"
date: 2006-06-15
forum: General Help
---

### Post by lapsey on 2006-06-15
this makes me very sad as i find inkscape a really great program other than the instability issue

```
(inkscape:6421): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed
``` x 100000

```
** (inkscape:6421): CRITICAL **: gail_notebook_real_remove_gtk: assertion `obj' failed

(inkscape:6421): Gdk-CRITICAL **: gdk_drawable_get_size: assertion `GDK_IS_DRAWABLE (drawable)' failed

(inkscape:6421): Gdk-CRITICAL **: gdk_pixbuf_get_from_drawable: assertion `src != NULL' failed

(inkscape:6421): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy: assertion `pixbuf != NULL' failed

(inkscape:6421): GdkPixbuf-CRITICAL **: gdk_pixbuf_saturate_and_pixelate: assertion `GDK_IS_PIXBUF (src)' failed

(inkscape:6421): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(inkscape:6421): Gdk-CRITICAL **: gdk_draw_pixbuf: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(inkscape:6421): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
The program 'inkscape' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 1140488 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

sometimes it will just die, other times even x.org is killed in the crash.

i have no idea where to file this, if this is even a bug with inkscape itself. is this common?

---

### Post by verbalshadow on 2006-06-15
any chance that you are using composite is there? if so then i beilieve that this is fixed in the soon to be released version

if not try looking in [http://www.sf.net/projects/inkscape](http://www.sf.net/projects/inkscape) and then click bugs  and look for similiar bug reports

---


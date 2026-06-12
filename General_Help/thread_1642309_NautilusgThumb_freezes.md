---
title: "Nautilus/gThumb freezes"
date: 2010-12-10
forum: General Help
---

### Post by claus on 2010-12-10
Hi all,

for some mysterious reason, Nautilus & gThumb freeze when I make an attempt to change the respective directory. I'm using Ubuntu 9.10. What can be the reason behind this? Here are the shell messages I'm getting:

> 
(nautilus:2646): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:2646): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2646): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2646): WARNING **: No marshaller for signature of signal 'ShareCreateError'

(nautilus:2646): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_height > 0' failed

(nautilus:2646): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(nautilus:2646): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(nautilus:2646): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(nautilus:2646): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:2646): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_height > 0' failed

(nautilus:2646): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(nautilus:2646): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(nautilus:2646): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(nautilus:2646): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:2646): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_height > 0' failed

(nautilus:2646): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(nautilus:2646): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(nautilus:2646): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(nautilus:2646): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:2646): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_height > 0' failed

(nautilus:2646): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(nautilus:2646): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(nautilus:2646): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(nautilus:2646): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Killed


Any help appreciated,

Claus

---


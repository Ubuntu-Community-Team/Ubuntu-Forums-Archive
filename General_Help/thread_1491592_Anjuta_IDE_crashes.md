---
title: "Anjuta IDE crashes"
date: 2010-05-23
forum: General Help
---

### Post by CJay554 on 2010-05-23
Hey guys, i just started using Anjuta IDE, the first time i used it it was great, and then i closed it...

im getting this as in the terminal:

```
krys@krys-laptop:~$ anjuta

(anjuta:23014): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkMenu'

(anjuta:23014): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
Assertion 'pthread_setspecific(t->key, userdata) == 0' failed at pulsecore/thread-posix.c:196, function pa_tls_set(). Aborting.
Aborted

```

Any ideas? Seems when i google it happens to ALOT of applications such as Cairo-dock, GLX-dock, pino-twitter. All of these exit with this message thats included above as well.

```
Assertion 'pthread_setspecific(t->key, userdata) == 0' failed at pulsecore/thread-posix.c:196, function pa_tls_set(). Aborting.
```

---

### Post by FirstByté on 2010-07-10
I'm having similar crashes any time I try to build any project even a new GTKMM ("HelloWorld")app.

I'm just trying to get my feet wet with Linux app development but my experiences with Anjuta hasn't been much fun. I love Anjuta's 'Light looks' don't wanna try any other one for now.

Thanks.
```

~$ anjuta

(anjuta:7385): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_subpixbuf: assertion `src_y >= 0 && src_y + height <= src_pixbuf->height' failed

(anjuta:7385): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_subpixbuf: assertion `src_y >= 0 && src_y + height <= src_pixbuf->height' failed

(anjuta:7385): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_subpixbuf: assertion `src_y >= 0 && src_y + height <= src_pixbuf->height' failed

(anjuta:7385): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_subpixbuf: assertion `src_y >= 0 && src_y + height <= src_pixbuf->height' failed

(anjuta:7385): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_subpixbuf: assertion `src_y >= 0 && src_y + height <= src_pixbuf->height' failed

(anjuta:7385): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_subpixbuf: assertion `src_y >= 0 && src_y + height <= src_pixbuf->height' failed

(anjuta:7385): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_subpixbuf: assertion `src_y >= 0 && src_y + height <= src_pixbuf->height' failed

(anjuta:7385): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_subpixbuf: assertion `src_x >= 0 && src_x + width <= src_pixbuf->width' failed

(anjuta:7385): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
**
Gtk:ERROR:/build/buildd/gtk+2.0-2.20.1/gtk/gtkimage.c:2125:gtk_image_expose: code should not be reached
Aborted


```

---

### Post by FirstByté on 2010-07-10
Similar bug filed here

[http://bugs.gentoo.org/show_bug.cgi?id=276549](http://bugs.gentoo.org/show_bug.cgi?id=276549)

---

### Post by FirstByté on 2010-07-29
BUMP!

HELP!!

Will this bug ever get fixed? Anyone?

[https://bugs.launchpad.net/ubuntu/+source/anjuta/+bug/605215](https://bugs.launchpad.net/ubuntu/+source/anjuta/+bug/605215)

---

### Post by iguest on 2010-08-13
Hey there,

I had the same problem that [CJay554]("http://www.uluga.ubuntuforums.org/member.php?u=269230") had.  Anjuta would just crash on startup after picking either the Document plugin or the Glade plugin. The error from STDOUT:

 anjuta Assertion 'pthread_setspecific(t->key, userdata) == 0' failed at pulsecore/thread-posix.c:196, function pa_tls_set(). Aborting. ]

Workaround:  I deleted all of my hack experiment projects that I had created, and then restarted Anjuita.  Anjuta came up fine afterwards, and I preceded to create a new project.  To be fair I had been playing with Code::Blocks, and may have hacked around in the last saved Anjuita project from Code::blocks.  I can't say...

Good luck.

Iestyn Guest

---

### Post by FirstByté on 2010-09-20
> **iguest said:**
> Hey there,

I had the same problem that [CJay554]("http://www.uluga.ubuntuforums.org/member.php?u=269230") had.  Anjuta would just crash on startup after picking either the Document plugin or the Glade plugin. The error from STDOUT:

 anjuta Assertion 'pthread_setspecific(t->key, userdata) == 0' failed at pulsecore/thread-posix.c:196, function pa_tls_set(). Aborting. ]

Workaround:  I deleted all of my hack experiment projects that I had created, and then restarted Anjuita.  Anjuta came up fine afterwards, and I preceded to create a new project.  To be fair I had been playing with Code::Blocks, and may have hacked around in the last saved Anjuita project from Code::blocks.  I can't say...

Good luck.

Iestyn Guest

Thanks for the input. I tried removing [Even through terminal] all AND any instance that may be relating to Anjuta
```
$ sudo apt-get purge anjuta*
```

Reintsalled Anjuta;

```
$ sudo apt-get install anjuta
```
Still the problem was not resolved
> (anjuta:13792): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_subpixbuf: assertion `src_x >= 0 && src_x + width <= src_pixbuf->width' failed

(anjuta:13792): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
**
Gtk:ERROR:/build/buildd/gtk+2.0-2.20.1/gtk/gtkimage.c:2125:gtk_image_expose: code should not be reached
Aborted

The I downloaded the tar files and installed v.2.28 [.configure, make, make install], it stalled correctly but crashes on same error.

I removed v.2.28 [make uninstall], and installed v.2.30 also but same error was encountered.

I look forward installing Anjuta on a fresh install of Ubuntu 10.10 when it's out 'cause my machine runs and upgraded 9.04 all the way to 10.04. 

Who knows a fresh install might save me; unless someone is able to fix my issues, I may be out of luck developing my desired apps. [Netbeans/QT 4?? options?]

---


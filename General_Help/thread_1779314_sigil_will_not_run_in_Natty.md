---
title: "sigil will not run in Natty"
date: 2011-06-10
forum: General Help
---

### Post by cloyd on 2011-06-10
I installed Sigil ( linux (x86) build 0.3.4 ) on my 10.4 netbook, and it ran fine. Then I tried to install it on my larger laptop running Natty. It installed without a hitch. When I tried to run it, a white window flashed momentarily, and then vanished. I tried to run it from the terminal by navigating to the right directory, and running it with ./sigil, and got the following:

/usr/share/mime/application/xhtml+xml.xml:1: parser error : Document is empty

^
/usr/share/mime/application/xhtml+xml.xml:1: parser error : Document is empty

^

(<unknown>:21823): GdkPixbuf-WARNING **: Bug! loader 'png' didn't set an error on failure

(<unknown>:21823): Gtk-WARNING **: Error loading theme icon 'window-close' for stock: Internal error: Image loader module 'png' failed to complete an operation, but didn't give a reason for the failure

(<unknown>:21823): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (<unknown>:21823): CRITICAL **: murrine_style_draw_render_icon: assertion `base_pixbuf != NULL' failed

(<unknown>:21823): Gtk-CRITICAL **: IA__gtk_style_render_icon: assertion `pixbuf != NULL' failed

(<unknown>:21823): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(<unknown>:21823): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(<unknown>:21823): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed
Segmentation fault


I thought, try it in classic mode . . . still didn't work. Looking at the error message, it looks like I'm missing something essential, but what is it?  I would appreciate the help. I don't just have to have this on this machine, but I'd like to. Thanks in advance.

---

### Post by Frogs Hair on 2011-06-10
This is the most current information I could find . Most of what I found when searching was for 9.10 .[http://www.jonathanmoeller.com/screed/?p=3064](http://www.jonathanmoeller.com/screed/?p=3064)

---

### Post by cloyd on 2011-06-10
Thanks for the reply.
It installed without any problem. It just won't run. I think I am going to try an experimental build and see what happens. 

Update: I tried this:        linux (x86) build 0.4.0RC1 (EXPERIMENTAL). It runs. I won't have time to work with it till this evening to find out if there are any problems with it.

I did not use the uninstall program. I simply deleted the old directory directory, and then installed in a new folder.

---

### Post by Frogs Hair on 2011-06-10
Great ! :o

---


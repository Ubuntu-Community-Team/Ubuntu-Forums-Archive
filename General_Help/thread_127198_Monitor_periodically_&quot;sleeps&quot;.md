---
title: "Monitor periodically &quot;sleeps&quot;"
date: 2006-02-08
forum: General Help
---

### Post by Ninjagecko on 2006-02-08
Might anyone have any idea what's going on?

My monitor periodically turns black, and when I try to hit keys it doesn't turn back on. I have to do ctrl-alt-f1 and then ctrl-alt-f7, and then my monitor has a 50% of coming back on. If it does, Firefox crashes immediately. If it doesn't, I have to reboot.

The odd thing is, I've turned off sleep *everywhere* on my computer! o.O If anyone knows how to make 100% sure I have all forms of sleep turned off, please help.

Using a Toshiba Portege m200 laptop.

Thanks.

____ Errors spewed out by Firefox:...

(Gecko:13030): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(Gecko:13030): Gdk-CRITICAL **: gdk_pixbuf_get_from_drawable: assertion `gdk_window_is_viewable (src)' failed

(Gecko:13030): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `pixbuf != NULL' failed

(Gecko:13030): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_bits_per_sample: assertion `pixbuf != NULL' failed

(Gecko:13030): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(Gecko:13030): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(Gecko:13030): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(Gecko:13030): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadClass, invalid event class'.
  (Details: serial 47374 error_code 173 request_code 147 minor_code 6)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---


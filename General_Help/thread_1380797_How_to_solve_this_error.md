---
title: "How to solve this error"
date: 2010-01-14
forum: General Help
---

### Post by ganeshredcobra on 2010-01-14
ganesh@ganesh-desktop:~$ sudo xsplash
[sudo] password for ganesh: 

(xsplash:1975): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(xsplash:1975): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(xsplash:1975): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `GDK_IS_PIXBUF (src)' failed

(xsplash:1975): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(xsplash:1975): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(xsplash:1975): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_subpixbuf: assertion `GDK_IS_PIXBUF (src_pixbuf)' failed

(xsplash:1975): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(xsplash:1975): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed
The program 'xsplash' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 129 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
ganesh@ganesh-desktop:~$

---

### Post by akakingess on 2010-01-14
My first attempt would be at a purge and then reinstall, but I am not too familiar with xsplash.

---

### Post by JBAlaska on 2010-01-14
Did you check the naming of the xspash image your trying to use for syntax errors?

Like bg_XXXX[COLOR="Red"]_[/COLOR]XXXX.jpg instead of bg_XXXX[COLOR="Red"]x[/COLOR]XXXX.jpg

---


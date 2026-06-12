---
title: "F-Spot Encountering Fatal Error"
date: 2009-11-05
forum: General Help
---

### Post by HeretikSaint on 2009-11-05
I just upgraded to Karmic Koala and all of a sudden, F-spot doesn't want to work.  I'm currently trying to research the problem but I can't even view the pictures in a folder because of this.  I need this to work pretty quickly.  I tried opening it in a terminal and I got the following errors:
```
[Info  11:17:11.684] Initializing DBus
[Info  11:17:11.776] Initializing Mono.Addins
[Info  11:17:11.915] Starting new FSpot server (f-spot 0.6.1.4)

** (f-spot:2650): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2650): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2650): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2650): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2650): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  11:17:12.553] Starting BeagleService
[Info  11:17:12.567] Hack for gnome-settings-daemon engaged

(f-spot:2650): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 3124 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Thank you for any and all help.  Let me know if I can provide any further information.

---

### Post by directhex on 2009-11-05
Try changing GNOME theme.

---

### Post by Giblet5 on 2009-11-05
> **directhex said:**
> Try changing GNOME theme.

+1

This is probably a failure to allocate an appropriate colormap.

The price of a pretty desktop on a cost-conscious system is BADALLOC errors from Xlib...

---

### Post by keithb on 2009-11-05
Thanks

I changed from New Wave back to Human theme and now f-spot will open. I don't really understand why it works but it does.

---


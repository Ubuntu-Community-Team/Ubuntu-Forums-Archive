---
title: "need help F-spot dont load, crashes !"
date: 2009-12-05
forum: General Help
---

### Post by qwerty2009 on 2009-12-05
hi i had to reinestall ubuntu last night as i switched to kde (opensuse,kubuntu) but couldnt install applications i needed to install as they were gtk

anyway this is a fresh install of ubuntu but for some reason s-spot fails to load ive tried completely removing it from package manager and then installing it again still stops from fully loading loading 

when launching f-spot from terminal this is what shows 

> myname@myname-laptop:~$ f-spot
[Info  18:12:22.476] Initializing DBus
[Info  18:12:22.609] Initializing Mono.Addins
[Info  18:12:22.802] Starting new FSpot server (f-spot 0.6.1.5)

** (f-spot:2478): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2478): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2478): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2478): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2478): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  18:12:23.907] Starting BeagleService
[Info  18:12:23.927] Hack for gnome-settings-daemon engaged

(f-spot:2478): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2138 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
myname@myname-laptop:~$ 

anyhelp appreciated

---

### Post by qwerty2009 on 2009-12-05
can anyone help f-spot is the only decent photo manager so i would realy like this fixed

---

### Post by qwerty2009 on 2009-12-05
bump

---


---
title: "F-Spot photo manager execute fail"
date: 2010-01-22
forum: General Help
---

### Post by donato roque on 2010-01-22
The first time I use F-spot and it failed to open.  Terminal shows these:

(/usr/lib/f-spot/f-spot.exe:6547): GLib-WARNING **: g_set_prgname() called multiple times
[Info  17:16:58.232] Initializing DBus
[Info  17:16:58.329] Initializing Mono.Addins
[Info  17:16:58.480] Starting new FSpot server (f-spot 0.6.1.5)

** (/usr/lib/f-spot/f-spot.exe:6547): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:6547): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:6547): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:6547): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:6547): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  17:16:59.346] Starting BeagleService
[Info  17:16:59.361] Hack for gnome-settings-daemon engaged

(/usr/lib/f-spot/f-spot.exe:6547): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program '/usr/lib/f-spot/f-spot.exe' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2944 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


I have tried to reinstall and delete f-spot folders in /user/gconf/f-spot.  Run out of ideas so I posted the problem here.  

Anyone who also encountered this?

---

### Post by TnTMike on 2010-01-23
There have been a number of posts about this problem. The same thing was happening to me try thread [http://ubuntuforums.org/showthread.php?t=1307641&highlight=f-spot]("http://ubuntuforums.org/showthread.php?t=1307641&highlight=f-spot") suggests a fix that worked for me as well as a few others.
I changed my desktop theme to human from new wave.

---


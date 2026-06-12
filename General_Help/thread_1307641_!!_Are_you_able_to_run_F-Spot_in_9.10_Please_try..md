---
title: "!! Are you able to run F-Spot in 9.10? Please try."
date: 2009-10-31
forum: General Help
---

### Post by Isaacgallegos on 2009-10-31
F-spot tries to open but closes after a second. To see what was going on I executed it in the terminal:
```
isaac@isaac-desktop:~$ f-spot
[Info  07:07:57.516] Initializing DBus
[Info  07:07:57.630] Initializing Mono.Addins
[Info  07:07:57.780] Starting new FSpot server (f-spot 0.6.1.3)

** (f-spot:23110): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:23110): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:23110): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:23110): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:23110): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  07:07:58.563] Starting BeagleService
[Info  07:07:58.578] Hack for gnome-settings-daemon engaged

(f-spot:23110): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2915 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
isaac@isaac-desktop:~$ 
```
What happes for you?

---

### Post by BFG on 2009-10-31
I get similar:

```
mark@BLACKu:~$ f-spot
[Info  12:18:16.265] Initializing DBus
[Info  12:18:16.357] Initializing Mono.Addins
[Info  12:18:16.595] Starting new FSpot server (f-spot 0.6.1.3)

** (f-spot:4594): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:4594): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:4594): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:4594): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:4594): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  12:18:17.177] Starting BeagleService
[Info  12:18:17.192] Hack for gnome-settings-daemon engaged

(f-spot:4594): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
^C
mark@BLACKu:~$ 

```

---

### Post by 6205 on 2009-10-31
F-Spot has been updated in Karmic to 0.6.1.4 - anyway it's working for me without a problems..

---

### Post by Xanthomryr on 2009-10-31
No Problems here.

[[IMG]http://img5.imagebanana.com/img/l2db8cc/screenshot2.png[/IMG]](http://img5.imagebanana.com/)

---

### Post by FrostCake on 2009-10-31
Same here. Can't run.

```

xxx-ubuntu:~$ f-spot
[Info  20:41:51.476] Initializing DBus
[Info  20:41:51.687] Initializing Mono.Addins
[Info  20:41:52.039] Starting new FSpot server (f-spot 0.6.1.3)

** (f-spot:5107): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:5107): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:5107): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:5107): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:5107): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  20:41:53.656] Starting BeagleService
[Info  20:41:53.689] Hack for gnome-settings-daemon engaged

(f-spot:5107): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
Stacktrace:

  at (wrapper managed-to-native) Gtk.Style.gtk_paint_box (intptr,intptr,int,int,intptr,intptr,intptr,int,int,int,int) <0x00004>
  at (wrapper managed-to-native) Gtk.Style.gtk_paint_box (intptr,intptr,int,int,intptr,intptr,intptr,int,int,int,int) <0xffffffff>
  at Gtk.Style.PaintBox (Gtk.Style,Gdk.Drawable,Gtk.StateType,Gtk.ShadowType,Gdk.Rectangle,Gtk.Widget,string,int,int,int,int) <0x000cd>
  at FSpot.GroupSelector/Limit.Draw (Gdk.Rectangle) <0x00159>
  at FSpot.GroupSelector.OnExposeEvent (Gdk.EventExpose) <0x005f4>
  at Gtk.Widget.exposeevent_cb (intptr,intptr) <0x00069>
  at (wrapper native-to-managed) Gtk.Widget.exposeevent_cb (intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0xffffffff>
  at Gtk.Application.Run () <0x0000a>
  at FSpot.Driver.Main (string[]) <0x01a6e>
  at (wrapper runtime-invoke) FSpot.Driver.runtime_invoke_int_object (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

    f-spot [0x80c8824]
    f-spot [0x80f4693]
    [0x980410]
    /lib/tls/i686/cmov/libc.so.6(memcpy+0x46) [0x293006]
    [0x87736f8]
    /usr/lib/libgdk-x11-2.0.so.0 [0x84aca6]
    /usr/lib/libgdk-x11-2.0.so.0 [0x8387e9]
    /usr/lib/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x13f) [0x81472f]
    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so [0x96ee67]
    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so [0x9704f0]
    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so [0x96cd29]
    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so [0x96da49]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_paint_shadow+0xee) [0x730598e]
    /usr/lib/libgtk-x11-2.0.so.0 [0x730dca8]
    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so [0x96de95]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_paint_box+0xee) [0x730544e]
    [0x792b392]
    [0x792b2fe]
    [0x792b092]
    [0x792a40d]
    [0x7929de2]
    [0x238a747]
    /usr/lib/libgtk-x11-2.0.so.0 [0x7287474]
    /usr/lib/libgobject-2.0.so.0 [0x75b6f9]
    /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0x75cf98]
    /usr/lib/libgobject-2.0.so.0 [0x77249e]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x648) [0x7739b8]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x773fb6]
    /usr/lib/libgtk-x11-2.0.so.0 [0x73a396e]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1a3) [0x71f2683]
    /usr/lib/libgtk-x11-2.0.so.0 [0x71f26b1]
    /usr/lib/libgtk-x11-2.0.so.0 [0x71bf9b5]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0xa4) [0x71f31f4]
    /usr/lib/libgtk-x11-2.0.so.0 [0x71f44aa]
    /usr/lib/libgtk-x11-2.0.so.0 [0x7287474]
    /usr/lib/libgobject-2.0.so.0 [0x75b6f9]
    /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0x75cf98]
    /usr/lib/libgobject-2.0.so.0 [0x77249e]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x648) [0x7739b8]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x773fb6]
    /usr/lib/libgtk-x11-2.0.so.0 [0x73a396e]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1a3) [0x71f2683]
    /usr/lib/libgtk-x11-2.0.so.0 [0x71f26b1]
    /usr/lib/libgtk-x11-2.0.so.0 [0x72ae63d]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0xa4) [0x71f31f4]
    /usr/lib/libgtk-x11-2.0.so.0 [0x71f44aa]
    /usr/lib/libgtk-x11-2.0.so.0 [0x72b129f]
    /usr/lib/libgtk-x11-2.0.so.0 [0x7287474]
    /usr/lib/libgobject-2.0.so.0 [0x75b6f9]
    /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0x75cf98]
    /usr/lib/libgobject-2.0.so.0 [0x77249e]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x648) [0x7739b8]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x773fb6]
    /usr/lib/libgtk-x11-2.0.so.0 [0x73a396e]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1a3) [0x71f2683]
    /usr/lib/libgtk-x11-2.0.so.0 [0x71f26b1]
    /usr/lib/libgtk-x11-2.0.so.0 [0x71bf9b5]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0xa4) [0x71f31f4]
    /usr/lib/libgtk-x11-2.0.so.0 [0x71f44aa]
    /usr/lib/libgtk-x11-2.0.so.0 [0x7287474]
    /usr/lib/libgobject-2.0.so.0 [0x75b6f9]
    /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0x75cf98]
    /usr/lib/libgobject-2.0.so.0 [0x77249e]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x648) [0x7739b8]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x773fb6]
    /usr/lib/libgtk-x11-2.0.so.0 [0x73a396e]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1a3) [0x71f2683]
    /usr/lib/libgtk-x11-2.0.so.0 [0x71f26b1]
    /usr/lib/libgtk-x11-2.0.so.0 [0x71bf9b5]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0xa4) [0x71f31f4]
    /usr/lib/libgtk-x11-2.0.so.0 [0x71f44aa]
    /usr/lib/libgtk-x11-2.0.so.0 [0x7287474]
    /usr/lib/libgobject-2.0.so.0 [0x75b6f9]
    /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0x75cf98]
    /usr/lib/libgobject-2.0.so.0 [0x77249e]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x648) [0x7739b8]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x773fb6]
    /usr/lib/libgtk-x11-2.0.so.0 [0x73a396e]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1a3) [0x71f2683]
    /usr/lib/libgtk-x11-2.0.so.0 [0x71f26b1]
    /usr/lib/libgtk-x11-2.0.so.0 [0x71bb82d]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0xa4) [0x71f31f4]
    /usr/lib/libgtk-x11-2.0.so.0 [0x71f44aa]
    /usr/lib/libgtk-x11-2.0.so.0 [0x73be6a1]
    /usr/lib/libgtk-x11-2.0.so.0 [0x7287474]
    /usr/lib/libgobject-2.0.so.0 [0x75b6f9]
    /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0x75d072]
    /usr/lib/libgobject-2.0.so.0 [0x77249e]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x648) [0x7739b8]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x773fb6]
    /usr/lib/libgtk-x11-2.0.so.0 [0x73a396e]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x500) [0x7281190]
    /usr/lib/libgdk-x11-2.0.so.0 [0x83a1d4]
    /usr/lib/libgdk-x11-2.0.so.0 [0x85d734]
    /usr/lib/libgdk-x11-2.0.so.0 [0x83187f]
    /usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_updates+0x150) [0x835a50]
    /usr/lib/libgtk-x11-2.0.so.0 [0x73be273]
    /usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c) [0x76a9fc]
    /usr/lib/libgobject-2.0.so.0 [0x75b6f9]
    /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0x75d072]
    /usr/lib/libgobject-2.0.so.0 [0x77249e]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7bd) [0x773b2d]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x773fb6]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_check_resize+0x8a) [0x71f331a]
    /usr/lib/libgtk-x11-2.0.so.0 [0x71f3370]
    /usr/lib/libgdk-x11-2.0.so.0 [0x80ff78]
    /lib/libglib-2.0.so.0 [0x16a0f1]
    /lib/libglib-2.0.so.0(g_main_context_dispatch+0x1f8) [0x16be78]
    /lib/libglib-2.0.so.0 [0x16f720]
    /lib/libglib-2.0.so.0(g_main_loop_run+0x1bf) [0x16fb8f]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9) [0x7281419]
    [0x4638c50]
    [0x4638c13]
    [0xc79d57]
    [0xc78203]
    f-spot(mono_runtime_exec_main+0x15b) [0x811132b]
    f-spot(mono_runtime_run_main+0x15a) [0x81134da]
    f-spot(mono_main+0x1aad) [0x80b19bd]
    f-spot [0x805aba5]
    /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x234b56]
    f-spot [0x805aae1]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
[New Thread 0x31d6b70 (LWP 5114)]
[New Thread 0x3073b70 (LWP 5113)]
[New Thread 0x4e18b70 (LWP 5111)]
[New Thread 0x6483b70 (LWP 5109)]
[New Thread 0x1f7b70 (LWP 5108)]
0x00980422 in __kernel_vsyscall ()
  6 Thread 0x1f7b70 (LWP 5108)  0x00980422 in __kernel_vsyscall ()
  5 Thread 0x6483b70 (LWP 5109)  0x00980422 in __kernel_vsyscall ()
  4 Thread 0x4e18b70 (LWP 5111)  0x00980422 in __kernel_vsyscall ()
  3 Thread 0x3073b70 (LWP 5113)  0x00980422 in __kernel_vsyscall ()
  2 Thread 0x31d6b70 (LWP 5114)  0x00980422 in __kernel_vsyscall ()
* 1 Thread 0x9236f0 (LWP 5107)  0x00980422 in __kernel_vsyscall ()

Thread 6 (Thread 0x1f7b70 (LWP 5108)):
#0  0x00980422 in __kernel_vsyscall ()
#1  0x007ee466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a3658 in ?? ()
#3  0x007e680e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0x002ea7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0x6483b70 (LWP 5109)):
#0  0x00980422 in __kernel_vsyscall ()
#1  0x007ecf75 in sem_wait@@GLIBC_2.1 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0812bb29 in ?? ()
#3  0x0814f96c in ?? ()
#4  0x081bf9f2 in ?? ()
#5  0x081de055 in ?? ()
#6  0x007e680e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0x002ea7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0x4e18b70 (LWP 5111)):
#0  0x00980422 in __kernel_vsyscall ()
#1  0x007eae15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()
#3  0x081a84f4 in ?? ()
#4  0x081c3dcf in ?? ()
#5  0x0814c923 in ?? ()
#6  0x04b2d24d in ?? ()
#7  0x04b2cfad in ?? ()
#8  0x04b2cec1 in ?? ()
#9  0x00c86e30 in ?? ()
#10 0x0810e6a4 in mono_runtime_delegate_invoke ()
#11 0x0814f9d7 in ?? ()
#12 0x081bf9f2 in ?? ()
#13 0x081de055 in ?? ()
#14 0x007e680e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x002ea7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0x3073b70 (LWP 5113)):
#0  0x00980422 in __kernel_vsyscall ()
#1  0x007eae15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()
#3  0x081a84f4 in ?? ()
#4  0x081c3dcf in ?? ()
#5  0x0814b189 in ?? ()
#6  0x024b7770 in ?? ()
#7  0x024b766b in ?? ()
#8  0x024b7524 in ?? ()
#9  0x00c86e30 in ?? ()
#10 0x0810e6a4 in mono_runtime_delegate_invoke ()
#11 0x0814f9d7 in ?? ()
#12 0x081bf9f2 in ?? ()
#13 0x081de055 in ?? ()
#14 0x007e680e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x002ea7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0x31d6b70 (LWP 5114)):
#0  0x00980422 in __kernel_vsyscall ()
#1  0x007eae15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()
#3  0x081a84f4 in ?? ()
#4  0x081c3dcf in ?? ()
#5  0x0814b189 in ?? ()
#6  0x024b7770 in ?? ()
#7  0x024b766b in ?? ()
#8  0x024b7919 in ?? ()
#9  0x00c86e30 in ?? ()
#10 0x0810e6a4 in mono_runtime_delegate_invoke ()
#11 0x0814f9d7 in ?? ()
#12 0x081bf9f2 in ?? ()
#13 0x081de055 in ?? ()
#14 0x007e680e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x002ea7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0x9236f0 (LWP 5107)):
#0  0x00980422 in __kernel_vsyscall ()
#1  0x007edc8b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x080c89be in ?? ()
#3  0x080f4693 in ?? ()
#4  <signal handler called>
#5  0x00293006 in memcpy () from /lib/tls/i686/cmov/libc.so.6
#6  0x087736f8 in ?? ()
#7  0x0084aca6 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#8  0x008387e9 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#9  0x0081472f in gdk_draw_pixbuf () from /usr/lib/libgdk-x11-2.0.so.0
#10 0x0096ee67 in ?? () from /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
#11 0x009704f0 in ?? () from /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
#12 0x0096cd29 in ?? () from /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
#13 0x0096da49 in ?? () from /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
#14 0x0730598e in gtk_paint_shadow () from /usr/lib/libgtk-x11-2.0.so.0
#15 0x0730dca8 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#16 0x0096de95 in ?? () from /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
#17 0x0730544e in gtk_paint_box () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x0792b392 in ?? ()
#19 0x0792b2fe in ?? ()
#20 0x0792b092 in ?? ()
#21 0x0792a40d in ?? ()
#22 0x07929de2 in ?? ()
#23 0x0238a747 in ?? ()
#24 0x07287474 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#25 0x0075b6f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#26 0x0075cf98 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#27 0x0077249e in ?? () from /usr/lib/libgobject-2.0.so.0
#28 0x007739b8 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#29 0x00773fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#30 0x073a396e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#31 0x071f2683 in gtk_container_propagate_expose ()
   from /usr/lib/libgtk-x11-2.0.so.0
#32 0x071f26b1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#33 0x071bf9b5 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#34 0x071f31f4 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#35 0x071f44aa in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#36 0x07287474 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#37 0x0075b6f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#38 0x0075cf98 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#39 0x0077249e in ?? () from /usr/lib/libgobject-2.0.so.0
#40 0x007739b8 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#41 0x00773fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#42 0x073a396e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#43 0x071f2683 in gtk_container_propagate_expose ()
   from /usr/lib/libgtk-x11-2.0.so.0
#44 0x071f26b1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#45 0x072ae63d in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#46 0x071f31f4 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#47 0x071f44aa in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#48 0x072b129f in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#49 0x07287474 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#50 0x0075b6f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#51 0x0075cf98 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#52 0x0077249e in ?? () from /usr/lib/libgobject-2.0.so.0
#53 0x007739b8 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#54 0x00773fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#55 0x073a396e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#56 0x071f2683 in gtk_container_propagate_expose ()
   from /usr/lib/libgtk-x11-2.0.so.0
#57 0x071f26b1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#58 0x071bf9b5 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#59 0x071f31f4 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#60 0x071f44aa in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#61 0x07287474 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#62 0x0075b6f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#63 0x0075cf98 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#64 0x0077249e in ?? () from /usr/lib/libgobject-2.0.so.0
#65 0x007739b8 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#66 0x00773fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#67 0x073a396e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#68 0x071f2683 in gtk_container_propagate_expose ()
   from /usr/lib/libgtk-x11-2.0.so.0
#69 0x071f26b1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#70 0x071bf9b5 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#71 0x071f31f4 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#72 0x071f44aa in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#73 0x07287474 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#74 0x0075b6f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#75 0x0075cf98 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#76 0x0077249e in ?? () from /usr/lib/libgobject-2.0.so.0
#77 0x007739b8 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#78 0x00773fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#79 0x073a396e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#80 0x071f2683 in gtk_container_propagate_expose ()
   from /usr/lib/libgtk-x11-2.0.so.0
#81 0x071f26b1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#82 0x071bb82d in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#83 0x071f31f4 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#84 0x071f44aa in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#85 0x073be6a1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#86 0x07287474 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#87 0x0075b6f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#88 0x0075d072 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#89 0x0077249e in ?? () from /usr/lib/libgobject-2.0.so.0
#90 0x007739b8 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#91 0x00773fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#92 0x073a396e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#93 0x07281190 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#94 0x0083a1d4 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#95 0x0085d734 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#96 0x0083187f in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#97 0x00835a50 in gdk_window_process_updates ()
   from /usr/lib/libgdk-x11-2.0.so.0
#98 0x073be273 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#99 0x0076a9fc in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#100 0x0075b6f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#101 0x0075d072 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#102 0x0077249e in ?? () from /usr/lib/libgobject-2.0.so.0
#103 0x00773b2d in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#104 0x00773fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#105 0x071f331a in gtk_container_check_resize ()
   from /usr/lib/libgtk-x11-2.0.so.0
#106 0x071f3370 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#107 0x0080ff78 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#108 0x0016a0f1 in ?? () from /lib/libglib-2.0.so.0
#109 0x0016be78 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#110 0x0016f720 in ?? () from /lib/libglib-2.0.so.0
#111 0x0016fb8f in g_main_loop_run () from /lib/libglib-2.0.so.0
#112 0x07281419 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#113 0x04638c50 in ?? ()
#114 0x04638c13 in ?? ()
#115 0x00c79d57 in ?? ()
#116 0x00c78203 in ?? ()
#117 0x0811132b in mono_runtime_exec_main ()
#118 0x081134da in mono_runtime_run_main ()
#119 0x080b19bd in mono_main ()
#120 0x0805aba5 in ?? ()
#121 0x00234b56 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#122 0x0805aae1 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)
xxx-ubuntu:~$ 

```

---

### Post by andymorton on 2009-10-31
> **Isaacgallegos said:**
> F-spot tries to open but closes after a second. To see what was going on I executed it in the terminal:
```
isaac@isaac-desktop:~$ f-spot
[Info  07:07:57.516] Initializing DBus
[Info  07:07:57.630] Initializing Mono.Addins
[Info  07:07:57.780] Starting new FSpot server (f-spot 0.6.1.3)

** (f-spot:23110): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:23110): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:23110): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:23110): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:23110): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  07:07:58.563] Starting BeagleService
[Info  07:07:58.578] Hack for gnome-settings-daemon engaged

(f-spot:23110): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2915 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
isaac@isaac-desktop:~$ 
```
What happes for you?

The exact same thing happens to me too. :(

---

### Post by ~unknown on 2009-10-31
Works for me :o

---

### Post by Isaacgallegos on 2009-10-31
It's so strange. It's a hit or miss problem.

---

### Post by davedosch on 2009-10-31
My problem is it crashes as soon as I try to import any photos:

 f-spot
[Info  11:17:00.921] Initializing DBus
[Info  11:17:01.017] Initializing Mono.Addins
[Info  11:17:01.228] Starting new FSpot server (f-spot 0.6.1.4)

** (f-spot:5964): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:5964): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:5964): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:5964): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:5964): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  11:17:01.950] Starting BeagleService
[Info  11:17:01.987] Hack for gnome-settings-daemon engaged

(f-spot:5964): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 2400 error_code 1 request_code 135 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by mdshaver on 2009-10-31
mine also crashes immediately after start-up

---

### Post by murphdiggity on 2009-10-31
same here, same errors when running through terminal

---

### Post by Coge on 2009-10-31
Same here.

---

### Post by rifak on 2009-10-31
its working for me. i opened, imported, and played around with some photos. im not sure whats going wrong with the ones that are crashing. i have all desktop effects turned off, maybe having them on is causing it? (since its showing an X window error)...i dunno, just guessing

```
[switham@linux: ~]$ f-spot
[Info  15:47:20.495] Initializing DBus
[Info  15:47:20.670] Initializing Mono.Addins
[Info  15:47:22.472] Starting new FSpot server (f-spot 0.6.1.3)

** (f-spot:9504): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:9504): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:9504): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:9504): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:9504): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
cleanup context
cleanup context

(f-spot:9504): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
item ImportCommand+SourceItem
Stopping
[Info  15:48:54.782] Starting BeagleService
[Warn  15:48:54.786] Failed to set the web proxy settings
[Info  15:48:54.857] Hack for gnome-settings-daemon engaged

(f-spot:9504): Gdk-WARNING **: losing last reference to undestroyed window

[Info  15:49:42.627] Exiting

```

---

### Post by mdshaver on 2009-10-31
I simply switched to Fotoxx. I was never super fond of F-Spot anyway. No big loss if you ask me.

---

### Post by Isaacgallegos on 2009-10-31
I'm downloading Fotoxx. Thanks for the advice.

---

### Post by bibekdai on 2009-10-31
it works on my system (9.10)

---

### Post by des.matthewman on 2009-11-01
It's not working for me too. Anyone know if a bug has been raised?

Cheers

---

### Post by Martin_sensei on 2009-11-01
Doesn't work for me either:

```
[Info  14:30:34.099] Initializing DBus
[Info  14:30:34.346] Initializing Mono.Addins
[Info  14:30:34.640] Starting new FSpot server (f-spot 0.6.1.3)

** (f-spot:2769): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2769): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2769): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2769): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2769): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  14:30:35.991] Starting BeagleService
[Info  14:30:36.018] Hack for gnome-settings-daemon engaged

(f-spot:2769): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 3733 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
xxx@ubuntuman:/usr/lib/f-spot$ 

```

Anyone had this issue then resolved it?

---

### Post by Soul-Sing on 2009-11-01
you could do a regr.of f-spot via: [https://edge.launchpad.net/~mwhudson/+archive/ppa/+packages](https://edge.launchpad.net/~mwhudson/+archive/ppa/+packages)

---

### Post by ricardisimo on 2009-11-01
It's running without crashing (so far) but is not sending photos via evolution as it always has in the past. And of course [I'll get my Gnome-bashing in here] I can't edit *squat* in f-spot preferences, so I can't tell where the problem might be in f-spot, or if it's with the mail app instead.

P.S. - An email has gone out, but with zero photos attached.

---

### Post by kapkevin on 2009-11-02
Same problem. Here's the output:

> The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 4256 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by directhex on 2009-11-02
Which graphics driver are you all using?

---

### Post by soni1770 on 2009-11-02
works for me

---

### Post by Martin_sensei on 2009-11-03
> **directhex said:**
> Which graphics driver are you all using?

Latest NVIDIA drivers, available from the restricted hardware.

Cheers

Martin

---

### Post by jnew93 on 2009-11-03
Working fine for me. 9.10, ATI Proprietary Drivers, latest F-Spot version.

---

### Post by Xanthomryr on 2009-11-04
> **Martin_sensei said:**
> Latest NVIDIA drivers, available from the restricted hardware.

Cheers

Martin
Same here.

---

### Post by directhex on 2009-11-04
Apparently this might be caused by your GNOME theme - try changing to a different theme & see if it helps

---

### Post by Legendário on 2009-11-05
> **directhex said:**
> Apparently this might be caused by your GNOME theme - try changing to a different theme & see if it helps

It worked for me!!! :D

---

### Post by keithb on 2009-11-05
I was using New Wave theme and f-spot would not open. I changed back to Human theme and now it works.

---

### Post by Martin_sensei on 2009-11-06
> **keithb said:**
> I was using New Wave theme and f-spot would not open. I changed back to Human theme and now it works.

I am using new wave theme too.  Thats a shame, it was my favourite theme (that's why I chose it).  

Is there a way of tweaking the New Wave theme so F-Spot doesn't crash?

---

### Post by directhex on 2009-11-06
> **Martin_sensei said:**
> I am using new wave theme too.  Thats a shame, it was my favourite theme (that's why I chose it).  

Is there a way of tweaking the New Wave theme so F-Spot doesn't crash?

Try switching to a diff theme, run F-SPot, in the preferences window change F-Spot so it's hard-coded to something like Human, then switch back to New Wave for your system theme

---

### Post by DarthBrady on 2009-11-07
F-Spot doesn't work for me, either. Tries to open, and then closes immediately. 

Tried to open it with a terminal using both "f-spot", and "sudo f-spot", both give me the same error(s). Also suing the new wave theme. But as much as i want this program, I am not changing my theme back to that ugly orange human theme.

```

$ f-spot
[Info  19:34:06.195] Initializing DBus
[Info  19:34:06.380] Initializing Mono.Addins
[Info  19:34:06.725] Starting new FSpot server (f-spot 0.6.1.4)

** (f-spot:4791): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:4791): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:4791): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:4791): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:4791): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  19:34:08.078] Starting BeagleService
[Info  19:34:08.102] Hack for gnome-settings-daemon engaged

(f-spot:4791): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2939 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by directhex on 2009-11-08
> **DarthBrady said:**
> F-Spot doesn't work for me, either. Tries to open, and then closes immediately. 

Tried to open it with a terminal using both "f-spot", and "sudo f-spot", both give me the same error(s). Also suing the new wave theme. But as much as i want this program, I am not changing my theme back to that ugly orange human theme.

```

$ f-spot
[Info  19:34:06.195] Initializing DBus
[Info  19:34:06.380] Initializing Mono.Addins
[Info  19:34:06.725] Starting new FSpot server (f-spot 0.6.1.4)

** (f-spot:4791): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:4791): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:4791): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:4791): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:4791): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  19:34:08.078] Starting BeagleService
[Info  19:34:08.102] Hack for gnome-settings-daemon engaged

(f-spot:4791): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2939 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

New Wave is bugged. You can set a specific override in F-Spot, in the Preferences window, to avoid the problem - but you need to TEMPORARILY switch your system theme to something else, to allow F-Spot to run, to allow you to set F-Spot to a specific non-New-Wave theme (rather than the system theme) before setting the system theme back to New Wave.

---

### Post by crazy ivan on 2009-11-12
Using "Clearlooks" everything starts fine.. But the very comfortable "send email" function does not work + it crashes when you try "print preview"

Any solutions to the send email dilemma??

---

### Post by crazy ivan on 2009-11-12
Now it just prints the gnome-photo-icon!!!! when I try to print a photo!!! enough is enough.. Removed this buggy piece of thought-to-be <standard software>.

Downloaded the jaunty version and tried to install it (sudo dpkg -i), didn't succeed because of the following missing packages:
* libmono0
* libflickrnet2.1.5-cil
* libgconf2.24-cil
* libgnome-vfs2.24-cil

```
 sudo apt-get install libmono0 
```

Got libflickrnet2.1.5-cil from jaunty repository, no problems installing it

For the two last ones it gets a little more intricate: the first post in
[http://ubuntuforums.org/showthread.php?p=8304958]("http://ubuntuforums.org/showthread.php?t=1305248") shows how you can change package dependencies for a package.. Now within the newly obtained "common/DEBIAN/control" file I changed 

```
libgconf2.24-cil > libgconf2.0-cil
libgnome-vfs2.24-cil >  libgnome-vfs2.0-cil
```

And now install works fine :p, welcome back to the old version...

Result: Finally I can print photos again!
Problem: Still no luck with "send email" :( 

Really some tough times with this upgrade

---

### Post by crazy ivan on 2009-11-12
.. forgot one more problem: it killed my f-spot database (even though I had a backup; replacing "~/.gconf/apps/f-spot" did not bring it back). 

Not too bad.. since I had them all in one folder.. but still messed up "imports" and so forth.

---

### Post by rolandjo on 2009-11-13
Nope, for me crashes immediately after start-up,
I get just this for a few milliseconds
 [[IMG]http://img33.imageshack.us/img33/6697/screenshotig.th.png[/IMG]]("http://img33.imageshack.us/i/screenshotig.png/")

```
roland@roland-laptop:~$ sudo f-spot
** No session dbus found. Starting one **
[Info  11:28:40.543] Initializing DBus
[Info  11:28:41.147] Initializing Mono.Addins
[Info  11:28:42.139] Starting new FSpot server (f-spot 0.6.1.5)

** (f-spot:28781): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:28781): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:28781): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:28781): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:28781): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  11:28:45.867] Starting BeagleService
[Info  11:28:45.972] Hack for gnome-settings-daemon engaged

(f-spot:28781): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2925 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by directhex on 2009-11-13
> **rolandjo said:**
> Nope, for me crashes immediately after start-up,
I get just this for a few milliseconds
 [[IMG]http://img33.imageshack.us/img33/6697/screenshotig.th.png[/IMG]]("http://img33.imageshack.us/i/screenshotig.png/")

```
roland@roland-laptop:~$ sudo f-spot
** No session dbus found. Starting one **
[Info  11:28:40.543] Initializing DBus
[Info  11:28:41.147] Initializing Mono.Addins
[Info  11:28:42.139] Starting new FSpot server (f-spot 0.6.1.5)

** (f-spot:28781): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:28781): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:28781): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:28781): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:28781): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  11:28:45.867] Starting BeagleService
[Info  11:28:45.972] Hack for gnome-settings-daemon engaged

(f-spot:28781): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2925 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

The GTK theme is bugged!

---

### Post by necromonger on 2009-11-13
No problem for me.

---

### Post by Paul41 on 2009-11-13
Mine is OK

---

### Post by ricardisimo on 2009-12-11
> **crazy ivan said:**
> Problem: Still no luck with "send email" :( 

I think I may have figured it out... Go to Preferred Applications, and for email see if it says Evolution, Mozilla Thunderbird, or simply "Custom". Mine was set to "Custom". I first tried Thunderbird (which has it's own problems sending photos by email... don't want to get into that) then i switched to Evolution.

Voilá! Custom doesn't cut it. You have to choose Evolution, rather than having the system default to it, at least in this case.

---

### Post by crazy ivan on 2010-01-08
Thanks for your hint ricardisimo:
It *really does* matter, what you select as preferred application.. Now I'm able to send them with Thunderbird again.. Getting this nasty "Sending of message failed. Unable to open temporary file .." error again, when trying to send compressed pictures. Due to too early deletion of the files by f-spot.. Got the solution from the answer to YOUR ;) question in

[http://ubuntuforums.org/archive/index.php/t-988418.html]("http://ubuntuforums.org/archive/index.php/t-988418.html")

as for the version before.. Only this time I had to CREATE the gconf-editor entry 

/apps/f-spot/export/email/delete_timeout_seconds 2400

..to me f-spot is the *enfant terrible* of GNOME :-k

---

### Post by bluestar14 on 2010-01-08
mines works fine, try running update manager

---

### Post by Slowjoe on 2010-01-10
I was having the same problem, and changing away from the New Wave theme allowed F-spot to open for me.  I've yet to see if it works when I change back.

---


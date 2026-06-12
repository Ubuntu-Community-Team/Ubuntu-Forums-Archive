---
title: "Issue using gdb, cannot get back to 'gdb' prompt after reproducing crash, or Ctrl+C"
date: 2011-02-26
forum: General Help
---

### Post by mr_luksom on 2011-02-26
Hi,

I'm using gdb to try and get a backtrace on nautilus to take a look at an unexpected result using nautilus, and I'm having trouble using the gdb tool.

After attaching the pid to gdb using the 'attach <pid>' command, and continuing the program to interact with it and produce the bug, I then cannot get back to the gdb prompt to perform the backtrace. I get stuck here:

Any idea what I am doing wrong?

```

Reading symbols from /usr/lib/gio/modules/libgioremote-volume-monitor.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gio/modules/libgioremote-volume-monitor.so
Reading symbols from /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-jpeg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
Reading symbols from /usr/lib/libjpeg.so.62...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/pango/1.6.0/modules/pango-basic-fc.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
Reading symbols from /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
Reading symbols from /usr/lib/libibus.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libibus.so.2
Reading symbols from /usr/lib/gio/modules/libgiogconf.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gio/modules/libgiogconf.so
Reading symbols from /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
0x00007f5c2f361203 in poll () from /lib/libc.so.6
(gdb) continue
Continuing.
^C^C

```

---


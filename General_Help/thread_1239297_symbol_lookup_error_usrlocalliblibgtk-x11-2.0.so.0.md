---
title: "symbol lookup error: /usr/local/lib/libgtk-x11-2.0.so.0: undefined symbol: gdk_screen"
date: 2009-08-13
forum: General Help
---

### Post by favrik on 2009-08-13
Hello,

I just updated my Ubuntu 8.10 64bit version, and I cannot start gtk applications due to the following error:

symbol lookup error: /usr/local/lib/libgtk-x11-2.0.so.0: undefined symbol: gdk_screen_get_default_colormap

I already did an ldd /usr/bin/nm-applet | grep libgtk and everything looked normal (no "not found" errors).

Any hint?


Thanks,

Favio

---

### Post by favrik on 2009-08-13
Plese delete this thread, I found out that my system has RAM issues, so it somehow corrupted that part of the system.

Sorry for the trouble. :)

---


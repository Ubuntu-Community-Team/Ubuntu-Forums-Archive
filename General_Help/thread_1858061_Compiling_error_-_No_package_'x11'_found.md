---
title: "Compiling error - No package 'x11' found"
date: 2011-10-11
forum: General Help
---

### Post by newgen23 on 2011-10-11
pkg-config --libs X11
Package X11 was not found in the pkg-config search path.
Perhaps you should add the directory containing `X11.pc'
to the PKG_CONFIG_PATH environment variable
No package 'X11' found

libX11.so should be in /usr/lib, while X11.pc should be in /usr/lib/pkg-config.

Unfortunatly, ubuntu in the amd64 version installs it to:
 /usr/lib/x86_64-linux-gnu/
and 
 /usr/lib/x86_64-linux-gnu/pkg-config

and can therefore not be found. How do I fix this BUG? Setting PKG_CONFIG_PATH to 
PKG_CONFIG_PATH=" /usr/lib/x86_64-linux-gnu/pkg-config"
or 
PKG_CONFIG_PATH=" /usr/lib/x86_64-linux-gnu/"
does not work...

---

### Post by oldos2er on 2011-10-11
Post moved to its own thread, please don't hijack other users' posts.

Please give more details of your problem, which program are you trying to compile, which version of Ubuntu are you using, etc.

---

### Post by gmargo on 2011-10-11
> **newgen23 said:**
> pkg-config --libs X11
Package X11 was not found

Try lower case; use "x11" instead of "X11".
```

$ pkg-config --libs x11
-lX11  

$ dpkg -S /usr/lib/pkgconfig/x11.pc
libx11-dev: /usr/lib/pkgconfig/x11.pc

```

---


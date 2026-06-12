---
title: "Can't compile any Gtk+ at all after update to Natty."
date: 2011-05-14
forum: General Help
---

### Post by stravant on 2011-05-14
After updating to natty I cannot compile any Gtk+ code, no matter what I do I get linker errors. This is not a problem with the way I'm building it, I'm familiar with the correct usage of pkg-config.

Even this code will fail to link:
```

#include <gtk/gtk.h>
int main(int argc, char** argv) {
    gkt_init(&argc, &argv);
    gtk_main();
}

```
(Compiled with the standard commands to compile Gtk+ stuff)

I always get the following output:
```

/usr/lib/libgtk-x11-2.0.so: undefined reference to `g_source_get_time'
/usr/lib/libgtk-x11-2.0.so: undefined reference to `g_get_monotonic_time'
/usr/lib/libgdk_pixbuf-2.0.so: undefined reference to `g_simple_async_result_take_error'
/usr/lib/libgdk-x11-2.0.so: undefined reference to `g_slist_free_full'

```

I've already looked at the similar problems which GNOME Shell is having, and I've tried the solutions there; none of them have any effect. No-one else who I've talked to has this problem, so it must be something screwed up with the libraries on my system, but I have no idea how to go about fixing it.

---

### Post by stravant on 2011-05-14
Further information which may be useful:
```

stravant@stravant-desktop:~$ ldd /usr/lib/libgtk-x11-2.0.so | grep "glib"	
libglib-2.0.so.0 => /lib/i386-linux-gnu/libglib-2.0.so.0 (0xb6eb9000)
stravant@stravant-desktop:~$ objdump -T /lib/i386-linux-gnu/libglib-2.0.so.0 | grep "g_source_get_time"
00042230 g    DF .text	00000166  Base        g_source_get_time

```

It appears that g_source_get_time is there as a dynamic symbol, and the file it's in is listed as a dependency in the file the linker complains about. (I've only looked libgtk-x11 so far, however I would imagine it's the same story for the others) Why would the linker even care what the .so's dependencies are in the first place / could this be a problem with dynamic vs static linking of a symbol?

---

### Post by stravant on 2011-05-14
As a last resort I tried building and installing the latest glib from git.... and it magically fixed it.

I have no idea how it fixed it, but if you have a similar problem try that.

---


---
title: "gtk problem"
date: 2006-02-09
forum: General Help
---

### Post by Infestdead on 2006-02-09
Whenever I try to compile something from source (for example - gFTP, sylpheed) that requiers gtk I get this message:
```

checking for gtk+-2.0 >= 2.2.0 gdk-2.0 gdk-pixbuf-xlib-2.0... 
Package gtk+-2.0 was not found in the pkg-config search path. 
Perhaps you should add the directory containing `gtk+-2.0.pc' 
to the PKG_CONFIG_PATH environment variable 

No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.2.0 
gdk-2.0 gdk-pixbuf-xlib-2.0) not met; 
consider adjusting the PKG_CONFIG_PATH environment variable if your libraries
 are in a nonstandard prefix so pkg-config can find them

```

What do I need to install or do? 
I tried to search for the gtk+-2.0.pc file, but didn't find it,
PKG_CONFIG_PATH="/usr/lib/pkgconfig" && export PKG_CONFIG_PATH also didn't work.
Tried to apt-get install gtk*, or gtk+-2.0, or gtk2.0 or any combination, but the problem persists.
So what do you suggest?

Thank you in advance ;)

---

### Post by queenorych on 2006-02-09
Dumb Q.  Do you have the gtk-2.0-dev package installed?

---

### Post by Infestdead on 2006-02-09
Yes, libgtk2.0-dev - got it. Problem persists.

---


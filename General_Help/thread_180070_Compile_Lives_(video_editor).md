---
title: "Compile Lives (video editor)"
date: 2006-05-21
forum: General Help
---

### Post by meditolafuga on 2006-05-21
Hi to all !

I try to compile lives to my ubuntu brezzy ! ([http://lives.sourceforge.net/](http://lives.sourceforge.net/))

this is my problem :

> 

...cut...

checking whether ln -s works... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.4.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GTK_CFLAGS and GTK_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.


Thanks for helps !!

Marco

---

### Post by ob211 on 2006-05-21
Did you install the gtk+ development libraries? They should be called something like gtk+-dev, in your package manager.

/edit The package name is libgtk2.0-dev.

---

### Post by claydoh on 2006-05-21
If you look in the downloads section of the LiVES site, there is a deb repository available, it is -pre2, and the current is -pre3, however, but that should not be a big issue

---


---
title: "Problems Installing GTK+-2.18.7"
date: 2010-02-19
forum: General Help
---

### Post by timetraveller85 on 2010-02-19
Hi,

I am trying to install GTK-2.18.7 to get the latest release of rhythmbox. I've installed the required dependencies- glib-2.22.4 and pango-1.26.2.

However, when i perform ./configure in the gtk-2.18.7 directory, I get the following error:

[B]Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.[/B]

I checked other forums and did this:
**export PKG_CONFIG_PATH=/usr/lib/pkgconfi**g

Then when I reinstalled Glib-2.22.4, and then perform ./configure in the gtk+ directory, it won't even recognize the newly installed glib and gives me this:

[B]Requested 'glib-2.0 >= 2.21.3' but version of GLib is 2.18.2

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/B]

I must admit I don't what in the world export PKG_CONFIG_PATH does. I read somewhere that it's like a repository of the list of directories pointing to files needed for installation and what not.** And I do not know where GTK+ gets installed.**

**Please help!!!**

---


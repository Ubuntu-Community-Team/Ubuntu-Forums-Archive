---
title: "GLIB - cannot find..."
date: 2006-02-22
forum: General Help
---

### Post by jansenh on 2006-02-22
Hi group

I am trying to install gFTP; it requires GLIB 1.2.3 or higher. The only package I could find is libglib2.0-dev, which I installed. But the config-script for gFTP still complaines and tells me:

[SIZE="1"]checking for GLIB - version >= 1.2.3... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: gFTP needs GLIB 1.2.3 or higher[/SIZE]

Where and how do I find these paths ... ?

regards, Henning

---

### Post by carlosqueso on 2006-02-22
you may need the libglib1.2-dev package The two should coexist, but gftp is looking for a 1.x version of libglib.

---


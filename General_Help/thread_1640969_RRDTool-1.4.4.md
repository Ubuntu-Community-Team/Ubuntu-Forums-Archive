---
title: "RRDTool-1.4.4"
date: 2010-12-08
forum: General Help
---

### Post by Drum2000 on 2010-12-08
I am trying to run configure for RRDTool-1.4.4 but I keep getting the following error::

checking for pango_cairo_context_set_font_options in -lpangocairo-1.0... no
checking for pkg-config... (cached) pkg-config
checking for pango_cairo_context_set_font_options in -lpangocairo-1.0... no
configure: WARNING:
----------------------------------------------------------------------------
* I could not find a working copy of pangocairo. Check config.log for hints on why
  this is the case. Maybe you need to set LDFLAGS and CPPFLAGS appropriately
  so that compiler and the linker can find libpangocairo-1.0 and its header files. If
  you have not installed pangocairo, you can get it either from its original home on

     [http://ftp.gnome.org/pub/GNOME/sources/pango/1.17](http://ftp.gnome.org/pub/GNOME/sources/pango/1.17)

  You can find also find an archive copy on

     [http://oss.oetiker.ch/rrdtool/pub/libs](http://oss.oetiker.ch/rrdtool/pub/libs)

  The last tested version of pangocairo is 1.17.

       LIBS=-lglib-2.0 -lcairo -lcairo -lcairo -lm  -lcairo -lpng12   -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
   LDFLAGS= -L/usr/local/lib     -L/usr/local/lib
  CPPFLAGS= -I/usr/local/include/cairo -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/include/pixman-1 -I/usr/local/include/freetype2 -I/usr/include/libpng12   -I/usr/local/include/pango-1.0 -I/usr/local/include/cairo -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/include/pixman-1 -I/usr/local/include/freetype2 -I/usr/include/libpng12

----------------------------------------------------------------------------

I have installed all the dependencies, including pango-1.17.0, and cairo-1.10.0.

---


---
title: "Can OpenRPG be installed on Ubuntu  12.04?"
date: 2012-06-24
forum: General Help
---

### Post by ShaggyShaggs on 2012-06-24
I'm trying to move into a new (to me) computer and I can't find any working way to install the program, let alone run it.  It seems to want WxPython which as far as I can tell is obsolete, but I have no idea how to work around it.  Any information I come up with searching also seems to be obsolete and no longer usable.  Is it even possible to use the program with newer Ubuntu versions?

This is the last thing tying me to that ancient desktop and I'd really like to move on.

---

### Post by idoitprone on 2012-06-24
> **ShaggyShaggs said:**
> I'm trying to move into a new (to me) computer and I can't find any working way to install the program, let alone run it.  It seems to want WxPython which as far as I can tell is obsolete, but I have no idea how to work around it.  Any information I come up with searching also seems to be obsolete and no longer usable.  Is it even possible to use the program with newer Ubuntu versions?

This is the last thing tying me to that ancient desktop and I'd really like to move on.

i only found it until natty

[https://launchpad.net/openrpg/trunk](https://launchpad.net/openrpg/trunk)

i guess you have to compile it yourself 
[http://sourceforge.net/projects/openrpg/support](http://sourceforge.net/projects/openrpg/support)

---

### Post by ShaggyShaggs on 2012-06-24
So for that I gotta compile wxpython, and for that I gotta compile wxwidgets, and I'm running into probs even getting wxwidgets compiled.

sudo ./configure in ~/wxWidgets-2.8.12 dies before finishing and tells me

*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.

config.log contents are [linked here](http://pastebin.com/N0Md108v).

I'm lost... I don't know what I'm doing.

---

### Post by idoitprone on 2012-06-24
> **ShaggyShaggs said:**
> So for that I gotta compile wxpython, and for that I gotta compile wxwidgets, and I'm running into probs even getting wxwidgets compiled.

sudo ./configure in ~/wxWidgets-2.8.12 dies before finishing and tells me

*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.

config.log contents are [linked here](http://pastebin.com/N0Md108v).

I'm lost... I don't know what I'm doing.

README?
INSTALL?

you need to have those developers packages
usually they should end with dev so you can compile your programed

---


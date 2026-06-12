---
title: "Boxee Errors While Processing"
date: 2010-10-11
forum: General Help
---

### Post by MaleBag on 2010-10-11
Hey guys,

I just recently installed 10.10 and now I'm trying to install boxee from a .deb file the following is the result.


dave@dave-laptop:~/Desktop$ sudo dpkg --install boxee-0.9.22.13692.x86_64.deb
(Reading database ... 170826 files and directories currently installed.)
Preparing to replace boxee 0.9.22.13692 (using boxee-0.9.22.13692.x86_64.deb) ...
Unpacking replacement boxee ...
dpkg: dependency problems prevent configuration of boxee:
 boxee depends on libglew1.5; however:
  Package libglew1.5 is not installed.
 boxee depends on liblzo2-2; however:
  Package liblzo2-2 is not installed.
 boxee depends on libsdl-gfx1.2-4; however:
  Package libsdl-gfx1.2-4 is not installed.
 boxee depends on libmad0; however:
  Package libmad0 is not installed.
 boxee depends on libtre4 | libtre5; however:
  Package libtre4 is not installed.
  Package libtre5 is not installed.
 boxee depends on libxmlrpc-c3; however:
  Package libxmlrpc-c3 is not installed.
 boxee depends on xsel; however:
  Package xsel is not installed.
dpkg: error processing boxee (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 boxee


Boxee appears in my application drop down and says its starting up but then just disappears.

Any ideas what could be wrong?  Thanks 

Dave

---

### Post by GeoPirate on 2010-10-11
There is an error with the deb from the boxee site it won't accept a newer package of one of the dependencies.  Someone made a modified deb that will work.

[http://forums.boxee.tv/showthread.php?t=19973&highlight=libdirectfb](http://forums.boxee.tv/showthread.php?t=19973&highlight=libdirectfb)

---


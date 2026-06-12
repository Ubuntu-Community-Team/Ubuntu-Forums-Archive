---
title: "gnome phone manager - synaptic - 64bit"
date: 2006-03-17
forum: General Help
---

### Post by kingmonkey on 2006-03-17
Hello,

Trying to install gnome-phone-manager but it says:

gnome-phone-manager:
 Depends: libbtctl1 (>=0.4.1) but it is not installable

libbtct2 is installed on my system which replaces libbtct1.


How do I go about getting it to install?

Thank you in advance.

---

### Post by dumbbeatnix on 2006-03-24
Try creating a link from the library that it is trying to find, for example:

ln -s libtcl2 libtcl1

This may not  help, but if you know exactly what library like:

ln -s libtcl.2.0.0.so.0 libtcl.0.4.1.so.0

It would help.  This is all gobbly gook, so if anyone has anything to add please feel free to.

Its very hard for windows users to get the hang of linking.  Believe me though it works better than having hardware shutdown and windows to keep on bluing on.....
:D :D :D

---


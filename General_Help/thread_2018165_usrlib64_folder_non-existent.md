---
title: "usr/lib64 folder non-existent"
date: 2012-07-06
forum: General Help
---

### Post by kjmitch on 2012-07-06
:confused:

I'm trying to install Autodesk Maya 2013 and went to create a symbolic link with the following command:

 ln -s /usr/lib64/x86_64-linux-gnu/libtiff.so.4.3.3 /usr/lib/libtiff.so.3

That's when I had a look for the /usr/lib64 folder just to make sure everything would go smoothly.........nope, nada, nothing. Help!

---

### Post by kjmitch on 2012-07-06
I seem to have located a similar file in /usr/lib/x86_64-linux-gnu libtiff.so.4.3.4

This is what I'm getting now:

/usr/autodesk/maya2013-x64/bin/maya.bin: error while loading shared libraries: libfam.so.0: cannot open shared object file: No such file or directory

---


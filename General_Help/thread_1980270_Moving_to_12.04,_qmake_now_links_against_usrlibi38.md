---
title: "Moving to 12.04, qmake now links against /usr/lib/i386-linux-gnu"
date: 2012-05-14
forum: General Help
---

### Post by strattonbrazil on 2012-05-14
After upgrading to 12.04, my Qt builds no longer complete because qmake is now linking against /usr/lib/i386-linux-gnu and don't include libraries in /usr/lib like assimp.  

/usr/bin/ld: cannot find -lassimp

Running qmake --version:

QMake version 2.01a
Using Qt version 4.8.1 in /usr/lib/i386-linux-gnu

I assume that due to this multiarch change with libs in different dirs, I can't easily link against one directory anymore and have it pull every file correctly.  Can I do anything besides just hardcode -L/usr/lib into my qmake build?  

How are build systems supposed to distinguish between the two directories?

---


---
title: "problem with compiling"
date: 2011-07-21
forum: General Help
---

### Post by blueeyedlion on 2011-07-21
when I try to compile a program that uses SFML with g++, this appears:

```
/usr/local/include/SFML/Window/OpenGL.hpp:47:23: fatal error: GL/gl.h: No such file or directory
```

How can I fix it?

---

### Post by Mr. Shannon on 2011-07-21
I still haven't got into SFML yet but I think installing **freeglut** is the easiest way to pull in the files it's looking for.  So in a terminal just type:
```
sudo apt-get install freeglut3 freeglut3-dev freeglut3-dbg
```
You might be able to leave off the last one but I was never sure if you need the dbg symbols to debug your own programs that use the library or not.

---

### Post by blueeyedlion on 2011-07-22
Thanks, that worked

---


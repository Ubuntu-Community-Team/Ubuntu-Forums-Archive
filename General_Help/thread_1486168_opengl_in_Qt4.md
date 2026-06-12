---
title: "opengl in Qt4"
date: 2010-05-17
forum: General Help
---

### Post by orky7 on 2010-05-17
hi i am compiling a code given at [http://lab.bachem-it.com/opengl/redbook/](http://lab.bachem-it.com/opengl/redbook/) actually i tried the first two codes(polygon and square transformation) but a 3 error occurred in my Qt creator with Qt 4.5 
1.error: using typedef-name ‘Window’ after ‘class’.
2. /usr/include/X11/X.h:101: error: ‘Window’ has a previous declaration here
3./home/orky/Desktop/draw/main.cpp:29: error: request for member ‘show’ in ‘window’, which is of non-class type ‘Window’.

i think they are correct codes but do not know why the error occurred any help will be appreciated.

---

### Post by orky7 on 2010-05-17
problem solved i was missing libglu1-mesa-dev library

---


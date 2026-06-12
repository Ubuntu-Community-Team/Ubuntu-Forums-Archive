---
title: "gnome.h"
date: 2010-11-02
forum: General Help
---

### Post by i.c on 2010-11-02
Hi!
There is a problem...
After building a project with glade-2, when i do make i got the following error:
```
main.c:11: fatal error: gnome.h: &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;
```
Because I live in Russia.
English Translate:
```
main.c:11: fatal error: gnome.h: no such file or directory
```
I installed "libgnomeui-dev". It did not help...

---

### Post by matt_symes on 2010-11-02
Hi 

How are you building it? Is it a project you have written. Does it use a make file?

You can tell GCC where to look for include files and libraries using switches amongst other things

[http://www.network-theory.co.uk/docs/gccintro/gccintro_21.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_21.html)

Kind regards

---

### Post by i.c on 2010-11-02
I am building it:
```
cd Projects/MyProg
./autogen.sh
make

```

---

### Post by gmargo on 2010-11-02
Add something like this to your makefile to add the right include and linker options.

```

CFLAGS+=$(shell pkg-config --cflags libgnomeui-2.0)
LDLIBS+=$(shell pkg-config --libs libgnomeui-2.0)

```

---

### Post by i.c on 2010-11-02
Not working.

---

### Post by i.c on 2010-11-02
Thanks!
[http://ubuntuforums.org/showthread.php?t=295105](http://ubuntuforums.org/showthread.php?t=295105)

---


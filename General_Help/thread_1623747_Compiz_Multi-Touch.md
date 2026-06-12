---
title: "Compiz Multi-Touch"
date: 2010-11-17
forum: General Help
---

### Post by superzanti on 2010-11-17
I'm trying to get this to work, and it will make, and make install, just fine, but it doesn't work. As soon as the plugin receives any TUIO input, all of compiz crashes. So, I've been trying to fix some of the compiling errors. Do you think you could help?

The source is here if you want to look:
[http://code.google.com/p/touchpy/source/browse/trunk/multitouch-compiz-plugin/multitouch.c?r=82](http://code.google.com/p/touchpy/source/browse/trunk/multitouch-compiz-plugin/multitouch.c?r=82)

And I'm getting this error:
```
superzanti@superzanti:~/Documents/compiz-multitouch$ sudo make
convert   : multitouch.xml.in -> build/multitouch.xml
bcop'ing  : build/multitouch.xml -> build/multitouch_options.h
bcop'ing  : build/multitouch.xml -> build/multitouch_options.c
schema    : build/multitouch.xml -> build/compiz-multitouch.schema
compiling : multitouch.c -> build/multitouch.lo
multitouch.c: In function ‘makefire’:
multitouch.c:579: warning: unused variable ‘md’
multitouch.c: In function ‘gesture_handler’:
multitouch.c:735: warning: cast from pointer to integer of different size
multitouch.c:735: warning: passing argument 2 of ‘compAddTimeout’ makes integer from pointer without a cast
/usr/include/compiz/compiz.h:123: note: expected ‘int’ but argument is of type ‘void *’
multitouch.c:735: warning: passing argument 3 of ‘compAddTimeout’ makes pointer from integer without a cast
/usr/include/compiz/compiz.h:123: note: expected ‘CallBackProc’ but argument is of type ‘int’
multitouch.c:737: warning: cast from pointer to integer of different size
multitouch.c:737: warning: passing argument 2 of ‘compAddTimeout’ makes integer from pointer without a cast
/usr/include/compiz/compiz.h:123: note: expected ‘int’ but argument is of type ‘void *’
multitouch.c:737: warning: passing argument 3 of ‘compAddTimeout’ makes pointer from integer without a cast
/usr/include/compiz/compiz.h:123: note: expected ‘CallBackProc’ but argument is of type ‘int’
multitouch.c:738: warning: cast from pointer to integer of different size
multitouch.c:738: warning: passing argument 2 of ‘compAddTimeout’ makes integer from pointer without a cast
/usr/include/compiz/compiz.h:123: note: expected ‘int’ but argument is of type ‘void *’
multitouch.c:738: warning: passing argument 3 of ‘compAddTimeout’ makes pointer from integer without a cast
/usr/include/compiz/compiz.h:123: note: expected ‘CallBackProc’ but argument is of type ‘int’
multitouch.c:762: warning: cast to pointer from integer of different size
multitouch.c:957: warning: cast to pointer from integer of different size
multitouch.c:962: warning: cast from pointer to integer of different size
multitouch.c:962: warning: passing argument 2 of ‘compAddTimeout’ makes integer from pointer without a cast
/usr/include/compiz/compiz.h:123: note: expected ‘int’ but argument is of type ‘void *’
multitouch.c:962: warning: passing argument 3 of ‘compAddTimeout’ makes pointer from integer without a cast
/usr/include/compiz/compiz.h:123: note: expected ‘CallBackProc’ but argument is of type ‘int’
multitouch.c:975: warning: cast from pointer to integer of different size
multitouch.c:985: warning: cast to pointer from integer of different size
multitouch.c:1000: warning: cast from pointer to integer of different size
multitouch.c:1000: warning: passing argument 2 of ‘compAddTimeout’ makes integer from pointer without a cast
/usr/include/compiz/compiz.h:123: note: expected ‘int’ but argument is of type ‘void *’
multitouch.c:1000: warning: passing argument 3 of ‘compAddTimeout’ makes pointer from integer without a cast
/usr/include/compiz/compiz.h:123: note: expected ‘CallBackProc’ but argument is of type ‘int’
compiling : multitouch.c -> build/multitouch.lo
compiling : build/multitouch_options.c -> build/multitouch_options.lo
linking   : build/libmultitouch.la
superzanti@superzanti:~/Documents/compiz-multitouch$ 

```

---

### Post by dr_james2k on 2010-11-17
Hi, as discussed here: [http://nuigroup.com/forums/viewthread/11237/](http://nuigroup.com/forums/viewthread/11237/)
the plugin has been updated to work with 64 bit ubuntu and to correct the compilation warning messages.  The latest version and its instructions can be found here: [http://jamcnaughton.wordpress.com/2010/05/20/how-to-install-the-compiz-multi-touch-plugin/](http://jamcnaughton.wordpress.com/2010/05/20/how-to-install-the-compiz-multi-touch-plugin/)

---


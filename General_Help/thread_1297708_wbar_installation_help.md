---
title: "wbar installation help"
date: 2009-10-22
forum: General Help
---

### Post by bashphoenux on 2009-10-22
i followed the following instructions for installing wbar

$ sudo apt-get install libimlib2-dev


$ wget [http://www.tecapli.com.ar/rodolfo/wbar-1.3.3.tbz2](http://www.tecapli.com.ar/rodolfo/wbar-1.3.3.tbz2)
$ tar xjf wbar-1.3.3.tbz2


3. Change to the extracted folder and make
$ cd wbar-1.3.3/
$ make
 i get this error
```
g++ `imlib2-config --cflags` -Wall -O2    -c -o XWin.o XWin.cc
XWin.cc: In constructor ‘XWin::XWin(int, int, int, int)’:
XWin.cc:33: warning: deprecated conversion from string constant to ‘char*’
XWin.cc:33: warning: deprecated conversion from string constant to ‘char*’
g++ `imlib2-config --cflags` -Wall -O2    -c -o Icon.o Icon.cc
g++ `imlib2-config --cflags` -Wall -O2    -c -o Bar.o Bar.cc
g++ `imlib2-config --cflags` -Wall -O2    -c -o IconLoader.o IconLoader.cc
IconLoader.cc: In constructor ‘IconLoader::IconLoader(const char*)’:
IconLoader.cc:20: error: ‘getenv’ was not declared in this scope
make: *** [IconLoader.o] Error 1

```what do i do ???

---

### Post by bwang on 2009-10-22
Try the .deb file here: [http://code.google.com/p/wbar/downloads/list](http://code.google.com/p/wbar/downloads/list)

---

### Post by bashphoenux on 2009-10-22
never mind i got the wbar working ...
downloaded the .DEB file and installed it :)
thanks

---


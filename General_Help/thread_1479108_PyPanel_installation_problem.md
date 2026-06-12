---
title: "PyPanel installation problem"
date: 2010-05-10
forum: General Help
---

### Post by th5th on 2010-05-10
With the arrival of my new netbook (Samsung NB30), I have been playing with a Lucid Lynx minimal install from mini.iso. Most things have been working swimmingly (had to install grub again because the first time the installer plonked it on the usb drive, had to download a firmware update for the wireless chip), and I have Openbox installed and running.

I would like to install PyPanel now, and got the last tarball from Sourceforge (2.4). I installed Imlib2 and the dev package which seem to be required, and python-xlib. The setup.py script needed some fixing to see my libimlib2 files but that worked out.

Problem is when I run

```
python setup.py install
```

as instructed in README I get the following errors:

```
th5th@anvil:~/PyPanel-2.4$ python setup.py install
running install
running build
running build_ext
building 'ppmodule' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -DHAVE_XFT=1 -DIMLIB2_FIX=1 -I/usr/X11R6/include -I/usr/include/freetype2 -I/usr/include/python2.6 -c ppmodule.c -o build/temp.linux-i686-2.6/ppmodule.o -Wall
ppmodule.c:21:20: error: Python.h: No such file or directory
ppmodule.c:37:25: error: X11/Xft/Xft.h: No such file or directory
ppmodule.c:40: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ppmodule.c:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ppmodule.c:53: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ppmodule.c:68: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ppmodule.c:123: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ppmodule.c:144: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ppmodule.c:193: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ppmodule.c:235: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ppmodule.c:296: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘PPMethods’
ppmodule.c: In function ‘initppmodule’:
ppmodule.c:310: warning: implicit declaration of function ‘Py_InitModule’
ppmodule.c:310: error: ‘PPMethods’ undeclared (first use in this function)
ppmodule.c:310: error: (Each undeclared identifier is reported only once
ppmodule.c:310: error: for each function it appears in.)
error: command 'gcc' failed with exit status 1
```

Has anyone come across this problem? It seems like these two lines may hold a clue:

```
ppmodule.c:21:20: error: Python.h: No such file or directory
ppmodule.c:37:25: error: X11/Xft/Xft.h: No such file or directory
```

Anyone know which package provides these headers?

Thanks!

---

### Post by th5th on 2010-05-10
I managed to solve this with Google's fine help. I needed to:

```
sudo apt-get install python-dev libxft-dev
```

Job done!

---


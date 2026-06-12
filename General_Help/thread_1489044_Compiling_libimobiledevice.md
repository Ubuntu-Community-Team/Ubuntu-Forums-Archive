---
title: "Compiling libimobiledevice"
date: 2010-05-20
forum: General Help
---

### Post by Evilhugbear on 2010-05-20
I have been trying to compile libimobiledevice, but whenever I type ./configure it says : 

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for a Python interpreter with version >= 2.3... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/dist-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/dist-packages
checking for swig... no
configure: WARNING: cannot find 'swig' program. You should look at [http://www.swig.org](http://www.swig.org) or install your distribution specific swig package.
checking for style of include used by make... GNU
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for python2.6... (cached) /usr/bin/python
checking for a version of Python >= '2.1.0'... yes
checking for the distutils Python package... yes
checking for Python include path... -I/usr/include/python2.6
checking for Python library path... -L/usr/lib/python2.6 -lpython2.6
checking for Python site-packages path... /usr/lib/python2.6/dist-packages
checking python extra libraries... -lssl -lcrypto  -lssl -lcrypto      -L/usr/lib -lz -lpthread -ldl  -lutil
checking python extra linking flags... -Xlinker -export-dynamic -Wl,-O1 -Wl,-Bsymbolic-functions
checking consistency of all components of python development environment... no
configure: error:
  Could not link test program to Python. Maybe the main Python library has been
  installed in some non-standard library path. If so, pass it to configure,
  via the LDFLAGS environment variable.
  Example: ./configure LDFLAGS="-L/usr/non-standard-path/python/lib"
  ============================================================================
   ERROR!
   You probably have to install the development version of the Python package
   for your distribution.  The exact name of this package varies among them.
  ============================================================================
	   
How do I fix this? It seems like there is a problem with python. I am very new to ubuntu and have never compiled anything so please explain :)
This is ubuntu 10.04 32bit

---

### Post by xubis on 2010-05-21
You need to install the python-dev package :) From the terminal enter
```
sudo apt-get install python2.6-dev
```

---

### Post by druitex on 2011-03-27
I novate en ubuntu and in install software.. I need conect my Ipod...but I have this problem to install Libimobiledevice!!! someone do you have any idea?

druitex@XXX:~/Descargas/libimobiledevice-1.0.4$ sudo make
[sudo] password for druitex: 
make  all-recursive
make[1]: se ingresa al directorio «/home/harold/Descargas/libimobiledevice-1.0.4»
Making all in src
make[2]: se ingresa al directorio «/home/harold/Descargas/libimobiledevice-1.0.4/src»
make[2]: No se hace nada para «all».
make[2]: se sale del directorio «/home/harold/Descargas/libimobiledevice-1.0.4/src»
Making all in include
make[2]: se ingresa al directorio «/home/harold/Descargas/libimobiledevice-1.0.4/include»
make[2]: No se hace nada para «all».
make[2]: se sale del directorio «/home/harold/Descargas/libimobiledevice-1.0.4/include»
Making all in swig
make[2]: se ingresa al directorio «/home/harold/Descargas/libimobiledevice-1.0.4/swig»
false -python -I../include  -I/usr/local/include -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/python2.6 -I/usr/include -I../src -o imobiledevice_wrap.cxx imobiledevice.i
make[2]: *** [imobiledevice_wrap.cxx] Error 1
make[2]: se sale del directorio «/home/harold/Descargas/libimobiledevice-1.0.4/swig»
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio «/home/harold/Descargas/libimobiledevice-1.0.4»
make: *** [all] Error 2

---


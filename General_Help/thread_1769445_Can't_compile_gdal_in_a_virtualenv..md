---
title: "Can't compile gdal in a virtualenv."
date: 2011-05-28
forum: General Help
---

### Post by libertyaikido on 2011-05-28
Hello there,

I'm having a heck of a time installing gdal using pip while inside of a virtualenv created with the --no-site-packages option.

First off, the error message tells me that it can't find gdal-config.  That was fixed by changing the gdal_config variable in build/gdal/setup.cfg to read as follows:
gdal_config = /usr/bin/gdal-config

Now I get the following:

```
(force)natgeo@deathstar-app1:~/code/force$ pip install gdal
Downloading/unpacking gdal
  Running setup.py egg_info for package gdal
    /home/natgeo/code/force/build/gdal/setup.py:78: DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.
      import popen2
    numpy include /home/natgeo/code/force/lib/python2.6/site-packages/numpy/core/include
Installing collected packages: gdal
  Running setup.py install for gdal
    /home/natgeo/code/force/build/gdal/setup.py:78: DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.
      import popen2
    numpy include /home/natgeo/code/force/lib/python2.6/site-packages/numpy/core/include
    building 'osgeo._gdal' extension
    gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I../../port -I../../gcore -I../../alg -I../../ogr/ -I/usr/include/python2.6 -I/home/natgeo/code/force/lib/python2.6/site-packages/numpy/core/include -I/usr/include -c extensions/gdal_wrap.cpp -o build/temp.linux-x86_64-2.6/extensions/gdal_wrap.o
    cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
    extensions/gdal_wrap.cpp:2587:22: error: cpl_port.h: No such file or directory
    extensions/gdal_wrap.cpp:2588:24: error: cpl_string.h: No such file or directory
    extensions/gdal_wrap.cpp:2590:18: error: gdal.h: No such file or directory
    extensions/gdal_wrap.cpp:2591:23: error: gdal_priv.h: No such file or directory
    extensions/gdal_wrap.cpp:2592:22: error: gdal_alg.h: No such file or directory
    extensions/gdal_wrap.cpp:2593:24: error: gdalwarper.h: No such file or directory
    extensions/gdal_wrap.cpp: In function 'void SWIG_Python_AddErrorMsg(const char*)':
    extensions/gdal_wrap.cpp:870: warning: format not a string literal and no format arguments
    extensions/gdal_wrap.cpp: At global scope:
    extensions/gdal_wrap.cpp:2610: error: expected initializer before 'VeryQuietErrorHandler'
    extensions/gdal_wrap.cpp:2494: warning: 'swig_module' defined but not used
    error: command 'gcc' failed with exit status 1
    Complete output from command /home/natgeo/code/force/bin/python -c "import setuptools;__file__='/home/natgeo/code/force/build/gdal/setup.py';exec(compile(open(__file__).read().replace('\r\n', '\n'), __file__, 'exec'))" install --single-version-externally-managed --record /tmp/pip-1sMMXY-record/install-record.txt --install-headers /home/natgeo/code/force/include/site/python2.6:
    /home/natgeo/code/force/build/gdal/setup.py:78: DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.

  import popen2

numpy include /home/natgeo/code/force/lib/python2.6/site-packages/numpy/core/include

running install

running build

running build_py

running build_ext

building 'osgeo._gdal' extension

gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I../../port -I../../gcore -I../../alg -I../../ogr/ -I/usr/include/python2.6 -I/home/natgeo/code/force/lib/python2.6/site-packages/numpy/core/include -I/usr/include -c extensions/gdal_wrap.cpp -o build/temp.linux-x86_64-2.6/extensions/gdal_wrap.o

cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++

extensions/gdal_wrap.cpp:2587:22: error: cpl_port.h: No such file or directory

extensions/gdal_wrap.cpp:2588:24: error: cpl_string.h: No such file or directory

extensions/gdal_wrap.cpp:2590:18: error: gdal.h: No such file or directory

extensions/gdal_wrap.cpp:2591:23: error: gdal_priv.h: No such file or directory

extensions/gdal_wrap.cpp:2592:22: error: gdal_alg.h: No such file or directory

extensions/gdal_wrap.cpp:2593:24: error: gdalwarper.h: No such file or directory

extensions/gdal_wrap.cpp: In function 'void SWIG_Python_AddErrorMsg(const char*)':

extensions/gdal_wrap.cpp:870: warning: format not a string literal and no format arguments

extensions/gdal_wrap.cpp: At global scope:

extensions/gdal_wrap.cpp:2610: error: expected initializer before 'VeryQuietErrorHandler'

extensions/gdal_wrap.cpp:2494: warning: 'swig_module' defined but not used

error: command 'gcc' failed with exit status 1

----------------------------------------
Command /home/natgeo/code/force/bin/python -c "import setuptools;__file__='/home/natgeo/code/force/build/gdal/setup.py';exec(compile(open(__file__).read().replace('\r\n', '\n'), __file__, 'exec'))" install --single-version-externally-managed --record /tmp/pip-1sMMXY-record/install-record.txt --install-headers /home/natgeo/code/force/include/site/python2.6 failed with error code 1
Storing complete log in /home/natgeo/.pip/pip.log
```

It seems to be failing to find a bunch of files that *do* exist on the local filesystem.  Any ideas on how I can tell the installer where they are?  I really want the virtualenv to be as self contained as possible, so I don't want to break down and run code against the system Python libs.  Any help is greatly appreciated.

Thanks in advance.

---

### Post by echelonIV on 2012-03-05
I had the same issue.  Despite being almost a year old this thread appears near the top of google searches, so hopefully this will help someone out.

It looks like the header files (gotten via gdal-devel) aren't being found - if they are on your local filesystem you can specify the include dirs when installing via pip.

```

pip install --no-install GDAL

```

Then cd into ENV/build/GDAL

```
python setup.py build_ext --include-dirs=<path_to_headers>
```

Then 
```
pip install --no-download GDAL
```

Also, make sure that the version of GDAL that you have on your system matches the one you're trying to install via pip.

---


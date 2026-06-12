---
title: "mypaint will not install, please help?"
date: 2010-02-25
forum: General Help
---

### Post by system9 on 2010-02-25
[LEFT]I have a drawing tablet, and have been excited to try this program called mypaint. BUt I have been trying to get it to work for a few days with no luck. In fact, i even upgraded to ubuntu 9.10 to see if it would help, but it didnt. Here is the process i am using
sudo apt-get install python-dev libglib2.0-dev python-numpy swig scons
wget [http://download.gna.org/mypaint/mypaint-0.8.1.tar.bz2](http://download.gna.org/mypaint/mypaint-0.8.1.tar.bz2)
tar -xvjf mypaint-0.8.1.tar.bz2
cd mypaint-0.8.1
sudo scons prefix=/usr/local install
rm -r mypaint-0.8.1*

and here is the error
[/LEFT]

Install file: "mypaint" as "/usr/local/bin/mypaint"
o lib/mypaintlib_wrap.os -c -Wall -Wno-sign-compare -Wno-write-strings -fno-strict-aliasing -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/python2.6/dist-packages/numpy/core/include -I/usr/include/python2.6 lib/mypaintlib_wrap.cpp
sh: o: not found
o lib/_mypaintlib.so -shared lib/mypaintlib_wrap.os -lglib-2.0
sh: o: not found
Install file: "lib/_mypaintlib.so" as "/usr/local/lib/mypaint/_mypaintlib.so"
scons: *** [/usr/local/lib/mypaint/_mypaintlib.so] lib/_mypaintlib.so: No such file or directory
scons: building terminated because of errors.

---

### Post by julipanno on 2010-02-26
You don't have to compile MyPaint yourself if you don't want to, as it is readily available for Ubuntu 9.10 at GetDeb.net: [http://www.getdeb.net/software/MyPaint](http://www.getdeb.net/software/MyPaint)

---

### Post by system9 on 2010-02-26
> **julipanno said:**
> You don't have to compile MyPaint yourself if you don't want to, as it is readily available for Ubuntu 9.10 at GetDeb.net: [http://www.getdeb.net/software/MyPaint](http://www.getdeb.net/software/MyPaint)

I installed it from getdeb. Now i can see the mypaint icon in my graphics apps launch menu, but when i click it, nothing happens.
I went into the synaptic package manager, and uninstalled mypaint completely, so that i could start fresh. I then re-installed from getdeb. Everything seemed to install ok, but again when i click the icon to launchthe app, nothing happens at all. If i go to the terminal, and type in mypaint, i get this error

We are not correctly installed or compiled!
script: "/usr/local/bin/mypaint"
deduced prefix: "/usr/local"
lib_shared: "/usr/local/share/mypaint/"
lib_compiled: "/usr/local/lib/mypaint/"

Traceback (most recent call last):
  File "/usr/local/bin/mypaint", line 54, in <module>
    from lib import mypaintlib
ImportError: No module named lib

---


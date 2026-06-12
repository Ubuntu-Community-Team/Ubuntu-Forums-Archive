---
title: "is it possible to install Eric5 on ubuntu 11.10?"
date: 2011-10-20
forum: General Help
---

### Post by Imnotroot on 2011-10-20
Well topic says it all, it it possible already to run Eric5 on ubuntu? i searched all over the web for a way to get it working, but no luck.

Thanks in advance.

---

### Post by gsmanners on 2011-10-20
Compile the source? I'll give that a try...

---

### Post by gsmanners on 2011-10-20
Okay, I got it working on my system. I'll have a look through my bash history file and do a write-up on how to do this, once I get back.

EDIT: Okay, here goes:

How to make Eric5 on Ubuntu 11.10:

- Download

Eric5: [http://sourceforge.net/projects/eric-ide/files/eric5/stable](http://sourceforge.net/projects/eric-ide/files/eric5/stable)
PyQt4: [http://www.riverbankcomputing.com/software/pyqt/download](http://www.riverbankcomputing.com/software/pyqt/download)
QScintilla: [http://www.riverbankcomputing.com/software/qscintilla/download](http://www.riverbankcomputing.com/software/qscintilla/download)

Extract the tar.gz files somewhere handy.

- In the repository

```
sudo apt-get install build-essential python3-dev libqt4-dev python-sip-dev python3-sip-dev
```

I'm pretty sure that's all you need.

Start a terminal in the extracted PyQt folder and do:

```
python3 configure.py 
make
sudo make install
```

This will give you PyQt4, suitable for use in Python 3. The make command will probably take a while.

Then, if all went well, change directory to your QScintilla folder and do:

```
cd Qt4
qmake qscintilla.pro
make
sudo make install
cd ../Python
python3 configure.py 
make
sudo make install
```

The above two installs will give you QScintilla2 and its PyQt4 wrapper (I'm pretty sure you need both).

Then, as long as nothing is giving you any serious errors, change to the Eric5 folder and do:

```
sudo python3 install.py
```

Let me know if I missed a step somewhere.

---

### Post by Imnotroot on 2011-10-21
Thanks, ill give it a try when i get home from work!

---

### Post by Imnotroot on 2011-10-21
Got a error at the first step:

name@host:~/bin/PyQt-x11-gpl-4.8.5$ python3 configure.py 
Determining the layout of your Qt installation...
Error: Failed to determine the layout of your Qt installation. Try again using
the --verbose flag to see more detail about the problem.
name@host:~/bin/PyQt-x11-gpl-4.8.5$

verbose output:

Determining the layout of your Qt installation...
/usr/bin/qmake -o qtdirs.mk qtdirs.pro
make -f qtdirs.mk
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DQT_WEBKIT -DQT_NO_DEBUG -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4 -I. -o qtdirs.o qtdirs.cpp
make: g++: Command not found
make: *** [qtdirs.o] Error 127
Error: Failed to determine the layout of your Qt installation. Try again using
the --verbose flag to see more detail about the problem.

so i installed G++:

sudo apt-get install g++

then it worked.

---

### Post by gsmanners on 2011-10-21
Oops. :D

You also apparently need build-essential. Let me add that to the list.

---

### Post by Imnotroot on 2011-10-21
Following your steps i got it working, thanks a lot for your help. Marking as Solved!

---

### Post by murphycc on 2012-04-29
Hi folks,

I tried the great instructions from gsmanners, and it all works without an error til I get to the running the 

```
python3 configure.py
```in the QScintilla folder.

I get the following error:

```
cmurphy@kdesktop:~/Downloads/QScintilla-gpl-2.6.1/Python$ python3 configure.py 
Error: Unable to find either PyQt v3 or v4.
```I am on Kubuntu 12.04 now. Any suggestions?

Thanks,
Chris

---


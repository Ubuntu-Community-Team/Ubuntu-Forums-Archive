---
title: "Instalation problem with Eric-5 &quot;Error: No module named PyQt4.QtCore&quot;"
date: 2010-10-19
forum: General Help
---

### Post by Irvine_himself on 2010-10-19
I already have the Python IDE Eric-4 installed from the repos, and am trying to install Eric-5 for Python 3

I have doubled checked the dependencies and they are okay, but when I try to run the installation script, I get the following error message:

```
Checking dependencies
Python Version: 3.1.2
Sorry, please install PyQt4.
Error: No module named PyQt4.QtCore

```I re-installed pyqt4 from the repos and checked the version dependencies, (again,) but still the same error message. Does anyone understand what is happening and how I can fix this?

Thanks in advance.

---

### Post by cinecek on 2010-10-23
I have the same problem.

EDIT: I have 64-bit Ubuntu Karmic

---

### Post by morii on 2010-11-10
The same on 64-bit and 10.10 :(

---

### Post by hsantanna on 2010-11-10
The same on 64-bit KUbuntu 10.10.

---

### Post by hsantanna on 2010-12-01
anyone could help?

---

### Post by benson444 on 2010-12-01
When you install PyQt4 from the repository it will be built with Python 2. You're going to need to build Eric's dependencies with Python 3. I learnt a bit of Python 3/PyQt a while ago and had to build PyQt, although I didn't use Eric.

To be honest, I'd recommend sticking to the repository versions and using Python 2, but, if you really want it, this worked for me:

Go to riverbankcomputing.co.uk and download SIP, QScintilla2 and PyQt4. First install SIP. Unpack it, cd to the directory and run:

```
python3 configure.py
make
sudo make install
```

Now install QScintilla. Unpack it, cd to its Qt4 subdirectory and run:

```
qmake qscintilla.pro
qmake
sudo make install
```

Now PyQt4. Unpack it, cd to the directory and run (this takes a while):

```
python3 configure.py
make
sudo make install
```

Now the QScintilla Python bindings. cd to the Python subdirectory of QScintilla and run (again):

```
python3 configure.py
make
sudo make install
```

Finally, install Eric 5:

```
sudo python3 install.py
```

---

### Post by cjejuni on 2011-01-23
installing qscintilla, error:
> In file included from qsciscintilla.cpp:33:
Qsci/qsciscintilla.h:39: fatal error: qobject.h: No such file or directory
compilation terminated.what falls?
thanks...
cjejuni

---

### Post by benson444 on 2011-01-23
Looks like you don't have the Qt4 development libraries installed.

```
sudo apt-get install libqt4-dev
```

---

### Post by cjejuni on 2011-01-24
tnx bens...so far so good. almost made install, but new stumbling:
"make" on the PyQT section, the error:

/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
make[1]: *** [QtHelp.so] Error 1
make[1]: Leaving directory `/home/les/Downloads/PyQt-x11-gpl-4.8.2/QtHelp'
make: *** [install] Error 2

thanks again.
cjejuni

---

### Post by benson444 on 2011-01-25
OK, another missing library. Probably libxext-dev. Install that and then run configure again, before make.

Let me know when/if it finally works.

---

### Post by cjejuni on 2011-01-25
hey bens thanks for ur help! Eric-5 is working. just finished compiling/installing. will configure, will learn programming. 
appreciate
cjejuni

---

### Post by serafim on 2011-08-10
Would like to let you know that bensons installation procedure worked fine in ubuntu 11.04.

However I would very much enjoy packages (deb and rpm) and installers for eric-5 as I plan to use python3 in a course.

Thanks for this little how-to.

---

### Post by Imnotroot on 2011-10-19
Well i tried the install steps, however at the last step, installing eric5 itself, it give me a error:

Found PyQt4
Sorry, please install QtHelp.
Error: No module named QtHelp

Anyone know a way to fix this?

---

### Post by WangWeiLin on 2011-10-26
I have the same problem.

The issue seems to be that QtHelp is not build in Ubuntu. The Bug can be found here ... it's supposed to be fixed but I cannot confirm this. I use ppa and I have the same error.
[https://bugs.launchpad.net/ubuntu/+source/python-qt4/+bug/692822](https://bugs.launchpad.net/ubuntu/+source/python-qt4/+bug/692822)

---

### Post by Imnotroot on 2011-10-27
a sollution can be found [here](http://ubuntuforums.org/showthread.php?p=11374902). good luck!

---

### Post by kosovafan on 2012-02-11
Hello,

has someone running Eric5 on Ubuntu and know how it run? I try to install but it ends with Error message about QTHelp. 

Would be nice. 

Regards
Silvio

---


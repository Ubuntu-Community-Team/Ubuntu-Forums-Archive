---
title: "Error installing PyQt-x11-gpl-4.8.3"
date: 2011-04-11
forum: General Help
---

### Post by Ralph L on 2011-04-11
I am trying to install PyQt-x11-gpl-4.8.3, which is needed to install the latest version of fcronq.  However, I get the following messages (see below)--plus a bunch more.  QFile, QLibraryInfo, and QTextStream are "#include" when qtdirs.cpp is compiled during the command "python configure.py", the first command of the installation.  My guess is that I am missing some standard files, but I don't know where to find them.

Any help would be appreciated.
Ralph

ralph@ralph-laptop:~/Documents/Download_folder/PyQt4/PyQt-x11-gpl-4.8.3$ python configure.py -q/usr/share/qt4/bin/qmake --verbose
Determining the layout of your Qt installation...
/usr/share/qt4/bin/qmake -o qtdirs.mk qtdirs.pro
make -f qtdirs.mk
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4 -I. -o qtdirs.o qtdirs.cpp
qtdirs.cpp:1:17: error: QFile: No such file or directory
qtdirs.cpp:2:24: error: QLibraryInfo: No such file or directory
qtdirs.cpp:3:23: error: QTextStream: No such file or directory

---

### Post by davidmohammed on 2011-04-11
at a guess - have you installed build-essential?

Have you installed the QT-dev libraries - search for QT in synaptic manager?

You might have to configure --qmake option to point to QT4 dev libraries

---

### Post by Ralph L on 2011-04-11
Using Synaptic I installed qt4-dev-tools 4.6.2.  After that "python configure.py" ran to completion.  I didn't install build-essentials.  I then entered the command "make".  This ran for a long time but finally got an error as shown below. Any ideas?  Do I need to install build-essentials?

Thanks
Ralph 

g++ -shared -Wl,-O1 -Wl,-rpath,/usr/lib -Wl,--version-script=QtHelp.exp -o QtHelp.so sipQtHelpcmodule.o sipQtHelpQList0100QHelpSearchQuery.o sipQtHelpQMap0100QString0100QUrl.o sipQtHelpQList0100QStringList.o sipQtHelpQHelpSearchResultWidget.o sipQtHelpQHelpSearchQueryWidget.o sipQtHelpQHelpSearchEngine.o sipQtHelpQHelpSearchQuery.o sipQtHelpQHelpIndexWidget.o sipQtHelpQHelpIndexModel.o sipQtHelpQHelpEngine.o sipQtHelpQHelpEngineCore.o sipQtHelpQHelpContentWidget.o sipQtHelpQHelpContentModel.o sipQtHelpQHelpContentItem.o -L/usr/lib -L/usr/X11R6/lib -lQtHelp -lQtGui -lQtCore -lXext -lX11 -lm -lpthread
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
make[1]: *** [QtHelp.so] Error 1
make[1]: Leaving directory `/media/Shared_Data/documents_ralph/Download_folder/PyQt4/PyQt-x11-gpl-4.8.3/QtHelp'
make: *** [all] Error 2

---

### Post by davidmohammed on 2011-04-11
looks like its trying to link a library called libxext - have you installed the libxext-dev library from synaptic?

generally if you see "l*foo*" linking type errors - look in synapic for "lib*foo*-dev" and install that

---

### Post by Ralph L on 2011-04-11
Thanks again.

I used Synaptic to add libxext-dev 1.1.1-2.  With that installed make ran to completion.  Now I will try sudo make install.

Thanks

Ralph

---

### Post by Ralph L on 2011-04-11
Now that I have PyQt-x11-gpl-4.8.3 installed (I hope correctly) I am back trying to install fcronq-0.3.0.  I have downloaded it, untared it and have done a cd to its folder.  I tried make and got the error shown below.  Any ideas?  I don't know what it means to attach PyQt4 to Python v3.  

Incidentally I had to manually set the permissions of PyQt4, uic,pyuic.py all to 766.  This is how the permissions of all the other folders in /usr/lib/python2.6/dist-packages/PyQt4/uic/pyuic.py chain were set.

Thanks

Ralph

ralph@ralph-laptop:~/Documents/Download_folder/fcron_fcronq/fcronq-0.3.0/FcronQ/Build$ make
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/pyuic.py", line 36, in <module>
    from PyQt4 import QtCore
ImportError: cannot import name QtCore
Makefile:149: *** Error: The required 'PyQt4' module can't be found; ensure it's attached to 'Python v3' before building.  Stop.
ralph@ralph-laptop:~/Documents/Download_folder/fcron_fcronq/fcronq-0.3.0/FcronQ/Build$ ^C
ralph@ralph-laptop:~/Documents/Download_folder/fcron_fcronq/fcronq-0.3.0/FcronQ/Build$

---

### Post by davidmohammed on 2011-04-12
not sure about that error.

I typed qtcore into synaptic - 

it gave 4 results - python-pyside.qtcore, libqtcore4, libqtgui4 and python-gt4..

Try installing each one (if they havent already been installed) to see if it resolves your error.

---


---
title: "Error when installing PyQt4"
date: 2010-03-12
forum: General Help
---

### Post by eranga1988 on 2010-03-12
Hey guyz, when I tried  to install PyQt4 i got the following error.

```
senzeh@senzeh-laptop:~/Python/PyQt-x11-gpl-4.7$ python3.1 configure.py
Determining the layout of your Qt installation...
Error: Failed to determine the layout of your Qt installation. Try again using
the --verbose flag to see more detail about the problem.
senzeh@senzeh-laptop:~/Python/PyQt-x11-gpl-4.7$ 
```

Please help me to solve this and install PyQt4
(I have already installed Sip-4.10)

---

### Post by eranga1988 on 2010-03-12
Can anyone pls help me?

---

### Post by eranga1988 on 2010-03-12
Pls help me.....

> senzeh@senzeh-laptop:~/Python/PyQt-x11-gpl-4.7$ python3.1 configure.py --verbose flag
Determining the layout of your Qt installation...
/usr/bin/qmake -o qtdirs.mk qtdirs.pro
make -f qtdirs.mk
Error: Failed to determine the layout of your Qt installation. Try again using
the --verbose flag to see more detail about the problem.
b'g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4 -I. -o qtdirs.o qtdirs.cpp\n'b'qtdirs.cpp:1:17: error: QFile: No such file or directory\n'b'qtdirs.cpp:2:24: error: QLibraryInfo: No such file or directory\n'b'qtdirs.cpp:3:23: error: QTextStream: No such file or directory\n'b'qtdirs.cpp: In function \xe2\x80\x98int main(int, char**)\xe2\x80\x99:\n'b'qtdirs.cpp:7: error: \xe2\x80\x98QFile\xe2\x80\x99 was not declared in this scope\n'b'qtdirs.cpp:7: error: expected \xe2\x80\x98;\xe2\x80\x99 before \xe2\x80\x98outf\xe2\x80\x99\n'b'qtdirs.cpp:9: error: \xe2\x80\x98outf\xe2\x80\x99 was not declared in this scope\n'b'qtdirs.cpp:9: error: \xe2\x80\x98QIODevice\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:9: error: \xe2\x80\x98QIODevice\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:9: error: \xe2\x80\x98QIODevice\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:12: error: \xe2\x80\x98QTextStream\xe2\x80\x99 was not declared in this scope\n'b'qtdirs.cpp:12: error: expected \xe2\x80\x98;\xe2\x80\x99 before \xe2\x80\x98out\xe2\x80\x99\n'b'qtdirs.cpp:14: error: \xe2\x80\x98out\xe2\x80\x99 was not declared in this scope\n'b'qtdirs.cpp:14: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:14: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:15: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:15: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:16: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:16: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:17: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:17: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:18: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:18: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:19: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:19: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:21: error: \xe2\x80\x98QT_VERSION\xe2\x80\x99 was not declared in this scope\n'b'qtdirs.cpp:22: error: \xe2\x80\x98QT_EDITION\xe2\x80\x99 was not declared in this scope\n'b'qtdirs.cpp:24: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:86: error: \xe2\x80\x98qreal\xe2\x80\x99 was not declared in this scope\n'b'make: *** [qtdirs.o] Error 1\n'senzeh@senzeh-laptop:~/Python/PyQt-x11-gpl-4.7$ 


---

### Post by SomZumTod on 2010-04-18
i was facing the same problem,

but after awhile i figured out that the problem was with the Qt paths 

python configure.py -q qmake path

in my case it is:

python configure.py -q /home/mahmoud/qtsdk-2009.05/qt/bin/qmake
 
hope it could help :)

---

### Post by vvxtsunami on 2010-06-02
Hi, yes, that's the solution....
Just have to look for the qmake file and pass it in the -q parameter.
Thanks for the help.

---


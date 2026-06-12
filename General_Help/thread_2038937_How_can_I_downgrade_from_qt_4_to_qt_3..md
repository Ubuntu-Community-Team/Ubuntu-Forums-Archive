---
title: "How can I downgrade from qt 4 to qt 3. ?"
date: 2012-08-07
forum: General Help
---

### Post by Gusss on 2012-08-07
I want to install an older program which wont compile with qt4 - how do I downgrade to Qt 3 ?

---

### Post by spjackson on 2012-08-07
You can install Qt3 alongside Qt4: there is no need it remove Qt4. On Ubuntu 12.04 the package you want is qt3-dev-tools (and optionally qt3-designer, qt3-assistant if you need these). The packages are probably the same in older Ubuntu versions.

These packages are installable via synaptic or apt-get. I don't know how to find them in Software Centre.

---

### Post by Gusss on 2012-08-07
> **spjackson said:**
> You can install Qt3 alongside Qt4: there is no need it remove Qt4. On Ubuntu 12.04 the package you want is qt3-dev-tools (and optionally qt3-designer, qt3-assistant if you need these). The packages are probably the same in older Ubuntu versions.

These packages are installable via synaptic or apt-get. I don't know how to find them in Software Centre.

Thanks. In that case how do I set qt3 to be the default ?

---

### Post by spjackson on 2012-08-07
> **Gusss said:**
> Thanks. In that case how do I set qt3 to be the default ?
You mean for qmake, designer, assistant etc.? You can use update-alternatives to choose the default for these commands.

---

### Post by Gusss on 2012-08-07
> **spjackson said:**
> You mean for qmake, designer, assistant etc.? You can use update-alternatives to choose the default for these commands.

I guess so - Im not really sure which parts of qt the program uses to compile so I would like to set the whole of qt to version 3 . Exactly what would I type into terminal ?

---

### Post by 3Miro on 2012-08-07
> **Gusss said:**
> I guess so - Im not really sure which parts of qt the program uses to compile so I would like to set the whole of qt to version 3 . Exactly what would I type into terminal ?

Your program is made either for QT3 or QT4. You cannot chose to compile or run a program with a different version of QT (maybe different versions of QT4, like 4.1, 4.2, but not QT3).

Unless you have an old program or you have not installed all QT3 libraries (libqt4-qt3support), then the program should pick that automatically.

---

### Post by Gusss on 2012-08-07
> **3Miro said:**
> Your program is made either for QT3 or QT4. You cannot chose to compile or run a program with a different version of QT (maybe different versions of QT4, like 4.1, 4.2, but not QT3).

Unless you have an old program or you have not installed all QT3 libraries (libqt4-qt3support), then the program should pick that automatically.

thanks again - 
 I get this error when I try to ./configure (after it does some stuff succesully)

```
checking for main in -lqt-mt... yes
checking whether QTDIR environment variable is set... no
configure: error: QTDIR must be properly set.

```

---

### Post by spjackson on 2012-08-08
> **Gusss said:**
>  
 I get this error when I try to ./configure (after it does some stuff succesully)

```
checking for main in -lqt-mt... yes
checking whether QTDIR environment variable is set... no
configure: error: QTDIR must be properly set.

```
You need to set that yourself.
```

export QTDIR=/usr/share/qt3

```
Add it to ~/.bashrc if you want to make it permanent.

---

### Post by Gusss on 2012-08-08
> **spjackson said:**
> You need to set that yourself.
```

export QTDIR=/usr/share/qt3

```
Add it to ~/.bashrc if you want to make it permanent.

Thanks that seems to work - except when I make I get a problem :

```
make[1]: Entering directory `/home/dew/swonder2.1.1'
make[1]: *** No rule to make target `swonder'. Stop.
make[1]: Leaving directory `/home/dew/swonder2.1.1'
make: *** [swonder] Error 2
```


qmake gets a little bit further but......
The config details are below :

```
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for flex... no
checking for lex... no
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
checking whether ln -s works... yes
checking for bison... no
checking for byacc... no
checking for ranlib... ranlib
checking for main in -lX11... yes
checking for main in -lXext... yes
checking for main in -lm... yes
checking for main in -lqt-mt... yes
checking whether QTDIR environment variable is set... /usr/share/qt3
checking for Qt library... qt-mt
checking for Qt library version >= 3.1.1... yes
checking for qmake... /usr/bin/qmake
checking for moc... /usr/bin/moc
checking for uic... /usr/bin/uic
checking for main in -lqt-mt... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for pid_t... yes
checking for function prototypes... yes
checking whether setvbuf arguments are reversed... no
checking for floor... no
checking for pow... no
checking for pipe... yes
checking for sqrt... no
checking for strerror... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating swonder.pro
config.status: creating lib/config.h


```

---

### Post by spjackson on 2012-08-09
The output from configure seems to suggest that you have a working Qt3 development system. However,  I'm afraid that I don't know anything about swonder, and I don't know why it won't build for you.

---


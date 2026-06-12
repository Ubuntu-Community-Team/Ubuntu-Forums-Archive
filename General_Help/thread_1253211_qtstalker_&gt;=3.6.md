---
title: "qtstalker &gt;=3.6"
date: 2009-08-29
forum: General Help
---

### Post by random guy on 2009-08-29
the ubuntu repos have version .32 of qtstalker.  it appears as though .36 has been around since like may of 2008 or earlier so i can only imagine how old .32 is.

i have been trying to install the cvs version but am having issues. i would appreciate some help either compiling the cvs version of if maintainer could update the version.  if no one is maintaining this package in the repos i would be interested in doing it (i don't really know how but i would learn.  i want to give something back to the community)

anyway this is what i have been doing:

the instructions say to download compile and make ta-lib so i did that, appears to work fine.  

then to download qtstalker and run .configure.  

that says that it worked fine after i added a path include to point the configure script to the location where i compiled ta-lib.  the configure script said that i can do make and do make install.

but those throw lots of errors,  it appears as though there may be lots of missing headers.  im not sure why.

```

root@bashir-laptop:/home/bashir/qtstalker# ./configure 
./configure: 3: INCLUDEPATH: not found
Determining Qt version ... 4.5.0 ... okay
Determining TA-Lib version ... 0.4.0 ... okay

Building Makefile ...
Project MESSAGE: Using .qmake.cache
Project MESSAGE: Using INCLUDEPATH=/usr/include/qt4/Qt /usr/local/include/ta-lib
Project MESSAGE: Using LIBS=
Project MESSAGE: Operating system: unix linux
Done

Creating national language files in i18n ...
./configure: 65: lupdate-qt4: not found
Done
Compiling existing translations ...
./configure: 68: lrelease-qt4: not found
Done

You may now 'make && sudo make install'
root@bashir-laptop:/home/bashir/qtstalker# 


```

```

root@bashir-laptop:/home/bashir/qtstalker# make && sudo make install
cd lib/ && make -f Makefile 
make[1]: Entering directory `/home/bashir/qtstalker/lib'
g++ -c -pipe -rdynamic -ffast-math -O2 -g -Wall -W -D_REENTRANT -fPIC -DQT_NO_COMPAT -DDEBUG -D_DEBUG -DQT_SQL_LIB -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSql -I/usr/include/qt4 -I/usr/include/qt4/Qt -I/usr/local/include/ta-lib -I/usr/include/qt4/Qt -I. -I. -o IndicatorPlugin.o IndicatorPlugin.cpp
In file included from IndicatorPlugin.h:25,
                 from IndicatorPlugin.cpp:22:
PlotLine.h:25:19: error: QString: No such file or directory
PlotLine.h:26:17: error: QList: No such file or directory
PlotLine.h:27:18: error: QColor: No such file or directory
PlotLine.h:28:21: error: QDateTime: No such file or directory
In file included from PlotLine.h:29,
                 from IndicatorPlugin.h:25,
                 from IndicatorPlugin.cpp:22:
Setting.h:26:23: error: QStringList: No such file or directory
Setting.h:27:17: error: QHash: No such file or directory
In file included from IndicatorPlugin.cpp:22:
IndicatorPlugin.h:32:19: error: QObject: No such file or directory
IndicatorPlugin.cpp:25:19: error: QtDebug: No such file or directory
In file included from PlotLine.h:29,
                 from IndicatorPlugin.h:25,
                 from IndicatorPlugin.cpp:22:
Setting.h:34: error: ‘QString’ has not been declared
Setting.h:34: error: ‘QString’ has not been declared
Setting.h:35: error: ‘QString’ has not been declared
Setting.h:36: error: ‘QString’ has not been declared
Setting.h:37: error: ‘QString’ has not been declared
Setting.h:37: error: ‘QString’ has not been declared
Setting.h:38: error: ‘QStringList’ has not been declared
Setting.h:39: error: ‘QString’ has not been declared
Setting.h:40: error: ‘QString’ has not been declared
Setting.h:41: error: ‘QString’ has not been declared
Setting.h:47: error: ISO C++ forbids declaration of ‘QHash’ with no type
Setting.h:47: error: expected ‘;’ before ‘<’ token
In file included from IndicatorPlugin.h:25,
                 from IndicatorPlugin.cpp:22:
PlotLine.h:38: error: ‘QColor’ does not name a type
PlotLine.h:64: error: ‘QString’ has not been declared
PlotLine.h:65: error: ‘QColor’ has not been declared
PlotLine.h:65: error: ‘void PlotLine::setColor(int&)’ cannot be overloaded
PlotLine.h:64: error: with ‘void PlotLine::setColor(int&)’
PlotLine.h:66: error: ‘QColor’ has not been declared
PlotLine.h:68: error: ‘QString’ has not been declared
PlotLine.h:70: error: ‘QString’ has not been declared
PlotLine.h:71: error: ‘QString’ has not been declared
PlotLine.h:73: error: ‘QColor’ has not been declared
PlotLine.h:74: error: ‘QColor’ has not been declared
PlotLine.h:75: error: ‘QDateTime’ has not been declared
PlotLine.h:76: error: ‘QDateTime’ has not been declared
PlotLine.h:78: error: ‘QColor’ has not been declared
PlotLine.h:80: error: ‘QColor’ has not been declared
PlotLine.h:81: error: ‘QDateTime’ has not been declared
PlotLine.h:93: error: ‘QStringList’ has not been declared
PlotLine.h:94: error: ‘QColor’ has not been declared
PlotLine.h:95: error: ‘QColor’ has not been declared
PlotLine.h:98: error: ‘QString’ has not been declared
PlotLine.h:99: error: ‘QList’ has not been declared
PlotLine.h:99: error: expected ‘,’ or ‘...’ before ‘<’ token
PlotLine.h:100: error: ‘QList’ has not been declared
PlotLine.h:100: error: expected ‘,’ or ‘...’ before ‘<’ token
PlotLine.h:101: error: ‘QList’ has not been declared
PlotLine.h:101: error: expected ‘,’ or ‘...’ before ‘<’ token
PlotLine.h:101: error: ‘void PlotLine::getData(int)’ cannot be overloaded
PlotLine.h:79: error: with ‘double PlotLine::getData(int)’
PlotLine.h:104: error: ISO C++ forbids declaration of ‘QList’ with no type
PlotLine.h:104: error: expected ‘;’ before ‘<’ token
PlotLine.h:105: error: ISO C++ forbids declaration of ‘QList’ with no type
PlotLine.h:105: error: expected ‘;’ before ‘<’ token
PlotLine.h:106: error: ‘QColor’ does not name a type
PlotLine.h:108: error: ‘QString’ does not name a type
In file included from BarData.h:29,
                 from IndicatorPlugin.h:26,
                 from IndicatorPlugin.cpp:22:
Bar.h:37: error: ‘QDateTime’ has not been declared
Bar.h:38: error: ‘QDateTime’ has not been declared
Bar.h:52: error: ‘QString’ has not been declared
Bar.h:53: error: ‘QString’ has not been declared
Bar.h:54: error: ‘QString’ has not been declared
Bar.h:55: error: ‘QString’ has not been declared
Bar.h:56: error: ‘QString’ has not been declared
Bar.h:57: error: ‘QTime’ has not been declared
Bar.h:58: error: ‘QString’ has not been declared
Bar.h:58: error: ‘QString’ has not been declared
Bar.h:59: error: ‘QString’ has not been declared
Bar.h:59: error: ‘QString’ has not been declared
Bar.h:61: error: ‘QString’ has not been declared
Bar.h:62: error: ‘QStringList’ has not been declared
Bar.h:67: error: ISO C++ forbids declaration of ‘QHash’ with no type
Bar.h:67: error: expected ‘;’ before ‘<’ token
Bar.h:68: error: ‘QDateTime’ does not name a type
In file included from IndicatorPlugin.h:26,
                 from IndicatorPlugin.cpp:22:
BarData.h:62: error: expected `)' before ‘&’ token
BarData.h:65: error: ‘QDateTime’ has not been declared
BarData.h:73: error: ‘QDateTime’ has not been declared
BarData.h:77: error: ‘QStringList’ has not been declared
BarData.h:79: error: ‘QString’ has not been declared
BarData.h:80: error: ‘QStringList’ has not been declared
BarData.h:84: error: ‘QString’ has not been declared
BarData.h:86: error: ‘QString’ has not been declared
BarData.h:87: error: ‘QString’ has not been declared
BarData.h:88: error: ‘QString’ has not been declared
BarData.h:89: error: ‘QString’ has not been declared
BarData.h:90: error: ‘QString’ has not been declared
BarData.h:91: error: ‘QString’ has not been declared
BarData.h:94: error: ‘QString’ has not been declared
BarData.h:95: error: ‘QString’ has not been declared
BarData.h:96: error: ‘QString’ has not been declared
BarData.h:100: error: ISO C++ forbids declaration of ‘QList’ with no type
BarData.h:100: error: expected ‘;’ before ‘<’ token
BarData.h:101: error: ISO C++ forbids declaration of ‘QHash’ with no type
BarData.h:101: error: expected ‘;’ before ‘<’ token
BarData.h:105: error: ‘QString’ does not name a type
BarData.h:106: error: ‘QString’ does not name a type
BarData.h:107: error: ‘QString’ does not name a type
In file included from Indicator.h:28,
                 from IndicatorPlugin.h:28,
                 from IndicatorPlugin.cpp:22:
IndicatorParms.h:35: error: ‘QString’ has not been declared
IndicatorParms.h:36: error: ‘QString’ has not been declared
IndicatorParms.h:37: error: ‘QString’ has not been declared
IndicatorParms.h:37: error: ‘QString’ has not been declared
IndicatorParms.h:38: error: ‘QString’ has not been declared
IndicatorParms.h:38: error: ‘QString’ has not been declared
IndicatorParms.h:39: error: ‘QString’ has not been declared
IndicatorParms.h:40: error: ‘QString’ has not been declared
IndicatorParms.h:41: error: ‘QString’ has not been declared
IndicatorParms.h:42: error: ‘QString’ has not been declared
IndicatorParms.h:45: error: ‘QColor’ has not been declared
IndicatorParms.h:46: error: ‘QColor’ has not been declared
IndicatorParms.h:47: error: ‘QString’ has not been declared
IndicatorParms.h:48: error: ‘QString’ has not been declared
IndicatorParms.h:49: error: ‘QString’ has not been declared
IndicatorParms.h:50: error: ‘QString’ has not been declared
IndicatorParms.h:53: error: ISO C++ forbids declaration of ‘QHash’ with no type
IndicatorParms.h:53: error: expected ‘;’ before ‘<’ token
In file included from IndicatorPlugin.h:28,
                 from IndicatorPlugin.cpp:22:
Indicator.h:37: error: ‘QString’ has not been declared
Indicator.h:38: error: ‘QString’ has not been declared
Indicator.h:47: error: ‘QString’ has not been declared
Indicator.h:48: error: ‘QString’ has not been declared
Indicator.h:56: error: ISO C++ forbids declaration of ‘QList’ with no type
Indicator.h:56: error: expected ‘;’ before ‘<’ token
Indicator.h:57: error: ‘QString’ does not name a type
In file included from IndicatorPlugin.cpp:22:
IndicatorPlugin.h:36: error: expected class-name before ‘{’ token
IndicatorPlugin.h:37: error: ‘Q_OBJECT’ does not name a type
IndicatorPlugin.h:48: error: ‘QStringList’ has not been declared
IndicatorPlugin.h:49: error: ‘QList’ has not been declared
IndicatorPlugin.h:49: error: expected ‘,’ or ‘...’ before ‘<’ token
IndicatorPlugin.h:50: error: ‘QHash’ has not been declared
IndicatorPlugin.h:50: error: expected ‘,’ or ‘...’ before ‘<’ token
IndicatorPlugin.h:52: error: ‘QStringList’ has not been declared
IndicatorPlugin.h:54: error: ‘QString’ has not been declared
IndicatorPlugin.h:55: error: ‘QString’ has not been declared
IndicatorPlugin.h:55: error: ‘QHash’ has not been declared
IndicatorPlugin.h:55: error: expected ‘,’ or ‘...’ before ‘<’ token
IndicatorPlugin.h:56: error: ‘QHash’ has not been declared
IndicatorPlugin.h:56: error: expected ‘,’ or ‘...’ before ‘<’ token
IndicatorPlugin.h:57: error: ‘QHash’ has not been declared
IndicatorPlugin.h:57: error: expected ‘,’ or ‘...’ before ‘<’ token
IndicatorPlugin.h:59: error: expected `:' before ‘slots’
IndicatorPlugin.h:60: error: expected primary-expression before ‘void’
IndicatorPlugin.h:60: error: ISO C++ forbids declaration of ‘slots’ with no type
IndicatorPlugin.h:60: error: expected ‘;’ before ‘void’
IndicatorPlugin.h:64: error: ‘QStringList’ does not name a type
IndicatorPlugin.h:65: error: ‘QStringList’ does not name a type
In file included from IndicatorPlugin.cpp:23:
BARS.h:41: error: ‘QHash’ has not been declared
BARS.h:41: error: expected ‘,’ or ‘...’ before ‘<’ token
BARS.h:42: error: ‘QHash’ has not been declared
BARS.h:42: error: expected ‘,’ or ‘...’ before ‘<’ token
BARS.h:43: error: ‘QHash’ has not been declared
BARS.h:43: error: expected ‘,’ or ‘...’ before ‘<’ token
BARS.h:44: error: ‘QStringList’ has not been declared
BARS.h:47: error: ‘QStringList’ does not name a type
In file included from IndicatorPlugin.cpp:24:
UTIL.h:52: error: ‘QHash’ has not been declared
UTIL.h:52: error: expected ‘,’ or ‘...’ before ‘<’ token
UTIL.h:53: error: ‘QHash’ has not been declared
UTIL.h:53: error: expected ‘,’ or ‘...’ before ‘<’ token
UTIL.h:54: error: ‘QHash’ has not been declared
UTIL.h:54: error: expected ‘,’ or ‘...’ before ‘<’ token
UTIL.h:55: error: ‘QHash’ has not been declared
UTIL.h:55: error: expected ‘,’ or ‘...’ before ‘<’ token
UTIL.h:56: error: ‘QHash’ has not been declared
UTIL.h:56: error: expected ‘,’ or ‘...’ before ‘<’ token
UTIL.h:57: error: ‘QHash’ has not been declared
UTIL.h:57: error: expected ‘,’ or ‘...’ before ‘<’ token
UTIL.h:58: error: ‘QHash’ has not been declared
UTIL.h:58: error: expected ‘,’ or ‘...’ before ‘<’ token
UTIL.h:59: error: ‘QHash’ has not been declared
UTIL.h:59: error: expected ‘,’ or ‘...’ before ‘<’ token
UTIL.h:60: error: ‘QHash’ has not been declared
UTIL.h:60: error: expected ‘,’ or ‘...’ before ‘<’ token
UTIL.h:61: error: ‘QHash’ has not been declared
UTIL.h:61: error: expected ‘,’ or ‘...’ before ‘<’ token
UTIL.h:62: error: ‘QStringList’ has not been declared
UTIL.h:63: error: ‘QString’ has not been declared
UTIL.h:66: error: ‘QStringList’ does not name a type
UTIL.h:67: error: ‘QStringList’ does not name a type
IndicatorPlugin.cpp: In member function ‘void IndicatorPlugin::setDefaults()’:
IndicatorPlugin.cpp:47: error: ‘lineTypes’ was not declared in this scope
IndicatorPlugin.cpp:49: error: ‘maList’ was not declared in this scope
IndicatorPlugin.cpp:62: error: ‘qDebug’ was not declared in this scope
IndicatorPlugin.cpp: At global scope:
IndicatorPlugin.cpp:70: error: variable or field ‘getMATypes’ declared void
IndicatorPlugin.cpp:70: error: ‘QStringList’ was not declared in this scope
IndicatorPlugin.cpp:70: error: ‘l’ was not declared in this scope
IndicatorPlugin.cpp:75: error: no ‘void IndicatorPlugin::wakeup()’ member function declared in class ‘IndicatorPlugin’
IndicatorPlugin.cpp:80: error: variable or field ‘calculate’ declared void
IndicatorPlugin.cpp:80: error: ‘QList’ was not declared in this scope
IndicatorPlugin.cpp:80: error: expected primary-expression before ‘*’ token
IndicatorPlugin.cpp:80: error: expected primary-expression before ‘>’ token
IndicatorPlugin.cpp:80: error: ‘lines’ was not declared in this scope
make[1]: *** [IndicatorPlugin.o] Error 1
make[1]: Leaving directory `/home/bashir/qtstalker/lib'
make: *** [sub-lib-make_default] Error 2
root@bashir-laptop:/home/bashir/qtstalker# 


```

any ideas?

i also found a .deb file somewhere on the net which is supposed to be version .36 but it wants a dependency  libdb4.3 (>= 4.3.28-1)

but i have installed all the following and it wont work:
libdb4.3-ruby1.9
libdb4.4
libdb4.6
libdb4.7

there is no libdb4.3 in the repos for ubuntu 9.04.  im using 32 bit.

any ideas of any way to get the latest stable or unstable release?  thanks,

---


---
title: "Ktigcc"
date: 2010-02-18
forum: General Help
---

### Post by srilyk on 2010-02-18
Hi, I'm trying to install the Open Source TI calc SDK from [http://tigcc.ticalc.org/](http://tigcc.ticalc.org/)

I downloaded the linux version and ran into many dependency errors when running ./configure

Now I'm running into massive error hemorrhage and my google-fu seems to fail me and I'm a little brain-sore.

Here's what I get when I try to make:

 
```
ktigcc$ sudo make
g++ -c -pipe -g -Wall -W -Os -g -Wno-non-virtual-dtor -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/tilp2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/tilp2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/tilp2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/tilp2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -D_REENTRANT  -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_NO_DEBUG -I/usr/share/qt3/mkspecs/default -I. -I/usr/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/ktigcc.o ktigcc.cpp
In file included from /usr/include/kdecore_export.h:24,
                 from /usr/include/kdeversion.h:30,
                 from /usr/include/kapplication.h:25,
                 from ktigcc.cpp:28:
/usr/include/kdemacros.h:162:29: error: QtCore/qglobal.h: No such file or directory
In file included from ktigcc.cpp:28:
/usr/include/kapplication.h:44:30: error: QtGui/QApplication: No such file or directory
In file included from /usr/include/kconfig.h:27,
                 from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from ktigcc.cpp:28:
/usr/include/kconfigbase.h:29:27: error: QtCore/QtGlobal: No such file or directory
In file included from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from ktigcc.cpp:28:
/usr/include/kconfig.h:31:26: error: QtCore/QString: No such file or directory
/usr/include/kconfig.h:32:27: error: QtCore/QVariant: No such file or directory
/usr/include/kconfig.h:33:29: error: QtCore/QByteArray: No such file or directory
/usr/include/kconfig.h:34:24: error: QtCore/QList: No such file or directory
In file included from /usr/include/ksharedconfig.h:26,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from ktigcc.cpp:28:
/usr/include/ksharedptr.h:30:47: error: QtCore/QExplicitlySharedDataPointer: No such file or directory
/usr/include/ksharedptr.h:31:33: error: QtCore/QAtomicPointer: No such file or directory
In file included from ktigcc.cpp:28:
/usr/include/kapplication.h:49:26: error: QtGui/QX11Info: No such file or directory
In file included from ktigcc.cpp:29:
/usr/include/kcmdlineargs.h:23:24: error: QtCore/QBool: No such file or directory
In file included from /usr/include/klocale.h:26,
                 from /usr/include/kcmdlineargs.h:25,
                 from ktigcc.cpp:29:
/usr/include/klocalizedstring.h:25:24: error: QtCore/QChar: No such file or directory
/usr/include/klocalizedstring.h:26:30: error: QtCore/QLatin1Char: No such file or directory
/usr/include/klocalizedstring.h:27:30: error: QtCore/QStringList: No such file or directory
In file included from ktigcc.cpp:30:
/usr/include/kaboutdata.h:30:37: error: QtCore/QSharedDataPointer: No such file or directory
In file included from /usr/include/kicontheme.h:32,
                 from ktigcc.cpp:35:
/usr/include/kiconloader.h:27:26: error: QtCore/QObject: No such file or directory
In file included from ktigcc.cpp:26:
/usr/include/qt3/qimage.h: In member function ‘bool QImageTextKeyLang::operator<(const QImageTextKeyLang&) const’:
/usr/include/qt3/qimage.h:61: warning: suggest parentheses around ‘&&’ within ‘||’
In file included from /usr/include/kconfig.h:27,
                 from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from ktigcc.cpp:28:
/usr/include/kconfigbase.h: At global scope:
/usr/include/kconfigbase.h:66: error: ‘WriteConfigFlags’ has not been declared
/usr/include/kconfigbase.h:71: error: expected ‘;’ before ‘virtual’
/usr/include/kconfigbase.h:112: error: ‘WriteConfigFlags’ has not been declared
/usr/include/kconfigbase.h:113: error: ‘WriteConfigFlags’ has not been declared
/usr/include/kconfigbase.h:114: error: ‘WriteConfigFlags’ has not been declared
/usr/include/kconfigbase.h:171: error: ‘WriteConfigFlags’ has not been declared
/usr/include/kconfigbase.h:180: error: expected constructor, destructor, or type conversion before ‘(’ token
In file included from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from ktigcc.cpp:28:
/usr/include/kconfig.h:99: error: ‘OpenFlags’ has not been declared
/usr/include/kconfig.h:126: error: expected ‘;’ before ‘explicit’
/usr/include/kconfig.h:157: error: ‘OpenFlags’ has not been declared
/usr/include/kconfig.h:370: error: expected ‘;’ before ‘<’ token
/usr/include/kconfig.h:376: error: ‘WriteConfigFlags’ has not been declared
/usr/include/kconfig.h:396: error: expected ‘;’ before ‘Q_DECLARE_PRIVATE’
/usr/include/kconfig.h:397: error: expected ‘;’ before ‘}’ token
/usr/include/kconfig.h:398: error: expected constructor, destructor, or type conversion before ‘(’ token
In file included from /usr/include/ksharedconfig.h:26,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from ktigcc.cpp:28:
/usr/include/ksharedptr.h:197: error: expected constructor, destructor, or type conversion before ‘bool’
/usr/include/ksharedptr.h:203: error: expected constructor, destructor, or type conversion before ‘bool’
/usr/include/ksharedptr.h:209: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/ksharedptr.h:220: error: expected constructor, destructor, or type conversion before ‘void’
In file included from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from ktigcc.cpp:28:
/usr/include/ksharedconfig.h:41: error: expected class-name before ‘{’ token
/usr/include/ksharedconfig.h:69: error: ‘OpenFlags’ has not been declared
/usr/include/ksharedconfig.h:97: error: ‘OpenFlags’ has not been declared
/usr/include/ksharedconfig.h:106: error: ‘OpenFlags’ has not been declared
In file included from /usr/include/kapplication.h:45,
                 from ktigcc.cpp:28:
/usr/include/kcomponentdata.h:25: error: using typedef-name ‘QByteArray’ after ‘class’
/usr/include/qt3/qcstring.h:119: error: ‘QByteArray’ has a previous declaration here
In file included from ktigcc.cpp:28:
/usr/include/kapplication.h:82: error: invalid use of incomplete type ‘struct QApplication’
/usr/include/qt3/qwindowdefs.h:169: error: forward declaration of ‘struct QApplication’
/usr/include/kapplication.h:83: error: ‘QVariant’ has not been declared
/usr/include/kapplication.h:83: error: ‘QVariant’ has not been declared
/usr/include/kapplication.h:194: error: ‘QSessionManager’ has not been declared
/usr/include/kapplication.h:201: error: ‘QSessionManager’ has not been declared
/usr/include/kapplication.h:400: error: expected ‘:’ before ‘Q_SLOTS’
/usr/include/kapplication.h:406: error: ‘Q_SCRIPTABLE’ was not declared in this scope
/usr/include/kapplication.h:406: error: expected ‘;’ before ‘void’
/usr/include/kapplication.h:409: error: expected ‘;’ before ‘void’
/usr/include/kapplication.h:410: error: expected ‘;’ before ‘void’
/usr/include/kapplication.h:440: error: expected primary-expression before ‘void’
/usr/include/kapplication.h:440: error: expected ‘;’ before ‘void’
/usr/include/kapplication.h:475: error: ‘d’ is not a type
/usr/include/kapplication.h:476: error: expected ‘;’ before ‘Q_PRIVATE_SLOT’
/usr/include/kapplication.h:478: error: expected ‘;’ before ‘}’ token
In file included from /usr/include/klocale.h:26,
                 from /usr/include/kcmdlineargs.h:25,
                 from ktigcc.cpp:29:
/usr/include/klocalizedstring.h:429: error: ‘qlonglong’ has not been declared
/usr/include/klocalizedstring.h:429: error: ‘KLocalizedString KLocalizedString::subs(int, int, int, const QChar&) const’ cannot be overloaded
/usr/include/klocalizedstring.h:369: error: with ‘KLocalizedString KLocalizedString::subs(int, int, int, const QChar&) const’
/usr/include/klocalizedstring.h:444: error: ‘qulonglong’ has not been declared
/usr/include/klocalizedstring.h:444: error: ‘KLocalizedString KLocalizedString::subs(int, int, int, const QChar&) const’ cannot be overloaded
/usr/include/klocalizedstring.h:369: error: with ‘KLocalizedString KLocalizedString::subs(int, int, int, const QChar&) const’
/usr/include/klocalizedstring.h:370: error: ‘QLatin1Char’ was not declared in this scope
/usr/include/klocalizedstring.h:385: error: ‘QLatin1Char’ was not declared in this scope
/usr/include/klocalizedstring.h:400: error: ‘QLatin1Char’ was not declared in this scope
/usr/include/klocalizedstring.h:415: error: ‘QLatin1Char’ was not declared in this scope
/usr/include/klocalizedstring.h:430: error: ‘QLatin1Char’ was not declared in this scope
/usr/include/klocalizedstring.h:445: error: ‘QLatin1Char’ was not declared in this scope
/usr/include/klocalizedstring.h:461: error: ‘QLatin1Char’ was not declared in this scope
/usr/include/klocalizedstring.h:474: error: ‘QLatin1Char’ was not declared in this scope
/usr/include/klocalizedstring.h:487: error: ‘QLatin1Char’ was not declared in this scope
In file included from /usr/include/kcmdlineargs.h:25,
                 from ktigcc.cpp:29:
/usr/include/klocale.h:566: error: ‘DateTimeFormatOptions’ has not been declared
/usr/include/klocale.h:578: error: expected ‘;’ before ‘QString’
/usr/include/klocale.h:1400: error: expected constructor, destructor, or type conversion before ‘(’ token
In file included from ktigcc.cpp:29:
/usr/include/kcmdlineargs.h:30: error: using typedef-name ‘QByteArray’ after ‘class’
/usr/include/qt3/qcstring.h:119: error: ‘QByteArray’ has a previous declaration here
/usr/include/kcmdlineargs.h:269: error: ‘StdCmdLineArgs’ has not been declared
/usr/include/kcmdlineargs.h:288: error: expected ‘;’ before ‘static’
/usr/include/kcmdlineargs.h:311: error: ‘StdCmdLineArgs’ has not been declared
/usr/include/kcmdlineargs.h:330: error: ‘StdCmdLineArgs’ has not been declared
/usr/include/kcmdlineargs.h:311: error: ‘StdCmdLineArgs’ was not declared in this scope
/usr/include/kcmdlineargs.h:330: error: ‘StdCmdLineArgs’ was not declared in this scope
/usr/include/kcmdlineargs.h:656: error: expected constructor, destructor, or type conversion before ‘(’ token
In file included from ktigcc.cpp:30:
/usr/include/kaboutdata.h:248: error: default argument for parameter of type ‘const QByteArray&’ has type ‘const char [20]’
/usr/include/kaboutdata.h:867: error: expected ‘;’ before ‘<’ token
In file included from /usr/include/kicontheme.h:32,
                 from ktigcc.cpp:35:
/usr/include/kiconloader.h:436: error: expected ‘:’ before ‘Q_SLOTS’
/usr/include/kiconloader.h:440: error: expected primary-expression before ‘void’
/usr/include/kiconloader.h:440: error: expected ‘;’ before ‘void’
/usr/include/kiconloader.h:446: error: expected primary-expression before ‘void’
/usr/include/kiconloader.h:446: error: expected ‘;’ before ‘void’
ktigcc.cpp:53: error: ‘KCmdLineLastOption’ was not declared in this scope
ktigcc.cpp:54: warning: extended initializer lists only available with -std=c++0x or -std=gnu++0x
ktigcc.cpp: In function ‘int main(int, char**)’:
ktigcc.cpp:97: error: no matching function for call to ‘KAboutData::KAboutData(const char [7], const char [18], const char [5], const char [20], KAboutData::LicenseKey, const char [120], const char [318], const char [31], const char [22])’
/usr/include/kaboutdata.h:255: note: candidates are: KAboutData::KAboutData(const KAboutData&)
/usr/include/kaboutdata.h:239: note:                 KAboutData::KAboutData(const QByteArray&, const QByteArray&, const KLocalizedString&, const QByteArray&, const KLocalizedString&, KAboutData::LicenseKey, const KLocalizedString&, const KLocalizedString&, const QByteArray&, const QByteArray&)
ktigcc.cpp:99: error: the default argument for parameter 3 of ‘static void KCmdLineArgs::init(int, char**, const KAboutData*, int)’ has not yet been parsed
ktigcc.cpp:100: error: no matching function for call to ‘KCmdLineArgs::addCmdLineOptions(KCmdLineOptions [1])’
/usr/include/kcmdlineargs.h:395: note: candidates are: static void KCmdLineArgs::addCmdLineOptions(const KCmdLineOptions&, const KLocalizedString&, const QByteArray&, const QByteArray&)
ktigcc.cpp:101: error: ‘addCmdLineOptions’ is not a member of ‘KApplication’
ktigcc.cpp:105: error: ‘KIcon’ has not been declared
ktigcc.cpp:111: error: cannot convert ‘KSharedConfigPtr’ to ‘KConfig*’ in assignment
ktigcc.cpp:173: error: ‘class KApplication’ has no member named ‘setMainWidget’
ktigcc.cpp:176: error: ‘class KApplication’ has no member named ‘exec’
In file included from /usr/include/ksharedconfig.h:26,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from ktigcc.cpp:28:
/usr/include/ksharedptr.h: In destructor ‘KSharedPtr<T>::~KSharedPtr() [with T = KSharedConfig]’:
/usr/include/klocale.h:91:   instantiated from here
/usr/include/ksharedptr.h:90: error: ‘class KSharedConfig’ has no member named ‘ref’
make: *** [.obj/ktigcc.o] Error 1

```

Some of the error messages suggest kdelibs3 but it doesn't appear to be available in karmic?

Any help would be wonderful!
TIA,
Wayne

---

### Post by Speaks on 2010-11-29
I am encountering something very similar trying to build Konquest.

```
chris@chris-laptop:~/workspace/Konquest$ make
Scanning dependencies of target konquest_automoc
Generating planet.moc
Generating sector.moc
Generating minimapview.moc
Generating gamelogic.moc
Generating mainwin.moc
Generating map.moc
Generating mapitems.moc
Generating gameview.moc
Generating fleet.moc
Generating mapscene.moc
Generating newgamedlg.moc
Generating mapview.moc
[  0%] Built target konquest_automoc
[  5%] Generating ui_newGameDialog.h
Scanning dependencies of target konquest
[ 10%] Building CXX object CMakeFiles/konquest.dir/konquest_automoc.o
[ 15%] Building CXX object CMakeFiles/konquest.dir/Konquest.o
In file included from /usr/include/kdecore_export.h:24,
                 from /usr/include/kdeversion.h:30,
                 from /usr/include/kapplication.h:25,
                 from /home/chris/workspace/Konquest/Konquest.cc:22:
/usr/include/kdemacros.h:162: fatal error: QtCore/qglobal.h: No such file or directory
compilation terminated.
make[2]: *** [CMakeFiles/konquest.dir/Konquest.o] Error 1
make[1]: *** [CMakeFiles/konquest.dir/all] Error 2
make: *** [all] Error 2
chris@chris-laptop:~/workspace/Konquest$ ^C

```

---

### Post by ashmew2 on 2011-03-28
Was sing Maverick , then installed kubuntu-desktop..
Installed KDevelop after that , but it gave me all sorts of errors concerning header files (C++ Programming)...So , i went ahead and installed kde5libs-dev and the header file problem was solved , but then i started getting the :
```

/usr/include/kapplication.h:44: fatal error: QtGui/QApplication: No such file or directory

```

error. I explored the directories..and then found that the Qt* folders it expects inside the /usr/include directory are actually inside /usr/include/qt4..

I tried making a link , but to no avail...Any Suggestions ?

---

### Post by ashmew2 on 2011-03-28
Well , i dont really know whats up with #1 and #2 , but i fixed the error by making the appropriate CMakeLists.txt in KDevelop.
(Thanks to [http://techbase.kde.org/Development/Tutorials/First_Program](http://techbase.kde.org/Development/Tutorials/First_Program) , just scroll down)

Maybe someone who goes googling will find this ! :D

Cheers ! :D :D :D :D

---

### Post by agemon on 2011-03-29
> **ashmew2 said:**
> Well , i dont really know whats up with #1 and #2 , but i fixed the error by making the appropriate CMakeLists.txt in KDevelop.
(Thanks to [http://techbase.kde.org/Development/Tutorials/First_Program](http://techbase.kde.org/Development/Tutorials/First_Program) , just scroll down)

Maybe someone who goes googling will find this ! :D

Cheers ! :D :D :D :D

The link you provided has been moved to:[http://techbase.kde.org/Development/Tutorials/First_program](http://techbase.kde.org/Development/Tutorials/First_program) but in anycase, many thanks for the solution; I had the same problem compiling konquest as Speaks
cheers!

---


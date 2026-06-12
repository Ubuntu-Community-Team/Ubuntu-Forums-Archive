---
title: "Compiling qtella"
date: 2005-03-04
forum: General Help
---

### Post by cdhotfire on 2005-03-04
i was trying to compile this new p2p program i found i and i get this error:

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/isidro/qtella-0.6.5/missing: Unknown `--run' option
Try `/home/isidro/qtella-0.6.5/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for Qt moc...
Qt's moc not found! If you have installed Qt in an
unusual place, please use the "--with-qt-moc=" option
``` 

any help would be appreciated

---

### Post by rwabel on 2005-03-05
same for me here. But I've the libraries, but maybe they are not compiled with thread support. Is there a way to check if the libraries are compiled with thread support?

thanks
here is the output of the libraries:
rwabel@RALPH:~/compiling $ locate qt-mt
/usr/lib/libqt-mt.so.3
/usr/lib/libqt-mt.so.3.3.3
/usr/lib/libqt-mt.so.3.3
/usr/share/qt3/lib/libqt-mt.so.3
/usr/share/qt3/lib/libqt-mt.so.3.3

---

### Post by bored2k on 2005-03-05
[QUOTE=rwabel]same for me here. But I've the libraries, but maybe they are not compiled with thread support. Is there a way to check if the libraries are compiled with thread support?

thanks
here is the output of the libraries:
rwabel@RALPH:~/compiling $ locate qt-mt
/usr/lib/libqt-mt.so.3
/usr/lib/libqt-mt.so.3.3.3
/usr/lib/libqt-mt.so.3.3
/usr/share/qt3/lib/libqt-mt.so.3
/usr/share/qt3/lib/libqt-mt.so.3.3[/QUOTE]


> $./configure --with-qt-moc=/usr/lib/qt3/ 

and that does.... ?

---

### Post by rwabel on 2005-03-05
No luck. I tried with your idea and I tried all kind of other paths. Maybe it's that qt isn't compiled with threads.

---

### Post by metasquier on 2005-05-24
I was doing the same thing, and I got like one step further than that.  To includ the librarys you need to do:

```
./configure --with-qt-includes=/usr/include/qt3 --with-kde=no
``` 

If you have Kubuntu, or if you have KDE installed then all you need to do is:

```
./configure --with-qt-includes=/usr/include/qt3
``` 

The only problem is that for some reason there is no "qlist.h" header file, and upon doing the "make" it complains about this file not existing.  I tried getting the source code for this file, and just putting it in as a header file, but after that it complains about errors in the "main.cpp" file.  So Im stuck right now, tell me if it works for you.  Maybe Ill try including the KDE header files :)

---

### Post by rwabel on 2005-05-25
[QUOTE=metasquier]I was doing the same thing, and I got like one step further than that.  To includ the librarys you need to do:

```
./configure --with-qt-includes=/usr/include/qt3 --with-kde=no
``` 

If you have Kubuntu, or if you have KDE installed then all you need to do is:

```
./configure --with-qt-includes=/usr/include/qt3
``` 

The only problem is that for some reason there is no "qlist.h" header file, and upon doing the "make" it complains about this file not existing.  I tried getting the source code for this file, and just putting it in as a header file, but after that it complains about errors in the "main.cpp" file.  So Im stuck right now, tell me if it works for you.  Maybe Ill try including the KDE header files :)[/QUOTE]
 same for me here...too bad

---

### Post by rwabel on 2005-05-25
Ì've read somewhere in a forum that you need this package
 ```
libqt3-compat-headers
```

but didn't help, get now these errors
 ```
In file included from QtellaSub.cpp:39:
../include/MessengerContacts.h:3:32: BMessengerContacts.h: No such file or directory
In file included from ../include/MessengerContacts.h:4,
				 from QtellaSub.cpp:39:
../include/Messenger.h:3:24: BMessenger.h: No such file or directory
In file included from ../include/MessengerContacts.h:4,
				 from QtellaSub.cpp:39:
../include/Messenger.h:7: error: parse error before `{' token
../include/Messenger.h:8: error: virtual outside class declaration
../include/Messenger.h:8: error: non-member function `const char* className()'
   cannot have `const' method qualifier
../include/Messenger.h:8: error: virtual outside class declaration
../include/Messenger.h:8: error: virtual outside class declaration
../include/Messenger.h:8: error: virtual outside class declaration
../include/Messenger.h:8: error: virtual outside class declaration
../include/Messenger.h: In function `QObject* qObject()':
../include/Messenger.h:8: error: invalid use of `this' in non-member function
../include/Messenger.h: At global scope:
../include/Messenger.h:8: error: parse error before `private'
../include/Messenger.h:11: error: destructors must be member functions
../include/Messenger.h:16: error: non-member function `const QString& getWho()'
   cannot have `const' method qualifier
../include/Messenger.h:18: error: parse error before `private'
../include/Messenger.h:24: error: parse error before `}' token
In file included from QtellaSub.cpp:39:
../include/MessengerContacts.h:13: error: parse error before `{' token
../include/MessengerContacts.h:14: error: virtual outside class declaration
../include/MessengerContacts.h:14: error: non-member function `const char*
   className()' cannot have `const' method qualifier
../include/MessengerContacts.h:14: error: virtual outside class declaration
../include/MessengerContacts.h:14: error: virtual outside class declaration
../include/MessengerContacts.h:14: error: virtual outside class declaration
../include/MessengerContacts.h:14: error: virtual outside class declaration
../include/MessengerContacts.h: In function `QObject* qObject()':
../include/MessengerContacts.h:14: error: redefinition of `QObject* qObject()'
../include/Messenger.h:8: error: `QObject* qObject()' previously defined here
../include/MessengerContacts.h:14: error: redefinition of `QObject* qObject()'
../include/Messenger.h:8: error: `QObject* qObject()' previously defined here
../include/MessengerContacts.h:14: error: invalid use of `this' in non-member
   function
../include/MessengerContacts.h: At global scope:
../include/MessengerContacts.h:14: error: default argument given for parameter
   2 of `QString tr(const char*, const char*)'
../include/Messenger.h:8: error: after previous specification in `QString
   tr(const char*, const char*)'
../include/MessengerContacts.h:14: error: default argument given for parameter
   2 of `QString trUtf8(const char*, const char*)'
../include/Messenger.h:8: error: after previous specification in `QString
   trUtf8(const char*, const char*)'
../include/MessengerContacts.h:14: error: parse error before `private'
../include/MessengerContacts.h:18: error: destructors must be member functions
../include/MessengerContacts.h:24: error: syntax error before `*' token
../include/MessengerContacts.h:27: error: parse error before `private'
../include/MessengerContacts.h:30: error: virtual outside class declaration
../include/MessengerContacts.h:31: error: virtual outside class declaration
../include/MessengerContacts.h:33: error: parse error before `protected'
../include/MessengerContacts.h:35: error: syntax error before `*' token
../include/MessengerContacts.h:42: error: type/value mismatch at argument 1 in
   template parameter list for `template<class type> class QPtrList'
../include/MessengerContacts.h:42: error:   expected a type, got `Messenger'
../include/MessengerContacts.h:42: error: ISO C++ forbids declaration of `
   _messengers' with no type
../include/MessengerContacts.h:43: error: parse error before `}' token
QtellaSub.cpp: In constructor `QtellaSub::QtellaSub(QApplication*, const char*,
   unsigned int)':
QtellaSub.cpp:454: error: parse error before `(' token
QtellaSub.cpp:455: error: `setIcon' undeclared (first use this function)
QtellaSub.cpp:455: error: (Each undeclared identifier is reported only once for
   each function it appears in.)
QtellaSub.cpp:456: error: `hide' undeclared (first use this function)
QtellaSub.cpp:462: error: `init' undeclared (first use this function)
QtellaSub.cpp: In member function `void QtellaSub::slotMenu(int)':
QtellaSub.cpp:1793: error: cannot convert `MessengerContacts*' to `QWidget*' in
   assignment
make[2]: *** [QtellaSub.o] Error 1
make[2]: Leaving directory `/home/rwabel/compiling/qtella-0.7.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rwabel/compiling/qtella-0.7.0'
make: *** [all] Error 2

```  

I'll try later if I can fix that....well, finally why do I need qtella? ;-)

---


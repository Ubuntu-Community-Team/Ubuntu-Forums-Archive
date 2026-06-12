---
title: "error: #error &quot;Qt has not been ported to this OS"
date: 2009-12-21
forum: General Help
---

### Post by shariefbe on 2009-12-21
Hello,
   I am trying to compile the QT browser for arm processor. But i am getting the below error as 

```

../../include/QtCore/../../src/corelib/global/qglobal.h:261:4: error: #error "Qt has not been ported to this OS - talk to qt-bugs@trolltech.com"
make[1]: *** [.pch/release-shared-emb-arm/QtCore.gch/c++] Error 1
make[1]: Leaving directory `/home/ariem/Desktop/qt-everywhere-opensource-src-4.6.0/src/corelib'
make: *** [sub-corelib-make_default-ordered] Error 2
ariem@ariem-desktop:~/Desktop/qt-everywhere-opensource-src-4.6.0$ 

```
Can anyone help me what will be the problem.

---

### Post by shariefbe on 2009-12-21
Now i am getting this error

```

arm-none-linux-gnueabi-g++ -c -pipe -fno-exceptions -O2 -Wall -W -D_REENTRANT -fPIC -DQT_SHARED -DQT_BUILD_CORE_LIB -DQT_NO_USING_NAMESPACE -DQT_NO_CAST_TO_ASCII -DQT_ASCII_CAST_WARNINGS -DQT3_SUPPORT -DQT_MOC_COMPAT -DHB_EXPORT=Q_CORE_EXPORT -DQT_NO_DEBUG -I../../mkspecs/qws/linux-arm-g++ -I. -I../../include -I../../include/QtCore -I.rcc/release-shared-emb-arm -Iglobal -I../3rdparty/zlib -I../3rdparty/harfbuzz/src -I../3rdparty/md5 -I../3rdparty/md4 -I.moc/release-shared-emb-arm -o .obj/release-shared-emb-arm/qabstractanimation.o animation/qabstractanimation.cpp
make[1]: arm-none-linux-gnueabi-g++: Command not found
make[1]: *** [.obj/release-shared-emb-arm/qabstractanimation.o] Error 127
make[1]: Leaving directory `/home/ariem/Desktop/qt-everywhere-opensource-src-4.6.0/src/corelib'
make: *** [sub-corelib-make_default-ordered] Error 2
root@ariem-desktop:/home/ariem/Desktop/qt-everywhere-opensource-src-4.6.0# cd mkspecs/qws/linux-arm-g++/

```

---

### Post by EOSYSTEMS on 2010-10-14
Were you able to identify the Command not found error associated with qabstractanimation.cpp?  I have exactly the same error using Qt embedded version 4.7.

The configure line I am using is:
./configure -embedded arm -platform /qws/linux-x86-g++ -xplatform /qws/linux-arm-gnueabi-g++ -qvfb -little-endian

The error is:
arm-none-linux-gnueabi-g++ -c -pipe -O2 -Wall -W -D_REENTRANT -fPIC -DQT_SHARED -DQT_BUILD_CORE_LIB -DQT_NO_USING_NAMESPACE -DQT_NO_CAST_TO_ASCII -DQT_ASCII_CAST_WARNINGS -DQT3_SUPPORT -DQT_MOC_COMPAT -DQT_USE_FAST_OPERATOR_PLUS -DQT_USE_FAST_CONCATENATION -DELF_INTERPRETER=\"/lib/ld-linux.so.2\" -DHB_EXPORT=Q_CORE_EXPORT -DQT_NO_DEBUG -D_LARGEFILE64_SOURCE -D_LARGEFILE_SOURCE -I../../mkspecs/qws/linux-arm-gnueabi-g++ -I. -I../../include -I../../include/QtCore -I.rcc/release-shared-emb-arm -Iglobal -I../3rdparty/zlib -I../3rdparty/harfbuzz/src -I../3rdparty/md5 -I../3rdparty/md4 -I.moc/release-shared-emb-arm -o .obj/release-shared-emb-arm/qabstractanimation.o animation/qabstractanimation.cpp
make[1]: arm-none-linux-gnueabi-g++: Command not found
make[1]: *** [.obj/release-shared-emb-arm/qabstractanimation.o] Error 127
make[1]: Leaving directory `/home/richard/EO_Work/OMAP/Qt_embedded/qt-everywhere-opensource-src-4.7.0/src/corelib'
make: *** [sub-corelib-make_default-ordered] Error 2

Thank you in advance.  Richard

---


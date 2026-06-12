---
title: "error when i compile JackTrip"
date: 2010-08-25
forum: General Help
---

### Post by firens on 2010-08-25
Hello all 

my  problem is that I tried to install software called Jacktrip on Ubuntu Lucid, which allows for HQ audio communicationson the net ...  ... the only worry is that i have a problem during the compilation  

The software requires are qt3-dev-tools and audio jack that I installed on my PC ... 
But...When I go to compile JackTrip as indicated by the instructions using qmake jacktrip.pro and make release, that's what I get ...

```

make -f Makefile.Release
make[1]: entrant dans le répertoire « /media/DATA/jacktrip/src »
g++ -c -pipe -g -O2 -O2 -D_REENTRANT -Wall -W -D__LINUX__ -DQT_NO_DEBUG -DQT_NETWORK_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4 -I../../qt4/include -Irelease -o release/DataProtocol.o DataProtocol.cpp
g++ -c -pipe -g -O2 -O2 -D_REENTRANT -Wall -W -D__LINUX__ -DQT_NO_DEBUG -DQT_NETWORK_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4 -I../../qt4/include -Irelease -o release/JackAudioInterface.o JackAudioInterface.cpp
g++ -c -pipe -g -O2 -O2 -D_REENTRANT -Wall -W -D__LINUX__ -DQT_NO_DEBUG -DQT_NETWORK_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4 -I../../qt4/include -Irelease -o release/JackTrip.o JackTrip.cpp
g++ -c -pipe -g -O2 -O2 -D_REENTRANT -Wall -W -D__LINUX__ -DQT_NO_DEBUG -DQT_NETWORK_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4 -I../../qt4/include -Irelease -o release/jacktrip_globals.o jacktrip_globals.cpp
jacktrip_globals.cpp: In function ‘int set_fifo_priority(bool)’:
jacktrip_globals.cpp:146: error: ‘stderr’ was not declared in this scope
jacktrip_globals.cpp:148: error: ‘fprintf’ was not declared in this scope
jacktrip_globals.cpp:158: error: ‘stderr’ was not declared in this scope
jacktrip_globals.cpp:159: error: ‘fprintf’ was not declared in this scope
jacktrip_globals.cpp: In function ‘int set_realtime_priority()’:
jacktrip_globals.cpp:177: error: ‘perror’ was not declared in this scope
make[1]: *** [release/jacktrip_globals.o] Erreur 1
make[1]: quittant le répertoire « /media/DATA/jacktrip/src »
make: *** [release] Erreur 2

```I  had problems with other .h (QThread, jack etc...), but i resolved the problem by copying them  directly to the folder where I compile the program..

... someone can help me (excuse me for my bad english)

Thk a lot

---


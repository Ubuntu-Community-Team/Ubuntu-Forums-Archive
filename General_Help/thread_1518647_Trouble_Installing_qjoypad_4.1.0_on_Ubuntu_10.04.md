---
title: "Trouble Installing qjoypad 4.1.0 on Ubuntu 10.04"
date: 2010-06-26
forum: General Help
---

### Post by japzone on 2010-06-26
I've been trying for 3 hours to get it to install but I just can't get it to install. I keep on getting an error when compiling.
```
qjoypad-4.1.0/src$ ./config
Error: you will need libxtst to compile this program

```
I've tried installing everything suggested that's close to QT and XWindows(Xorg). Turns out Xorg comes with 10.04. I've installed anything suggested that'd help with QT (Probably ended up installing a bunch of unneeded junk on my Computer). I even looked into libxtst but everything I look at and check says it's installed. So I just can't figure out why.

I tried installing older version but that gives me an error as well.
```
user@ubuntu:~/qjoypad-3.4.1/src$ ./config

Configuring QJoyPad installation...
------------------------------------------------------------

Device directory: /dev/input
-- Devices will be looked for in:
     /dev/input/js0
     /dev/input/js1
     etc.

Prefix directory: /usr/local
-- Files to be installed in:
     /usr/local/bin
     /usr/local/doc
     /usr/local/share/pixmaps
	 
---------------------------------------------------------
If these settings are okay, go ahead and run 'make' and
then 'make install'.

To make changes, run ./config --help for details.

user@ubuntu:~/qjoypad-3.4.1/src$ make
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DDEVDIR='"/dev/input"' -DICON24='"/usr/local/share/pixmaps/qjoypad/icon24.png"' -DICON64='"/usr/local/share/pixmaps/qjoypad/icon64.png"' -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -Itrayicon -I/usr/include/qt3 -o axis.o axis.cpp
In file included from component.h:13,
                 from axis.h:8,
                 from axis.cpp:1:
event.h:5:34: error: X11/extensions/XTest.h: No such file or directory
axis.cpp: In member function ‘virtual void Axis::move(bool)’:
axis.cpp:267: warning: ‘e.xevent::value2’ may be used uninitialized in this function
axis.cpp:267: warning: ‘e.xevent::value1’ may be used uninitialized in this function
axis.cpp:267: warning: ‘e.xevent::type’ may be used uninitialized in this function
make: *** [axis.o] Error 1
user@ubuntu:~/qjoypad-3.4.1/src$ make install
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DDEVDIR='"/dev/input"' -DICON24='"/usr/local/share/pixmaps/qjoypad/icon24.png"' -DICON64='"/usr/local/share/pixmaps/qjoypad/icon64.png"' -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -Itrayicon -I/usr/include/qt3 -o axis.o axis.cpp
In file included from component.h:13,
                 from axis.h:8,
                 from axis.cpp:1:
event.h:5:34: error: X11/extensions/XTest.h: No such file or directory
axis.cpp: In member function ‘virtual void Axis::move(bool)’:
axis.cpp:267: warning: ‘e.xevent::value2’ may be used uninitialized in this function
axis.cpp:267: warning: ‘e.xevent::value1’ may be used uninitialized in this function
axis.cpp:267: warning: ‘e.xevent::type’ may be used uninitialized in this function
make: *** [axis.o] Error 1

```

Any help would be GREATLY appreciated as I have been desperately wanting to get a key2pad translator working in linux. My pad actually came with one, It works great, When I'm using Windows. Unfortunately it doesn't run on Linux, not even under Wine so It's useless to me now since I rarely use Windows anymore. Please Help me get qjoypad to work [-o<

---

### Post by meepone23 on 2010-07-24
same problem spent all night on it even tried downloading joy2key and theres no gui for that for some reason and i dont even know what rejoystick does. please help

---

### Post by meepone23 on 2010-07-28
Bump

---

### Post by Rycuda on 2010-08-04
[INDENT]qjoypad-4.1.0/src$ ./config
Error: you will need libxtst to compile this program[/INDENT]

sudo aptitude install libxtst-dev

then head back to 
./configure
make
sudo make install

---

### Post by taon7 on 2010-11-08
how do i re-make? it just says 'nothing to do' since i already made it..

i'm on 10.10. cant run the program after install either. dpkg calls it 'src' but typing src does nothing...

---

### Post by nickleboyblue on 2011-02-11
Re-run ./configure in the src directory of qjoypad.  *Then* run make and make install again and you'll get a working qjoypad.

---


---
title: "Muon broken after update"
date: 2012-09-13
forum: General Help
---

### Post by horseatingweeds on 2012-09-13
I did some updates to Muon, now it's broken. Update manager, software manager, and package manager are all gone under the System menu. 

I tried uninstalling and reinstalling from the terminal. Here's what it gave me: 

```

ben@kubuntu-640WD:~$ sudo apt-get purge muon
[sudo] password for ben: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package muon is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libkrb5-3:i386 libatk1.0-0:i386 libk5crypto3:i386 libstdc++6:i386 libxfixes3:i386
  libaccess-bridge-java libxcomposite1:i386 libldap-2.4-2:i386 libidn11:i386 libnss3:i386
  libwrap0:i386 nspluginwrapper libsamplerate0:i386 ubufox libjack-jackd2-0:i386
  libnspr4-0d:i386 libcairo2:i386 libgnutls26:i386 libtasn1-3:i386 libfreetype6:i386
  libexpat1:i386 libdatrie1:i386 libavahi-common-data:i386 libjson0:i386
  libgdk-pixbuf2.0-0:i386 flashplugin-downloader:i386 libxcb1:i386
  libaccess-bridge-java-jni libxau6:i386 libpixman-1-0:i386 libcups2:i386 libcurl3:i386
  libxinerama1:i386 libkrb5support0:i386 nspluginviewer:i386 libxft2:i386 libice6:i386
  libspeexdsp1:i386 libxdmcp6:i386 libgcrypt11:i386 libthai0:i386 libkeyutils1:i386
  libasound2:i386 libflac8:i386 libxrender1:i386 libnspr4:i386 libvorbisenc2:i386
  libasyncns0:i386 libtiff4:i386 libjasper1:i386 libpng12-0:i386 libjpeg62:i386
  libavahi-client3:i386 libx11-6:i386 libsasl2-2:i386 libfontconfig1:i386
  libpango1.0-0:i386 libsm6:i386 libpulse0:i386 libxdamage1:i386 libxcb-render0:i386
  librtmp0:i386 libgssapi-krb5-2:i386 libxi6:i386 libvorbis0a:i386 libxcursor1:i386
  libxcb-shm0:i386 libxt6:i386 libxext6:i386 libsasl2-modules:i386 libavahi-common3:i386
  libxrandr2:i386 libnss3-1d:i386 libsndfile1:i386 libsqlite3-0:i386 libgtk2.0-0:i386
  libssl1.0.0:i386 libasound2-plugins:i386 libgpg-error0:i386 libogg0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ben@kubuntu-640WD:~$ sudo apt-get install muon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 muon : Depends: libmuonprivate1 but it is not going to be installed
        Depends: libqtcore4 (>= 4:4.8.0) but 4:4.7.4-0ubuntu8.1 is to be installed
        Depends: libqtgui4 (>= 4:4.8.0) but 4:4.7.4-0ubuntu8.1 is to be installed
        Recommends: muon-updater but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

I'm not sure what to do from here. Is there a way to install an older version of muon through the terminal? What should I do?

Kubuntu 11.10

---

### Post by horseatingweeds on 2012-09-13
I tried:

sudo apt-get install --fix-broken
sudo apt-get autoclean
sudo apt-get autoremove

Then tried uninstalling and reinstalling again, with same results as above.

---

### Post by horseatingweeds on 2012-09-13
Someone in the IRC channel helped me figure out a repository was the trouble. I remember now, when I first installed Kubuntu 11.10 64bit, Muon was crashing, and the solution was to use an older version, which came from this repository.

After commenting out these repositories I installed Muon successfully. 

So now the package manager is back, however, the separate Software Center and Update manager are still gone. Aren't these part of Muon? I've been searching around and it looks like everything is installed.

---

### Post by drmrgd on 2012-09-13
I believe you also need to add muon-installer, muon-notifier, and muon-updater in addition to muon (the package manager).  Try installing those to see if it fixes it.

---

### Post by horseatingweeds on 2012-09-14
Hi drmrgd, I had muon-installer missing from that list. After installing it, software center reappeared in the menu, but it crashed when I open it. I tried filing a bug report, but it said Bugzilla encountered an error.

I also tried uninstalling muon and reinstalling:

```
apt-get --purge remove muon
apt-get install muon
```

No change though. Package Manager works. Software Center crashed. And Upgrade Manager is missing from the menu. 

Here is what the bug report gives after Software Center crashes:

```
Application: Muon Software Center (muon-installer), signal: Segmentation fault
[Current thread is 1 (Thread 0x7f439fc5c780 (LWP 3371))]

Thread 2 (Thread 0x7f438b3e0700 (LWP 3375)):
#0  timerSourcePrepareHelper (src=0x155fc00, timeout=0x7f438b3dfc3c) at kernel/qeventdispatcher_glib.cpp:136
#1  0x00007f439e9df4f5 in timerSourcePrepare (source=<optimized out>, timeout=<optimized out>) at kernel/qeventdispatcher_glib.cpp:169
#2  0x00007f4399093ff2 in g_main_context_prepare () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007f4399094dfd in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x00007f4399095429 in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x00007f439e9dff3e in QEventDispatcherGlib::processEvents (this=0x1514cd0, flags=<optimized out>) at kernel/qeventdispatcher_glib.cpp:424
#6  0x00007f439e9b3cf2 in QEventLoop::processEvents (this=<optimized out>, flags=...) at kernel/qeventloop.cpp:149
#7  0x00007f439e9b3ef7 in QEventLoop::exec (this=0x7f438b3dfdd0, flags=...) at kernel/qeventloop.cpp:201
#8  0x00007f439e8cb27f in QThread::exec (this=<optimized out>) at thread/qthread.cpp:498
#9  0x00007f439e996cbf in QInotifyFileSystemWatcherEngine::run (this=0x14d1d80) at io/qfilesystemwatcher_inotify.cpp:248
#10 0x00007f439e8cdd05 in QThreadPrivate::start (arg=0x14d1d80) at thread/qthread_unix.cpp:331
#11 0x00007f4399b76efc in start_thread (arg=0x7f438b3e0700) at pthread_create.c:304
#12 0x00007f439c82d59d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112
#13 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f439fc5c780 (LWP 3371)):
[KCrash Handler]
#6  0x00007f439e91ba5e in QtPrivate::QStringList_contains (that=0x7ffff957b9b0, str=..., cs=Qt::CaseSensitive) at tools/qstringlist.cpp:318
#7  0x000000000042416b in contains (cs=Qt::CaseSensitive, str=..., this=0x7ffff957b9b0) at /usr/include/qt4/QtCore/qstringlist.h:171
#8  ApplicationWindow::populateViews (this=0x146c9f0) at /build/buildd/muon-1.2.1/installer/ApplicationWindow.cpp:229
#9  0x000000000042771c in ApplicationWindow::qt_metacall (this=0x146c9f0, _c=QMetaObject::InvokeMetaMethod, _id=<optimized out>, _a=0x7ffff957bf80) at /build/buildd/muon-1.2.1/obj-x86_64-linux-gnu/installer/ApplicationWindow.moc:113
#10 0x00007f439e9c7eba in QMetaObject::activate (sender=0x14a9740, m=<optimized out>, local_signal_index=<optimized out>, argv=0x0) at kernel/qobject.cpp:3278
#11 0x000000000041c31c in ApplicationBackend::qt_metacall (this=0x14a9740, _c=QMetaObject::InvokeMetaMethod, _id=<optimized out>, _a=0x7ffff957c0e0) at /build/buildd/muon-1.2.1/obj-x86_64-linux-gnu/installer/moc_ApplicationBackend.cpp:109
#12 0x00007f439e9c7eba in QMetaObject::activate (sender=0x146c9f0, m=<optimized out>, local_signal_index=<optimized out>, argv=0x7ffff957c0e0) at kernel/qobject.cpp:3278
#13 0x00007f439f842e7f in MuonMainWindow::backendReady (this=<optimized out>, _t1=0x14e3590) at /build/buildd/muon-1.2.1/obj-x86_64-linux-gnu/libmuon/MuonMainWindow.moc:168
#14 0x00007f439f842f8e in MuonMainWindow::initObject (this=0x146c9f0) at /build/buildd/muon-1.2.1/libmuon/MuonMainWindow.cpp:79
#15 0x0000000000422fa0 in ApplicationWindow::initObject (this=0x146c9f0) at /build/buildd/muon-1.2.1/installer/ApplicationWindow.cpp:116
#16 0x0000000000427619 in ApplicationWindow::qt_metacall (this=0x146c9f0, _c=QMetaObject::InvokeMetaMethod, _id=<optimized out>, _a=0x7ffff957c1b0) at /build/buildd/muon-1.2.1/obj-x86_64-linux-gnu/installer/ApplicationWindow.moc:104
#17 0x00007f439e9c7eba in QMetaObject::activate (sender=0x152bb80, m=<optimized out>, local_signal_index=<optimized out>, argv=0x0) at kernel/qobject.cpp:3278
#18 0x00007f439e9cff7f in QSingleShotTimer::timerEvent (this=0x152bb80) at kernel/qtimer.cpp:308
#19 0x00007f439e9cb789 in QObject::event (this=0x152bb80, e=<optimized out>) at kernel/qobject.cpp:1181
#20 0x00007f439cfee474 in notify_helper (e=0x7ffff957c720, receiver=0x152bb80, this=0x131b100) at kernel/qapplication.cpp:4486
#21 QApplicationPrivate::notify_helper (this=0x131b100, receiver=0x152bb80, e=0x7ffff957c720) at kernel/qapplication.cpp:4458
#22 0x00007f439cff32e1 in QApplication::notify (this=0x7ffff957ca20, receiver=0x152bb80, e=0x7ffff957c720) at kernel/qapplication.cpp:4365
#23 0x00007f439e1d3466 in KApplication::notify (this=0x7ffff957ca20, receiver=0x152bb80, event=0x7ffff957c720) at ../../kdeui/kernel/kapplication.cpp:311
#24 0x00007f439e9b4afc in QCoreApplication::notifyInternal (this=0x7ffff957ca20, receiver=0x152bb80, event=0x7ffff957c720) at kernel/qcoreapplication.cpp:787
#25 0x00007f439e9e1d62 in sendEvent (event=0x7ffff957c720, receiver=<optimized out>) at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:215
#26 QTimerInfoList::activateTimers (this=0x131a500) at kernel/qeventdispatcher_unix.cpp:603
#27 0x00007f439e9df514 in timerSourceDispatch (source=<optimized out>) at kernel/qeventdispatcher_glib.cpp:184
#28 0x00007f4399094a5d in g_main_context_dispatch () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#29 0x00007f4399095258 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#30 0x00007f4399095429 in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#31 0x00007f439e9dfed6 in QEventDispatcherGlib::processEvents (this=0x12f16f0, flags=<optimized out>) at kernel/qeventdispatcher_glib.cpp:422
#32 0x00007f439d09610e in QGuiEventDispatcherGlib::processEvents (this=<optimized out>, flags=<optimized out>) at kernel/qguieventdispatcher_glib.cpp:204
#33 0x00007f439e9b3cf2 in QEventLoop::processEvents (this=<optimized out>, flags=...) at kernel/qeventloop.cpp:149
#34 0x00007f439e9b3ef7 in QEventLoop::exec (this=0x7ffff957c9b0, flags=...) at kernel/qeventloop.cpp:201
#35 0x00007f439e9b8789 in QCoreApplication::exec () at kernel/qcoreapplication.cpp:1064
#36 0x000000000041bd67 in main (argc=1, argv=0x7ffff957cc98) at /build/buildd/muon-1.2.1/installer/main.cpp:61
```

---

### Post by horseatingweeds on 2012-09-14
Would it be wise to upgrade this installation from Kubuntu 11.10 to 12.4?

---

### Post by Epodx64 on 2012-09-14
> **horseatingweeds said:**
> Would it be wise to upgrade this installation from Kubuntu 11.10 to 12.4?

Only if your gonna do a clean install

you could try adding this PPA [https://launchpad.net/~echidnaman/+archive/qapt](https://launchpad.net/~echidnaman/+archive/qapt) and upgrading to the newer version of muon in the mean time just download synaptic it will double as an updater software manager etc...

---

### Post by horseatingweeds on 2012-09-14
What kind of problems might occur from upgrading?

---

### Post by horseatingweeds on 2012-10-04
I'm still trying to figure this out. Is the information given after the crash a stack trace? This is the last line: 

#36 0x000000000041bd67 in main (argc=1, argv=0x7ffff957cc98) at /build/buildd/muon-1.2.1/installer/main.cpp:61

What does this mean? Why would Muon run main.cpp in the installer folder when I'm trying to open Software Center?

---

### Post by Sdrabor on 2013-01-15
horseatingweeds, did you ever find a solution to this?  I'm having the same issue on a clean install of 11.10 64-bit... so far haven't been able to find a solution outside of installing synaptic as a workaround.

---

### Post by r.stiltskin on 2013-02-26
Why install 11.10 after 12.04LTS and 12.10 have been released?

I remember some problems with Muon a year or two ago similar to what you describe, but the 12.x versions seem to have that all fixed.

---


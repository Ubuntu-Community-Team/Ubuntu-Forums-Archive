---
title: "Issues with Kubuntu 11.10"
date: 2012-01-26
forum: General Help
---

### Post by davethewave83 on 2012-01-26
I installed Kubuntu 11.10
just after, I launched Muon Software Center. It opens a window up, and then closes with a segmentation fault. ```
Application: Muon Software Center (muon-installer), signal: Segmentation fault
[Current thread is 1 (Thread 0x7f6a1c8e2780 (LWP 2932))]

Thread 2 (Thread 0x7f6a0806e700 (LWP 2936)):
#0  0x00007f6a194a8773 in __GI___poll (fds=<optimized out>, nfds=<optimized out>, timeout=<optimized out>) at ../sysdeps/unix/sysv/linux/poll.c:87
#1  0x00007f6a15d1df68 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f6a15d1e429 in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007f6a1b666ed6 in QEventDispatcherGlib::processEvents (this=0x1419210, flags=<optimized out>) at kernel/qeventdispatcher_glib.cpp:422
#4  0x00007f6a1b63acf2 in QEventLoop::processEvents (this=<optimized out>, flags=...) at kernel/qeventloop.cpp:149
#5  0x00007f6a1b63aef7 in QEventLoop::exec (this=0x7f6a0806ddd0, flags=...) at kernel/qeventloop.cpp:201
#6  0x00007f6a1b55227f in QThread::exec (this=<optimized out>) at thread/qthread.cpp:498
#7  0x00007f6a1b61dcbf in QInotifyFileSystemWatcherEngine::run (this=0x14626b0) at io/qfilesystemwatcher_inotify.cpp:248
#8  0x00007f6a1b554d05 in QThreadPrivate::start (arg=0x14626b0) at thread/qthread_unix.cpp:331
#9  0x00007f6a167ffefc in start_thread (arg=0x7f6a0806e700) at pthread_create.c:304
#10 0x00007f6a194b489d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112
#11 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f6a1c8e2780 (LWP 2932)):
[KCrash Handler]
#6  0x00007f6a1b5a2a5e in QtPrivate::QStringList_contains (that=0x7fff155c5110, str=..., cs=Qt::CaseSensitive) at tools/qstringlist.cpp:318
#7  0x000000000042416b in contains (cs=Qt::CaseSensitive, str=..., this=0x7fff155c5110) at /usr/include/qt4/QtCore/qstringlist.h:171
#8  ApplicationWindow::populateViews (this=0x13f1710) at /build/buildd/muon-1.2.1/installer/ApplicationWindow.cpp:229
#9  0x000000000042771c in ApplicationWindow::qt_metacall (this=0x13f1710, _c=QMetaObject::InvokeMetaMethod, _id=<optimized out>, _a=0x7fff155c56e0) at /build/buildd/muon-1.2.1/obj-x86_64-linux-gnu/installer/ApplicationWindow.moc:113
#10 0x00007f6a1b64eeba in QMetaObject::activate (sender=0x1433770, m=<optimized out>, local_signal_index=<optimized out>, argv=0x0) at kernel/qobject.cpp:3278
#11 0x000000000041c31c in ApplicationBackend::qt_metacall (this=0x1433770, _c=QMetaObject::InvokeMetaMethod, _id=<optimized out>, _a=0x7fff155c5840) at /build/buildd/muon-1.2.1/obj-x86_64-linux-gnu/installer/moc_ApplicationBackend.cpp:109
#12 0x00007f6a1b64eeba in QMetaObject::activate (sender=0x13f1710, m=<optimized out>, local_signal_index=<optimized out>, argv=0x7fff155c5840) at kernel/qobject.cpp:3278
#13 0x00007f6a1c4c4e7f in MuonMainWindow::backendReady (this=<optimized out>, _t1=0x1496210) at /build/buildd/muon-1.2.1/obj-x86_64-linux-gnu/libmuon/MuonMainWindow.moc:168
#14 0x00007f6a1c4c4f8e in MuonMainWindow::initObject (this=0x13f1710) at /build/buildd/muon-1.2.1/libmuon/MuonMainWindow.cpp:79
#15 0x0000000000422fa0 in ApplicationWindow::initObject (this=0x13f1710) at /build/buildd/muon-1.2.1/installer/ApplicationWindow.cpp:116
#16 0x0000000000427619 in ApplicationWindow::qt_metacall (this=0x13f1710, _c=QMetaObject::InvokeMetaMethod, _id=<optimized out>, _a=0x7fff155c5910) at /build/buildd/muon-1.2.1/obj-x86_64-linux-gnu/installer/ApplicationWindow.moc:104
#17 0x00007f6a1b64eeba in QMetaObject::activate (sender=0x1496e30, m=<optimized out>, local_signal_index=<optimized out>, argv=0x0) at kernel/qobject.cpp:3278
#18 0x00007f6a1b656f7f in QSingleShotTimer::timerEvent (this=0x1496e30) at kernel/qtimer.cpp:308
#19 0x00007f6a1b652789 in QObject::event (this=0x1496e30, e=<optimized out>) at kernel/qobject.cpp:1181
#20 0x00007f6a19c75474 in notify_helper (e=0x7fff155c5e80, receiver=0x1496e30, this=0x12aae60) at kernel/qapplication.cpp:4486
#21 QApplicationPrivate::notify_helper (this=0x12aae60, receiver=0x1496e30, e=0x7fff155c5e80) at kernel/qapplication.cpp:4458
#22 0x00007f6a19c7a2e1 in QApplication::notify (this=0x7fff155c6180, receiver=0x1496e30, e=0x7fff155c5e80) at kernel/qapplication.cpp:4365
#23 0x00007f6a1ae5a466 in KApplication::notify (this=0x7fff155c6180, receiver=0x1496e30, event=0x7fff155c5e80) at ../../kdeui/kernel/kapplication.cpp:311
#24 0x00007f6a1b63bafc in QCoreApplication::notifyInternal (this=0x7fff155c6180, receiver=0x1496e30, event=0x7fff155c5e80) at kernel/qcoreapplication.cpp:787
#25 0x00007f6a1b668d62 in sendEvent (event=0x7fff155c5e80, receiver=<optimized out>) at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:215
#26 QTimerInfoList::activateTimers (this=0x12a7bd0) at kernel/qeventdispatcher_unix.cpp:603
#27 0x00007f6a1b666514 in timerSourceDispatch (source=<optimized out>) at kernel/qeventdispatcher_glib.cpp:184
#28 0x00007f6a15d1da5d in g_main_context_dispatch () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#29 0x00007f6a15d1e258 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#30 0x00007f6a15d1e429 in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#31 0x00007f6a1b666ed6 in QEventDispatcherGlib::processEvents (this=0x12826f0, flags=<optimized out>) at kernel/qeventdispatcher_glib.cpp:422
#32 0x00007f6a19d1d10e in QGuiEventDispatcherGlib::processEvents (this=<optimized out>, flags=<optimized out>) at kernel/qguieventdispatcher_glib.cpp:204
#33 0x00007f6a1b63acf2 in QEventLoop::processEvents (this=<optimized out>, flags=...) at kernel/qeventloop.cpp:149
#34 0x00007f6a1b63aef7 in QEventLoop::exec (this=0x7fff155c6110, flags=...) at kernel/qeventloop.cpp:201
#35 0x00007f6a1b63f789 in QCoreApplication::exec () at kernel/qcoreapplication.cpp:1064
#36 0x000000000041bd67 in main (argc=5, argv=0x7fff155c63f8) at /build/buildd/muon-1.2.1/installer/main.cpp:61

```

so I forget about using that for now and instead launch rekonq. 
rekonq loads the main page, but no images appear, instead of appearing on the website, the images all open individually in Gwenview (spamming my desktop) 

I try to open Konsole but it never starts, when I open home or root folder, it says "Could not start process Unable to create io-slave: klauncher said: Unknown protocol 'file'

Muon Update Manager pops up saying there are updates available, so I think "maybe this will fix my Kubuntu" so I press to update, but it stops at 56% and never progresses

so I try to run Konsole from ALT F2 but as soon as I press alt f2, everything locks up. I tried Alt+sysrq REISUB but nothing happened, so I hard-powered off. 

Powered on.

Kubuntu loads, but there is no Wi-Fi and my touchpad is not working, so I fight my way through using keyboard to try to find out where my touchpad and wi-fi functionality went, finally resorting to Konsole (which launched this time) in Konsole I dpkg --configure -a

reboot

everything seems to be working

I launch rekonq and go to my google mail, it asks for login name and password, after supplying my username and password and pressing submit, it loads the authorization page in HTML code, and never goes to my inbox. :confused:

so I install firefox

and go to my inbox (it works) 

also, the IRC "Quassel IRC" crashes when I use the Ctrl+F to search through the text, if I search once it works, if I search a second time it crashes.

is 11.10 beta? and if so what is the stable version I should download? 

Thanks :)

---

### Post by paradigm2 on 2012-02-03
Hi, I just wanted to report that I had the same strangeness with Muon and rekonq/gwenview.

[http://ubuntuforums.org/showthread.php?p=11661448](http://ubuntuforums.org/showthread.php?p=11661448)

Also rekonq at one time was telling me that it did not know how to handle the http protocol. (!)

You message is over a week old but I ended up installing OpenSUSE.  You might try re-installing Kubuntu though to see if the same thing occurs.  It could possibly be some strangely botched install despite us both having roughly the same issues.

---

### Post by davethewave83 on 2012-02-03
> **paradigm2 said:**
> Hi, I just wanted to report that I had the same strangeness with Muon and rekonq/gwenview.

[http://ubuntuforums.org/showthread.php?p=11661448](http://ubuntuforums.org/showthread.php?p=11661448)

Also rekonq at one time was telling me that it did not know how to handle the http protocol. (!)

You message is over a week old but I ended up installing OpenSUSE.  You might try re-installing Kubuntu though to see if the same thing occurs.  It could possibly be some strangely botched install despite us both having roughly the same issues.

On another machine, I had Ubuntu Oneiric Ocelot installed and installed the Kubuntu Desktop from Synaptic. That installation had no problems, it's just the one from the ISO that has issues it would appear.

---


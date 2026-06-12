---
title: "Muon Software Center Crashing"
date: 2012-09-29
forum: General Help
---

### Post by horseatingweeds on 2012-09-29
After some updates, Muon Software Center started crashing when I try to start it. Here i sthe developer information it gives me after the crash:

```

 p, li { white-space: pre-wrap; }  Application: Muon Software Center (muon-installer), signal: Segmentation fault
 [Current thread is 1 (Thread 0x7f47a3adb780 (LWP 9302))]
  Thread 2 (Thread 0x7f478f3d7700 (LWP 9303)):
 #0  0x00007f47a06a0473 in __GI___poll (fds=<optimized out>, nfds=<optimized out>, timeout=<optimized out>) at ../sysdeps/unix/sysv/linux/poll.c:87
 #1  0x00007f479cf13f68 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #2  0x00007f479cf14429 in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #3  0x00007f47a285ef3e in QEventDispatcherGlib::processEvents (this=0x2429ff0, flags=<optimized out>) at kernel/qeventdispatcher_glib.cpp:424
 #4  0x00007f47a2832cf2 in QEventLoop::processEvents (this=<optimized out>, flags=...) at kernel/qeventloop.cpp:149
 #5  0x00007f47a2832ef7 in QEventLoop::exec (this=0x7f478f3d6dd0, flags=...) at kernel/qeventloop.cpp:201
 #6  0x00007f47a274a27f in QThread::exec (this=<optimized out>) at thread/qthread.cpp:498
 #7  0x00007f47a2815cbf in QInotifyFileSystemWatcherEngine::run (this=0x24537a0) at io/qfilesystemwatcher_inotify.cpp:248
 #8  0x00007f47a274cd05 in QThreadPrivate::start (arg=0x24537a0) at thread/qthread_unix.cpp:331
 #9  0x00007f479d9f5efc in start_thread (arg=0x7f478f3d7700) at pthread_create.c:304
 #10 0x00007f47a06ac59d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112
 #11 0x0000000000000000 in ?? ()
  Thread 1 (Thread 0x7f47a3adb780 (LWP 9302)):
 [KCrash Handler]
 #6  0x00007f47a279aa5e in QtPrivate::QStringList_contains (that=0x7fff0c2d1480, str=..., cs=Qt::CaseSensitive) at tools/qstringlist.cpp:318
 #7  0x000000000042416b in contains (cs=Qt::CaseSensitive, str=..., this=0x7fff0c2d1480) at /usr/include/qt4/QtCore/qstringlist.h:171
 #8  ApplicationWindow::populateViews (this=0x2421720) at /build/buildd/muon-1.2.1/installer/ApplicationWindow.cpp:229
 #9  0x000000000042771c in ApplicationWindow::qt_metacall (this=0x2421720, _c=QMetaObject::InvokeMetaMethod, _id=<optimized out>, _a=0x7fff0c2d1a50) at /build/buildd/muon-1.2.1/obj-x86_64-linux-gnu/installer/ApplicationWindow.moc:113
 #10 0x00007f47a2846eba in QMetaObject::activate (sender=0x2497e60, m=<optimized out>, local_signal_index=<optimized out>, argv=0x0) at kernel/qobject.cpp:3278
 #11 0x000000000041c31c in ApplicationBackend::qt_metacall (this=0x2497e60, _c=QMetaObject::InvokeMetaMethod, _id=<optimized out>, _a=0x7fff0c2d1bb0) at /build/buildd/muon-1.2.1/obj-x86_64-linux-gnu/installer/moc_ApplicationBackend.cpp:109
 #12 0x00007f47a2846eba in QMetaObject::activate (sender=0x2421720, m=<optimized out>, local_signal_index=<optimized out>, argv=0x7fff0c2d1bb0) at kernel/qobject.cpp:3278
 #13 0x00007f47a36c1e7f in MuonMainWindow::backendReady (this=<optimized out>, _t1=0x247dcc0) at /build/buildd/muon-1.2.1/obj-x86_64-linux-gnu/libmuon/MuonMainWindow.moc:168
 #14 0x00007f47a36c1f8e in MuonMainWindow::initObject (this=0x2421720) at /build/buildd/muon-1.2.1/libmuon/MuonMainWindow.cpp:79
 #15 0x0000000000422fa0 in ApplicationWindow::initObject (this=0x2421720) at /build/buildd/muon-1.2.1/installer/ApplicationWindow.cpp:116
 #16 0x0000000000427619 in ApplicationWindow::qt_metacall (this=0x2421720, _c=QMetaObject::InvokeMetaMethod, _id=<optimized out>, _a=0x7fff0c2d1c80) at /build/buildd/muon-1.2.1/obj-x86_64-linux-gnu/installer/ApplicationWindow.moc:104
 #17 0x00007f47a2846eba in QMetaObject::activate (sender=0x24d5420, m=<optimized out>, local_signal_index=<optimized out>, argv=0x0) at kernel/qobject.cpp:3278
 #18 0x00007f47a284ef7f in QSingleShotTimer::timerEvent (this=0x24d5420) at kernel/qtimer.cpp:308
 #19 0x00007f47a284a789 in QObject::event (this=0x24d5420, e=<optimized out>) at kernel/qobject.cpp:1181
 #20 0x00007f47a0e6d474 in notify_helper (e=0x7fff0c2d21f0, receiver=0x24d5420, this=0x22c0f70) at kernel/qapplication.cpp:4486
 #21 QApplicationPrivate::notify_helper (this=0x22c0f70, receiver=0x24d5420, e=0x7fff0c2d21f0) at kernel/qapplication.cpp:4458
 #22 0x00007f47a0e722e1 in QApplication::notify (this=0x7fff0c2d24f0, receiver=0x24d5420, e=0x7fff0c2d21f0) at kernel/qapplication.cpp:4365
 #23 0x00007f47a2052466 in KApplication::notify (this=0x7fff0c2d24f0, receiver=0x24d5420, event=0x7fff0c2d21f0) at ../../kdeui/kernel/kapplication.cpp:311
 #24 0x00007f47a2833afc in QCoreApplication::notifyInternal (this=0x7fff0c2d24f0, receiver=0x24d5420, event=0x7fff0c2d21f0) at kernel/qcoreapplication.cpp:787
 #25 0x00007f47a2860d62 in sendEvent (event=0x7fff0c2d21f0, receiver=<optimized out>) at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:215
 #26 QTimerInfoList::activateTimers (this=0x22bd950) at kernel/qeventdispatcher_unix.cpp:603
 #27 0x00007f47a285e514 in timerSourceDispatch (source=<optimized out>) at kernel/qeventdispatcher_glib.cpp:184
 #28 0x00007f479cf13a5d in g_main_context_dispatch () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #29 0x00007f479cf14258 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #30 0x00007f479cf14429 in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #31 0x00007f47a285eed6 in QEventDispatcherGlib::processEvents (this=0x22986f0, flags=<optimized out>) at kernel/qeventdispatcher_glib.cpp:422
 #32 0x00007f47a0f1510e in QGuiEventDispatcherGlib::processEvents (this=<optimized out>, flags=<optimized out>) at kernel/qguieventdispatcher_glib.cpp:204
 #33 0x00007f47a2832cf2 in QEventLoop::processEvents (this=<optimized out>, flags=...) at kernel/qeventloop.cpp:149
 #34 0x00007f47a2832ef7 in QEventLoop::exec (this=0x7fff0c2d2480, flags=...) at kernel/qeventloop.cpp:201
 #35 0x00007f47a2837789 in QCoreApplication::exec () at kernel/qcoreapplication.cpp:1064
 #36 0x000000000041bd67 in main (argc=5, argv=0x7fff0c2d2768) at /build/buildd/muon-1.2.1/installer/main.cpp:61
 
```

I've tried uninstalling and reinstalling Muon. The problem continues.

---

### Post by horseatingweeds on 2012-10-01
Ideas?

---


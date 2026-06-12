---
title: "Problem with Opera and Konqueror"
date: 2011-09-09
forum: General Help
---

### Post by jazzerit on 2011-09-09
I have a problem with the BBC Iplayer in Ubuntu. The site loads normally. When I click on a specific broadcast (recorded tv and radio, and live radio: not sure about live tv) to play it the page loads but the flash (10.3 r183) element does not. This happens with Konqueror as well as Opera, but Firefox behaves normally. I've re-installed flash and Opera, and emptied the cache in Opera.

I'm using Ubuntu 10.10, and this also happens on another computer with Ubunto 11.04 which which shares the same router.

Does anyone have any idea how to fix this?


Konqueror provided this error message on loading:
```

Application: nspluginviewer (nspluginviewer), signal: Segmentation fault
[Current thread is 1 (Thread 0xb788f710 (LWP 8329))]

Thread 5 (Thread 0xb75c4b70 (LWP 8330)):
#0  0x008a8416 in __kernel_vsyscall ()
#1  0x009d6df6 in poll () from /lib/libc.so.6
#2  0x00587a1b in g_poll () from /lib/libglib-2.0.so.0
#3  0x0057a43c in ?? () from /lib/libglib-2.0.so.0
#4  0x0057aba7 in g_main_loop_run () from /lib/libglib-2.0.so.0
#5  0x019dd9c4 in ?? () from /usr/lib/libgio-2.0.so.0
#6  0x005a148f in ?? () from /lib/libglib-2.0.so.0
#7  0x00268cc9 in start_thread () from /lib/libpthread.so.0
#8  0x009e569e in clone () from /lib/libc.so.6

Thread 4 (Thread 0xb27dfb70 (LWP 8334)):
#0  0x008a8416 in __kernel_vsyscall ()
#1  0x0026d4dc in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
#2  0x009f2d9d in pthread_cond_wait () from /lib/libc.so.6
#3  0xb2a4f087 in ?? () from /usr/lib/firefox/plugins/flashplugin-alternative.so
#4  0xb2b62bf5 in ?? () from /usr/lib/firefox/plugins/flashplugin-alternative.so
#5  0xb2a4f18d in ?? () from /usr/lib/firefox/plugins/flashplugin-alternative.so
#6  0xb2a4f816 in ?? () from /usr/lib/firefox/plugins/flashplugin-alternative.so
#7  0x00268cc9 in start_thread () from /lib/libpthread.so.0
#8  0x009e569e in clone () from /lib/libc.so.6

Thread 3 (Thread 0xb07deb70 (LWP 8335)):
#0  0x008a8416 in __kernel_vsyscall ()
#1  0x0026d4dc in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
#2  0x009f2d9d in pthread_cond_wait () from /lib/libc.so.6
#3  0xb2a4f087 in ?? () from /usr/lib/firefox/plugins/flashplugin-alternative.so
#4  0xb2b62bf5 in ?? () from /usr/lib/firefox/plugins/flashplugin-alternative.so
#5  0xb2a4f18d in ?? () from /usr/lib/firefox/plugins/flashplugin-alternative.so
#6  0xb2a4f816 in ?? () from /usr/lib/firefox/plugins/flashplugin-alternative.so
#7  0x00268cc9 in start_thread () from /lib/libpthread.so.0
#8  0x009e569e in clone () from /lib/libc.so.6

Thread 2 (Thread 0xae5cdb70 (LWP 8337)):
#0  0x008a8416 in __kernel_vsyscall ()
#1  0x0026d884 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
#2  0x009f2df4 in pthread_cond_timedwait () from /lib/libc.so.6
#3  0x0236394f in QWaitCondition::wait(QMutex*, unsigned long) () from /usr/lib/libQtCore.so.4
#4  0x023575b3 in ?? () from /usr/lib/libQtCore.so.4
#5  0x02362df9 in ?? () from /usr/lib/libQtCore.so.4
#6  0x00268cc9 in start_thread () from /lib/libpthread.so.0
#7  0x009e569e in clone () from /lib/libc.so.6

Thread 1 (Thread 0xb788f710 (LWP 8329)):
[KCrash Handler]
#7  0xb2be6e6b in ?? () from /usr/lib/firefox/plugins/flashplugin-alternative.so
#8  0xb2d16cc7 in ?? () from /usr/lib/firefox/plugins/flashplugin-alternative.so
#9  0xb2a3785c in ?? () from /usr/lib/firefox/plugins/flashplugin-alternative.so
#10 0xb2a3e20a in ?? () from /usr/lib/firefox/plugins/flashplugin-alternative.so
#11 0x08050a69 in ?? ()
#12 0x08055541 in ?? ()
#13 0x08057227 in ?? ()
#14 0x08057491 in ?? ()
#15 0x080575db in ?? ()
#16 0x0246a8ca in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#17 0x0247d6ad in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#18 0x00356589 in KIO::TransferJob::data(KIO::Job*, QByteArray const&) () from /usr/lib/libkio.so.5
#19 0x003593d2 in KIO::TransferJob::slotData(QByteArray const&) () from /usr/lib/libkio.so.5
#20 0x0035d1c5 in KIO::TransferJob::qt_metacall(QMetaObject::Call, int, void**) () from /usr/lib/libkio.so.5
#21 0x0246a8ca in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#22 0x0247d6ad in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#23 0x00418b23 in KIO::SlaveInterface::data(QByteArray const&) () from /usr/lib/libkio.so.5
#24 0x0041c25e in KIO::SlaveInterface::dispatch(int, QByteArray const&) () from /usr/lib/libkio.so.5
#25 0x00418ec3 in KIO::SlaveInterface::dispatch() () from /usr/lib/libkio.so.5
#26 0x0040b838 in KIO::Slave::gotInput() () from /usr/lib/libkio.so.5
#27 0x0040ba43 in KIO::Slave::qt_metacall(QMetaObject::Call, int, void**) () from /usr/lib/libkio.so.5
#28 0x0246a8ca in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#29 0x0247d6ad in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#30 0x00324ed7 in KIO::Connection::readyRead() () from /usr/lib/libkio.so.5
#31 0x0032723e in ?? () from /usr/lib/libkio.so.5
#32 0x0032736e in KIO::Connection::qt_metacall(QMetaObject::Call, int, void**) () from /usr/lib/libkio.so.5
#33 0x0246a8ca in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#34 0x02475df6 in QMetaCallEvent::placeMetaCall(QObject*) () from /usr/lib/libQtCore.so.4
#35 0x024776a2 in QObject::event(QEvent*) () from /usr/lib/libQtCore.so.4
#36 0x06262fdc in QApplicationPrivate::notify_helper(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
#37 0x0626904e in QApplication::notify(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
#38 0x01183d8a in KApplication::notify(QObject*, QEvent*) () from /usr/lib/libkdeui.so.5
#39 0x02464b3b in QCoreApplication::notifyInternal(QObject*, QEvent*) () from /usr/lib/libQtCore.so.4
#40 0x02467d8b in QCoreApplicationPrivate::sendPostedEvents(QObject*, int, QThreadData*) () from /usr/lib/libQtCore.so.4
#41 0x02467f4d in QCoreApplication::sendPostedEvents(QObject*, int) () from /usr/lib/libQtCore.so.4
#42 0x02493a74 in ?? () from /usr/lib/libQtCore.so.4
#43 0x00576855 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#44 0x0057a668 in ?? () from /lib/libglib-2.0.so.0
#45 0x0057a848 in g_main_context_iteration () from /lib/libglib-2.0.so.0
#46 0x02493565 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#47 0x06324be5 in ?? () from /usr/lib/libQtGui.so.4
#48 0x02463609 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#49 0x02463a8a in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#50 0x0246800f in QCoreApplication::exec() () from /usr/lib/libQtCore.so.4
#51 0x06261e07 in QApplication::exec() () from /usr/lib/libQtGui.so.4
#52 0x0805c8f5 in ?? ()
#53 0x0092bce7 in __libc_start_main () from /lib/libc.so.6
#54 0x0804e451 in _start ()

```

EDIT: I've also found a discussion of this problem on the opera forums here:[http://my.opera.com/community/forums/topic.dml?id=1033152](http://my.opera.com/community/forums/topic.dml?id=1033152)

EDIT 2: Programmes will still play on their home page, but not on the iplayer. For example The Sky At Night does work via [http://www.bbc.co.uk/programmes/b006mk7h](http://www.bbc.co.uk/programmes/b006mk7h) but not through [http://www.bbc.co.uk/iplayer/episode/b014f7tm/The_Sky_at_Night_Final_Frontier/](http://www.bbc.co.uk/iplayer/episode/b014f7tm/The_Sky_at_Night_Final_Frontier/)

---


---
title: "Update messep up my Kubuntu"
date: 2010-09-17
forum: General Help
---

### Post by carl_pr on 2010-09-17
I installed Kubuntu 10.10 on my netbook because i tried the new unity and i didnt like it. So everything was fine with Kubuntu but suddenly a few minutes ago i did an update which messed up my wireless, i cant connect now, somethings in the taskbar are mess up like the volume icon is different. When KDE loads at the biggining i get an error saying KDE daemon failed to load.

Is there a way to roll back the update or reload that thing whatever it is? I was starting to get use to KDE, i didnt had any issue even tho is a beta until now. aaaa why everything have to be so difficult.

---

### Post by carl_pr on 2010-09-17
-- Backtrace:
Application: KDE Daemon (kdeinit4), signal: Segmentation fault
[KCrash Handler]
#7  0x007d970f in QObject::connect (sender=0x53, signal=0x5372f68 "2SessionConnected(QDBusObjectPath)", receiver=0x873d5f0, method=0x5372f44 "1SessionConnected(QDBusObjectPath)", type=Qt::AutoConnection) at kernel/qobject.cpp:2491
#8  0x05365850 in ObexFtpDaemon::ObexFtpDaemon(QObject*, QList<QVariant> const&) () from /usr/lib/kde4/kded_obexftpdaemon.so
#9  0x0536d068 in QObject* KPluginFactory::createInstance<ObexFtpDaemon, QObject>(QWidget*, QObject*, QList<QVariant> const&) () from /usr/lib/kde4/kded_obexftpdaemon.so
#10 0x00eae450 in KPluginFactory::create(char const*, QWidget*, QObject*, QList<QVariant> const&, QString const&) () from /usr/lib/libkdecore.so.5
#11 0x0206221b in ?? () from /usr/lib/libkdeinit4_kded4.so
#12 0x020640c7 in ?? () from /usr/lib/libkdeinit4_kded4.so
#13 0x02066531 in ?? () from /usr/lib/libkdeinit4_kded4.so
#14 0x002f0800 in ?? () from /usr/lib/libkdeui.so.5
#15 0x002f0f62 in ?? () from /usr/lib/libkdeui.so.5
#16 0x006039dc in QDBusConnectionPrivate::deliverCall (this=0x8618970, object=0x8713880, msg=..., metaTypes=..., slotIdx=4) at qdbusintegrator.cpp:916
#17 0x00604cbf in QDBusConnectionPrivate::activateCall (this=0x8618970, object=0x8713880, flags=337, msg=...) at qdbusintegrator.cpp:819
#18 0x00605770 in QDBusConnectionPrivate::activateObject (this=0x8618970, node=..., msg=..., pathStartPos=16) at qdbusintegrator.cpp:1376
#19 0x00605a2a in QDBusActivateObjectEvent::placeMetaCall (this=0x87168c0) at qdbusintegrator.cpp:1490
#20 0x007d56a2 in QObject::event (this=0xbfd87b00, e=0x53) at kernel/qobject.cpp:1219
#21 0x007c29db in QCoreApplication::event (this=0xbfd87b00, e=0x87168c0) at kernel/qcoreapplication.cpp:1561
#22 0x01041524 in QApplication::event (this=0xbfd87b00, e=0x87168c0) at kernel/qapplication.cpp:2439
#23 0x0103e02c in QApplicationPrivate::notify_helper (this=0x86105c8, receiver=0xbfd87b00, e=0x87168c0) at kernel/qapplication.cpp:4396
#24 0x0104409e in QApplication::notify (this=0xbfd87b00, receiver=0xbfd87b00, e=0x87168c0) at kernel/qapplication.cpp:3798
#25 0x002e868a in KApplication::notify(QObject*, QEvent*) () from /usr/lib/libkdeui.so.5
#26 0x007c2b3b in QCoreApplication::notifyInternal (this=0xbfd87b00, receiver=0xbfd87b00, event=0x87168c0) at kernel/qcoreapplication.cpp:732
#27 0x007c5d8b in sendEvent (receiver=0x0, event_type=0, data=0x85bef20) at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:215
#28 QCoreApplicationPrivate::sendPostedEvents (receiver=0x0, event_type=0, data=0x85bef20) at kernel/qcoreapplication.cpp:1373
#29 0x007c5f4d in QCoreApplication::sendPostedEvents (receiver=0x0, event_type=0) at kernel/qcoreapplication.cpp:1266
#30 0x007f1a74 in sendPostedEvents (s=0x8612778) at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:220
#31 postEventSourceDispatch (s=0x8612778) at kernel/qeventdispatcher_glib.cpp:277
#32 0x04bdc015 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#33 0x04bdfe28 in ?? () from /lib/libglib-2.0.so.0
#34 0x04be0008 in g_main_context_iteration () from /lib/libglib-2.0.so.0
#35 0x007f1565 in QEventDispatcherGlib::processEvents (this=0x85c01d0, flags=...) at kernel/qeventdispatcher_glib.cpp:415
#36 0x010ffa35 in QGuiEventDispatcherGlib::processEvents (this=0x85c01d0, flags=...) at kernel/qguieventdispatcher_glib.cpp:204
#37 0x007c1609 in QEventLoop::processEvents (this=0xbfd87a54, flags=) at kernel/qeventloop.cpp:149
#38 0x007c1a8a in QEventLoop::exec (this=0xbfd87a54, flags=...) at kernel/qeventloop.cpp:201
#39 0x007c600f in QCoreApplication::exec () at kernel/qcoreapplication.cpp:1009
#40 0x0103ce57 in QApplication::exec () at kernel/qapplication.cpp:3672
#41 0x02064cf7 in kdemain () from /usr/lib/libkdeinit4_kded4.so
#42 0x0804e4d1 in _start ()

---


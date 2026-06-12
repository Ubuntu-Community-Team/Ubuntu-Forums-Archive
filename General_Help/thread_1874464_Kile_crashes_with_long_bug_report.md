---
title: "Kile crashes with long bug report"
date: 2011-11-03
forum: General Help
---

### Post by balampixan on 2011-11-03
Hello everyone.
I have been using kile for long time and I never had problem before. However, since today every time I try to open kile I get:

'We are sorry, kile closed unexpectedly.
you can help us improve KDE Software by reporting this error.'

And in the 'Developer information'
I get the next bug:

 
 p, li { white-space: pre-wrap; }  Application: Kile (kile), signal: Aborted
 [Current thread is 1 (Thread 0x7fbbc44b3780 (LWP 4300))]
 
 Thread 4 (Thread 0x7fbbae937700 (LWP 4303)):
 #0  0x00007fbbc0442773 in poll () from /lib/x86_64-linux-gnu/libc.so.6
 #1  0x00007fbbbb8ebf68 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #2  0x00007fbbbb8ec792 in g_main_loop_run () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #3  0x00007fbbb5058516 in ?? () from /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0
 #4  0x00007fbbbb9112b6 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #5  0x00007fbbbc3b9efc in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
 #6  0x00007fbbc044e89d in clone () from /lib/x86_64-linux-gnu/libc.so.6
 #7  0x0000000000000000 in ?? ()
 
 Thread 3 (Thread 0x7fbba323a700 (LWP 4304)):
 #0  0x00007fbbc0442773 in poll () from /lib/x86_64-linux-gnu/libc.so.6
 #1  0x00007fbbbb8ebf68 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #2  0x00007fbbbb8ec429 in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #3  0x00007fbbc1d18f3e in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #4  0x00007fbbc1ceccf2 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #5  0x00007fbbc1cecef7 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #6  0x00007fbbc1c0427f in QThread::exec() () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #7  0x00007fbbc1ccfcbf in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #8  0x00007fbbc1c06d05 in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #9  0x00007fbbbc3b9efc in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
 #10 0x00007fbbc044e89d in clone () from /lib/x86_64-linux-gnu/libc.so.6
 #11 0x0000000000000000 in ?? ()
 
 Thread 2 (Thread 0x7fbba16d5700 (LWP 4361)):
 #0  0x00007fbbbc3be04c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/x86_64-linux-gnu/libpthread.so.0
 #1  0x00007fbbbe766fe2 in ?? () from /usr/lib/x86_64-linux-gnu/libQtScript.so.4
 #2  0x00007fbbbe767019 in ?? () from /usr/lib/x86_64-linux-gnu/libQtScript.so.4
 #3  0x00007fbbbc3b9efc in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
 #4  0x00007fbbc044e89d in clone () from /lib/x86_64-linux-gnu/libc.so.6
 #5  0x0000000000000000 in ?? ()
 
 Thread 1 (Thread 0x7fbbc44b3780 (LWP 4300)):
 [KCrash Handler]
 #6  0x00007fbbc03a33a5 in raise () from /lib/x86_64-linux-gnu/libc.so.6
 #7  0x00007fbbc03a6b0b in abort () from /lib/x86_64-linux-gnu/libc.so.6
 #8  0x00007fbbc1bfd43b in qt_message_output(QtMsgType, char const*) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #9  0x00007fbbc1bfd7ef in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #10 0x00007fbbc1bfd994 in qFatal(char const*, ...) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #11 0x00007fbba42d0e5c in QSpiAdaptor::GetChildren() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #12 0x00007fbba42d15bf in QSpiAdaptor::getCacheItem() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #13 0x00007fbba42c64d1 in QSpiAccessibleBridge::notifyAboutCreation(QSpiAdaptor*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #14 0x00007fbba42c5bd8 in QSpiAccessibleBridge::interfaceToAccessible(QAccessibleInterface*, int, bool) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #15 0x00007fbba42cb7cb in QSpiAdaptor::getChild(int) const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #16 0x00007fbba42d0de7 in QSpiAdaptor::GetChildren() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #17 0x00007fbba42d15bf in QSpiAdaptor::getCacheItem() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #18 0x00007fbba42c64d1 in QSpiAccessibleBridge::notifyAboutCreation(QSpiAdaptor*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #19 0x00007fbba42c5bd8 in QSpiAccessibleBridge::interfaceToAccessible(QAccessibleInterface*, int, bool) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #20 0x00007fbba42cb7cb in QSpiAdaptor::getChild(int) const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #21 0x00007fbba42d0de7 in QSpiAdaptor::GetChildren() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #22 0x00007fbba42d15bf in QSpiAdaptor::getCacheItem() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #23 0x00007fbba42c64d1 in QSpiAccessibleBridge::notifyAboutCreation(QSpiAdaptor*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #24 0x00007fbba42c5bd8 in QSpiAccessibleBridge::interfaceToAccessible(QAccessibleInterface*, int, bool) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #25 0x00007fbba42cb7cb in QSpiAdaptor::getChild(int) const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #26 0x00007fbba42d0de7 in QSpiAdaptor::GetChildren() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #27 0x00007fbba42d15bf in QSpiAdaptor::getCacheItem() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #28 0x00007fbba42c64d1 in QSpiAccessibleBridge::notifyAboutCreation(QSpiAdaptor*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #29 0x00007fbba42c5bd8 in QSpiAccessibleBridge::interfaceToAccessible(QAccessibleInterface*, int, bool) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #30 0x00007fbba42c6aaf in QSpiAccessibleBridge::objectToAccessible(QObject*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #31 0x00007fbba42e11fe in QSpiAccessible::getParentReference() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #32 0x00007fbba42d14e4 in QSpiAdaptor::getCacheItem() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #33 0x00007fbba42c64d1 in QSpiAccessibleBridge::notifyAboutCreation(QSpiAdaptor*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #34 0x00007fbba42c5bd8 in QSpiAccessibleBridge::interfaceToAccessible(QAccessibleInterface*, int, bool) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #35 0x00007fbba42c6aaf in QSpiAccessibleBridge::objectToAccessible(QObject*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #36 0x00007fbba42e11fe in QSpiAccessible::getParentReference() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #37 0x00007fbba42d14e4 in QSpiAdaptor::getCacheItem() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #38 0x00007fbba42c64d1 in QSpiAccessibleBridge::notifyAboutCreation(QSpiAdaptor*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #39 0x00007fbba42c5bd8 in QSpiAccessibleBridge::interfaceToAccessible(QAccessibleInterface*, int, bool) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #40 0x00007fbba42c6aaf in QSpiAccessibleBridge::objectToAccessible(QObject*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #41 0x00007fbba42e11fe in QSpiAccessible::getParentReference() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #42 0x00007fbba42d14e4 in QSpiAdaptor::getCacheItem() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #43 0x00007fbba42c64d1 in QSpiAccessibleBridge::notifyAboutCreation(QSpiAdaptor*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #44 0x00007fbba42c5bd8 in QSpiAccessibleBridge::interfaceToAccessible(QAccessibleInterface*, int, bool) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #45 0x00007fbba42c6aaf in QSpiAccessibleBridge::objectToAccessible(QObject*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #46 0x00007fbba42e11fe in QSpiAccessible::getParentReference() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #47 0x00007fbba42d14e4 in QSpiAdaptor::getCacheItem() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #48 0x00007fbba42c64d1 in QSpiAccessibleBridge::notifyAboutCreation(QSpiAdaptor*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #49 0x00007fbba42c5bd8 in QSpiAccessibleBridge::interfaceToAccessible(QAccessibleInterface*, int, bool) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #50 0x00007fbba42c6aaf in QSpiAccessibleBridge::objectToAccessible(QObject*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #51 0x00007fbba42e11fe in QSpiAccessible::getParentReference() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #52 0x00007fbba42d14e4 in QSpiAdaptor::getCacheItem() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #53 0x00007fbba42c64d1 in QSpiAccessibleBridge::notifyAboutCreation(QSpiAdaptor*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #54 0x00007fbba42c5bd8 in QSpiAccessibleBridge::interfaceToAccessible(QAccessibleInterface*, int, bool) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #55 0x00007fbba42c6aaf in QSpiAccessibleBridge::objectToAccessible(QObject*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #56 0x00007fbba42e11fe in QSpiAccessible::getParentReference() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #57 0x00007fbba42d14e4 in QSpiAdaptor::getCacheItem() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #58 0x00007fbba42c64d1 in QSpiAccessibleBridge::notifyAboutCreation(QSpiAdaptor*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #59 0x00007fbba42c5bd8 in QSpiAccessibleBridge::interfaceToAccessible(QAccessibleInterface*, int, bool) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #60 0x00007fbba42cb7cb in QSpiAdaptor::getChild(int) const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #61 0x00007fbba42d0de7 in QSpiAdaptor::GetChildren() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #62 0x00007fbba42d15bf in QSpiAdaptor::getCacheItem() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #63 0x00007fbba42c64d1 in QSpiAccessibleBridge::notifyAboutCreation(QSpiAdaptor*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #64 0x00007fbba42c5bd8 in QSpiAccessibleBridge::interfaceToAccessible(QAccessibleInterface*, int, bool) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #65 0x00007fbba42c6aaf in QSpiAccessibleBridge::objectToAccessible(QObject*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #66 0x00007fbba42e11fe in QSpiAccessible::getParentReference() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #67 0x00007fbba42d14e4 in QSpiAdaptor::getCacheItem() const () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #68 0x00007fbba42c64d1 in QSpiAccessibleBridge::notifyAboutCreation(QSpiAdaptor*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #69 0x00007fbba42c5bd8 in QSpiAccessibleBridge::interfaceToAccessible(QAccessibleInterface*, int, bool) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #70 0x00007fbba42c6aaf in QSpiAccessibleBridge::objectToAccessible(QObject*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #71 0x00007fbba42c6fc3 in QSpiAccessibleBridge::windowActivated(QObject*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #72 0x00007fbba42ea5c0 in QSpiAccessibleBridge::qt_metacall(QMetaObject::Call, int, void**) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #73 0x00007fbbc1d00eba in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #74 0x00007fbba42e9fbf in QSpiApplication::windowActivated(QObject*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #75 0x00007fbba42c2bc6 in QSpiApplication::eventFilter(QObject*, QEvent*) () from /usr/lib/qt4/plugins/accessiblebridge/libqspiaccessiblebridge.so
 #76 0x00007fbbc1cedbcc in QCoreApplicationPrivate::sendThroughApplicationEventFilters(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #77 0x00007fbbc0e25396 in QApplicationPrivate::notify_helper(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
 #78 0x00007fbbc0e2a291 in QApplication::notify(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
 #79 0x00007fbbc27231e6 in KApplication::notify(QObject*, QEvent*) () from /usr/lib/libkdeui.so.5
 #80 0x00007fbbc1cedafc in QCoreApplication::notifyInternal(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #81 0x00007fbbc0e28c1d in QApplication::setActiveWindow(QWidget*) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
 #82 0x00007fbbc0ea4bbd in QApplication::x11ProcessEvent(_XEvent*) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
 #83 0x00007fbbc0ecd412 in ?? () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
 #84 0x00007fbbbb8eba5d in g_main_context_dispatch () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #85 0x00007fbbbb8ec258 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #86 0x00007fbbbb8ec429 in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #87 0x00007fbbc1d18ed6 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #88 0x00007fbbc0ecd07e in ?? () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
 #89 0x00007fbbc1cf192f in QCoreApplication::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #90 0x0000000000518c8f in ?? ()
 #91 0x000000000057190a in ?? ()
 #92 0x00000000005b7ccc in ?? ()
 #93 0x00000000004d30da in ?? ()
 #94 0x00000000004e14d4 in ?? ()
 #95 0x00007fbbc1d00eba in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #96 0x00000000005b9cf0 in ?? ()
 #97 0x00000000005baa5b in ?? ()
 #98 0x00007fbbc1d00eba in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #99 0x00007fbbc1286f1e in QTabWidget::currentChanged(int) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
 #100 0x00007fbbc1287028 in ?? () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
 #101 0x00007fbbc12872d0 in QTabWidget::qt_metacall(QMetaObject::Call, int, void**) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
 #102 0x00007fbbc2805105 in KTabWidget::qt_metacall(QMetaObject::Call, int, void**) () from /usr/lib/libkdeui.so.5
 #103 0x00007fbbc1d00eba in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #104 0x00007fbbc127ca7e in QTabBar::currentChanged(int) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
 #105 0x00007fbbc12836ea in QTabBar::insertTab(int, QIcon const&, QString const&) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
 #106 0x00007fbbc1286252 in QTabWidget::insertTab(int, QWidget*, QIcon const&, QString const&) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
 #107 0x00007fbbc12862de in QTabWidget::insertTab(int, QWidget*, QString const&) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
 #108 0x00000000005b9ecf in ?? ()
 #109 0x00000000005ab305 in ?? ()
 #110 0x00000000004dc80f in ?? ()
 #111 0x00000000004e0ab6 in ?? ()
 #112 0x000000000043697b in ?? ()
 #113 0x00007fbbc038e30d in __libc_start_main () from /lib/x86_64-linux-gnu/libc.so.6
 #114 0x0000000000439005 in _start ()
 



I'm using Ubuntu 11.10 64b and I never had such a problem before.

I tried to remove and then to install again but nothing. 
Best,
BalamP.

---

### Post by krige on 2011-11-30
I have the same problem. Have you found a solution?

This is what I get when I run it from console:

```
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-c6qY4ErCRj,guid=0f7e8b8055d9360375269cd100000026" 
Registered DEC:  true 
kile(8492)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkonsolepart.so"
Invalid parent:  0x1389580 Kile(0x7fffb2e08500) 
QAccessibleWidget::rect: This implementation does not support subelements! (ID 1 unknown for KileWidget::OutputView)
Requesting child objects for an interface that is a virtual child itself. 
QAccessibleWidget::rect: This implementation does not support subelements! (ID 2 unknown for KileWidget::OutputView)
Requesting child objects for an interface that is a virtual child itself. 
QAccessibleWidget::rect: This implementation does not support subelements! (ID 3 unknown for KileWidget::OutputView)
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Invalid parent:  0x167b570 QToolBox(0xf3a3a0) 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0xf3a3a0) 1 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0xf3a3a0) 2 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0xf3a3a0) 3 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0xf3a3a0) 4 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0xf3a3a0) 5 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0xf3a3a0) 6 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0xf3a3a0) 7 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0xf3a3a0) 8 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0xf3a3a0) 9 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0xf3a3a0) 10 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0xf3a3a0) 11 
ASSERT: "interface->childCount() == children.count()" in file adaptor.cpp, line 200
KCrash: Application 'kile' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/lackovic/.kde/socket-dc5700/kdeinit4__0

[1]+  Stopped                 kile
user@dc5700:~$ QSocketNotifier: Invalid socket 23 and type 'Read', disabling...

```

---

### Post by balampixan on 2011-11-30
Hi, I haven't found any solution and no body amongs my friends knows what to do...
however, if you find something please let me know!
Best,
BalamP.

---

### Post by Ekhcsub on 2011-12-07
I think it is related to this [Bug]("http://goo.gl/dpJR8")

The fix is to disable QtAccessibility, i.e. to set the environment variable to 0 before starting kile from command line

```
export QT_ACCESSIBILITY=0
```

---

### Post by balampixan on 2011-12-08
Thank you :) It does work!

---


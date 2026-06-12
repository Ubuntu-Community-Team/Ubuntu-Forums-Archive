---
title: "amarok 1.4 crash on start up"
date: 2009-08-30
forum: General Help
---

### Post by DougieFresh4U on 2009-08-30
This started yesterday. When I open amarok, it freezes system instantly. So I started it via terminal and this is what was spat out at me:
```
dougie@DougiesLeanMachine:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
Amarok: [Loader] amarokapp probably crashed!
dougie@DougiesLeanMachine:~$ 
```
Any idea as to what is happening?
Thanks

---

### Post by lunalui on 2011-10-19
Hi,
I have the same problem with amarok 1.4 since today, probably after updating the system (lucid). I tried to remove and reinstall amarok from scratch several times, but to no effect. Does anyone know how to fix this? Thanks a lot in advance for your help.

In case it can help:
This is the message I get when I run amarok from a terminal

Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
DCOP Cleaning up dead connections.
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
X Error: BadLength (poly request too large or internal Xlib length error) 16
  Major opcode:  153
  Minor opcode:  17
  Resource id:  0x7c001e7
QGLContext::makeCurrent(): Cannot make invalid context current.


and this is the crash report:
 p, li { white-space: pre-wrap; } 
 ======== DEBUG INFORMATION  =======
 Version:    1.4.10
 Engine:     xine-engine
 Build date: Feb 17 2010
 CC version: 4.3.3
 KDElibs:    3.5.10
 Qt:         3.3.8b
 TagLib:     1.5.0
 CPU count:  4
 NDEBUG:     true
 ==== file `which amarokapp` =======
 /usr/bin/amarokapp: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
 
 
 ==== (gdb) bt =====================
 [Thread debugging using libthread_db enabled]
 0x006b2422 in __kernel_vsyscall ()
 #0  0x006b2422 in __kernel_vsyscall ()
 #1  0x00ba37fb in waitpid () from /lib/tls/i686/cmov/libc.so.6
 #2  0x0804d6fa in Amarok::Crash::crashHandler(int) ()
 #3  <signal handler called>
 #4  0x03eba686 in glGenTextures () from /usr/lib/mesa/libGL.so.1
 #5  0x005a7cdb in GLAnalyzer2::loadTexture( QString, unsigned int&) ()
    from /usr/lib/libamarok.so.0
 #6  0x005a8952 in GLAnalyzer2::GLAnalyzer2( QWidget*) ()
    from /usr/lib/libamarok.so.0
 #7  0x005a233d in Analyzer::Factory::createPlaylistAnalyzer( QWidget*) ()
    from /usr/lib/libamarok.so.0
 #8  0x0022e90d in Amarok::AnalyzerContainer::changeAnalyzer() ()
    from /usr/lib/libamarok.so.0
 #9  0x00230527 in Amarok::AnalyzerContainer::AnalyzerContainer(QWidget*) ()
    from /usr/lib/libamarok.so.0
 #10 0x00230620 in Amarok::AnalyzerAction:: plug( QWidget*, int) ()
    from /usr/lib/libamarok.so.0
 #11 0x06c9f513 in KXMLGUI::BuildHelper:: processActionElement( QDomElement const&, int) () from /usr/lib/libkdeui.so.4
 #12 0x06d3ca76 in KXMLGUI::BuildHelper:: processActionOrCustomElement( QDomElement const&, bool) () from /usr/lib/libkdeui.so.4
 #13 0x06e228c8 in KXMLGUI::BuildHelper:: processElement( QDomElement const&) ()
    from /usr/lib/libkdeui.so.4
 #14 0x06e22bf2 in KXMLGUI::BuildHelper::build( QDomElement const&) ()
    from /usr/lib/libkdeui.so.4
 #15 0x06e22ce2 in KXMLGUI::BuildHelper:: processContainerElement(QDomElement const&, QString const&, QString const&) () from /usr/lib/libkdeui.so.4
 #16 0x06e2299b in KXMLGUI::BuildHelper:: processElement(QDomElement const&) ()
    from /usr/lib/libkdeui.so.4
 #17 0x06e22bf2 in KXMLGUI::BuildHelper::build( QDomElement const&) ()
    from /usr/lib/libkdeui.so.4
 #18 0x06e23c26 in KXMLGUIFactory::addClient(KXMLGUIClient*) ()
    from /usr/lib/libkdeui.so.4
 #19 0x0049e45d in PlaylistWindow::createGUI() () from /usr/lib/libamarok.so.0
 #20 0x004a09af in PlaylistWindow::init() () from /usr/lib/libamarok.so.0
 #21 0x002417a8 in App::continueInit() () from /usr/lib/libamarok.so.0
 #22 0x0024227b in App::qt_invoke(int, QUObject*) ()
    from /usr/lib/libamarok.so.0
 #23 0x00fd519a in QObject::activate_signal( QConnectionList*, QUObject*) ()
    from /usr/lib/libqt-mt.so.3
 #24 0x01333d0e in QSignal::signal( QVariant const&) ()
    from /usr/lib/libqt-mt.so.3
 #25 0x00ff1b27 in QSignal::activate() () from /usr/lib/libqt-mt.so.3
 #26 0x00ff92e3 in QSingleShotTimer::event(QEvent*) ()
    from /usr/lib/libqt-mt.so.3
 #27 0x00f703d7 in QApplication::internalNotify( QObject*, QEvent*) ()
    from /usr/lib/libqt-mt.so.3
 #28 0x00f7134b in QApplication::notify( QObject*, QEvent*) ()
    from /usr/lib/libqt-mt.so.3
 #29 0x00a9078b in KApplication::notify( QObject*, QEvent*) ()
    from /usr/lib/libkdecore.so.4
 #30 0x00f65e42 in QEventLoop::activateTimers() () from /usr/lib/libqt-mt.so.3
 #31 0x00f1b1b6 in QEventLoop:: processEvents(unsigned int) ()
    from /usr/lib/libqt-mt.so.3
 #32 0x00f893b0 in QEventLoop::enterLoop() () from /usr/lib/libqt-mt.so.3
 #33 0x00f89256 in QEventLoop::exec() () from /usr/lib/libqt-mt.so.3
 #34 0x00f70a2f in QApplication::exec() () from /usr/lib/libqt-mt.so.3
 #35 0x0804bf03 in ?? ()
 #36 0x00b22bd6 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
 #37 0x0804b4b1 in ?? ()
 #0  0x006b2422 in __kernel_vsyscall ()
 No symbol table info available.
 #1  0x00ba37fb in waitpid () from /lib/tls/i686/cmov/libc.so.6
 No symbol table info available.
 #2  0x0804d6fa in Amarok::Crash::crashHandler(int) ()
 No symbol table info available.
 #3  <signal handler called>
 No symbol table info available.
 #4  0x03eba686 in glGenTextures () from /usr/lib/mesa/libGL.so.1
 No symbol table info available.
 #5  0x005a7cdb in GLAnalyzer2::loadTexture(QString, unsigned int&) ()
    from /usr/lib/libamarok.so.0
 No symbol table info available.
 #6  0x005a8952 in GLAnalyzer2::GLAnalyzer2(QWidget*) ()
    from /usr/lib/libamarok.so.0
 No symbol table info available.
 #7  0x005a233d in Analyzer::Factory::createPlaylistAnalyzer(QWidget*) ()
    from /usr/lib/libamarok.so.0
 No symbol table info available.
 #8  0x0022e90d in Amarok::AnalyzerContainer::changeAnalyzer() ()
    from /usr/lib/libamarok.so.0
 No symbol table info available.
 #9  0x00230527 in Amarok::AnalyzerContainer::AnalyzerContainer(QWidget*) ()
    from /usr/lib/libamarok.so.0
 No symbol table info available.
 #10 0x00230620 in Amarok::AnalyzerAction:: plug(QWidget*, int) ()
    from /usr/lib/libamarok.so.0
 No symbol table info available.
 #11 0x06c9f513 in KXMLGUI::BuildHelper:: processActionElement(QDomElement const&, int) () from /usr/lib/libkdeui.so.4
 No symbol table info available.
 #12 0x06d3ca76 in KXMLGUI::BuildHelper:: processActionOrCustomElement( QDomElement const&, bool) () from /usr/lib/libkdeui.so.4
 No symbol table info available.
 #13 0x06e228c8 in KXMLGUI::BuildHelper:: processElement( QDomElement const&) ()
    from /usr/lib/libkdeui.so.4
 No symbol table info available.
 #14 0x06e22bf2 in KXMLGUI::BuildHelper::build( QDomElement const&) ()
    from /usr/lib/libkdeui.so.4
 No symbol table info available.
 #15 0x06e22ce2 in KXMLGUI::BuildHelper:: processContainerElement( QDomElement const&, QString const&, QString const&) () from /usr/lib/libkdeui.so.4
 No symbol table info available.
 #16 0x06e2299b in KXMLGUI::BuildHelper:: processElement( QDomElement const&) ()
    from /usr/lib/libkdeui.so.4
 No symbol table info available.
 #17 0x06e22bf2 in KXMLGUI::BuildHelper::build(QDomElement const&) ()
    from /usr/lib/libkdeui.so.4
 No symbol table info available.
 #18 0x06e23c26 in KXMLGUIFactory::addClient(KXMLGUIClient*) ()
    from /usr/lib/libkdeui.so.4
 No symbol table info available.
 #19 0x0049e45d in PlaylistWindow::createGUI() () from /usr/lib/libamarok.so.0
 No symbol table info available.
 #20 0x004a09af in PlaylistWindow::init() () from /usr/lib/libamarok.so.0
 No symbol table info available.
 #21 0x002417a8 in App::continueInit() () from /usr/lib/libamarok.so.0
 No symbol table info available.
 #22 0x0024227b in App::qt_invoke(int, QUObject*) ()
    from /usr/lib/libamarok.so.0
 No symbol table info available.
 #23 0x00fd519a in QObject::activate_signal( QConnectionList*, QUObject*) ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #24 0x01333d0e in QSignal::signal( QVariant const&) ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #25 0x00ff1b27 in QSignal::activate() () from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #26 0x00ff92e3 in QSingleShotTimer::event( QEvent*) ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #27 0x00f703d7 in QApplication::internalNotify( QObject*, QEvent*) ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #28 0x00f7134b in QApplication::notify( QObject*, QEvent*) ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #29 0x00a9078b in KApplication::notify(QObject*, QEvent*) ()
    from /usr/lib/libkdecore.so.4
 No symbol table info available.
 #30 0x00f65e42 in QEventLoop::activateTimers() () from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #31 0x00f1b1b6 in QEventLoop:: processEvents(unsigned int) ()
    from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #32 0x00f893b0 in QEventLoop::enterLoop() () from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #33 0x00f89256 in QEventLoop::exec() () from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #34 0x00f70a2f in QApplication::exec() () from /usr/lib/libqt-mt.so.3
 No symbol table info available.
 #35 0x0804bf03 in ?? ()
 No symbol table info available.
 #36 0x00b22bd6 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
 No symbol table info available.
 #37 0x0804b4b1 in ?? ()
 No symbol table info available.
 ==== (gdb) thread apply all bt ====
 Thread 1 (Thread 0xb7744730 (LWP 3665)):
 #0  0x006b2422 in __kernel_vsyscall ()
 #1  0x00ba37fb in waitpid () from /lib/tls/i686/cmov/libc.so.6
 #2  0x0804d6fa in Amarok::Crash::crashHandler(int) ()
 #3  <signal handler called>
 #4  0x03eba686 in glGenTextures () from /usr/lib/mesa/libGL.so.1
 #5  0x005a7cdb in GLAnalyzer2::loadTexture(QString, unsigned int&) ()
    from /usr/lib/libamarok.so.0
 #6  0x005a8952 in GLAnalyzer2::GLAnalyzer2(QWidget*) ()
    from /usr/lib/libamarok.so.0
 #7  0x005a233d in Analyzer::Factory::createPlaylistAnalyzer(QWidget*) ()
    from /usr/lib/libamarok.so.0
 #8  0x0022e90d in Amarok::AnalyzerContainer::changeAnalyzer() ()
    from /usr/lib/libamarok.so.0
 #9  0x00230527 in Amarok::AnalyzerContainer::AnalyzerContainer(QWidget*) ()
    from /usr/lib/libamarok.so.0
 #10 0x00230620 in Amarok::AnalyzerAction:: plug(QWidget*, int) ()
    from /usr/lib/libamarok.so.0
 #11 0x06c9f513 in KXMLGUI::BuildHelper:: processActionElement(QDomElement const&, int) () from /usr/lib/libkdeui.so.4
 #12 0x06d3ca76 in KXMLGUI::BuildHelper:: processActionOrCustomElement(QDomElement const&, bool) () from /usr/lib/libkdeui.so.4
 #13 0x06e228c8 in KXMLGUI::BuildHelper:: processElement(QDomElement const&) ()
    from /usr/lib/libkdeui.so.4
 #14 0x06e22bf2 in KXMLGUI::BuildHelper::build(QDomElement const&) ()
    from /usr/lib/libkdeui.so.4
 #15 0x06e22ce2 in KXMLGUI::BuildHelper:: processContainerElement(QDomElement const&, QString const&, QString const&) () from /usr/lib/libkdeui.so.4
 #16 0x06e2299b in KXMLGUI::BuildHelper:: processElement(QDomElement const&) ()
    from /usr/lib/libkdeui.so.4
 #17 0x06e22bf2 in KXMLGUI::BuildHelper::build(QDomElement const&) ()
    from /usr/lib/libkdeui.so.4
 #18 0x06e23c26 in KXMLGUIFactory::addClient(KXMLGUIClient*) ()
    from /usr/lib/libkdeui.so.4
 #19 0x0049e45d in PlaylistWindow::createGUI() () from /usr/lib/libamarok.so.0
 #20 0x004a09af in PlaylistWindow::init() () from /usr/lib/libamarok.so.0
 #21 0x002417a8 in App::continueInit() () from /usr/lib/libamarok.so.0
 #22 0x0024227b in App::qt_invoke(int, QUObject*) ()
    from /usr/lib/libamarok.so.0
 #23 0x00fd519a in QObject::activate_signal(QConnectionList*, QUObject*) ()
    from /usr/lib/libqt-mt.so.3
 #24 0x01333d0e in QSignal::signal(QVariant const&) ()
    from /usr/lib/libqt-mt.so.3
 #25 0x00ff1b27 in QSignal::activate() () from /usr/lib/libqt-mt.so.3
 #26 0x00ff92e3 in QSingleShotTimer::event( QEvent*) ()
    from /usr/lib/libqt-mt.so.3
 #27 0x00f703d7 in QApplication::internalNotify( QObject*, QEvent*) ()
    from /usr/lib/libqt-mt.so.3
 #28 0x00f7134b in QApplication::notify( QObject*, QEvent*) ()
    from /usr/lib/libqt-mt.so.3
 #29 0x00a9078b in KApplication::notify( QObject*, QEvent*) ()
    from /usr/lib/libkdecore.so.4
 #30 0x00f65e42 in QEventLoop::activateTimers() () from /usr/lib/libqt-mt.so.3
 #31 0x00f1b1b6 in QEventLoop:: processEvents(unsigned int) ()
    from /usr/lib/libqt-mt.so.3
 #32 0x00f893b0 in QEventLoop::enterLoop() () from /usr/lib/libqt-mt.so.3
 #33 0x00f89256 in QEventLoop::exec() () from /usr/lib/libqt-mt.so.3
 #34 0x00f70a2f in QApplication::exec() () from /usr/lib/libqt-mt.so.3
 #35 0x0804bf03 in ?? ()
 #36 0x00b22bd6 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
 #37 0x0804b4b1 in ?? ()
 
 
 ==== kdBacktrace() ================

---

### Post by lunalui on 2011-10-20
nevermind: amarok is working again after today's updates and a reboot! I'm very happy but have no idea of what was the problem!

---


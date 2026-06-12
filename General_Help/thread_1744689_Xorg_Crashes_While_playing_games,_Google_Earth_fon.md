---
title: "Xorg Crashes While playing games, Google Earth fonts look terrible Kubuntu 11.04"
date: 2011-04-30
forum: General Help
---

### Post by Topazkitty on 2011-04-30
Hi, I just upgraded to Kubuntu 11.04 with a fresh install. However, I have been having some problems with it.

First, sometimes when I play games like Neverball or Extreme Tux Racer my whole x-server locks up
Second, When I run Google Earth the fonts look terrible and this makes the application unusable.
Finally 32-bit flash flickers a lot but I fixed that using 64 bit flash.

Any help would be appreciated fixing the problems above.

Thanks Topazkitty

My computer is a dell inspiron 1525
Kubuntu 11.04 64 bit 
Intel GMA 965 Graphics

None of these problems occured in 10.10
Edit: I also just got this error when watching youtube   p, li { white-space: pre-wrap; }  Executable: kwin PID: 1470 Signal: Segmentation fault (11)

---

### Post by Topazkitty on 2011-04-30
I just wanted to add an extra post with Kwin Crash info

Can anyone figure out what this means?

 p, li { white-space: pre-wrap; }  Application: KWin (kwin), signal: Segmentation fault
 [Current thread is 1 (Thread 0x7f68fc00d7a0 (LWP 3112))]
 
 Thread 3 (Thread 0x7f68e09c3700 (LWP 3119)):
 #0  0x00007f68fb855143 in select () from /lib/x86_64-linux-gnu/libc.so.6
 #1  0x00007f68f7c3332c in qt_safe_select(int, fd_set*, fd_set*, fd_set*, timeval const*) () from /usr/lib/libQtCore.so.4
 #2  0x00007f68f7c383d0 in QEventDispatcherUNIXPrivate::doSelect(QFlags<QEventLoop::ProcessEventsFlag>, timeval*) () from /usr/lib/libQtCore.so.4
 #3  0x00007f68f7c3904a in QEventDispatcherUNIX::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
 #4  0x00007f68f7c0a882 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
 #5  0x00007f68f7c0aabc in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
 #6  0x00007f68f7b21924 in QThread::exec() () from /usr/lib/libQtCore.so.4
 #7  0x00007f68f7becc2f in ?? () from /usr/lib/libQtCore.so.4
 #8  0x00007f68f7b24175 in ?? () from /usr/lib/libQtCore.so.4
 #9  0x00007f68f2217d8c in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
 #10 0x00007f68fb85d04d in clone () from /lib/x86_64-linux-gnu/libc.so.6
 #11 0x0000000000000000 in ?? ()
 
 Thread 2 (Thread 0x7f68e01c2700 (LWP 3120)):
 #0  0x00007f68f221cbac in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/x86_64-linux-gnu/libpthread.so.0
 #1  0x00007f68fa6bc2a2 in ?? () from /usr/lib/libQtScript.so.4
 #2  0x00007f68fa6bc2d9 in ?? () from /usr/lib/libQtScript.so.4
 #3  0x00007f68f2217d8c in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
 #4  0x00007f68fb85d04d in clone () from /lib/x86_64-linux-gnu/libc.so.6
 #5  0x0000000000000000 in ?? ()
 
 Thread 1 (Thread 0x7f68fc00d7a0 (LWP 3112)):
 [KCrash Handler]
 #6  0x00007f68e370f0a0 in intel_region_buffer () from /usr/lib/dri/i965_dri.so
 #7  0x00007f68e37026c2 in intelClearWithBlit () from /usr/lib/dri/i965_dri.so
 #8  0x00007f68e3704d2a in ?? () from /usr/lib/dri/i965_dri.so
 #9  0x00007f68fbbd3ce7 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #10 0x00007f68fbbcb88f in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #11 0x00007f68fbbc8c7a in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #12 0x00007f68fbbe6f19 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #13 0x00007f68e28075a6 in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #14 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #15 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion, KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #16 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #17 0x00007f68e27ae44d in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #18 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #19 0x00007f68e27c957b in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #20 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #21 0x00007f68e27dbe68 in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #22 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #23 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion, KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #24 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #25 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion, KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #26 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #27 0x00007f68e27b2fbd in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #28 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #29 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion, KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #30 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #31 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion, KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #32 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #33 0x00007f68e279a365 in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #34 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #35 0x00007f68e27ea256 in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #36 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #37 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion, KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #38 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #39 0x00007f68e27cfb8f in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #40 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #41 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion, KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #42 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #43 0x00007f68e2793bad in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #44 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #45 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion, KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #46 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #47 0x00007f68e27e2d86 in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #48 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #49 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion, KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #50 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #51 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion, KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #52 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #53 0x00007f68e27d939b in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #54 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #55 0x00007f68fbbcb0af in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #56 0x00007f68fbbdeef3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #57 0x00007f68fbbc6396 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #58 0x00007f68f7c1f1c9 in QObject::event(QEvent*) () from /usr/lib/libQtCore.so.4
 #59 0x00007f68f6fcc9e4 in QApplicationPrivate::notify_helper(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
 #60 0x00007f68f6fd13aa in QApplication::notify(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
 #61 0x00007f68fb358866 in KApplication::notify(QObject*, QEvent*) () from /usr/lib/libkdeui.so.5
 #62 0x00007f68f7c0b49c in QCoreApplication::notifyInternal(QObject*, QEvent*) () from /usr/lib/libQtCore.so.4
 #63 0x00007f68f7c38f12 in ?? () from /usr/lib/libQtCore.so.4
 #64 0x00007f68f7c3905b in QEventDispatcherUNIX::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
 #65 0x00007f68f7074c0c in ?? () from /usr/lib/libQtGui.so.4
 #66 0x00007f68f7c0a882 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
 #67 0x00007f68f7c0aabc in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
 #68 0x00007f68f7c0eecb in QCoreApplication::exec() () from /usr/lib/libQtCore.so.4
 #69 0x00007f68fbb641ec in kdemain () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #70 0x00007f68fb795eff in __libc_start_main () from /lib/x86_64-linux-gnu/libc.so.6
 #71 0x0000000000400669 in _start ()

---

### Post by Topazkitty on 2011-05-01
Ok so i've discovered the problem is with Kwin having compositing on but I can't figure out why this happens. Kwin crashes when watching youtube and increasing the volume or playing games with opengl in them with fullscreen on.

Any help to solve this problem would appreciated.

---


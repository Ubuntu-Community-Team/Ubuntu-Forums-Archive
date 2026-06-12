---
title: "ksirk crash..."
date: 2009-09-10
forum: General Help
---

### Post by Tadcrazio on 2009-09-10
Been trying to get the came to work and it seems to crash everytime. Searched everywhere for a solution cant seem to find one.. Hopefully someone here will have one
 p, li { white-space: pre-wrap; }  The application KsirK (ksirk) crashed and caused the signal 11 (SIGSEGV).

 p, li { white-space: pre-wrap; }  This backtrace appears to be of no use.
 This is probably because your packages are built in a way which prevents creation of proper backtraces, or the stack frame was seriously corrupted in the crash.
 
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 [Thread debugging using libthread_db enabled]
 [New Thread 0x7f19912de750 (LWP 17918)]
 [New Thread 0x7f19775f8950 (LWP 17933)]
 [New Thread 0x7f1977df9950 (LWP 17932)]
 [New Thread 0x7f1973ffe950 (LWP 17931)]
 [New Thread 0x7f197cc64950 (LWP 17922)]
 [New Thread 0x7f197dcd4950 (LWP 17921)]
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 0x00007f198cdc292f in waitpid () from /lib/libc.so.6
 [Current thread is 0 (LWP 17918)]
 
 Thread 6 (Thread 0x7f197dcd4950 (LWP 17921)):
 #0  0x00007f198cb0a56d in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
 #1  0x00007f197fa1ff91 in ?? () from /usr/lib/libxine.so.1
 #2  0x00007f198cb063ba in start_thread () from /lib/libpthread.so.0
 #3  0x00007f198ce00fcd in clone () from /lib/libc.so.6
 #4  0x0000000000000000 in ?? ()
 
 Thread 5 (Thread 0x7f197cc64950 (LWP 17922)):
 #0  0x00007f198cdf7496 in poll () from /lib/libc.so.6
 #1  0x00007f198941a77f in ?? () from /usr/lib/libglib-2.0.so.0
 #2  0x00007f198941aa7c in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
 #3  0x00007f198e5f3e8e in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
 #4  0x00007f198e5c9002 in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
 #5  0x00007f198e5c93cd in QEventLoop::exec () from /usr/lib/libQtCore.so.4
 #6  0x00007f198e4de9b8 in QThread::exec () from /usr/lib/libQtCore.so.4
 #7  0x00007f197fc7b62c in ?? () from /usr/lib/kde4/plugins/phonon_backend/phonon_xine.so
 #8  0x00007f198e4e1952 in ?? () from /usr/lib/libQtCore.so.4
 #9  0x00007f198cb063ba in start_thread () from /lib/libpthread.so.0
 #10 0x00007f198ce00fcd in clone () from /lib/libc.so.6
 #11 0x0000000000000000 in ?? ()
 
 Thread 4 (Thread 0x7f1973ffe950 (LWP 17931)):
 #0  0x00007f198cdf7496 in poll () from /lib/libc.so.6
 #1  0x00007f197d091e3d in ?? () from /usr/lib/libpulse.so.0
 #2  0x00007f197d0845a9 in pa_mainloop_poll () from /usr/lib/libpulse.so.0
 #3  0x00007f197d085bf8 in pa_mainloop_iterate () from /usr/lib/libpulse.so.0
 #4  0x00007f197d085cc0 in pa_mainloop_run () from /usr/lib/libpulse.so.0
 #5  0x00007f197d091c3d in ?? () from /usr/lib/libpulse.so.0
 #6  0x00007f197d0b5e10 in ?? () from /usr/lib/libpulse.so.0
 #7  0x00007f198cb063ba in start_thread () from /lib/libpthread.so.0
 #8  0x00007f198ce00fcd in clone () from /lib/libc.so.6
 #9  0x0000000000000000 in ?? ()
 
 Thread 3 (Thread 0x7f1977df9950 (LWP 17932)):
 #0  0x00007f198cdf7496 in poll () from /lib/libc.so.6
 #1  0x00007f197c25e969 in ?? () from /usr/lib/xine/plugins/1.26/xineplug_ao_out_alsa.so
 #2  0x00007f198cb063ba in start_thread () from /lib/libpthread.so.0
 #3  0x00007f198ce00fcd in clone () from /lib/libc.so.6
 #4  0x0000000000000000 in ?? ()
 
 Thread 2 (Thread 0x7f19775f8950 (LWP 17933)):
 #0  0x00007f198cb0a2e9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
 #1  0x00007f197fa31353 in ?? () from /usr/lib/libxine.so.1
 #2  0x00007f198cb063ba in start_thread () from /lib/libpthread.so.0
 #3  0x00007f198ce00fcd in clone () from /lib/libc.so.6
 #4  0x0000000000000000 in ?? ()
 
 Thread 1 (Thread 0x7f19912de750 (LWP 17918)):
 #0  0x00007f198cdc292f in waitpid () from /lib/libc.so.6
 #1  0x00007f198f20a423 in ?? () from /usr/lib/libkdeui.so.5
 #2  0x00007f198f20b2cb in KCrash::defaultCrashHandler () from /usr/lib/libkdeui.so.5
 #3  <signal handler called>
 #4  0x00000000004719ab in ?? ()
 #5  0x000000000044a1b1 in ?? ()
 #6  0x00007f198e5e01f2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
 #7  0x00000000004ed70d in ?? ()
 #8  0x00007f198da5e768 in QWidget::event () from /usr/lib/libQtGui.so.4
 #9  0x00007f198ddf840b in QFrame::event () from /usr/lib/libQtGui.so.4
 #10 0x00007f198e014d1b in QGraphicsView::viewportEvent () from /usr/lib/libQtGui.so.4
 #11 0x00000000004ed81e in ?? ()
 #12 0x00007f198e5c9a68 in QCoreApplicationPrivate::sendThroughObjectEventFilters () from /usr/lib/libQtCore.so.4
 #13 0x00007f198da0d75c in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
 #14 0x00007f198da160da in QApplication::notify () from /usr/lib/libQtGui.so.4
 #15 0x00007f198f1a526b in KApplication::notify () from /usr/lib/libkdeui.so.5
 #16 0x00007f198e5ca75c in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
 #17 0x00007f198da15328 in QApplicationPrivate::sendMouseEvent () from /usr/lib/libQtGui.so.4
 #18 0x00007f198da158a2 in QApplicationPrivate::sendSyntheticEnterLeave () from /usr/lib/libQtGui.so.4
 #19 0x00007f198da63d1a in QWidget::setVisible () from /usr/lib/libQtGui.so.4
 #20 0x00007f198da47905 in QStackedLayout::setCurrentIndex () from /usr/lib/libQtGui.so.4
 #21 0x000000000046b088 in ?? ()
 #22 0x0000000000434e33 in _start ()
 #0  0x00007f198cdc292f in waitpid () from /lib/libc.so.6

---


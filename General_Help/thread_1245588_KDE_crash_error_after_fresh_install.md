---
title: "KDE crash error after fresh install"
date: 2009-08-20
forum: General Help
---

### Post by spedax on 2009-08-20
I keep getting an error after installing kubuntu. First time I used the cd to install it, it worked fine, I had to reinstall because I messed up something.

Now everytime I install I keep getting the same error while using almost any application. Basicly everything is broken.

I tried reinstalling 4 times so far, still same problem.

This problem pops up almost instantly ( when trying to connect to wireless network ) and I havent installed any apps yet.

anyone know a solution for this?

It has something to do with KDE4, even the crash handlers crashes....

Error:

> Application: KDE Daemon (kded4), signal SIGSEGV
0x00007f758a74ecf0 in nanosleep () from /lib/libc.so.6

Thread 1 (Thread 0x7f758eeff750 (LWP 3475)):
[KCrash Handler]
#5  0x00007f757db110bb in Knm::Connection::settings () from /usr/lib/libknmstorage.so.4
#6  0x00007f757db16805 in Knm::ConnectionPersistence::walletOpenedForRead () from /usr/lib/libknmstorage.so.4
#7  0x00007f757db10fb1 in Knm::ConnectionPersistence::qt_metacall () from /usr/lib/libknmstorage.so.4
#8  0x00007f758c2881f2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#9  0x00007f758e2d0272 in KWallet::Wallet::walletOpened () from /usr/lib/libkdeui.so.5
#10 0x00007f758e2d1044 in KWallet::Wallet::qt_metacall () from /usr/lib/libkdeui.so.5
#11 0x00007f758c2881f2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#12 0x00007f758e38ec4f in ?? () from /usr/lib/libkdeui.so.5
#13 0x00007f758e390089 in ?? () from /usr/lib/libkdeui.so.5
#14 0x00007f758c590f83 in ?? () from /usr/lib/libQtDBus.so.4
#15 0x00007f758c598d0f in ?? () from /usr/lib/libQtDBus.so.4
#16 0x00007f758c282848 in QObject::event () from /usr/lib/libQtCore.so.4
#17 0x00007f758ce1b83d in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#18 0x00007f758ce23a2a in QApplication::notify () from /usr/lib/libQtGui.so.4
#19 0x00007f758e25026b in KApplication::notify () from /usr/lib/libkdeui.so.5
#20 0x00007f758c27275c in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#21 0x00007f758c2733ca in QCoreApplicationPrivate::sendPostedEvents () from /usr/lib/libQtCore.so.4
#22 0x00007f758c29c1e3 in ?? () from /usr/lib/libQtCore.so.4
#23 0x00007f758837a20a in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#24 0x00007f758837d8e0 in ?? () from /usr/lib/libglib-2.0.so.0
#25 0x00007f758837da7c in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#26 0x00007f758c29be6f in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#27 0x00007f758ceb3c9f in ?? () from /usr/lib/libQtGui.so.4
#28 0x00007f758c271002 in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#29 0x00007f758c2713cd in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#30 0x00007f758c273694 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#31 0x00007f758eb00cd7 in kdemain () from /usr/lib/libkdeinit4_kded4.so
#32 0x00007f758a6c55a6 in __libc_start_main () from /lib/libc.so.6
#33 0x0000000000400759 in _start ()

now also getting this error:

> This backtrace appears to be of no use.
This is probably because your packages are built in a way which prevents creation of proper backtraces, or the stack frame was seriously corrupted in the crash.

(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7fb76815a6f0 (LWP 28938)]
(no debugging symbols found)

0x00007fb767d43b85 in waitpid () from /lib/libpthread.so.0
[Current thread is 0 (process 28938)]

Thread 1 (Thread 0x7fb76815a6f0 (LWP 28938)):
#0  0x00007fb767d43b85 in waitpid () from /lib/libpthread.so.0
#1  0x00007fb75e0d0423 in ?? () from /usr/lib/libkdeui.so.5
#2  0x00007fb75e0d12cb in KCrash::defaultCrashHandler () from /usr/lib/libkdeui.so.5
#3  <signal handler called>
#4  0x00007fb763b04ab0 in QTreeWidgetItem::setData () from /usr/lib/libQtGui.so.4
#5  0x00007fb7641fe77e in ?? () from /usr/lib/python2.6/dist-packages/PyQt4/QtGui.so
#6  0x00007fb763afeee5 in ?? () from /usr/lib/libQtGui.so.4
#7  0x00007fb763b35d64 in QStyledItemDelegate::editorEvent () from /usr/lib/libQtGui.so.4
#8  0x00007fb763a92b07 in QAbstractItemViewPrivate::sendDelegateEvent () from /usr/lib/libQtGui.so.4
#9  0x00007fb763a92dd7 in QAbstractItemView::edit () from /usr/lib/libQtGui.so.4
#10 0x00007fb7641f3222 in ?? () from /usr/lib/python2.6/dist-packages/PyQt4/QtGui.so
#11 0x00007fb763a93084 in QAbstractItemView::mouseReleaseEvent () from /usr/lib/libQtGui.so.4
#12 0x00007fb764200aec in ?? () from /usr/lib/python2.6/dist-packages/PyQt4/QtGui.so
#13 0x00007fb7635c78cf in QWidget::event () from /usr/lib/libQtGui.so.4
#14 0x00007fb76396140b in QFrame::event () from /usr/lib/libQtGui.so.4
#15 0x00007fb763a962bd in QAbstractItemView::viewportEvent () from /usr/lib/libQtGui.so.4
#16 0x00007fb763accef0 in QTreeView::viewportEvent () from /usr/lib/libQtGui.so.4
#17 0x00007fb7641db772 in ?? () from /usr/lib/python2.6/dist-packages/PyQt4/QtGui.so
#18 0x00007fb765574a68 in QCoreApplicationPrivate::sendThroughObjectEventFilters () from /usr/lib/libQtCore.so.4
#19 0x00007fb76357675c in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#20 0x00007fb76357f0da in QApplication::notify () from /usr/lib/libQtGui.so.4
#21 0x00007fb75e06b26b in KApplication::notify () from /usr/lib/libkdeui.so.5
#22 0x00007fb75e8d1f36 in sipKApplication::notify () from /usr/lib/python2.6/dist-packages/PyKDE4/kdeui.so
#23 0x00007fb76557575c in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#24 0x00007fb76357e328 in QApplicationPrivate::sendMouseEvent () from /usr/lib/libQtGui.so.4
#25 0x00007fb7635e7e19 in ?? () from /usr/lib/libQtGui.so.4
#26 0x00007fb7635e6a88 in QApplication::x11ProcessEvent () from /usr/lib/libQtGui.so.4
#27 0x00007fb76360f464 in ?? () from /usr/lib/libQtGui.so.4
#28 0x00007fb764d8820a in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#29 0x00007fb764d8b8e0 in ?? () from /usr/lib/libglib-2.0.so.0
#30 0x00007fb764d8ba7c in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#31 0x00007fb76559ee6f in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#32 0x00007fb76360ebef in ?? () from /usr/lib/libQtGui.so.4
#33 0x00007fb765574002 in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#34 0x00007fb7655743cd in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#35 0x00007fb765576694 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#36 0x00007fb7644bf8d9 in ?? () from /usr/lib/python2.6/dist-packages/PyQt4/QtGui.so
#37 0x00000000004a2b03 in PyEval_EvalFrameEx ()
#38 0x00000000004a3dae in PyEval_EvalFrameEx ()
#39 0x00000000004a4649 in PyEval_EvalCodeEx ()
#40 0x00000000004a4762 in PyEval_EvalCode ()
#41 0x00000000004c4c3c in PyRun_FileExFlags ()
#42 0x00000000004c4f6b in PyRun_SimpleFileExFlags ()
#43 0x00000000004189ce in Py_Main ()
#44 0x00007fb76713d5a6 in __libc_start_main () from /lib/libc.so.6
#45 0x0000000000417ae9 in _start ()
#0  0x00007fb767d43b85 in waitpid () from /lib/libpthread.so.0


---

### Post by spedax on 2009-08-21
Still have same issues, have tried numerous things.

Please help!

---

### Post by McNils on 2009-08-21
Do you have a separate home partition? If you do you propably have some configuration is causing the crash. Rename or remove your ~/.kde directory berofere logging in.

---

### Post by spedax on 2009-08-21
no seperate home folder, I even formatted the whole disk before reinstalling it, so I dont think its possible any prev setup messed it up.

---

### Post by spedax on 2009-08-21
When just booting from CD, I dont get the errors when I do the same actions where I do get errors from when on the installed kubuntu, so I dont think its a hardware thing, any other things I could try ?

---

### Post by mechanic on 2009-08-22
> **spedax said:**
> When just booting from CD, I dont get the errors when I do the same actions where I do get errors from when on the installed kubuntu, so I dont think its a hardware thing, any other things I could try ?

The only other obvious thing is the install CD/DVD. Try checking the disk md5 checksum or run 'check disk integrity' from the CD menu, or try another distro install disk instead.  The hardware is not setup as in an install to disk though and there may be a problem with the hard disk itself that doesn't show up with the live CD. Does gparted show any problems with the hard disk?

---

### Post by apparle on 2009-08-22
If your problem is during connection to wireless network then it maybe a fault of the default network manager. I don't have wifi so I don't know but everyone says that the default one is quite problematic.
Try installing the package 'wicd'. Its a diffrent network manager. Ask help on #kubuntu on irc.freenode.net or search the forums for wicd etc.

---


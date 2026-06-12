---
title: "Problem adding media in amarok - told it was a taglib issue"
date: 2011-09-16
forum: General Help
---

### Post by 118118 on 2011-09-16
hi,

here is the backtrace 
> 
Program received signal SIGSEGV, Segmentation fault.
0x000000d9 in ?? ()
(gdb) bt
#0  0x000000d9 in ?? ()
#1  0x02e6bc0f in ?? () from /usr/lib/libtag-extras.so.1
#2  0x02e6e025 in TagLibExtras::RealMedia::File::~File() ()
   from /usr/lib/libtag-extras.so.1
#3  0x02e6e082 in TagLibExtras::RealMedia::File::~File() ()
   from /usr/lib/libtag-extras.so.1
#4  0x02e45476 in TagLib::FileRef::~FileRef() () from /usr/lib/libtag.so.1
#5  0x0099769e in Meta::Tag::readTags(QString const&, bool) ()
   from /usr/lib/libamaroklib.so.1
#6  0x009c30ca in MetaFile::Track::Private::readMetaData() ()
   from /usr/lib/libamaroklib.so.1
#7  0x009c4bcf in MetaFile::Track::Track(KUrl const&) ()
   from /usr/lib/libamaroklib.so.1
#8  0x00a4854d in CollectionManager::trackForUrl(KUrl const&) ()
   from /usr/lib/libamaroklib.so.1
#9  0x00c47285 in ?? () from /usr/lib/libamaroklib.so.1
#10 0x0061b47f in ?? () from /usr/lib/libamaroklib.so.1
#11 0x01e566ba in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#12 0x01e664ff in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#13 0x01b9dcc3 in KJob::finished(KJob*) () from /usr/lib/libkdecore.so.5
---Type <return> to continue, or q <return> to quit---
#14 0x01b9dedc in KJob::emitResult() () from /usr/lib/libkdecore.so.5
#15 0x0272b6fd in KIO::ListJob::slotResult(KJob*) () from /usr/lib/libkio.so.5
#16 0x02734952 in KIO::ListJob::qt_metacall(QMetaObject::Call, int, void**) ()
   from /usr/lib/libkio.so.5
#17 0x01e566ba in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#18 0x01e664ff in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#19 0x01b9de93 in KJob::result(KJob*) () from /usr/lib/libkdecore.so.5
#20 0x01b9dee8 in KJob::emitResult() () from /usr/lib/libkdecore.so.5
#21 0x0272b6fd in KIO::ListJob::slotResult(KJob*) () from /usr/lib/libkio.so.5
#22 0x02734952 in KIO::ListJob::qt_metacall(QMetaObject::Call, int, void**) ()
   from /usr/lib/libkio.so.5
#23 0x01e566ba in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#24 0x01e664ff in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#25 0x01b9de93 in KJob::result(KJob*) () from /usr/lib/libkdecore.so.5
#26 0x01b9dee8 in KJob::emitResult() () from /usr/lib/libkdecore.so.5
#27 0x0272b6fd in KIO::ListJob::slotResult(KJob*) () from /usr/lib/libkio.so.5
#28 0x02734952 in KIO::ListJob::qt_metacall(QMetaObject::Call, int, void**) ()
   from /usr/lib/libkio.so.5
---Type <return> to continue, or q <return> to quit---
#29 0x01e566ba in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#30 0x01e664ff in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#31 0x01b9de93 in KJob::result(KJob*) () from /usr/lib/libkdecore.so.5
#32 0x01b9dee8 in KJob::emitResult() () from /usr/lib/libkdecore.so.5
#33 0x0272b6fd in KIO::ListJob::slotResult(KJob*) () from /usr/lib/libkio.so.5
#34 0x02734952 in KIO::ListJob::qt_metacall(QMetaObject::Call, int, void**) ()
   from /usr/lib/libkio.so.5
#35 0x01e566ba in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#36 0x01e664ff in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#37 0x01b9de93 in KJob::result(KJob*) () from /usr/lib/libkdecore.so.5
#38 0x01b9dee8 in KJob::emitResult() () from /usr/lib/libkdecore.so.5
#39 0x0272b6fd in KIO::ListJob::slotResult(KJob*) () from /usr/lib/libkio.so.5
#40 0x02734952 in KIO::ListJob::qt_metacall(QMetaObject::Call, int, void**) ()
   from /usr/lib/libkio.so.5
#41 0x01e566ba in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#42 0x01e664ff in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
---Type <return> to continue, or q <return> to quit---
#43 0x01b9de93 in KJob::result(KJob*) () from /usr/lib/libkdecore.so.5
#44 0x01b9dee8 in KJob::emitResult() () from /usr/lib/libkdecore.so.5
#45 0x0272b6fd in KIO::ListJob::slotResult(KJob*) () from /usr/lib/libkio.so.5
#46 0x02734952 in KIO::ListJob::qt_metacall(QMetaObject::Call, int, void**) ()
   from /usr/lib/libkio.so.5
#47 0x01e566ba in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#48 0x01e664ff in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#49 0x01b9de93 in KJob::result(KJob*) () from /usr/lib/libkdecore.so.5
#50 0x01b9dee8 in KJob::emitResult() () from /usr/lib/libkdecore.so.5
#51 0x0272b6fd in KIO::ListJob::slotResult(KJob*) () from /usr/lib/libkio.so.5
#52 0x02734952 in KIO::ListJob::qt_metacall(QMetaObject::Call, int, void**) ()
   from /usr/lib/libkio.so.5
#53 0x01e566ba in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#54 0x01e664ff in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#55 0x01b9de93 in KJob::result(KJob*) () from /usr/lib/libkdecore.so.5
#56 0x01b9dee8 in KJob::emitResult() () from /usr/lib/libkdecore.so.5
#57 0x0272b6fd in KIO::ListJob::slotResult(KJob*) () from /usr/lib/libkio.so.5
#58 0x02734952 in KIO::ListJob::qt_metacall(QMetaObject::Call, int, void**) ()
---Type <return> to continue, or q <return> to quit---
   from /usr/lib/libkio.so.5
#59 0x01e566ba in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#60 0x01e664ff in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#61 0x01b9de93 in KJob::result(KJob*) () from /usr/lib/libkdecore.so.5
#62 0x01b9dee8 in KJob::emitResult() () from /usr/lib/libkdecore.so.5
#63 0x0272b6fd in KIO::ListJob::slotResult(KJob*) () from /usr/lib/libkio.so.5
#64 0x02734952 in KIO::ListJob::qt_metacall(QMetaObject::Call, int, void**) ()
   from /usr/lib/libkio.so.5
#65 0x01e566ba in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#66 0x01e664ff in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#67 0x01b9de93 in KJob::result(KJob*) () from /usr/lib/libkdecore.so.5
#68 0x01b9dee8 in KJob::emitResult() () from /usr/lib/libkdecore.so.5
#69 0x0272b6fd in KIO::ListJob::slotResult(KJob*) () from /usr/lib/libkio.so.5
#70 0x02734952 in KIO::ListJob::qt_metacall(QMetaObject::Call, int, void**) ()
   from /usr/lib/libkio.so.5
#71 0x01e566ba in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#72  0x01e664ff in QMetaObject::activate(QObject*, QMetaObject const*, int,  void*---Type <return> to continue, or q <return> to quit---
*) () from /usr/lib/libQtCore.so.4
#73 0x01b9de93 in KJob::result(KJob*) () from /usr/lib/libkdecore.so.5
#74 0x01b9dee8 in KJob::emitResult() () from /usr/lib/libkdecore.so.5
#75 0x0272b6fd in KIO::ListJob::slotResult(KJob*) () from /usr/lib/libkio.so.5
#76 0x02734952 in KIO::ListJob::qt_metacall(QMetaObject::Call, int, void**) ()
   from /usr/lib/libkio.so.5
#77 0x01e566ba in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#78 0x01e664ff in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#79 0x01b9de93 in KJob::result(KJob*) () from /usr/lib/libkdecore.so.5
#80 0x01b9dee8 in KJob::emitResult() () from /usr/lib/libkdecore.so.5
#81 0x0272b6fd in KIO::ListJob::slotResult(KJob*) () from /usr/lib/libkio.so.5
#82 0x02734952 in KIO::ListJob::qt_metacall(QMetaObject::Call, int, void**) ()
   from /usr/lib/libkio.so.5
#83 0x01e566ba in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#84 0x01e664ff in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#85 0x01b9de93 in KJob::result(KJob*) () from /usr/lib/libkdecore.so.5
#86 0x01b9dee8 in KJob::emitResult() () from /usr/lib/libkdecore.so.5
#87 0x0272d61b in KIO::SimpleJob::slotFinished() () from /usr/lib/libkio.so.5
---Type <return> to continue, or q <return> to quit---
#88 0x027307be in KIO::ListJob::slotFinished() () from /usr/lib/libkio.so.5
#89 0x0273490e in KIO::ListJob::qt_metacall(QMetaObject::Call, int, void**) ()
   from /usr/lib/libkio.so.5
#90 0x01e566ba in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#91 0x01e664ff in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#92 0x027dd5a7 in KIO::SlaveInterface::finished() () from /usr/lib/libkio.so.5
#93 0x027e03d7 in KIO::SlaveInterface::dispatch(int, QByteArray const&) ()
   from /usr/lib/libkio.so.5
#94 0x027dce53 in KIO::SlaveInterface::dispatch() () from /usr/lib/libkio.so.5
#95 0x027cf5c8 in KIO::Slave::gotInput() () from /usr/lib/libkio.so.5
#96 0x027cfcf3 in KIO::Slave::qt_metacall(QMetaObject::Call, int, void**) ()
   from /usr/lib/libkio.so.5
#97 0x01e566ba in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#98 0x01e664ff in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#99 0x026fa237 in KIO::Connection::readyRead() () from /usr/lib/libkio.so.5
#100 0x026faa56 in ?? () from /usr/lib/libkio.so.5
#101 0x026fab06 in KIO::Connection::qt_metacall(QMetaObject::Call, int, void**)
    () from /usr/lib/libkio.so.5
---Type <return> to continue, or q <return> to quit---
#102 0x01e566ba in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#103 0x01e60e16 in QMetaCallEvent::placeMetaCall(QObject*) ()
   from /usr/lib/libQtCore.so.4
#104 0x01e653b7 in QObject::event(QEvent*) () from /usr/lib/libQtCore.so.4
#105 0x01136d24 in QApplicationPrivate::notify_helper(QObject*, QEvent*) ()
   from /usr/lib/libQtGui.so.4
#106 0x0113b8ce in QApplication::notify(QObject*, QEvent*) ()
   from /usr/lib/libQtGui.so.4
#107 0x003103ca in KApplication::notify(QObject*, QEvent*) ()
   from /usr/lib/libkdeui.so.5
#108 0x01e500bb in QCoreApplication::notifyInternal(QObject*, QEvent*) ()
   from /usr/lib/libQtCore.so.4
#109 0x01e53c79 in QCoreApplicationPrivate::sendPostedEvents(QObject*, int, QThreadData*) () from /usr/lib/libQtCore.so.4
#110 0x01e53e0d in QCoreApplication::sendPostedEvents(QObject*, int) ()
   from /usr/lib/libQtCore.so.4
#111 0x01e7d3c4 in ?? () from /usr/lib/libQtCore.so.4
#112 0x033d7aa8 in g_main_context_dispatch ()
   from /lib/i386-linux-gnu/libglib-2.0.so.0
#113 0x033d8270 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#114 0x033d8524 in g_main_context_iteration ()
---Type <return> to continue, or q <return> to quit---
   from /lib/i386-linux-gnu/libglib-2.0.so.0
#115  0x01e7d53c in  QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>)  () from /usr/lib/libQtCore.so.4
#116 0x011ed1e5 in ?? () from /usr/lib/libQtGui.so.4
#117 0x01e4f289 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#118 0x01e4f522 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) ()
   from /usr/lib/libQtCore.so.4
#119 0x01e53ecc in QCoreApplication::exec() () from /usr/lib/libQtCore.so.4
#120 0x011348e7 in QApplication::exec() () from /usr/lib/libQtGui.so.4
#121 0x08050cf0 in _start ()thanks for any help?

---


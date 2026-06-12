---
title: "error in plasma desktop!!!"
date: 2010-03-18
forum: General Help
---

### Post by davidtuti on 2010-03-18
Hi,

Today I've installed amarok and I modify an option in fstab and when I boot I find an error in Plasma and I can't see the KDE.
The error says me:

Error in plasma
Executable:Kdeinit 4
Pid:2192
Signal 11
Segmentation Fault

I cant start kde with this error.
This is the file of the error:
```

Application: Ãrea de trabajo de Plasma (kdeinit4), signal: Segmentation fault
[KCrash Handler]
#6  0x01470a90 in Plasma::Wallpaper::setUsingRenderingCache(bool) () from /usr/lib/libplasma.so.3
#7  0x03036579 in ?? () from /usr/lib/kde4/plasma_wallpaper_image.so
#8  0x01470909 in Plasma::Wallpaper::restore(KConfigGroup const&) () from /usr/lib/libplasma.so.3
#9  0x0139685c in Plasma::Applet::paint(QPainter*, QStyleOptionGraphicsItem const*, QWidget*) () from /usr/lib/libplasma.so.3
#10 0x065f602c in ?? () from /usr/lib/libQtGui.so.4
#11 0x06610c34 in ?? () from /usr/lib/libQtGui.so.4
#12 0x066130e4 in ?? () from /usr/lib/libQtGui.so.4
#13 0x06613d6b in ?? () from /usr/lib/libQtGui.so.4
#14 0x0661473e in ?? () from /usr/lib/libQtGui.so.4
#15 0x0662ecab in QGraphicsView::paintEvent(QPaintEvent*) () from /usr/lib/libQtGui.so.4
#16 0x05fbf5d6 in QWidget::event(QEvent*) () from /usr/lib/libQtGui.so.4
#17 0x063bb733 in QFrame::event(QEvent*) () from /usr/lib/libQtGui.so.4
#18 0x064559b2 in QAbstractScrollArea::viewportEvent(QEvent*) () from /usr/lib/libQtGui.so.4
#19 0x0662b12b in QGraphicsView::viewportEvent(QEvent*) () from /usr/lib/libQtGui.so.4
#20 0x064582a5 in ?? () from /usr/lib/libQtGui.so.4
#21 0x010a1e8a in QCoreApplicationPrivate::sendThroughObjectEventFilters(QObject*, QEvent*) () from /usr/lib/libQtCore.so.4
#22 0x05f613a9 in QApplicationPrivate::notify_helper(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
#23 0x05f680b9 in QApplication::notify(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
#24 0x007bb42a in KApplication::notify(QObject*, QEvent*) () from /usr/lib/libkdeui.so.5
#25 0x010a2beb in QCoreApplication::notifyInternal(QObject*, QEvent*) () from /usr/lib/libQtCore.so.4
#26 0x05fc88e6 in QWidgetPrivate::drawWidget(QPaintDevice*, QRegion const&, QPoint const&, int, QPainter*, QWidgetBackingStore*) () from /usr/lib/libQtGui.so.4
#27 0x05fc9725 in QWidgetPrivate::paintSiblingsRecursive(QPaintDevice*, QList<QObject*> const&, int, QRegion const&, QPoint const&, int, QPainter*, QWidgetBackingStore*) ()
   from /usr/lib/libQtGui.so.4
#28 0x05fc8635 in QWidgetPrivate::drawWidget(QPaintDevice*, QRegion const&, QPoint const&, int, QPainter*, QWidgetBackingStore*) () from /usr/lib/libQtGui.so.4
#29 0x0619ef00 in ?? () from /usr/lib/libQtGui.so.4
#30 0x05fb8a93 in QWidgetPrivate::syncBackingStore() () from /usr/lib/libQtGui.so.4
#31 0x05fe638e in ?? () from /usr/lib/libQtGui.so.4
#32 0x05ff19f6 in QApplication::x11ProcessEvent(_XEvent*) () from /usr/lib/libQtGui.so.4
#33 0x0602100a in ?? () from /usr/lib/libQtGui.so.4
#34 0x05636e88 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#35 0x0563a730 in ?? () from /lib/libglib-2.0.so.0
#36 0x0563a863 in g_main_context_iteration () from /lib/libglib-2.0.so.0
#37 0x010ce805 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#38 0x06020b35 in ?? () from /usr/lib/libQtGui.so.4
#39 0x010a1209 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#40 0x010a165a in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#41 0x010a584f in QCoreApplication::exec() () from /usr/lib/libQtCore.so.4
#42 0x05f61467 in QApplication::exec() () from /usr/lib/libQtGui.so.4
#43 0x07ae180d in kdemain () from /usr/lib/libkdeinit4_plasma-desktop.so
#44 0x0804dff7 in _start ()

```

Pleaseeee Any help?
Many thanks and sorry for my english!

---


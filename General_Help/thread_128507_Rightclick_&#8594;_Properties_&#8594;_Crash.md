---
title: "Rightclick &#8594; Properties &#8594; Crash"
date: 2006-02-11
forum: General Help
---

### Post by SirKillalot on 2006-02-11
Hi,
I have a problem with Konqueror. Everytime I rightlick a directory and select Properties or Share Konqueror crashes. I can view at the properties of files but not folders.

This is the KCrash backtrace (Rightclick->Share):

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
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
[New Thread -1208367424 (LWP 2627)]
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0x49123924 in QGDict::hashKeyString () from /usr/lib/libqt-mt.so.3
#7  0x49125743 in QGDict::look_string () from /usr/lib/libqt-mt.so.3
#8  0xb6e8302c in SambaShare::getValue ()
   from /usr/lib/kde3/fileshare_propsdlgplugin.so
#9  0xb6e844c4 in SambaShare::getGlobalValue ()
   from /usr/lib/kde3/fileshare_propsdlgplugin.so
#10 0xb6e849be in SambaShare::setValue ()
   from /usr/lib/kde3/fileshare_propsdlgplugin.so
#11 0xb6e893db in SambaFile::openFile ()
   from /usr/lib/kde3/fileshare_propsdlgplugin.so
#12 0xb6e8991a in SambaFile::load ()
   from /usr/lib/kde3/fileshare_propsdlgplugin.so
#13 0xb6e54bc2 in PropertiesPage::loadSamba ()
   from /usr/lib/kde3/fileshare_propsdlgplugin.so
#14 0xb6e54da6 in PropertiesPage::load ()
   from /usr/lib/kde3/fileshare_propsdlgplugin.so
#15 0xb6e57a9d in PropertiesPage::PropertiesPage ()
   from /usr/lib/kde3/fileshare_propsdlgplugin.so
#16 0xb6e51ea8 in PropsDlgSharePlugin::PropsDlgSharePlugin ()
   from /usr/lib/kde3/fileshare_propsdlgplugin.so
#17 0xb6e5295b in KGenericFactory<PropsDlgSharePlugin, KPropertiesDialog>::createObject () from /usr/lib/kde3/fileshare_propsdlgplugin.so
#18 0x41a5f9de in KLibFactory::create () from /usr/lib/libkdecore.so.4
#19 0x421a0c0a in KPropertiesDialog::insertPages () from /usr/lib/libkio.so.4
#20 0x421a1097 in KPropertiesDialog::init () from /usr/lib/libkio.so.4
#21 0x421a254f in KPropertiesDialog::KPropertiesDialog ()
   from /usr/lib/libkio.so.4
#22 0x422bef7a in KonqPopupMenu::showPropertiesDialog ()
   from /usr/lib/libkonq.so.4
#23 0x422bf04c in KonqPopupMenu::slotOpenShareFileDialog ()
   from /usr/lib/libkonq.so.4
#24 0x422ea648 in KonqPopupMenu::qt_invoke () from /usr/lib/libkonq.so.4
#25 0x48e2e069 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#26 0x48e2eb04 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#27 0x41cfb7b6 in KAction::activated () from /usr/lib/libkdeui.so.4
#28 0x41d31d0b in KAction::slotActivated () from /usr/lib/libkdeui.so.4
#29 0x41d4d9ab in KAction::slotPopupActivated () from /usr/lib/libkdeui.so.4
#30 0x41d4dce2 in KAction::qt_invoke () from /usr/lib/libkdeui.so.4
#31 0x48e2e069 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#32 0x4918d5d2 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#33 0x48e4ba84 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#34 0x48f510a3 in QPopupMenu::mouseReleaseEvent () from /usr/lib/libqt-mt.so.3
#35 0x48e68a96 in QWidget::event () from /usr/lib/libqt-mt.so.3
#36 0x48dc56c0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#37 0x48dc5c40 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#38 0x41b041ac in KApplication::notify () from /usr/lib/libkdecore.so.4
#39 0x48d56565 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#40 0x48d517b2 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#41 0x48d4fdaf in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#42 0x48d6973f in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#43 0x48ddd43b in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#44 0x48dc437f in QApplication::enter_loop () from /usr/lib/libqt-mt.so.3
#45 0x48f55d17 in QPopupMenu::exec () from /usr/lib/libqt-mt.so.3
#46 0x4237ba16 in KonqMainWindow::slotPopupMenu ()
   from /usr/lib/libkdeinit_konqueror.so
#47 0x4237c8d2 in KonqMainWindow::slotPopupMenu ()
   from /usr/lib/libkdeinit_konqueror.so
#48 0x423b4a32 in KonqMainWindow::qt_invoke ()
   from /usr/lib/libkdeinit_konqueror.so
#49 0x48e2e069 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#50 0x42228e45 in KParts::BrowserExtension::popupMenu ()
   from /usr/lib/libkparts.so.2
#51 0xb705b873 in KonqBaseListViewWidget::popupMenu ()
   from /usr/lib/kde3/konq_listview.so
#52 0xb705804b in KonqBaseListViewWidget::slotPopupMenu ()
   from /usr/lib/kde3/konq_listview.so
#53 0xb705efb9 in KonqBaseListViewWidget::qt_invoke ()
   from /usr/lib/kde3/konq_listview.so
#54 0x48e2e069 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#55 0x491a42f8 in QListView::contextMenuRequested ()
   from /usr/lib/libqt-mt.so.3
#56 0x48f258bf in QListView::contentsContextMenuEvent ()
   from /usr/lib/libqt-mt.so.3
#57 0x48f60a2e in QScrollView::viewportContextMenuEvent ()
   from /usr/lib/libqt-mt.so.3
#58 0x48f63111 in QScrollView::eventFilter () from /usr/lib/libqt-mt.so.3
#59 0x48f27afd in QListView::eventFilter () from /usr/lib/libqt-mt.so.3
#60 0x48e2b1b2 in QObject::activate_filters () from /usr/lib/libqt-mt.so.3
#61 0x48e2b230 in QObject::event () from /usr/lib/libqt-mt.so.3
#62 0x48e689a8 in QWidget::event () from /usr/lib/libqt-mt.so.3
#63 0x48dc56c0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#64 0x48dc60b2 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#65 0x41b041ac in KApplication::notify () from /usr/lib/libkdecore.so.4
#66 0x48d56565 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#67 0x48d51ac2 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#68 0x48d4fdaf in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#69 0x48d6973f in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#70 0x48ddd43b in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#71 0x48ddd35e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#72 0x48dc4353 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#73 0x423af6dc in kdemain () from /usr/lib/libkdeinit_konqueror.so
#74 0x47b0cea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#75 0x080483e1 in ?? ()

```

---

### Post by SirKillalot on 2006-02-28
anyone? please...

---

### Post by Jucato on 2006-02-28
What version of KDE are you using? I'm not entirely sure, but upgrading to KDE 3.5.1 might help solve the problem.

---

### Post by Rog131 on 2006-02-28
KDE 3.5.1 seems more stabile. BUT sometimes it still crashes when using preview/thumbnails in konqueror.

---

### Post by Jucato on 2006-02-28
yeah, I get a few crashes here and there. but nothing to pull my hair... yet. :D
But hey, everyone gets crashes, too. It ain't just KDE (though they say KDE crashes more than GNOME. have to still verify that)

---

### Post by SirKillalot on 2006-03-01
Hello people,
I'm usig 3.5.1 and had the same problem with 3.5. I think its a problem with samba, but honestly, I'm too stupid to read that crash trace. Maybe there is anyone who can tell me where exactly the problem could be?
Thanks

---

### Post by R3linquish3r on 2006-03-03
[QUOTE=Fenyx]But hey, everyone gets crashes, too.[/QUOTE]

*COUGH* XP *COUGH*

---

### Post by Rog131 on 2006-03-04
"There are two kind of computers, those who are already down, and those who are just crashing."

"If it's not broken - you haven't tried enogh."

Unknown system administrator

---


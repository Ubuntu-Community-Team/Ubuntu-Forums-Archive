---
title: "Kmix  problems"
date: 2011-02-12
forum: General Help
---

### Post by Gaba_p on 2011-02-12
When I run Kmix from terminal I get this (it still opens):

[I]QMetaObject::invokeMethod: No such method KMixApp::loadCommandLineOptionsForNewInstance()
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No existe el fichero o el directorio
QFileSystemWatcher: failed to add paths: /home/USER/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon [/I]

Until I close it, I get several of this:

*kmix(13770) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider *

If I run as sudo:

[I]Error: "/var/tmp/kdecache-USER" is owned by uid 1000 instead of uid 0.
QMetaObject::invokeMethod: No such method KMixApp::loadCommandLineOptionsForNewInstance()
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No existe el fichero o el directorio
QFileSystemWatcher: failed to add paths: /home/USER/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
QSystemTrayIcon::setVisible: No Icon set[/I]

and up until closing, several of this:

*kmix(13875) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider *

All and all, it works fine. I just can't get the keyboard shortcuts to work. They only work when the 'mixer' window is open and if I restart 'kmix' the keyboard shortcut settings have disappeared.

Any help will be very much appreciated.

Cheers.

---

### Post by Gaba_p on 2011-02-14
I hate to do this, but.. bump

---

### Post by Gaba_p on 2011-02-15
bump

---


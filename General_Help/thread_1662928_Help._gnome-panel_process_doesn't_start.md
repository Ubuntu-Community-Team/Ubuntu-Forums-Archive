---
title: "Help. gnome-panel process doesn't start"
date: 2011-01-08
forum: General Help
---

### Post by luceerose on 2011-01-08
I forced a quick restart with 'sudo shutdown -f now' and when logged back in gnome-panel doesn't start at all.
I can right-click on the desktop & run terminal from there, so I'm running web browser from terminal.
I tried 'sudo killall gnome-panel' & got 'no process found'
I tried doing a full restart, still the same.


I tried running gnome-panel from the terminal.

'gnome-panel' gives me my panel after a 4 or 5 second delay. If I exit the terminal or Ctrl-C I lose the panel again.

'sudo gnome-panel' gives me what appears to be the panel for the root user.

---

### Post by luceerose on 2011-01-08
When starting the panel from the terminal, I do get this message;
```
(gnome-panel:2699): Gdk-WARNING **: /scratch/build-area/gtk+2.0-2.20.1/gdk/x11/gdkdrawable-x11.c:952 drawable is not a pixmap or window

** (gnome-panel:2699): CRITICAL **: panel_applet_frame_change_background: assertion `PANEL_IS_WIDGET (GTK_WIDGET (frame)->parent)' failed

```
I don't know if that means anything.
Someone help me. I really don't want to have to keep a terminal window open permanently just to have the gnome-panel.
I also don't want to use the ugly hackjob of adding it to Startup Applications.
I'd prefer to find why gnome-panel isn't starting as it normally should and fix it properly.

---

### Post by luceerose on 2011-01-08
Here is my .xsession-errors file, if it helps;
```
/etc/gdm3/Xsession: Beginning session setup...
script for ibus started.
script for auto started.
script for default started.
GNOME_KEYRING_CONTROL=/tmp/keyring-vE1w3f
SSH_AUTH_SOCK=/tmp/keyring-vE1w3f/ssh
GNOME_KEYRING_PID=2397
GNOME_KEYRING_CONTROL=/tmp/keyring-vE1w3f
SSH_AUTH_SOCK=/tmp/keyring-vE1w3f/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-vE1w3f
SSH_AUTH_SOCK=/tmp/keyring-vE1w3f/ssh
Window manager warning: Failed to read saved session file /home/larsenguitars/.config/metacity/sessions/1056f757f738225e40129454357388728700000023160032.ms: Failed to open file '/home/larsenguitars/.config/metacity/sessions/1056f757f738225e40129454357388728700000023160032.ms': No such file or directory

(polkit-gnome-authentication-agent-1:2503): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2503): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

(<unknown>:2484): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64
kdeinit4: preparing to launch /usr/lib/kde4/libkdeinit/libkdeinit4_klauncher.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit4: preparing to launch /usr/lib/kde4/libkdeinit/libkdeinit4_kded4.so
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
Initializing nautilus-open-terminal extension
kbuildsycoca4 running...
Initializing nautilus-gdu extension
kdeinit4: preparing to launch /usr/lib/kde4/libkdeinit/libkdeinit4_kconf_update.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
amarok(2519)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
amarok(2519)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/larsenguitars/.local/share/mime/magic"
kdeinit4: preparing to launch /usr/bin/kglobalaccel
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kglobalaccel(2660) GlobalShortcutsRegistry::loadSettings: Loading group  "amarok"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+A" for "amarok" : "playlist_add"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift++" for "amarok" : "seek_forward"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+-" for "amarok" : "seek_backward"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Media Previous" for "amarok" : "prev"
kglobalaccel(2660) KGlobalAccelImpl::grabKey: grab failed!
kglobalaccel(2660) GlobalShortcut::setActive: "prev" : Failed to register  "Media Previous"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Media Next" for "amarok" : "next"
kglobalaccel(2660) KGlobalAccelImpl::grabKey: grab failed!
kglobalaccel(2660) GlobalShortcut::setActive: "next" : Failed to register  "Media Next"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta++" for "amarok" : "increaseVolume"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+-" for "amarok" : "decreaseVolume"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+P" for "amarok" : "toggleMainWindow"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+O" for "amarok" : "showNotificationPopup"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+M" for "amarok" : "mute"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+L" for "amarok" : "loveTrack"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+S" for "amarok" : "skipTrack"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+1" for "amarok" : "rate1"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+2" for "amarok" : "rate2"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+3" for "amarok" : "rate3"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+4" for "amarok" : "rate4"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+5" for "amarok" : "rate5"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Media Stop" for "amarok" : "stop"
kglobalaccel(2660) KGlobalAccelImpl::grabKey: grab failed!
kglobalaccel(2660) GlobalShortcut::setActive: "stop" : Failed to register  "Media Stop"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+V" for "amarok" : "stop_after_current"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Media Play" for "amarok" : "play_pause"
kglobalaccel(2660) KGlobalAccelImpl::grabKey: grab failed!
kglobalaccel(2660) GlobalShortcut::setActive: "play_pause" : Failed to register  "Media Play"
amarok(2519)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(2519)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(2519)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(2519)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(2519)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QSystemTrayIcon::setVisible: No Icon set
QDBusConnection: name 'org.kde.kglobalaccel' had owner '' but we thought it was ':1.60'
kdeinit4: preparing to launch /usr/lib/kde4/kio_http.so
amarok(2519)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Amarok Script Console"
amarok(2519)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "LyricWiki"
amarok(2519)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Cool Streams"
amarok(2519)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Librivox.org"
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
********************************************************************************************** 
** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: ** 
** amarok --debug                                                                           ** 
********************************************************************************************** 
kded(2542)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "kded/networkstatus.desktop" not found
kded(2542)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "kded/networkstatus.desktop" not found
kglobalaccel(2660) KGlobalAccelImpl::x11Event: Got XMappingNotify event
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta++" for "amarok" : "increaseVolume"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+M" for "amarok" : "mute"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift++" for "amarok" : "seek_forward"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Media Next" for "amarok" : "next"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Media Previous" for "amarok" : "prev"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+L" for "amarok" : "loveTrack"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Media Stop" for "amarok" : "stop"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+O" for "amarok" : "showNotificationPopup"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+1" for "amarok" : "rate1"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+-" for "amarok" : "decreaseVolume"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+2" for "amarok" : "rate2"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+3" for "amarok" : "rate3"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+P" for "amarok" : "toggleMainWindow"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+4" for "amarok" : "rate4"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+5" for "amarok" : "rate5"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+A" for "amarok" : "playlist_add"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+S" for "amarok" : "skipTrack"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+V" for "amarok" : "stop_after_current"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+-" for "amarok" : "seek_backward"
kglobalaccel(2660) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Media Play" for "amarok" : "play_pause"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta++" for "amarok" : "increaseVolume"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+M" for "amarok" : "mute"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift++" for "amarok" : "seek_forward"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Media Next" for "amarok" : "next"
kglobalaccel(2660) KGlobalAccelImpl::grabKey: grab failed!
kglobalaccel(2660) GlobalShortcut::setActive: "next" : Failed to register  "Media Next"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Media Previous" for "amarok" : "prev"
kglobalaccel(2660) KGlobalAccelImpl::grabKey: grab failed!
kglobalaccel(2660) GlobalShortcut::setActive: "prev" : Failed to register  "Media Previous"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+L" for "amarok" : "loveTrack"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Media Stop" for "amarok" : "stop"
kglobalaccel(2660) KGlobalAccelImpl::grabKey: grab failed!
kglobalaccel(2660) GlobalShortcut::setActive: "stop" : Failed to register  "Media Stop"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+O" for "amarok" : "showNotificationPopup"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+1" for "amarok" : "rate1"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+-" for "amarok" : "decreaseVolume"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+2" for "amarok" : "rate2"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+3" for "amarok" : "rate3"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+P" for "amarok" : "toggleMainWindow"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+4" for "amarok" : "rate4"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+5" for "amarok" : "rate5"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+A" for "amarok" : "playlist_add"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+S" for "amarok" : "skipTrack"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+V" for "amarok" : "stop_after_current"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+-" for "amarok" : "seek_backward"
kglobalaccel(2660) GlobalShortcutsRegistry::registerKey: Registering key "Media Play" for "amarok" : "play_pause"
kglobalaccel(2660) KGlobalAccelImpl::grabKey: grab failed!
kglobalaccel(2660) GlobalShortcut::setActive: "play_pause" : Failed to register  "Media Play"
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
kdeinit4: preparing to launch /usr/lib/kde4/kio_http.so
kded(2542)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "kded/networkstatus.desktop" not found
kded(2542)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "kded/networkstatus.desktop" not found
kdeinit4: preparing to launch /usr/lib/kde4/kio_http.so
kded(2542)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "kded/networkstatus.desktop" not found
kded(2542)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "kded/networkstatus.desktop" not found
```

---

### Post by luceerose on 2011-01-08
Another thing I have noticed.
While the panel is down, I cannot Alt+F2 for a Run dialog.

---


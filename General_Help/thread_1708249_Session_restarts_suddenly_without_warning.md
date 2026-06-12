---
title: "Session restarts suddenly without warning"
date: 2011-03-16
forum: General Help
---

### Post by mi691207 on 2011-03-16
Hello,

since a few weeks suddenly my session terminates and shows me the login screen again. It happens randomly.

Using Kubuntu 10.10

I could not find any help searching with Google.

Can anybody help me please?

I am seriously considering a complete reinstall...

Thanks!

---

### Post by andrewthomas on 2011-03-16
Sounds like your xserver is crashing.  Are you fully updated?

When it crashes next, don't immediately log back in, but switch to a terminal using <ctl>+<alt>+F2 log in and ```
cat .xsession-errors > xsession-errors
```then switch back to kdm with <ctl>+<alt>+F7 and log back in

Now you will be able to look at the errors (.xsession-errors will be overwritten by the next session: this is why I had you copy it over from the terminal)

If you are updated and still getting errors, post the errors between code tags in your reply

---

### Post by mi691207 on 2011-03-16
Thank you very much. 
I will do as you say.

Thanks!

---

### Post by mi691207 on 2011-03-22
This is what xsession-errors says.
I don't know exactly what to look for. There is an "unexpected operator"... what does it mean?

I have my system running with the newest updates.
Now it has been a few days that I have not experienced this issue again. Now it just happened.

```

Xsession: X session started for michael at mar mar 22 15:05:20 CST 2011
Setting IM through im-switch for locale=es_MX.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
[: 225: ==: unexpected operator
startkde: Starting up...
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
kbuildsycoca4 running...
Agent registered 
Fetched layout groups from X server: 	layouts: ("latam") 	variants: ("") 
Fetched layout groups from X server: 	layouts: ("latam") 	variants: ("") 
kglobalaccel(1675) GlobalShortcutsRegistry::loadSettings: Loading group  "kmix"
kglobalaccel(1675) GlobalShortcutsRegistry::loadSettings: Loading group  "kwin"
kglobalaccel(1675) GlobalShortcut::setKeys: "Cylinder" skipping because key "" is already taken
kglobalaccel(1675) GlobalShortcut::setKeys: "ExposeClass" skipping because key "" is already taken
kglobalaccel(1675) GlobalShortcut::setKeys: "Sphere" skipping because key "" is already taken
kglobalaccel(1675) GlobalShortcut::setKeys: "Switch Focus Right" skipping because key "" is already taken
kglobalaccel(1675) GlobalShortcut::setKeys: "Switch Window Left" skipping because key "" is already taken
kglobalaccel(1675) GlobalShortcut::setKeys: "Switch Window Right" skipping because key "" is already taken
kglobalaccel(1675) GlobalShortcut::setKeys: "Switch to Desktop 12" skipping because key "" is already taken
kglobalaccel(1675) GlobalShortcut::setKeys: "Switch to Desktop 8" skipping because key "" is already taken
kglobalaccel(1675) GlobalShortcutsRegistry::loadSettings: Loading group  "plasma-netbook"
kglobalaccel(1675) GlobalShortcut::setKeys: "Systemtray-Klipper-5" skipping because key "" is already taken
kglobalaccel(1675) GlobalShortcutsRegistry::loadSettings: Loading group  "KDE Keyboard Layout Switcher"
kglobalaccel(1675) GlobalShortcut::setKeys: "Switch to Next Keyboard Layout" skipping because key "" is already taken
kglobalaccel(1675) GlobalShortcutsRegistry::loadSettings: Loading group  "ksmserver"
kglobalaccel(1675) GlobalShortcutsRegistry::loadSettings: Loading group  "krunner"
kglobalaccel(1675) GlobalShortcutsRegistry::loadSettings: Loading group  "kxkb"
kglobalaccel(1675) GlobalShortcutsRegistry::loadSettings: Loading group  "plasma-desktop"
kglobalaccel(1675) GlobalShortcut::setKeys: "Next Activity" skipping because key "" is already taken
kglobalaccel(1675) GlobalShortcut::setKeys: "Systemtray-Klipper-10" skipping because key "" is already taken
kglobalaccel(1675) GlobalShortcutsRegistry::loadSettings: Loading group  "khotkeys"
kglobalaccel(1675) GlobalShortcutsRegistry::loadSettings: Loading group  "amarok"
kglobalaccel(1675) GlobalShortcut::setKeys: "decreaseVolume" skipping because key "" is already taken
kglobalaccel(1675) GlobalShortcutsRegistry::loadSettings: Loading group  "kded"
kglobalaccel(1675) GlobalShortcutsRegistry::loadSettings: Loading group  "klipper"
kglobalaccel(1675) GlobalShortcutsRegistry::loadSettings: Loading group  "ktorrent"
QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()

Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)




















































Invalid D-BUS member name 'idle-hint' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'is-local' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'x11-display-device' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'x11-display' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'display-device' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'remote-host-name' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'session-type' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'unix-user' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
<unknown program name>(1658)/ KStartupInfo::createNewStartupId: creating:  "m3;1300827931;329678;1658_TIME0" : "unnamed app"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Monitor Brightness Up" for "kded" : "Increase Screen Brightness"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Monitor Brightness Down" for "kded" : "Decrease Screen Brightness"
kded(1661)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QDBusConnection: name 'org.kde.kglobalaccel' had owner '' but we thought it was ':1.11'
QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
kwalletd(1677) KWalletD::setupDialog: Application ' "Servicio de KDE" ' using kwallet without parent window! 
kwin(1753) Kephal::DesktopWidgetScreens::DesktopWidgetScreens: foo
kwin(1753) KDecorationPlugins::loadPlugin: kwin : path  "/usr/lib/kde4/kwin3_tabstrip.so"  for  "kwin3_tabstrip"
kwin(1753) KWin::Extensions::init: Extensions: shape: 0x "11"  composite: 0x "4"  render: 0x "b"  fixes: 0x "40"
kwin(1753) KWin::Workspace::setupCompositing: Compositing is turned off in options or disabled
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Tab" for "kwin" : "Walk Through Windows"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+Backtab" for "kwin" : "Walk Through Windows (Reverse)"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F3" for "kwin" : "Window Operations Menu"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F4" for "kwin" : "Window Close"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+A" for "kwin" : "Activate Window Demanding Attention"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Up" for "kwin" : "Switch Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Down" for "kwin" : "Switch Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Right" for "kwin" : "Window to Next Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Left" for "kwin" : "Window to Previous Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F1" for "kwin" : "Switch to Desktop 1"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F2" for "kwin" : "Switch to Desktop 2"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F3" for "kwin" : "Switch to Desktop 3"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F4" for "kwin" : "Switch to Desktop 4"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F5" for "kwin" : "Switch to Desktop 5"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F6" for "kwin" : "Switch to Desktop 6"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Right" for "kwin" : "Switch One Desktop to the Right"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Left" for "kwin" : "Switch One Desktop to the Left"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F12" for "kwin" : "Mouse Emulation"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Esc" for "kwin" : "Kill Window"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Print" for "kwin" : "Window Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Print" for "kwin" : "Desktop Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F12" for "kwin" : "Suspend Compositing"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F11" for "kwin" : "Enable/Disable Tiling"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+F" for "kwin" : "Toggle Floating"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+H" for "kwin" : "Switch Focus Left"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+K" for "kwin" : "Switch Focus Up"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+J" for "kwin" : "Switch Focus Down"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+H" for "kwin" : "Move Window Left"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+L" for "kwin" : "Move Window Right"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+K" for "kwin" : "Move Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+J" for "kwin" : "Move Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+PgDown" for "kwin" : "Next Layout"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+PgUp" for "kwin" : "Previous Layout"
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No existe el fichero o el directorio
QFileSystemWatcher: failed to add paths: /home/michael/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 63625
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 20971548 ;WMCLASS: "kwalletd" : "kwalletd" ;Caption: "Servicio de cartera de KDE" ' : 63625
kwin(1753) KWin::Workspace::allowClientActivation: Activation: No client active, allowing
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Servicio de cartera de KDE"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No existe el fichero o el directorio
QFileSystemWatcher: failed to add paths: /home/michael/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kio_trash(1751)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kio_trash(1751)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/michael/.local/share/mime/magic"
QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
<unknown program name>(1758)/ kdemain: !!{} STARTUP TIME 54336452 START (line: 48 )
QDBusObjectPath: invalid path ""
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F12" for "plasma-desktop" : "Show Dashboard"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+Tab" for "plasma-desktop" : "Previous Activity"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Q" for "plasma-desktop" : "manage activities"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F1" for "plasma-desktop" : "activate widget 5"
plasma-desktop(1759)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-6, -3) 
plasma-desktop(1759)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-6, -3) 
plasma-desktop(1759)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-6, -3) 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No existe el fichero o el directorio
QFileSystemWatcher: failed to add paths: /home/michael/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
kglobalaccel(1675) KGlobalAccelDPrivate::_k_newGlobalShortcutNotification: Showing Notification for component "plasma-desktop"
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
plasma-desktop(1759)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
plasma-desktop(1759)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
QGridLayoutEngine::addItem: Cell (1, 1) already taken
plasma-desktop(1759)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
plasma-desktop(1759) MessageIndicator::adjustViewSize: No parentWidget for applet widget()! 
plasma-desktop(1759) MessageIndicator::adjustViewSize: No parentWidget for applet widget()! 
plasma-desktop(1759)/libakonadi Akonadi::AgentManagerPrivate::createDBusInterface: AgentManager failed to get a valid AgentManager DBus interface. Error is: 1 "org.freedesktop.DBus.Error.NameHasNoOwner" "Could not get owner of name 'org.freedesktop.Akonadi.Control': no such name" 
plasma-desktop(1759)/libakonadi Akonadi::SessionPrivate::socketError: Socket error occurred: "QLocalSocket::connectToServer: Connection refused" 
plasma-desktop(1759)/libakonadi Akonadi::SessionPrivate::socketError: Socket error occurred: "QLocalSocket::connectToServer: Connection refused" 
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
[akonadiserver] search paths:  ("/home/michael/bin", "/usr/local/sbin", "/usr/local/bin", "/usr/sbin", "/usr/bin", "/sbin", "/bin", "/usr/games", "/usr/sbin", "/usr/local/sbin", "/usr/local/libexec", "/usr/libexec", "/opt/mysql/libexec", "/opt/local/lib/mysql5/bin", "/opt/mysql/sbin")
[akonadiserver] Found mysql_install_db:  "/usr/bin/mysql_install_db"
[akonadiserver] Found mysql_upgrade:  "/usr/bin/mysql_upgrade"
"akonadiserver" [out] "Looking for 'mysql' as: /usr/bin/mysql
" 
"akonadiserver" [out] "Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
" 
"akonadiserver" [out] "Running 'mysqlcheck' with connection arguments: '--port=3306' '--socket=/var/run/mysqld/mysqld.sock' '--socket=/home/michael/.local/share/akonadi/db_misc/mysql.socket' 
" 
[akonadiserver] /usr/bin/mysqlcheck: Got error: 2002: Can't connect to local MySQL server through socket '/home/michael/.local/share/akonadi/db_misc/mysql.socket' (2) when trying to connect
[akonadiserver] FATAL ERROR: Upgrade failed
plasma-desktop(1759)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/usr/share/applications/grpn.desktop" not found
plasma-desktop(1759)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/usr/share/applications/opera-browser.desktop" not found
plasma-desktop(1759)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/michael/.kde/share/apps/RecentDocuments/110316T2030-MinutasTorre.pdf[2].desktop" not found
plasma-desktop(1759)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/michael/.kde/share/apps/RecentDocuments/110316T2030-MinutasTorre.pdf.desktop" not found
plasma-desktop(1759)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/michael/.kde/share/apps/RecentDocuments/.desktop" not found
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
link MoonMaster hasn't been detected!
[akonadiserver] Database "akonadi" opened using driver "QMYSQL"
[akonadiserver] DbInitializer::run()
[akonadiserver] checking table  "SchemaVersionTable"
[akonadiserver] checking table  "ResourceTable"
[akonadiserver] checking table  "CollectionTable"
[akonadiserver] checking table  "MimeTypeTable"
[akonadiserver] checking table  "PimItemTable"
[akonadiserver] checking table  "FlagTable"
[akonadiserver] checking table  "PartTable"
[akonadiserver] checking table  "CollectionAttributeTable"
Invalid D-BUS interface name 'org.kde.plasma-desktop.PlasmaApp' found while parsing introspection
[akonadiserver] checking relation  "PimItemFlagRelation"
[akonadiserver] checking relation  "CollectionMimeTypeRelation"
[akonadiserver] checking relation  "CollectionPimItemRelation"
[akonadiserver] DbInitializer::run() done
[akonadiserver] skipping update 2
[akonadiserver] skipping update 3
[akonadiserver] skipping update 4
[akonadiserver] skipping update 8
[akonadiserver] skipping update 10
[akonadiserver] skipping update 12
[akonadiserver] skipping update 13
[akonadiserver] skipping update 14
[akonadiserver] skipping update 15
[akonadiserver] skipping update 16
[akonadiserver] skipping update 17
[akonadiserver] skipping update 18
[akonadiserver] skipping update 19
[akonadiserver] Nepomuk Query Server not available
[akonadiserver] DataStore::unhideAllPimItems()
[akonadiserver] Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
[akonadiserver] Database "akonadi" opened using driver "QMYSQL"
[akonadiserver] Database "akonadi" opened using driver "QMYSQL"
PLUGINS:  "/usr/share/akonadi/agents" 
PLUGINS:  ("birthdaysresource.desktop", "contactsresource.desktop", "icalresource.desktop", "imapresource.desktop", "kabcresource.desktop", "kcalresource.desktop", "knutresource.desktop", "kolabproxyresource.desktop", "localbookmarksresource.desktop", "maildirresource.desktop", "maildispatcheragent.desktop", "mboxresource.desktop", "microblog.desktop", "mtdummyresource.desktop", "nepomukcalendarfeeder.desktop", "nepomukcontactfeeder.desktop", "nepomuktagresource.desktop", "nntpresource.desktop", "notesresource.desktop", "pop3resource.desktop", "vcarddirresource.desktop", "vcardresource.desktop") 
search paths:  ("/home/michael/bin", "/usr/local/sbin", "/usr/local/bin", "/usr/sbin", "/usr/bin", "/sbin", "/bin", "/usr/games") 
PLUGINS inserting:  "akonadi_birthdays_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_contacts_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_ical_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_imap_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_kabc_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_kcal_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_knut_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_kolabproxy_resource" 0 ("Resource", "Unique", "NoConfig") 
PLUGINS inserting:  "akonadi_localbookmarks_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_maildir_resource" 1 ("Resource") 
PLUGINS inserting:  "akonadi_maildispatcher_agent" 0 ("Unique", "Autostart", "NoConfig") 
PLUGINS inserting:  "akonadi_mbox_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_microblog_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_mailtransport_dummy_resource" 0 ("Resource", "MailTransport") 
PLUGINS inserting:  "akonadi_nepomuk_calendar_feeder" 0 ("Unique", "NoConfig") 
PLUGINS inserting:  "akonadi_nepomuk_contact_feeder" 0 ("Unique", "Autostart", "NoConfig") 
PLUGINS inserting:  "akonadi_nepomuktag_resource" 0 ("Resource", "Virtual", "Unique", "NoConfig") 
PLUGINS inserting:  "akonadi_nntp_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_notes_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_pop3_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_vcarddir_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_vcard_resource" 1 ("Resource") 
PLUGINS:  "/usr/share/akonadi/agents" 
PLUGINS:  ("birthdaysresource.desktop", "contactsresource.desktop", "icalresource.desktop", "imapresource.desktop", "kabcresource.desktop", "kcalresource.desktop", "knutresource.desktop", "kolabproxyresource.desktop", "localbookmarksresource.desktop", "maildirresource.desktop", "maildispatcheragent.desktop", "mboxresource.desktop", "microblog.desktop", "mtdummyresource.desktop", "nepomukcalendarfeeder.desktop", "nepomukcontactfeeder.desktop", "nepomuktagresource.desktop", "nntpresource.desktop", "notesresource.desktop", "pop3resource.desktop", "vcarddirresource.desktop", "vcardresource.desktop") 
Akonadi server is now operational. 
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4294967295
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 35654603 ;WMCLASS: "plasma-desktop" : "plasma-desktop" ;Caption: "plasma-desktop" ' : 70270
kwin(1753) KWin::Workspace::allowClientActivation: Activation, compared: 'ID: 35654603 ;WMCLASS: "plasma-desktop" : "plasma-desktop" ;Caption: "plasma-desktop" ' : 70270 : 63625 : true
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4294967295
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, already exists: 0
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QCoreApplication::postEvent: Unexpected null receiver
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
[akonadiserver] Database "akonadi" opened using driver "QMYSQL"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "QLocalSocket::connectToServer: Connection refused"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "QLocalSocket::connectToServer: Connection refused"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "QLocalSocket::connectToServer: Connection refused"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "QLocalSocket::connectToServer: Connection refused"
[/usr/bin/akonadi_nepomuk_contact_feeder] Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
[akonadiserver] Database "akonadi" opened using driver "QMYSQL"
[akonadiserver] Database "akonadi" opened using driver "QMYSQL"
[/usr/bin/akonadi_nepomuk_contact_feeder] QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
[akonadiserver] Database "akonadi" opened using driver "QMYSQL"
plasma-desktop(1759)/libplasma Plasma::Applet::itemChange: Configuration object was requested prior to init(), which is too early. Please fix this item: QGraphicsWidget (this = 0x2079ed0 , parent = 0x0 , pos = QPointF(-8.38861e+07, -1.67772e+07) , z = 0 , flags =  ( ItemUsesExtendedStyleOption | ItemSendsGeometryChanges ) ) SystemTray::TaskArea (this = 0x2078840 , parent = 0x2070180 , pos = QPointF(4, 4) , z = 0 , flags =  ( ItemUsesExtendedStyleOption | ItemSendsGeometryChanges ) ) "Notificador de dispositivo" 
QMetaObject::invokeMethod: No such method PlasmaApp::loadCommandLineOptionsForNewInstance()
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
plasma-desktop(1759)/libakonadi Akonadi::EntityTreeModelPrivate::fetchJobDone: Job error:  "Error desconocido." 

QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
kio_trash(1817)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kio_trash(1817)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/michael/.local/share/mime/magic"
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
[akonadiserver] Database "akonadi" opened using driver "QMYSQL"
[akonadiserver] Database "akonadi" opened using driver "QMYSQL"
[/usr/bin/akonadi_nepomuk_contact_feeder] [/usr/bin/nepomukservicestub] Using Virtuoso Version: "6.1.2.3127-pthreads"
[/usr/bin/akonadi_nepomuk_contact_feeder] Using Virtuoso Version: "6.1.2.3127-pthreads"
[/usr/bin/akonadi_nepomuk_contact_feeder] void Soprano::VirtuosoController::writeConfigFile(const QString&, const Soprano::BackendSettings&) "/tmp/virtuoso_Lh1832.ini"
[/usr/bin/akonadi_nepomuk_contact_feeder] Starting Virtuoso server: "/usr/bin/virtuoso-t" ("+foreground", "+configfile", "/tmp/virtuoso_Lh1832.ini", "+wait")
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] "/usr/bin/akonadi_nepomuk_contact_feeder(1812)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/akonadi_nepomuk_contact_feeder] [/usr/bin/nepomukservicestub] "
[/usr/bin/akonadi_nepomuk_contact_feeder] "
[/usr/bin/akonadi_nepomuk_contact_feeder] "		Tue Mar 22 2011
[/usr/bin/akonadi_nepomuk_contact_feeder] "
[/usr/bin/akonadi_nepomuk_contact_feeder] [/usr/bin/nepomukservicestub] "15:05:48 OpenLink Virtuoso Universal Server
[/usr/bin/akonadi_nepomuk_contact_feeder] "
[/usr/bin/akonadi_nepomuk_contact_feeder] "15:05:48 Version 06.01.3127-pthreads for Linux as of Aug  2 2010
[/usr/bin/akonadi_nepomuk_contact_feeder] "
[/usr/bin/akonadi_nepomuk_contact_feeder] "15:05:48 uses parts of OpenSSL, PCRE, Html Tidy
[/usr/bin/akonadi_nepomuk_contact_feeder] "
[/usr/bin/akonadi_nepomuk_contact_feeder] [/usr/bin/nepomukservicestub] "15:05:49 Database version 3126
[/usr/bin/akonadi_nepomuk_contact_feeder] "
[/usr/bin/akonadi_nepomuk_contact_feeder] [/usr/bin/nepomukservicestub] "15:05:49 Entering Lite Mode
[/usr/bin/akonadi_nepomuk_contact_feeder] "
[/usr/bin/akonadi_nepomuk_contact_feeder] [/usr/bin/nepomukservicestub] "15:05:49 SQL Optimizer enabled (max 1000 layouts)
[/usr/bin/akonadi_nepomuk_contact_feeder] "
[/usr/bin/akonadi_nepomuk_contact_feeder] [/usr/bin/nepomukservicestub] "15:05:50 Compiler unit is timed at 0.001281 msec
[/usr/bin/akonadi_nepomuk_contact_feeder] "
kcminit(1681)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcm_kpk_update.so"
kcminit(1681)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcm_kpk_addrm.so"
<unknown program name>(1855)/ kdemain: Xlib XKB extension major= 1  minor= 0
kcminit(1681)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcm_hotkeys.so"
kcminit(1681)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcm_keys.so"
kaccess(1855) kdemain: X server XKB extension major= 1  minor= 0
QMetaObject::invokeMethod: No such method KAccessApp::loadCommandLineOptionsForNewInstance()
kcminit(1681)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcm_kpk_settings.so"
kcminit(1681)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcminit_nsplugins.so"
kcminit(1681)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcm_emoticons.so"
Couldn't find synaptics properties. No synaptics driver loaded?
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XMappingNotify event
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+J" for "kwin" : "Switch Focus Down"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Left" for "kwin" : "Switch One Desktop to the Left"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F12" for "kwin" : "Mouse Emulation"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F4" for "kwin" : "Window Close"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+PgUp" for "kwin" : "Previous Layout"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+J" for "kwin" : "Move Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+A" for "kwin" : "Activate Window Demanding Attention"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+Backtab" for "kwin" : "Walk Through Windows (Reverse)"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F1" for "kwin" : "Switch to Desktop 1"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F2" for "kwin" : "Switch to Desktop 2"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F3" for "kwin" : "Switch to Desktop 3"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F4" for "kwin" : "Switch to Desktop 4"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F5" for "kwin" : "Switch to Desktop 5"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F6" for "kwin" : "Switch to Desktop 6"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+K" for "kwin" : "Switch Focus Up"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Print" for "kwin" : "Window Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Left" for "kwin" : "Window to Previous Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Right" for "kwin" : "Switch One Desktop to the Right"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Right" for "kwin" : "Window to Next Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F3" for "kwin" : "Window Operations Menu"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+H" for "kwin" : "Switch Focus Left"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+F11" for "kwin" : "Enable/Disable Tiling"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+H" for "kwin" : "Move Window Left"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Tab" for "kwin" : "Walk Through Windows"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+K" for "kwin" : "Move Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+L" for "kwin" : "Move Window Right"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Esc" for "kwin" : "Kill Window"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Print" for "kwin" : "Desktop Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Up" for "kwin" : "Switch Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+PgDown" for "kwin" : "Next Layout"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+F12" for "kwin" : "Suspend Compositing"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+F" for "kwin" : "Toggle Floating"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Down" for "kwin" : "Switch Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F12" for "plasma-desktop" : "Show Dashboard"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F1" for "plasma-desktop" : "activate widget 5"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Q" for "plasma-desktop" : "manage activities"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+Tab" for "plasma-desktop" : "Previous Activity"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Monitor Brightness Up" for "kded" : "Increase Screen Brightness"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Monitor Brightness Down" for "kded" : "Decrease Screen Brightness"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+J" for "kwin" : "Switch Focus Down"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Left" for "kwin" : "Switch One Desktop to the Left"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F12" for "kwin" : "Mouse Emulation"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F4" for "kwin" : "Window Close"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+PgUp" for "kwin" : "Previous Layout"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+J" for "kwin" : "Move Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+A" for "kwin" : "Activate Window Demanding Attention"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+Backtab" for "kwin" : "Walk Through Windows (Reverse)"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F1" for "kwin" : "Switch to Desktop 1"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F2" for "kwin" : "Switch to Desktop 2"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F3" for "kwin" : "Switch to Desktop 3"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F4" for "kwin" : "Switch to Desktop 4"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F5" for "kwin" : "Switch to Desktop 5"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F6" for "kwin" : "Switch to Desktop 6"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+K" for "kwin" : "Switch Focus Up"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Print" for "kwin" : "Window Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Left" for "kwin" : "Window to Previous Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Right" for "kwin" : "Switch One Desktop to the Right"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Right" for "kwin" : "Window to Next Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F3" for "kwin" : "Window Operations Menu"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+H" for "kwin" : "Switch Focus Left"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F11" for "kwin" : "Enable/Disable Tiling"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+H" for "kwin" : "Move Window Left"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Tab" for "kwin" : "Walk Through Windows"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+K" for "kwin" : "Move Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+L" for "kwin" : "Move Window Right"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Esc" for "kwin" : "Kill Window"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Print" for "kwin" : "Desktop Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Up" for "kwin" : "Switch Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+PgDown" for "kwin" : "Next Layout"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F12" for "kwin" : "Suspend Compositing"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+F" for "kwin" : "Toggle Floating"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Down" for "kwin" : "Switch Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F12" for "plasma-desktop" : "Show Dashboard"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F1" for "plasma-desktop" : "activate widget 5"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Q" for "plasma-desktop" : "manage activities"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+Tab" for "plasma-desktop" : "Previous Activity"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Monitor Brightness Up" for "kded" : "Increase Screen Brightness"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Monitor Brightness Down" for "kded" : "Decrease Screen Brightness"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Del" for "ksmserver" : "Log Out"
Nepomuk server already running.
[/usr/bin/akonadi_nepomuk_contact_feeder] QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+Del" for "ksmserver" : "Log Out Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+PgDown" for "ksmserver" : "Halt Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+PgUp" for "ksmserver" : "Reboot Without Confirmation"
Could not find 'knetworkmanager' executable.
Announce the service on avahi
Starting ICA
Establecido bajo el nombre «italc michael»
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Display" for "kded" : "display"
New PolkitAgentListener  0xbbbca0 
Adding new listener  PolkitQt1::Agent::Listener(0xc9c020) for  0xbbbca0 

(process:1882): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(process:1882): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
QMetaObject::invokeMethod: No such method PolicyKitKDE::loadCommandLineOptionsForNewInstance()
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Print" for "khotkeys" : "{97d02ee2-9871-4d68-84f9-0bc670bf75db}"
kglobalaccel(1675) KdeDGlobalAccel::Component::cleanUp: 1
QMetaObject::invokeMethod: No such method KMixApp::loadCommandLineOptionsForNewInstance()
PORT=5900
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No existe el fichero o el directorio
QFileSystemWatcher: failed to add paths: /home/michael/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Volume Up" for "kmix" : "increase_volume"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Volume Down" for "kmix" : "decrease_volume"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Volume Mute" for "kmix" : "mute"
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+R" for "klipper" : "repeat_action"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+X" for "klipper" : "clipboard_action"
QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Tab" for "krunner" : "Run Command"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F2" for "krunner" : "Run Command on clipboard contents"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Esc" for "krunner" : "Show System Activity"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Ins" for "krunner" : "Switch User"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+L" for "krunner" : "Lock Session"
kglobalaccel(1675) GlobalShortcut::setKeys: "Systemtray-Klipper-10" skipping because key "Ctrl+Alt+V" is already taken
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
"/usr/bin/krunner(1868)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/krunner(1868)" Soprano: "QLocalSocket::connectToServer: Connection refused"
"/usr/bin/krunner(1868)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/krunner(1868)" Soprano: "QLocalSocket::connectToServer: Connection refused"
"/usr/bin/krunner(1868)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/krunner(1868)" Soprano: "QLocalSocket::connectToServer: Connection refused"
params.c:OpenConfFile() - Unable to open configuration file "/home/michael/.smb/smb.conf":
	No existe el fichero o el directorio
params.c:OpenConfFile() - Unable to open configuration file "/home/michael/.smb/smb.conf.append":
	No existe el fichero o el directorio
kmix(1927) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
I/O warning : failed to load external entity "/home/michael/.qalculate/eurofxref-daily.xml"
I/O warning : failed to load external entity "/home/michael/.qalculate/eurofxref-daily.xml"
krunner(1868)/libplasma Plasma::Package::isValid: Could not find required file mainscript , look in "/home/michael/Documentos/contents/code/main" 

QMetaObject::invokeMethod: No such method KRunnerApp::loadCommandLineOptionsForNewInstance()
kio_trash(1978)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kio_trash(1978)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/michael/.local/share/mime/magic"
[/usr/bin/akonadi_nepomuk_contact_feeder] [/usr/bin/nepomukservicestub] "15:06:03 Roll forward started
[/usr/bin/akonadi_nepomuk_contact_feeder] "
[/usr/bin/akonadi_nepomuk_contact_feeder] [/usr/bin/nepomukservicestub] "15:06:03 The transaction log file has been produced by server version '06.01.3126'. The version of this server is '06.01.3127'. If the transaction log is empty or you do not want to replay it then delete it and start the server again. Otherwise replay the log using the server of version '06.01.3126' and make checkpoint and shutdown to ensure that the log is empty, then delete it and start using new version.
[/usr/bin/akonadi_nepomuk_contact_feeder] "
[/usr/bin/akonadi_nepomuk_contact_feeder] [/usr/bin/nepomukservicestub] "15:06:03 Server exiting
[/usr/bin/akonadi_nepomuk_contact_feeder] "
[/usr/bin/akonadi_nepomuk_contact_feeder] [/usr/bin/nepomukservicestub] Virtuoso server stopped: 3
[/usr/bin/akonadi_nepomuk_contact_feeder] [/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(1832)" Soprano: "Failed to start Virtuoso"
[/usr/bin/akonadi_nepomuk_contact_feeder] [/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(1832)" Soprano: "Failed to start Virtuoso"
[/usr/bin/akonadi_nepomuk_contact_feeder] Application '/usr/bin/nepomukservicestub nepomukstorage' exited normally...
[/usr/bin/akonadi_nepomuk_contact_feeder] Nepomuk server already running.
[/usr/bin/akonadi_nepomuk_contact_feeder] QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XMappingNotify event
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Mute" for "kmix" : "mute"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Down" for "kmix" : "decrease_volume"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Up" for "kmix" : "increase_volume"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+J" for "kwin" : "Switch Focus Down"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Left" for "kwin" : "Switch One Desktop to the Left"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F12" for "kwin" : "Mouse Emulation"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F4" for "kwin" : "Window Close"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+PgUp" for "kwin" : "Previous Layout"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+J" for "kwin" : "Move Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+A" for "kwin" : "Activate Window Demanding Attention"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+Backtab" for "kwin" : "Walk Through Windows (Reverse)"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F1" for "kwin" : "Switch to Desktop 1"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F2" for "kwin" : "Switch to Desktop 2"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F3" for "kwin" : "Switch to Desktop 3"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F4" for "kwin" : "Switch to Desktop 4"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F5" for "kwin" : "Switch to Desktop 5"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F6" for "kwin" : "Switch to Desktop 6"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+K" for "kwin" : "Switch Focus Up"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Print" for "kwin" : "Window Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Left" for "kwin" : "Window to Previous Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Right" for "kwin" : "Switch One Desktop to the Right"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Right" for "kwin" : "Window to Next Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F3" for "kwin" : "Window Operations Menu"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+H" for "kwin" : "Switch Focus Left"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+F11" for "kwin" : "Enable/Disable Tiling"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+H" for "kwin" : "Move Window Left"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Tab" for "kwin" : "Walk Through Windows"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+K" for "kwin" : "Move Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+L" for "kwin" : "Move Window Right"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Esc" for "kwin" : "Kill Window"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Print" for "kwin" : "Desktop Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Up" for "kwin" : "Switch Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+PgDown" for "kwin" : "Next Layout"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+F12" for "kwin" : "Suspend Compositing"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+F" for "kwin" : "Toggle Floating"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Down" for "kwin" : "Switch Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Shift+Del" for "ksmserver" : "Log Out Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Shift+PgDown" for "ksmserver" : "Halt Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Shift+PgUp" for "ksmserver" : "Reboot Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Del" for "ksmserver" : "Log Out"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Esc" for "krunner" : "Show System Activity"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Tab" for "krunner" : "Run Command"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+L" for "krunner" : "Lock Session"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+F2" for "krunner" : "Run Command on clipboard contents"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Ins" for "krunner" : "Switch User"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F12" for "plasma-desktop" : "Show Dashboard"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F1" for "plasma-desktop" : "activate widget 5"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Q" for "plasma-desktop" : "manage activities"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+Tab" for "plasma-desktop" : "Previous Activity"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Print" for "khotkeys" : "{97d02ee2-9871-4d68-84f9-0bc670bf75db}"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Display" for "kded" : "display"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Monitor Brightness Up" for "kded" : "Increase Screen Brightness"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Monitor Brightness Down" for "kded" : "Decrease Screen Brightness"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+R" for "klipper" : "repeat_action"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+X" for "klipper" : "clipboard_action"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Volume Mute" for "kmix" : "mute"
Fetched layout groups from X server: 	layouts: ("latam") 	variants: ("") 
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Volume Down" for "kmix" : "decrease_volume"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Volume Up" for "kmix" : "increase_volume"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+J" for "kwin" : "Switch Focus Down"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Left" for "kwin" : "Switch One Desktop to the Left"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F12" for "kwin" : "Mouse Emulation"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F4" for "kwin" : "Window Close"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+PgUp" for "kwin" : "Previous Layout"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+J" for "kwin" : "Move Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+A" for "kwin" : "Activate Window Demanding Attention"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+Backtab" for "kwin" : "Walk Through Windows (Reverse)"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F1" for "kwin" : "Switch to Desktop 1"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F2" for "kwin" : "Switch to Desktop 2"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F3" for "kwin" : "Switch to Desktop 3"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F4" for "kwin" : "Switch to Desktop 4"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F5" for "kwin" : "Switch to Desktop 5"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F6" for "kwin" : "Switch to Desktop 6"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+K" for "kwin" : "Switch Focus Up"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Print" for "kwin" : "Window Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Left" for "kwin" : "Window to Previous Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Right" for "kwin" : "Switch One Desktop to the Right"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Right" for "kwin" : "Window to Next Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F3" for "kwin" : "Window Operations Menu"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+H" for "kwin" : "Switch Focus Left"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F11" for "kwin" : "Enable/Disable Tiling"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+H" for "kwin" : "Move Window Left"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Tab" for "kwin" : "Walk Through Windows"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+K" for "kwin" : "Move Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+L" for "kwin" : "Move Window Right"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Esc" for "kwin" : "Kill Window"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Print" for "kwin" : "Desktop Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Up" for "kwin" : "Switch Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+PgDown" for "kwin" : "Next Layout"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F12" for "kwin" : "Suspend Compositing"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+F" for "kwin" : "Toggle Floating"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Down" for "kwin" : "Switch Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+Del" for "ksmserver" : "Log Out Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+PgDown" for "ksmserver" : "Halt Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+PgUp" for "ksmserver" : "Reboot Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Del" for "ksmserver" : "Log Out"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Esc" for "krunner" : "Show System Activity"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Tab" for "krunner" : "Run Command"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+L" for "krunner" : "Lock Session"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F2" for "krunner" : "Run Command on clipboard contents"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Ins" for "krunner" : "Switch User"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F12" for "plasma-desktop" : "Show Dashboard"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F1" for "plasma-desktop" : "activate widget 5"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Q" for "plasma-desktop" : "manage activities"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+Tab" for "plasma-desktop" : "Previous Activity"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Print" for "khotkeys" : "{97d02ee2-9871-4d68-84f9-0bc670bf75db}"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Display" for "kded" : "display"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Monitor Brightness Up" for "kded" : "Increase Screen Brightness"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Monitor Brightness Down" for "kded" : "Decrease Screen Brightness"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+R" for "klipper" : "repeat_action"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+X" for "klipper" : "clipboard_action"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 107491
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 75497475 ;WMCLASS: "opera" : "securitypassworddialog" ;Caption: "Contraseña" ' : 107491
kwin(1753) KWin::Workspace::allowClientActivation: Activation: No client active, allowing
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Contraseña"
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4294967295
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 75497496 ;WMCLASS: "opera" : "opera" ;Caption: "Opera" ' : 119810
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Opera"
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
okular(3654)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
okular(3654)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
okular(3654)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4294967295
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 83886234 ;WMCLASS: "okular" : "okular" ;Caption: "Okular" ' : 521144
kwin(1753) KWin::Workspace::allowClientActivation: Activation, compared: 'ID: 83886234 ;WMCLASS: "okular" : "okular" ;Caption: "Okular" ' : 521144 : 124483 : true
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Okular"
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No existe el fichero o el directorio
QFileSystemWatcher: failed to add paths: /home/michael/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(1675) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(1675) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(1675) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

Object::disconnect: No such slot QObject::dataUpdated(QString,Plasma::DataEngine::Data)
Object::disconnect:  (sender name:   '/org/freedesktop/Hal/devices/volume_uuid_55D123D9E79ABF54')
Object::disconnect: No such slot QObject::dataUpdated(QString,Plasma::DataEngine::Data)
Object::disconnect:  (sender name:   '/org/freedesktop/Hal/devices/volume_uuid_3ECC_77C6')
QGraphicsLinearLayout::itemAt: invalid index 2
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
plasma-desktop(1759)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
QGraphicsLinearLayout::removeAt: invalid index 1
plasma-desktop(1759)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
kmix(1927) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
plasma-desktop(1759)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
QWidget::setMinimumSize: (/StackDialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/StackDialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/StackDialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 107491
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 35741806 ;WMCLASS: "plasma-desktop" : "plasma-desktop" ;Caption: "plasma-desktop" ' : 107491
kwin(1753) KWin::Workspace::allowClientActivation: Activation, compared: 'ID: 35741806 ;WMCLASS: "plasma-desktop" : "plasma-desktop" ;Caption: "plasma-desktop" ' : 107491 : 577717 : false
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
QWidget::setMinimumSize: (/StackDialog) Negative sizes (-1,-1) are not possible
kded(1661)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QObject::connect: Cannot connect (null)::ejectPressed(QString) to SolidAutoEject::onEjectPressed(QString)
kded(1661)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QObject::connect: Cannot connect (null)::ejectPressed(QString) to SolidAutoEject::onEjectPressed(QString)
kded(1661)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QObject::connect: Cannot connect (null)::ejectPressed(QString) to SolidAutoEject::onEjectPressed(QString)
kded(1661)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QObject::connect: Cannot connect (null)::ejectPressed(QString) to SolidAutoEject::onEjectPressed(QString)
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XMappingNotify event
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Mute" for "kmix" : "mute"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Down" for "kmix" : "decrease_volume"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Up" for "kmix" : "increase_volume"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+J" for "kwin" : "Switch Focus Down"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Left" for "kwin" : "Switch One Desktop to the Left"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F12" for "kwin" : "Mouse Emulation"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F4" for "kwin" : "Window Close"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+PgUp" for "kwin" : "Previous Layout"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+J" for "kwin" : "Move Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+A" for "kwin" : "Activate Window Demanding Attention"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+Backtab" for "kwin" : "Walk Through Windows (Reverse)"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F1" for "kwin" : "Switch to Desktop 1"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F2" for "kwin" : "Switch to Desktop 2"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F3" for "kwin" : "Switch to Desktop 3"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F4" for "kwin" : "Switch to Desktop 4"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F5" for "kwin" : "Switch to Desktop 5"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F6" for "kwin" : "Switch to Desktop 6"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+K" for "kwin" : "Switch Focus Up"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Print" for "kwin" : "Window Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Left" for "kwin" : "Window to Previous Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Right" for "kwin" : "Switch One Desktop to the Right"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Right" for "kwin" : "Window to Next Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F3" for "kwin" : "Window Operations Menu"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+H" for "kwin" : "Switch Focus Left"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+F11" for "kwin" : "Enable/Disable Tiling"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+H" for "kwin" : "Move Window Left"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Tab" for "kwin" : "Walk Through Windows"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+K" for "kwin" : "Move Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+L" for "kwin" : "Move Window Right"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Esc" for "kwin" : "Kill Window"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Print" for "kwin" : "Desktop Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Up" for "kwin" : "Switch Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+PgDown" for "kwin" : "Next Layout"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+F12" for "kwin" : "Suspend Compositing"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+F" for "kwin" : "Toggle Floating"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Down" for "kwin" : "Switch Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Shift+Del" for "ksmserver" : "Log Out Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Shift+PgDown" for "ksmserver" : "Halt Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Shift+PgUp" for "ksmserver" : "Reboot Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Del" for "ksmserver" : "Log Out"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Esc" for "krunner" : "Show System Activity"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Tab" for "krunner" : "Run Command"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+L" for "krunner" : "Lock Session"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+F2" for "krunner" : "Run Command on clipboard contents"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Ins" for "krunner" : "Switch User"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F12" for "plasma-desktop" : "Show Dashboard"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F1" for "plasma-desktop" : "activate widget 5"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Q" for "plasma-desktop" : "manage activities"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+Tab" for "plasma-desktop" : "Previous Activity"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Print" for "khotkeys" : "{97d02ee2-9871-4d68-84f9-0bc670bf75db}"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Display" for "kded" : "display"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Monitor Brightness Up" for "kded" : "Increase Screen Brightness"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Monitor Brightness Down" for "kded" : "Decrease Screen Brightness"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+R" for "klipper" : "repeat_action"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+X" for "klipper" : "clipboard_action"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Volume Mute" for "kmix" : "mute"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Volume Down" for "kmix" : "decrease_volume"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Volume Up" for "kmix" : "increase_volume"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+J" for "kwin" : "Switch Focus Down"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Left" for "kwin" : "Switch One Desktop to the Left"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F12" for "kwin" : "Mouse Emulation"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F4" for "kwin" : "Window Close"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+PgUp" for "kwin" : "Previous Layout"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+J" for "kwin" : "Move Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+A" for "kwin" : "Activate Window Demanding Attention"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+Backtab" for "kwin" : "Walk Through Windows (Reverse)"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F1" for "kwin" : "Switch to Desktop 1"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F2" for "kwin" : "Switch to Desktop 2"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F3" for "kwin" : "Switch to Desktop 3"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F4" for "kwin" : "Switch to Desktop 4"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F5" for "kwin" : "Switch to Desktop 5"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F6" for "kwin" : "Switch to Desktop 6"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+K" for "kwin" : "Switch Focus Up"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Print" for "kwin" : "Window Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Left" for "kwin" : "Window to Previous Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Right" for "kwin" : "Switch One Desktop to the Right"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Right" for "kwin" : "Window to Next Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F3" for "kwin" : "Window Operations Menu"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+H" for "kwin" : "Switch Focus Left"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F11" for "kwin" : "Enable/Disable Tiling"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+H" for "kwin" : "Move Window Left"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Tab" for "kwin" : "Walk Through Windows"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+K" for "kwin" : "Move Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+L" for "kwin" : "Move Window Right"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Esc" for "kwin" : "Kill Window"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Print" for "kwin" : "Desktop Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Up" for "kwin" : "Switch Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+PgDown" for "kwin" : "Next Layout"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F12" for "kwin" : "Suspend Compositing"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+F" for "kwin" : "Toggle Floating"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Down" for "kwin" : "Switch Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+Del" for "ksmserver" : "Log Out Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+PgDown" for "ksmserver" : "Halt Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+PgUp" for "ksmserver" : "Reboot Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Del" for "ksmserver" : "Log Out"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Esc" for "krunner" : "Show System Activity"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Tab" for "krunner" : "Run Command"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+L" for "krunner" : "Lock Session"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F2" for "krunner" : "Run Command on clipboard contents"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Ins" for "krunner" : "Switch User"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F12" for "plasma-desktop" : "Show Dashboard"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F1" for "plasma-desktop" : "activate widget 5"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Q" for "plasma-desktop" : "manage activities"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+Tab" for "plasma-desktop" : "Previous Activity"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Print" for "khotkeys" : "{97d02ee2-9871-4d68-84f9-0bc670bf75db}"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Display" for "kded" : "display"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Monitor Brightness Up" for "kded" : "Increase Screen Brightness"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Monitor Brightness Down" for "kded" : "Decrease Screen Brightness"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+R" for "klipper" : "repeat_action"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+X" for "klipper" : "clipboard_action"
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XMappingNotify event
Fetched layout groups from X server: 	layouts: ("latam") 	variants: ("") 
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Mute" for "kmix" : "mute"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Down" for "kmix" : "decrease_volume"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Up" for "kmix" : "increase_volume"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+J" for "kwin" : "Switch Focus Down"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Left" for "kwin" : "Switch One Desktop to the Left"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F12" for "kwin" : "Mouse Emulation"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F4" for "kwin" : "Window Close"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+PgUp" for "kwin" : "Previous Layout"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+J" for "kwin" : "Move Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+A" for "kwin" : "Activate Window Demanding Attention"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+Backtab" for "kwin" : "Walk Through Windows (Reverse)"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F1" for "kwin" : "Switch to Desktop 1"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F2" for "kwin" : "Switch to Desktop 2"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F3" for "kwin" : "Switch to Desktop 3"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F4" for "kwin" : "Switch to Desktop 4"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F5" for "kwin" : "Switch to Desktop 5"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F6" for "kwin" : "Switch to Desktop 6"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+K" for "kwin" : "Switch Focus Up"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Print" for "kwin" : "Window Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Left" for "kwin" : "Window to Previous Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Right" for "kwin" : "Switch One Desktop to the Right"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Right" for "kwin" : "Window to Next Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F3" for "kwin" : "Window Operations Menu"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+H" for "kwin" : "Switch Focus Left"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+F11" for "kwin" : "Enable/Disable Tiling"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+H" for "kwin" : "Move Window Left"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Tab" for "kwin" : "Walk Through Windows"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+K" for "kwin" : "Move Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+L" for "kwin" : "Move Window Right"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Esc" for "kwin" : "Kill Window"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Print" for "kwin" : "Desktop Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Up" for "kwin" : "Switch Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+PgDown" for "kwin" : "Next Layout"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+F12" for "kwin" : "Suspend Compositing"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+F" for "kwin" : "Toggle Floating"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Down" for "kwin" : "Switch Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Shift+Del" for "ksmserver" : "Log Out Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Shift+PgDown" for "ksmserver" : "Halt Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Shift+PgUp" for "ksmserver" : "Reboot Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Del" for "ksmserver" : "Log Out"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Esc" for "krunner" : "Show System Activity"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Tab" for "krunner" : "Run Command"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+L" for "krunner" : "Lock Session"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+F2" for "krunner" : "Run Command on clipboard contents"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Ins" for "krunner" : "Switch User"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F12" for "plasma-desktop" : "Show Dashboard"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F1" for "plasma-desktop" : "activate widget 5"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Q" for "plasma-desktop" : "manage activities"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+Tab" for "plasma-desktop" : "Previous Activity"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Print" for "khotkeys" : "{97d02ee2-9871-4d68-84f9-0bc670bf75db}"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Display" for "kded" : "display"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Monitor Brightness Up" for "kded" : "Increase Screen Brightness"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Monitor Brightness Down" for "kded" : "Decrease Screen Brightness"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+R" for "klipper" : "repeat_action"
kglobalaccel(1675) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+X" for "klipper" : "clipboard_action"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Volume Mute" for "kmix" : "mute"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Volume Down" for "kmix" : "decrease_volume"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Volume Up" for "kmix" : "increase_volume"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+J" for "kwin" : "Switch Focus Down"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Left" for "kwin" : "Switch One Desktop to the Left"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F12" for "kwin" : "Mouse Emulation"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F4" for "kwin" : "Window Close"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+PgUp" for "kwin" : "Previous Layout"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+J" for "kwin" : "Move Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+A" for "kwin" : "Activate Window Demanding Attention"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+Backtab" for "kwin" : "Walk Through Windows (Reverse)"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F1" for "kwin" : "Switch to Desktop 1"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F2" for "kwin" : "Switch to Desktop 2"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F3" for "kwin" : "Switch to Desktop 3"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F4" for "kwin" : "Switch to Desktop 4"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F5" for "kwin" : "Switch to Desktop 5"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F6" for "kwin" : "Switch to Desktop 6"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+K" for "kwin" : "Switch Focus Up"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Print" for "kwin" : "Window Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Left" for "kwin" : "Window to Previous Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Right" for "kwin" : "Switch One Desktop to the Right"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Right" for "kwin" : "Window to Next Desktop"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F3" for "kwin" : "Window Operations Menu"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+H" for "kwin" : "Switch Focus Left"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F11" for "kwin" : "Enable/Disable Tiling"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+H" for "kwin" : "Move Window Left"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Tab" for "kwin" : "Walk Through Windows"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+K" for "kwin" : "Move Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+L" for "kwin" : "Move Window Right"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Esc" for "kwin" : "Kill Window"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Print" for "kwin" : "Desktop Screenshot to Clipboard"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Up" for "kwin" : "Switch Window Up"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+PgDown" for "kwin" : "Next Layout"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F12" for "kwin" : "Suspend Compositing"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+F" for "kwin" : "Toggle Floating"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Down" for "kwin" : "Switch Window Down"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+Del" for "ksmserver" : "Log Out Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+PgDown" for "ksmserver" : "Halt Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+PgUp" for "ksmserver" : "Reboot Without Confirmation"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Del" for "ksmserver" : "Log Out"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Esc" for "krunner" : "Show System Activity"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Tab" for "krunner" : "Run Command"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+L" for "krunner" : "Lock Session"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F2" for "krunner" : "Run Command on clipboard contents"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Ins" for "krunner" : "Switch User"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F12" for "plasma-desktop" : "Show Dashboard"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F1" for "plasma-desktop" : "activate widget 5"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Q" for "plasma-desktop" : "manage activities"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+Tab" for "plasma-desktop" : "Previous Activity"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Print" for "khotkeys" : "{97d02ee2-9871-4d68-84f9-0bc670bf75db}"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Display" for "kded" : "display"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Monitor Brightness Up" for "kded" : "Increase Screen Brightness"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Monitor Brightness Down" for "kded" : "Decrease Screen Brightness"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+R" for "klipper" : "repeat_action"
kglobalaccel(1675) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+X" for "klipper" : "clipboard_action"
klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 1849286
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 35654032 ;WMCLASS: "plasma-desktop" : "plasma-desktop" ;Caption: "plasma-desktop" ' : 1849286
kwin(1753) KWin::Workspace::allowClientActivation: Activation, compared: 'ID: 35654032 ;WMCLASS: "plasma-desktop" : "plasma-desktop" ;Caption: "plasma-desktop" ' : 1849286 : 577717 : true
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

plasma-desktop(1759)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(1675) GlobalShortcutsRegistry::keyPressed: "Meta+Tab" = "Run Command"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 3233723
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 10485779 ;WMCLASS: "krunner" : "krunner" ;Caption: "Ejecutar orden" ' : 3233723
kwin(1753) KWin::Workspace::allowClientActivation: Activation, compared: 'ID: 10485779 ;WMCLASS: "krunner" : "krunner" ;Caption: "Ejecutar orden" ' : 3233723 : 2864202 : true
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Ejecutar orden"
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No existe el fichero o el directorio
QFileSystemWatcher: failed to add paths: /home/michael/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
krunner(1868)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 56) 
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 3237086
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48234526 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "kdesvn" ' : 3237086
kwin(1753) KWin::Workspace::allowClientActivation: Activation, compared: 'ID: 48234526 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "kdesvn" ' : 3237086 : 2864202 : true
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "kdesvn"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 3247819
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48242017 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Stado / Lista – kdesvn" ' : 3247819
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Stado / Lista – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(1675) GlobalShortcutsRegistry::keyPressed: "Meta+Tab" = "Run Command"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 3364287
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 10485779 ;WMCLASS: "krunner" : "krunner" ;Caption: "Ejecutar orden" ' : 3364287
kwin(1753) KWin::Workspace::allowClientActivation: Activation, compared: 'ID: 10485779 ;WMCLASS: "krunner" : "krunner" ;Caption: "Ejecutar orden" ' : 3364287 : 3364177 : true
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Ejecutar orden"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(1675) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(1675) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(1675) GlobalShortcutsRegistry::keyPressed: "Meta+Alt+Right" = "Window to Next Desktop"
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No existe el fichero o el directorio
QFileSystemWatcher: failed to add paths: /home/michael/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4641495
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48248096 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Stado / Lista – kdesvn" ' : 4641495
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Stado / Lista – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4641495
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48248872 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Stado / Lista – kdesvn" ' : 4641495
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Stado / Lista – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4641495
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48249858 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Stado / Lista – kdesvn" ' : 4641495
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Stado / Lista – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4641495
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48250451 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Stado / Lista – kdesvn" ' : 4641495
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Stado / Lista – kdesvn"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4641495
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48250470 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Stado / Lista – kdesvn <2>&#8206;" ' : 4641495
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Stado / Lista – kdesvn <2>&#8206;"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4641495
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48251318 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Stado / Lista – kdesvn <2>&#8206;" ' : 4641495
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Stado / Lista – kdesvn <2>&#8206;"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(1675) GlobalShortcutsRegistry::keyPressed: "Meta+Tab" = "Run Command"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4736092
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 10485779 ;WMCLASS: "krunner" : "krunner" ;Caption: "Ejecutar orden" ' : 4736092
kwin(1753) KWin::Workspace::allowClientActivation: Activation, compared: 'ID: 10485779 ;WMCLASS: "krunner" : "krunner" ;Caption: "Ejecutar orden" ' : 4736092 : 4735709 : true
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Ejecutar orden"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(1675) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4744855
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 85983405 ;WMCLASS: "python" : "python" ;Caption: "PySVN WorkBench" ' : 4744855
kwin(1753) KWin::Workspace::allowClientActivation: Activation, compared: 'ID: 85983405 ;WMCLASS: "python" : "python" ;Caption: "PySVN WorkBench" ' : 4744855 : 4748415 : false
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "PySVN WorkBench"
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(1675) GlobalShortcutsRegistry::keyPressed: "Meta+Tab" = "Run Command"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4748551
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 10485779 ;WMCLASS: "krunner" : "krunner" ;Caption: "Ejecutar orden" ' : 4748551
kwin(1753) KWin::Workspace::allowClientActivation: Activation, compared: 'ID: 10485779 ;WMCLASS: "krunner" : "krunner" ;Caption: "Ejecutar orden" ' : 4748551 : 4748415 : true
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Ejecutar orden"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4755598
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 88080887 ;WMCLASS: "rapidsvn" : "rapidsvn" ;Caption: "RapidSVN" ' : 4755598
kwin(1753) KWin::Workspace::allowClientActivation: Activation, compared: 'ID: 88080887 ;WMCLASS: "rapidsvn" : "rapidsvn" ;Caption: "RapidSVN" ' : 4755598 : 4748415 : true
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "RapidSVN"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4790846
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 88082577 ;WMCLASS: "rapidsvn" : "rapidsvn" ;Caption: "Error de RapidSVN" ' : 4790846
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Error de RapidSVN"
QClipboard::setData: Cannot set X11 selection owner for PRIMARY
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4795494
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 88082897 ;WMCLASS: "rapidsvn" : "rapidsvn" ;Caption: "Error de RapidSVN" ' : 4795494
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Error de RapidSVN"
QClipboard::setData: Cannot set X11 selection owner for PRIMARY
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4805430
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 88083913 ;WMCLASS: "rapidsvn" : "rapidsvn" ;Caption: "Preferencias" ' : 4805430
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Preferencias"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(1675) GlobalShortcutsRegistry::keyPressed: "Meta+Tab" = "Run Command"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4827204
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 10485779 ;WMCLASS: "krunner" : "krunner" ;Caption: "Ejecutar orden" ' : 4827204
kwin(1753) KWin::Workspace::allowClientActivation: Activation, compared: 'ID: 10485779 ;WMCLASS: "krunner" : "krunner" ;Caption: "Ejecutar orden" ' : 4827204 : 4827013 : true
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Ejecutar orden"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4294967295
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 92274716 ;WMCLASS: "kcmshell4" : "kcmshell4" ;Caption: "Obtener y eliminar software – Módulo de control de KDE" ' : 4833715
kwin(1753) KWin::Workspace::allowClientActivation: Activation, compared: 'ID: 92274716 ;WMCLASS: "kcmshell4" : "kcmshell4" ;Caption: "Obtener y eliminar software – Módulo de control de KDE" ' : 4833715 : 4827013 : true
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Obtener y eliminar software – Módulo de control de KDE"
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No existe el fichero o el directorio
QFileSystemWatcher: failed to add paths: /home/michael/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
QWidget::setMinimumSize: (/Plasma::Dialog) Negative sizes (-1,-1) are not possible
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(1675) GlobalShortcutsRegistry::keyPressed: "Meta+Tab" = "Run Command"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4870275
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 10485779 ;WMCLASS: "krunner" : "krunner" ;Caption: "Ejecutar orden" ' : 4870275
kwin(1753) KWin::Workspace::allowClientActivation: Activation, compared: 'ID: 10485779 ;WMCLASS: "krunner" : "krunner" ;Caption: "Ejecutar orden" ' : 4870275 : 4870119 : true
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Ejecutar orden"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No existe el fichero o el directorio
QFileSystemWatcher: failed to add paths: /home/michael/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4873550
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94371872 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Cervisia" ' : 4873550
kwin(1753) KWin::Workspace::allowClientActivation: Activation, compared: 'ID: 94371872 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Cervisia" ' : 4873550 : 4870119 : true
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Cervisia"
klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4882558
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94375579 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Crear nuevo repositorio (cvs init) – Cervisia" ' : 4882558
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Crear nuevo repositorio (cvs init) – Cervisia"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(1675) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4911798
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94385553 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Crear nuevo repositorio (cvs init) – Cervisia" ' : 4911798
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Crear nuevo repositorio (cvs init) – Cervisia"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4913621
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94387472 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Seleccionar carpeta – Cervisia" ' : 4913621
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Seleccionar carpeta – Cervisia"
kio_trash(17160)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kio_trash(17160)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/michael/.local/share/mime/magic"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4922342
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94394376 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Nueva carpeta – Cervisia" ' : 4922342
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Nueva carpeta – Cervisia"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4943598
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94403579 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Descarga de CVS – Cervisia" ' : 4943598
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Descarga de CVS – Cervisia"
plasma-desktop(1759)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 2 
[31mvoid DBusMenuImporter::slotItemUpdated(int)[0m: No action for id 9 
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4748415
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48264498 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Stado / Lista – kdesvn" ' : 4748415
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Stado / Lista – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4748415
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48264518 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Stado / Lista – kdesvn" ' : 4748415
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Stado / Lista – kdesvn"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4748415
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48264561 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Stado / Lista – kdesvn <2>&#8206;" ' : 4748415
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Stado / Lista – kdesvn <2>&#8206;"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4748415
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48264742 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Stado / Lista – kdesvn <2>&#8206;" ' : 4748415
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Stado / Lista – kdesvn <2>&#8206;"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5010341
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94410938 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Descarga de CVS – Cervisia <2>&#8206;" ' : 5010341
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Descarga de CVS – Cervisia <2>&#8206;"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5024942
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94416037 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Seleccionar carpeta – Cervisia" ' : 5024942
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Seleccionar carpeta – Cervisia"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5043734
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94422671 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Información – Cervisia" ' : 5043734
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Información – Cervisia"
kmix(1927) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(1675) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kglobalaccel(1675) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(1675) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5061302
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94426053 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Configurar el acceso a los repositorios – Cervisia" ' : 5061302
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Configurar el acceso a los repositorios – Cervisia"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5068678
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94429525 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Crear nuevo repositorio (cvs init) – Cervisia" ' : 5068678
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Crear nuevo repositorio (cvs init) – Cervisia"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5072013
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94430463 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Seleccionar carpeta – Cervisia" ' : 5072013
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Seleccionar carpeta – Cervisia"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5080270
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94435348 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Descarga de CVS – Cervisia" ' : 5080270
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Descarga de CVS – Cervisia"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5088566
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94437552 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Seleccionar carpeta – Cervisia" ' : 5088566
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Seleccionar carpeta – Cervisia"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5096437
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94442955 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Descarga de CVS – Cervisia <2>&#8206;" ' : 5096437
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Descarga de CVS – Cervisia <2>&#8206;"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5103526
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94445924 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Información – Cervisia" ' : 5103526
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Información – Cervisia"
kmix(1927) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
cervisia(17034)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5130214
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94453246 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Configurar el acceso a los repositorios – Cervisia" ' : 5130214
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Configurar el acceso a los repositorios – Cervisia"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5131711
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94455391 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Añadir repositorio – Cervisia" ' : 5131711
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Añadir repositorio – Cervisia"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5144006
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94461460 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Configurar el acceso a los repositorios – Cervisia" ' : 5144006
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Configurar el acceso a los repositorios – Cervisia"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5146574
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94462705 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Opciones del repositorio – Cervisia" ' : 5146574
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Opciones del repositorio – Cervisia"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5151277
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94467918 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Opciones del repositorio – Cervisia" ' : 5151277
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Opciones del repositorio – Cervisia"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5168125
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 94472647 ;WMCLASS: "cervisia" : "cervisia" ;Caption: "Opciones del repositorio – Cervisia" ' : 5168125
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Opciones del repositorio – Cervisia"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5200749
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 88085400 ;WMCLASS: "rapidsvn" : "rapidsvn" ;Caption: "Preferencias" ' : 5200749
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Preferencias"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5218765
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48267038 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Logs – kdesvn" ' : 5218765
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Logs – kdesvn"
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5220133
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48267129 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Stado / Lista – kdesvn" ' : 5220133
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Stado / Lista – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5224653
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48268074 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Registro SVN de /tags" ' : 5224653
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Registro SVN de /tags"
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5264304
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48278558 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Logs – kdesvn" ' : 5264304
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Logs – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5264304
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48268074 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Registro SVN de /trunk/bloques-rueda-demag-mexico.php" ' : 5264304
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Registro SVN de /trunk/bloques-rueda-demag-mexico.php"
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5286813
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48283754 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Annotate – kdesvn" ' : 5286813
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Annotate – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
Time elapsed: 5 ms
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5286813
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48284052 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "kdesvn" ' : 5286813
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "kdesvn"
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
klauncher(1659)/kio (KLauncher): SlavePool: No communication with slave. 

kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5303213
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48288840 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Diffing – kdesvn" ' : 5303213
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Diffing – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5303213
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48289388 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Visor de diferencias – kdesvn" ' : 5303213
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Visor de diferencias – kdesvn"
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5330453
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48294783 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Seleccionar revisión – kdesvn" ' : 5330453
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Seleccionar revisión – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5365046
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48305465 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Seleccionar revisión – kdesvn" ' : 5365046
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Seleccionar revisión – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5416317
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48313482 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Diffing – kdesvn" ' : 5416317
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Diffing – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5416317
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48289388 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Visor de diferencias – kdesvn" ' : 5416317
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Visor de diferencias – kdesvn"
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5443605
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48317790 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Diffing – kdesvn" ' : 5443605
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Diffing – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5443605
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48289388 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Visor de diferencias – kdesvn" ' : 5443605
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Visor de diferencias – kdesvn"
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5474549
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48328863 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Logs – kdesvn" ' : 5474549
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Logs – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5483197
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48330693 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Seleccionar revisión – kdesvn" ' : 5483197
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Seleccionar revisión – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5487197
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48334008 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Logs – kdesvn" ' : 5487197
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Logs – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5495445
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48335926 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Logs – kdesvn" ' : 5495445
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Logs – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5515758
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48338468 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Logs – kdesvn" ' : 5515758
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Logs – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5529493
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48341309 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "Annotate – kdesvn" ' : 5529493
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "Annotate – kdesvn"
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
Time elapsed: 3 ms
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 5529493
kwin(1753) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 48341692 ;WMCLASS: "kdesvn" : "kdesvn" ;Caption: "kdesvn" ' : 5529493
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
kwin(1753) KWin::Workspace::updateClientArea: screens:  1 desktops:  7
kwin(1753) KWin::Workspace::updateClientArea: Done.
kwin(1753) KWin::Workspace::createTile: Now tiling  "kdesvn"
kwin(1753) KWin::Workspace::allowFullClientRaising: Raising: Belongs to active application
kwin(1753) KWin::Workspace::allowClientActivation: Activation: Belongs to active application
python: Fatal IO error 11 (Recurso no disponible temporalmente) on X server :0.0.
Warning: Switch translation of <Work Bench starting> to U_!
krunner: Fatal IO error: client killed
kdeinit4: Fatal IO error: client killed
kdeinit4: sending SIGHUP to children.
kded4: Fatal IO error: client killed
bluedevil-monolithic: Fatal IO error: client killed
kglobalaccel: Fatal IO error: client killed
KCrash: Application 'ksmserver' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
Warning: connect() failed: : No existe el fichero o el directorio
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi directly
kwin: Fatal IO error: client killed
klauncher: Exiting on signal 1
XIO:  fatal IO error 4 (Llamada al sistema interrumpida) on X server ":0.0"
      after 21 requests (8 known processed) with 0 events remaining.
kdeinit4: sending SIGTERM to children.
kdeinit4: Exit.
[/usr/bin/akonadi_maildir_resource] akonadi_maildir_resource: Fatal IO error: client killed
[/usr/bin/akonadi_maildispatcher_agent] akonadi_maildispatcher_agent: Fatal IO error: client killed
[/usr/bin/akonadi_nepomuk_contact_feeder] ICE default IO error handler doing an exit(), pid = 1829, errno = 11
[/usr/bin/akonadi_nepomuk_contact_feeder] akonadi_nepomuk_contact_feeder: Fatal IO error: client killed
[/usr/bin/akonadi_nepomuk_contact_feeder] QCoreApplication::postEvent: Unexpected null receiver
[/usr/bin/akonadi_vcard_resource] akonadi_vcard_resource: Fatal IO error: client killed
ProcessControl: Application '/usr/bin/akonadi_maildir_resource' returned with exit code 1 (Unknown error)
ProcessControl: Application '/usr/bin/akonadi_maildispatcher_agent' returned with exit code 1 (Unknown error)
ICE default IO error handler doing an exit(), pid = 2106, errno = 11
ProcessControl: Application '/usr/bin/akonadi_nepomuk_contact_feeder' returned with exit code 1 (Unknown error)
[/usr/bin/akonadi_maildir_resource] akonadi_maildir_resource: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_maildir_resource' returned with exit code 1 (Unknown error)
[/usr/bin/akonadi_maildispatcher_agent] akonadi_maildispatcher_agent: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_vcard_resource' returned with exit code 1 (Unknown error)
ProcessControl: Application '/usr/bin/akonadi_maildispatcher_agent' returned with exit code 1 (Unknown error)
[/usr/bin/akonadi_nepomuk_contact_feeder] No protocol specified
[/usr/bin/akonadi_nepomuk_contact_feeder] akonadi_nepomuk_contact_feeder: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_nepomuk_contact_feeder' returned with exit code 1 (Unknown error)
[/usr/bin/akonadi_maildir_resource] No protocol specified
[/usr/bin/akonadi_maildir_resource] akonadi_maildir_resource: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_maildir_resource' returned with exit code 1 (Unknown error)
No protocol specified
opera: cannot connect to X server :0. Error: Recurso no disponible temporalmente
[/usr/bin/akonadi_vcard_resource] No protocol specified
[/usr/bin/akonadi_vcard_resource] akonadi_vcard_resource: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_vcard_resource' returned with exit code 1 (Unknown error)
[/usr/bin/akonadi_maildispatcher_agent] No protocol specified
[/usr/bin/akonadi_maildispatcher_agent] akonadi_maildispatcher_agent: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_maildispatcher_agent' returned with exit code 1 (Unknown error)
[/usr/bin/akonadi_nepomuk_contact_feeder] No protocol specified
[/usr/bin/akonadi_nepomuk_contact_feeder] akonadi_nepomuk_contact_feeder: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_nepomuk_contact_feeder' returned with exit code 1 (Unknown error)
[/usr/bin/akonadi_maildir_resource] No protocol specified
[/usr/bin/akonadi_maildir_resource] akonadi_maildir_resource: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_maildir_resource' returned with exit code 1 (Unknown error)
"/usr/bin/akonadi_maildir_resource" crashed too often and will not be restarted! 
[/usr/bin/akonadi_vcard_resource] No protocol specified
[/usr/bin/akonadi_vcard_resource] akonadi_vcard_resource: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_vcard_resource' returned with exit code 1 (Unknown error)
[/usr/bin/akonadi_maildispatcher_agent] No protocol specified
[/usr/bin/akonadi_maildispatcher_agent] akonadi_maildispatcher_agent: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_maildispatcher_agent' returned with exit code 1 (Unknown error)
"/usr/bin/akonadi_maildispatcher_agent" crashed too often and will not be restarted! 
[/usr/bin/akonadi_nepomuk_contact_feeder] No protocol specified
[/usr/bin/akonadi_nepomuk_contact_feeder] akonadi_nepomuk_contact_feeder: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_nepomuk_contact_feeder' returned with exit code 1 (Unknown error)
"/usr/bin/akonadi_nepomuk_contact_feeder" crashed too often and will not be restarted! 
[/usr/bin/akonadi_vcard_resource] No protocol specified
[/usr/bin/akonadi_vcard_resource] akonadi_vcard_resource: cannot connect to X server :0
ProcessControl: Application '/usr/bin/akonadi_vcard_resource' returned with exit code 1 (Unknown error)
"/usr/bin/akonadi_vcard_resource" crashed too often and will not be restarted! 
D-Bus session bus went down - quitting
[akonadiserver] D-Bus session bus went down - quitting
[akonadiserver] terminating service threads
[akonadiserver] terminating connection threads
[akonadiserver] stopping db process
Application 'akonadiserver' exited normally...



```

---

### Post by mi691207 on 2011-03-31
Can anybody help me please?!

---

### Post by TheSqueak on 2011-03-31
This started happening to me last night, and it hit me a half dozen times this morning.

Touch wood, a reboot seems to have fixed it. It turns out that when you install something that says it needs you to reboot afterwards, they actually mean that :)

---

### Post by mi691207 on 2011-03-31
Reboot did not help.

But the problem seems to be related with Firefox, I guess.
It happens more often when I use Firefox.

---

### Post by quequotion on 2012-01-18
Sorry I have no help to offer, but I understand how you feel.

I'm in a bit of a panic as my computer is also rebooting suddenly.

Sometimes these reboots result in data corruption on the hard disk.

Be very careful and remember whatever you were doing before the reboot.

In my case nearly everything that should have been logged before the reboot seems to be missing and often files related to whatever I was doing have random data inserted somewhere. This broke dpkg once since I was in the middle of an apt-get update.

I suspect it has something to do with the kernel's acpi functionality, but I have nothing to show for my theory.

---


---
title: "Taskbar is black not gray"
date: 2010-05-22
forum: General Help
---

### Post by anonymous01 on 2010-05-22
This is what it looks like:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157857&stc=1&d=1274522616[/IMG]

When I boot up for the first time Kubuntu 10.04, the taskbar color is normal but when I reboot the system, it turns black like the image above.

The only way I solve this problem is by using Bleachbit then reboot the system. But when I forgot to use it, it turns back to black. I think it is the problem of my configuration files.

I kill plasma desktop and load it again by using Konsole.

This is the output of Konsole when I use Bleachbit.
```

QDBusObjectPath: invalid path ""
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
plasma-desktop(1855): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 
plasma-desktop(1855): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 
plasma-desktop(1855): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 
plasma-desktop(1855): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 
plasma-desktop(1855) Controls::setDisplayedButtons: Minimum size before changing buttons: QSizeF(0, 0)
plasma-desktop(1855) Controls::setDisplayedButtons: Layout: QObject(0x0)
plasma-desktop(1855) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1855) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1855) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1855) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1855) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1855) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1855) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1855) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1855) Controls::setDisplayedButtons: Minimum size after changing buttons: QSizeF(92, 26)
QGraphicsLinearLayout::removeAt: invalid index 0
plasma-desktop(1855)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/lester/.kde/share/apps/RecentDocuments/Don't Turn Around Alejandro.mp3.desktop" not found
plasma-desktop(1855)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/lester/.kde/share/apps/RecentDocuments/youarenotalone.mid.desktop" not found
plasma-desktop(1855)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/lester/.kde/share/apps/RecentDocuments/telephone.flv.desktop" not found
plasma-desktop(1855)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/solid_hal_power.so" does not offer a qt_plugin_instance function.
plasma-desktop(1855) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "HAL-Power"
plasma-desktop(1855)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-11, -9) 
plasma-desktop(1855)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-11, -9) 
plasma-desktop(1855)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-11, -9) 
QGraphicsLinearLayout::removeAt: invalid index 0
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/lester/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
plasma-desktop(1855) MessageIndicator::adjustViewSize: No parentWidget for applet widget()! 
plasma-desktop(1855) MessageIndicator::adjustViewSize: No parentWidget for applet widget()! 
QGraphicsLinearLayout::removeAt: invalid index 0
QGraphicsLinearLayout::removeAt: invalid index 0
QGraphicsLinearLayout::removeAt: invalid index 0
plasma-desktop(1855) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
Object::connect: No such slot MediaPlayer::volumeChanged(qreal)
Object::connect: No such slot MediaPlayer::stateChanged(Phonon::State, Phonon::State)
Object::connect: No such slot MediaPlayer::seekableChanged(bool)
Object::connect: No such slot MediaPlayer::tick(qint64)
Object::connect: No such slot MediaPlayer::totalTimeChanged(qint64)
QCoreApplication::postEvent: Unexpected null receiver
QCoreApplication::postEvent: Unexpected null receiver
QCoreApplication::postEvent: Unexpected null receiver
QCoreApplication::postEvent: Unexpected null receiver
QCoreApplication::postEvent: Unexpected null receiver
plasma-desktop(1855) Controls::setDisplayedButtons: Minimum size before changing buttons: QSizeF(92, 26)
plasma-desktop(1855) Controls::setDisplayedButtons: Layout: QObject(0x0)
plasma-desktop(1855) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1855) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1855) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1855) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1855) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1855) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1855) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1855) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1855) Controls::setDisplayedButtons: Minimum size after changing buttons: QSizeF(92, 26)
plasma-desktop(1855) NowPlaying::findPlayer: Looking for players.  Possibilities: ("org.mpris.PlasmaMediaPlayer")
plasma-desktop(1855) NowPlaying::findPlayer: Installing "org.mpris.PlasmaMediaPlayer" as watched player
link MoonMaster hasn't been detected!
plasma-desktop(1855) Luna::calcStatus: last new  "5/14/2010 1:05 am"
plasma-desktop(1855) Luna::calcStatus: first quarter  "5/20/2010 11:43 pm"
plasma-desktop(1855) Luna::calcStatus: full moon  "5/27/2010 11:08 pm"
plasma-desktop(1855) Luna::calcStatus: third quarter  "6/4/2010 10:14 pm"
plasma-desktop(1855) Luna::calcStatus: next new  "6/12/2010 11:15 am"
plasma-desktop(1855) Luna::calcStatus: now  "5/22/2010 10:08 am"
plasma-desktop(1855) Luna::calcStatus: counter  8   -5
plasma-desktop(1855) Luna::calcStatus: around first quarter  9
plasma-desktop(1855) Luna::calcStatus: counter  9
Invalid D-BUS interface name 'org.kde.plasma-desktop.PlasmaApp' found while parsing introspection
plasma-desktop(1855)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
plasma-desktop(1855) Luna::calcStatus: last new  "5/14/2010 1:05 am"
plasma-desktop(1855) Luna::calcStatus: first quarter  "5/20/2010 11:43 pm"
plasma-desktop(1855) Luna::calcStatus: full moon  "5/27/2010 11:08 pm"
plasma-desktop(1855) Luna::calcStatus: third quarter  "6/4/2010 10:14 pm"
plasma-desktop(1855) Luna::calcStatus: next new  "6/12/2010 11:15 am"
plasma-desktop(1855) Luna::calcStatus: now  "5/22/2010 10:08 am"
plasma-desktop(1855) Luna::calcStatus: counter  8   -5
plasma-desktop(1855) Luna::calcStatus: around first quarter  9
plasma-desktop(1855) Luna::calcStatus: counter  9
plasma-desktop(1855)/plasma DBusWatcher::serviceChange: Already got a player at "org.mpris.PlasmaMediaPlayer" 
plasma-desktop(1855)/plasma SystemTray::DBusSystemTrayWidget::createMenuImporter: DBusMenu disabled for this application 
plasma-desktop(1855) WeatherApplet::weatherContent: Create new Plasma::IconWidget (condition)
QColor::setNamedColor: Unknown color name '4279505682'
QTextHtmlParser::applyAttributes: Unknown color name '4279505682'
plasma-desktop(1855) WeatherApplet::weatherContent: Create 5 Days Plasma::WeatherView
Object::connect: No such slot WeatherApplet::fiveDaysColumnResized(int, int, int)
plasma-desktop(1855) WeatherApplet::weatherContent: Create 5 Days QStandardItemModel
plasma-desktop(1855) WeatherApplet::weatherContent: Create Details Plasma::WeatherView
plasma-desktop(1855) WeatherApplet::weatherContent: Create Details QStandardItemModel

```

This is the output of Konsole when I didn't use Bleachbit.
```

Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
plasma-desktop(1855): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 
plasma-desktop(1855): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 
plasma-desktop(1855): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 
plasma-desktop(1855): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 
plasma-desktop(1855) Controls::setDisplayedButtons: Minimum size before changing buttons: QSizeF(0, 0)
plasma-desktop(1855) Controls::setDisplayedButtons: Layout: QObject(0x0)
plasma-desktop(1855) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1855) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1855) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1855) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1855) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1855) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1855) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1855) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1855) Controls::setDisplayedButtons: Minimum size after changing buttons: QSizeF(92, 26)
QGraphicsLinearLayout::removeAt: invalid index 0
plasma-desktop(1855)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/lester/.kde/share/apps/RecentDocuments/Don't Turn Around Alejandro.mp3.desktop" not found
plasma-desktop(1855)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/lester/.kde/share/apps/RecentDocuments/youarenotalone.mid.desktop" not found
plasma-desktop(1855)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/lester/.kde/share/apps/RecentDocuments/telephone.flv.desktop" not found
plasma-desktop(1855)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/solid_hal_power.so" does not offer a qt_plugin_instance function.
plasma-desktop(1855) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "HAL-Power"
plasma-desktop(1855)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-11, -9) 
plasma-desktop(1855)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-11, -9) 
plasma-desktop(1855)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-11, -9) 
QGraphicsLinearLayout::removeAt: invalid index 0
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/lester/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
plasma-desktop(1855) MessageIndicator::adjustViewSize: No parentWidget for applet widget()! 
plasma-desktop(1855) MessageIndicator::adjustViewSize: No parentWidget for applet widget()! 
QGraphicsLinearLayout::removeAt: invalid index 0
QGraphicsLinearLayout::removeAt: invalid index 0
QGraphicsLinearLayout::removeAt: invalid index 0
plasma-desktop(1855) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
Object::connect: No such slot MediaPlayer::volumeChanged(qreal)
Object::connect: No such slot MediaPlayer::stateChanged(Phonon::State, Phonon::State)
Object::connect: No such slot MediaPlayer::seekableChanged(bool)
Object::connect: No such slot MediaPlayer::tick(qint64)
Object::connect: No such slot MediaPlayer::totalTimeChanged(qint64)
QCoreApplication::postEvent: Unexpected null receiver
QCoreApplication::postEvent: Unexpected null receiver
QCoreApplication::postEvent: Unexpected null receiver
QCoreApplication::postEvent: Unexpected null receiver
QCoreApplication::postEvent: Unexpected null receiver
plasma-desktop(1855) Controls::setDisplayedButtons: Minimum size before changing buttons: QSizeF(92, 26)
plasma-desktop(1855) Controls::setDisplayedButtons: Layout: QObject(0x0)
plasma-desktop(1855) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1855) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1855) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1855) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1855) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1855) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1855) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1855) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1855) Controls::setDisplayedButtons: Minimum size after changing buttons: QSizeF(92, 26)
plasma-desktop(1855) NowPlaying::findPlayer: Looking for players.  Possibilities: ("org.mpris.PlasmaMediaPlayer")
plasma-desktop(1855) NowPlaying::findPlayer: Installing "org.mpris.PlasmaMediaPlayer" as watched player
link MoonMaster hasn't been detected!
plasma-desktop(1855) Luna::calcStatus: last new  "5/14/2010 1:05 am"
plasma-desktop(1855) Luna::calcStatus: first quarter  "5/20/2010 11:43 pm"
plasma-desktop(1855) Luna::calcStatus: full moon  "5/27/2010 11:08 pm"
plasma-desktop(1855) Luna::calcStatus: third quarter  "6/4/2010 10:14 pm"
plasma-desktop(1855) Luna::calcStatus: next new  "6/12/2010 11:15 am"
plasma-desktop(1855) Luna::calcStatus: now  "5/22/2010 10:08 am"
plasma-desktop(1855) Luna::calcStatus: counter  8   -5
plasma-desktop(1855) Luna::calcStatus: around first quarter  9
plasma-desktop(1855) Luna::calcStatus: counter  9
Invalid D-BUS interface name 'org.kde.plasma-desktop.PlasmaApp' found while parsing introspection
plasma-desktop(1855)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
plasma-desktop(1855) Luna::calcStatus: last new  "5/14/2010 1:05 am"
plasma-desktop(1855) Luna::calcStatus: first quarter  "5/20/2010 11:43 pm"
plasma-desktop(1855) Luna::calcStatus: full moon  "5/27/2010 11:08 pm"
plasma-desktop(1855) Luna::calcStatus: third quarter  "6/4/2010 10:14 pm"
plasma-desktop(1855) Luna::calcStatus: next new  "6/12/2010 11:15 am"
plasma-desktop(1855) Luna::calcStatus: now  "5/22/2010 10:08 am"
plasma-desktop(1855) Luna::calcStatus: counter  8   -5
plasma-desktop(1855) Luna::calcStatus: around first quarter  9
plasma-desktop(1855) Luna::calcStatus: counter  9
plasma-desktop(1855)/plasma DBusWatcher::serviceChange: Already got a player at "org.mpris.PlasmaMediaPlayer" 
lester@lester:~$ plasma-desktop(1855)/plasma SystemTray::DBusSystemTrayWidget::createMenuImporter: DBusMenu disabled for this application 
plasma-desktop(1855) WeatherApplet::weatherContent: Create new Plasma::IconWidget (condition)
QColor::setNamedColor: Unknown color name '4279505682'
QTextHtmlParser::applyAttributes: Unknown color name '4279505682'
plasma-desktop(1855) WeatherApplet::weatherContent: Create 5 Days Plasma::WeatherView
Object::connect: No such slot WeatherApplet::fiveDaysColumnResized(int, int, int)
plasma-desktop(1855) WeatherApplet::weatherContent: Create 5 Days QStandardItemModel
plasma-desktop(1855) WeatherApplet::weatherContent: Create Details Plasma::WeatherView
plasma-desktop(1855) WeatherApplet::weatherContent: Create Details QStandardItemModel

lester@lester:~$ killall plasma-desktop
lester@lester:~$ plasma-desktop
QDBusObjectPath: invalid path ""
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
plasma-desktop(1873): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 
plasma-desktop(1873): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 
plasma-desktop(1873): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 
plasma-desktop(1873): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 
plasma-desktop(1873) Controls::setDisplayedButtons: Minimum size before changing buttons: QSizeF(0, 0)
plasma-desktop(1873) Controls::setDisplayedButtons: Layout: QObject(0x0)
plasma-desktop(1873) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1873) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1873) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1873) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1873) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1873) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1873) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1873) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1873) Controls::setDisplayedButtons: Minimum size after changing buttons: QSizeF(92, 26)
QGraphicsLinearLayout::removeAt: invalid index 0
plasma-desktop(1873)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/lester/.kde/share/apps/RecentDocuments/Don't Turn Around Alejandro.mp3.desktop" not found
plasma-desktop(1873)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/lester/.kde/share/apps/RecentDocuments/youarenotalone.mid.desktop" not found
plasma-desktop(1873)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/lester/.kde/share/apps/RecentDocuments/telephone.flv.desktop" not found
plasma-desktop(1873)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/solid_hal_power.so" does not offer a qt_plugin_instance function.
plasma-desktop(1873) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "HAL-Power"
plasma-desktop(1873)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-11, -9) 
plasma-desktop(1873)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-11, -9) 
plasma-desktop(1873)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-11, -9) 
QGraphicsLinearLayout::removeAt: invalid index 0
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/lester/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
plasma-desktop(1873) MessageIndicator::adjustViewSize: No parentWidget for applet widget()! 
plasma-desktop(1873) MessageIndicator::adjustViewSize: No parentWidget for applet widget()! 
QGraphicsLinearLayout::removeAt: invalid index 0
QGraphicsLinearLayout::removeAt: invalid index 0
QGraphicsLinearLayout::removeAt: invalid index 0
plasma-desktop(1873) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
Object::connect: No such slot MediaPlayer::volumeChanged(qreal)
Object::connect: No such slot MediaPlayer::stateChanged(Phonon::State, Phonon::State)
Object::connect: No such slot MediaPlayer::seekableChanged(bool)
Object::connect: No such slot MediaPlayer::tick(qint64)
Object::connect: No such slot MediaPlayer::totalTimeChanged(qint64)
QCoreApplication::postEvent: Unexpected null receiver
QCoreApplication::postEvent: Unexpected null receiver
QCoreApplication::postEvent: Unexpected null receiver
QCoreApplication::postEvent: Unexpected null receiver
QCoreApplication::postEvent: Unexpected null receiver
plasma-desktop(1873) Controls::setDisplayedButtons: Minimum size before changing buttons: QSizeF(92, 26)
plasma-desktop(1873) Controls::setDisplayedButtons: Layout: QObject(0x0)
plasma-desktop(1873) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1873) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1873) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1873) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1873) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1873) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1873) showHideButton: Button minimum size: QSizeF(18, 18)
plasma-desktop(1873) showHideButton: Button preferred size: QSizeF(34, 34)
plasma-desktop(1873) Controls::setDisplayedButtons: Minimum size after changing buttons: QSizeF(92, 26)
plasma-desktop(1873) NowPlaying::findPlayer: Looking for players.  Possibilities: ("org.mpris.PlasmaMediaPlayer")
plasma-desktop(1873) NowPlaying::findPlayer: Installing "org.mpris.PlasmaMediaPlayer" as watched player
link MoonMaster hasn't been detected!
plasma-desktop(1873) Luna::calcStatus: last new  "5/14/2010 1:05 am"
plasma-desktop(1873) Luna::calcStatus: first quarter  "5/20/2010 11:43 pm"
plasma-desktop(1873) Luna::calcStatus: full moon  "5/27/2010 11:08 pm"
plasma-desktop(1873) Luna::calcStatus: third quarter  "6/4/2010 10:14 pm"
plasma-desktop(1873) Luna::calcStatus: next new  "6/12/2010 11:15 am"
plasma-desktop(1873) Luna::calcStatus: now  "5/22/2010 10:09 am"
plasma-desktop(1873) Luna::calcStatus: counter  8   -5
plasma-desktop(1873) Luna::calcStatus: around first quarter  9
plasma-desktop(1873) Luna::calcStatus: counter  9
Invalid D-BUS interface name 'org.kde.plasma-desktop.PlasmaApp' found while parsing introspection
plasma-desktop(1873)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
plasma-desktop(1873) Luna::calcStatus: last new  "5/14/2010 1:05 am"
plasma-desktop(1873) Luna::calcStatus: first quarter  "5/20/2010 11:43 pm"
plasma-desktop(1873) Luna::calcStatus: full moon  "5/27/2010 11:08 pm"
plasma-desktop(1873) Luna::calcStatus: third quarter  "6/4/2010 10:14 pm"
plasma-desktop(1873) Luna::calcStatus: next new  "6/12/2010 11:15 am"
plasma-desktop(1873) Luna::calcStatus: now  "5/22/2010 10:09 am"
plasma-desktop(1873) Luna::calcStatus: counter  8   -5
plasma-desktop(1873) Luna::calcStatus: around first quarter  9
plasma-desktop(1873) Luna::calcStatus: counter  9
plasma-desktop(1873)/plasma DBusWatcher::serviceChange: Already got a player at "org.mpris.PlasmaMediaPlayer" 
lester@lester:~$ plasma-desktop(1873)/plasma SystemTray::DBusSystemTrayWidget::createMenuImporter: DBusMenu disabled for this application 
plasma-desktop(1873) WeatherApplet::weatherContent: Create new Plasma::IconWidget (condition)
QColor::setNamedColor: Unknown color name '4279505682'
QTextHtmlParser::applyAttributes: Unknown color name '4279505682'
plasma-desktop(1873) WeatherApplet::weatherContent: Create 5 Days Plasma::WeatherView
Object::connect: No such slot WeatherApplet::fiveDaysColumnResized(int, int, int)
plasma-desktop(1873) WeatherApplet::weatherContent: Create 5 Days QStandardItemModel
plasma-desktop(1873) WeatherApplet::weatherContent: Create Details Plasma::WeatherView
plasma-desktop(1873) WeatherApplet::weatherContent: Create Details QStandardItemModel

```

I want to solve this problem permanently. Please help me.

---


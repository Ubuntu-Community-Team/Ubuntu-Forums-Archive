---
title: "Dolphin crashes when run as root"
date: 2010-02-13
forum: General Help
---

### Post by CentralCaFan on 2010-02-13
Since installing upgrades including KDE4.4 and having to reinstall plasma-desktop, when I launch Dolphin file manager via alt-f2 it always crashes. In the status at the bottom is reads...

" The process for the file protocol died unexpectedly. "

When I run Dolphin as my current logged in user there are no issues. Can anyone tell me what I might try to fix this? Thanks, John.

---

### Post by bertmanphx on 2010-03-05
CentralCalFan,
I've just started getting error as well when attempting to run Dolphin from alt-f2 "kdesu dolphin".  The output when trying to start it from konsole, is listed below.  Perhaps somebody can chime in here with some input.

bertmanphx

robert@DV8040:~$ sudo dolphin
[sudo] password for robert: 
Error: "/var/tmp/kdecache-robert" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-robert" is owned by uid 1000 instead of uid 0.
dolphin(2154)/kio (bookmarks) KBookmarkManager::KBookmarkManager: starting KDirWatch for  "/home/robert/.local/share//user-places.xbel"
dolphin(2154)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-robert/ksycoca4"
dolphin(2154)/kio (KDirListerCache) KDirListerCache::listDir: Listing directory: KUrl("trash:/")
Object::connect: No such slot DolphinSearchBox::slotClearButtonClicked()
Object::connect: No such signal DolphinController::requestUrlChange(const KUrl&)
dolphin(2154)/kio (KDirListerCache) KDirListerCache::listDir: Reloading directory: KUrl("file:///home/robert")
dolphin(2154)/kdecore (K*TimeZone*) KSystemTimeZonesPrivate::instance: instance(): ... initialised
dolphin(2154)/kdecore (K*TimeZone*) KSystemTimeZonesPrivate::readConfig: readConfig(): local zone= "America/Phoenix"
dolphin(2154)/kdecore (K*TimeZone*) KSystemTimeZonesPrivate::readZoneTab: readZoneTab( "/usr/share/zoneinfo/zone.tab" )
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
"/usr/bin/dolphin(2154)" Error in thread 140132231010304 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
dolphin(2154)/nepomuk (library) <unnamed>::GlobalModelContainer::init: Connecting to local socket "/home/robert/.kde/share/apps/nepomuk/socket"
"/usr/bin/dolphin(2154)" Error in thread 140132231010304 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140132231010304 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
robert@DV8040:~$ "/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2154)" Error in thread 140131934758672 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
dolphin(2154)/kio (KDirListerCache) KDirListerCache::listDir: Entry currently being listed: KUrl("trash:/") by (KDirLister(0x1df9040) )
dolphin(2154)/kio (Slave) KIO::Slave::createSlave: createSlave "trash" for KUrl("trash:/")
Error: "/tmp/ksocket-robert" is owned by uid 1000 instead of uid 0.
dolphin(2154)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-robert/dolphinbh2154.slave-socket"
dolphin(2154)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///home/robert")
dolphin(2154)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-robert/dolphinmn2154.slave-socket"
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/robert/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
dolphin(2154)/kio (KDirListerCache) KDirListerCache::slotResult: finished listing KUrl("trash:/")
dolphin(2154)/kio (Slave) KIO::Slave::timeout: slave failed to connect to application pid= 2167  protocol= "file"
dolphin(2154)/kio (Slave) KIO::Slave::timeout: Houston, we lost our slave, pid= 2167
dolphin(2154)/kio (Slave) KIO::Slave::timeout: slave died pid =  2167
dolphin(2154)/kio (KDirListerCache) KDirListerCache::slotResult: finished listing KUrl("file:///home/robert")

---

### Post by CentralCaFan on 2010-03-05
I haven't found a solution. But when I need to use Dolphin as root I just enter sudo dolphin in a console window. I see people here in this forum I believe reminding that using file managers as root is generally not a good practice. So as much as possible I try to use a console and command line instead of trying to work in a windows frame of mind.

For me this error message when I start Dolphin from krunner started when I installed the large group of updates including KDE4.4. Exact same thing happened on the Kubuntu 32-bit partition as a Kubuntu 64-bit partition that I have.

---

### Post by bertmanphx on 2010-03-05
CentralCaFan,
I agree, it should be done minimally.  I was simply copying over the 64 bit flash file, and thought it easier to fire up Dolphin as sudo.

I also had this working a couple of days ago, until some updates applied.

bertmanphx

---

### Post by gotaug on 2010-03-20
I'm having this problem to, and it is really making my life difficult!

---

### Post by bertmanphx on 2010-03-20
gotuag,
Using this workaround seems to work for me.
"kdesu dbus-launch dolphin"

bertmanphx

---


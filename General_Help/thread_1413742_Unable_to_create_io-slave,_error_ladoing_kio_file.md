---
title: "Unable to create io-slave, error ladoing kio_file"
date: 2010-02-22
forum: General Help
---

### Post by Skrim on 2010-02-22
Hi, I'm having some issues after having done a dist-upgrade.

Dolphin and Gwenview can't display much of anything other than an error message saying:

Could not start process Unable to create io-slave:
klauncher said: Error loading 'kio_file'.

Amarok displays the same error but is quite happy to play music afterwards.


Running Kubuntu 9.10 64bit

---

### Post by Skrim on 2010-02-23
Returned when opening dolphin from command line:


dolphin(9096)/kio (bookmarks) KBookmarkManager::KBookmarkManager: starting KDirWatch for  "/home/skrim/.local/share//user-places.xbel"                                                                                                    
dolphin(9096)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-skrim/ksycoca4"                                                                                                             
dolphin(9096)/kio (KDirListerCache) KDirListerCache::listDir: Listing directory: KUrl("trash:/")                     
Object::connect: No such slot DolphinSearchBox::slotClearButtonClicked()                                             
Object::connect: No such signal DolphinController::requestUrlChange(const KUrl&)                                     
dolphin(9096)/kio (KDirListerCache) KDirListerCache::listDir: Reloading directory: KUrl("file:///home/skrim")
dolphin(9096)/kdecore (K*TimeZone*) KSystemTimeZonesPrivate::instance: instance(): ... initialised
dolphin(9096)/kdecore (K*TimeZone*) KSystemTimeZonesPrivate::readConfig: readConfig(): local zone= "Europe/London"
dolphin(9096)/kdecore (K*TimeZone*) KSystemTimeZonesPrivate::readZoneTab: readZoneTab( "/usr/share/zoneinfo/zone.tab" )
Object::connect: No such signal DolphinController::requestUrlChange(const KUrl&)
dolphin(9096)/kio (KDirListerCache) KDirListerCache::listDir: Entry currently being listed: KUrl("file:///home/skrim") by (DolphinDirLister(0x9c47b0) )
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
"/usr/bin/dolphin(9096)" Error in thread 140305320294384 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
dolphin(9096)/nepomuk (library) <unnamed>::GlobalModelContainer::init: Connecting to local socket "/home/skrim/.kde/share/apps/nepomuk/socket"
"/usr/bin/dolphin(9096)" Error in thread 140305320294384 : "QLocalSocket::connectToServer: Invalid name"
dolphin(9096)/nepomuk (library) <unnamed>::GlobalModelContainer::init: Failed to connect to Nepomuk server via local socket "/home/skrim/.kde/share/apps/nepomuk/socket"
"/usr/bin/dolphin(9096)" Error in thread 140305320294384 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
dolphin(9096)/nepomuk (library) <unnamed>::GlobalModelContainer::init: Connecting to local socket "/home/skrim/.kde/share/apps/nepomuk/socket"
"/usr/bin/dolphin(9096)" Error in thread 140305320294384 : "QLocalSocket::connectToServer: Invalid name"
dolphin(9096)/nepomuk (library) <unnamed>::GlobalModelContainer::init: Failed to connect to Nepomuk server via local socket "/home/skrim/.kde/share/apps/nepomuk/socket"
"/usr/bin/dolphin(9096)" Error in thread 140305320294384 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
dolphin(9096)/nepomuk (library) <unnamed>::GlobalModelContainer::init: Connecting to local socket "/home/skrim/.kde/share/apps/nepomuk/socket"
"/usr/bin/dolphin(9096)" Error in thread 140305320294384 : "QLocalSocket::connectToServer: Invalid name"
dolphin(9096)/nepomuk (library) <unnamed>::GlobalModelContainer::init: Failed to connect to Nepomuk server via local socket "/home/skrim/.kde/share/apps/nepomuk/socket"
skrim@blackbox:~$ QStringList Solid::Backends::Hal::HalManager::findDeviceByDeviceInterface(const Solid::DeviceInterface::Type&)  error:  "org.freedesktop.DBus.Error.ServiceUnknown"

QStringList Solid::Backends::Hal::HalManager::findDeviceByDeviceInterface(const Solid::DeviceInterface::Type&)  error:  "org.freedesktop.DBus.Error.ServiceUnknown"

QStringList Solid::Backends::Hal::HalManager::findDeviceByDeviceInterface(const Solid::DeviceInterface::Type&)  error:  "org.freedesktop.DBus.Error.ServiceUnknown"

QStringList Solid::Backends::Hal::HalManager::findDeviceByDeviceInterface(const Solid::DeviceInterface::Type&)  error:  "org.freedesktop.DBus.Error.ServiceUnknown"

dolphin(9096)/kio (KDirListerCache) KDirListerCache::listDir: Entry currently being listed: KUrl("trash:/") by (KDirLister(0x955940) )
dolphin(9096)/kio (Slave) KIO::Slave::createSlave: createSlave "trash" for KUrl("trash:/")
dolphin(9096)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-skrim/dolphinjG9096.slave-socket"
dolphin(9096): couldn't create slave: "Unable to create io-slave:
klauncher said: Error loading 'kio_trash'.
"
dolphin(9096)/kio (KDirListerCache) KDirListerCache::slotResult: finished listing KUrl("trash:/")
dolphin(9096)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///home/skrim")
dolphin(9096)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-skrim/dolphinrA9096.slave-socket"
dolphin(9096): couldn't create slave: "Unable to create io-slave:
klauncher said: Error loading 'kio_file'.
"
dolphin(9096)/kio (KDirListerCache) KDirListerCache::slotResult: finished listing KUrl("file:///home/skrim")

---

### Post by Skrim on 2010-02-23
Solution:

[http://kubuntuforums.net/forums/index.php?topic=3110214.0](http://kubuntuforums.net/forums/index.php?topic=3110214.0)

---

### Post by adamf663 on 2012-02-01
bad link

---

### Post by Rallye on 2012-02-20
I also have this issue and can say the link Skrim posted is broken.

---

### Post by overdrank on 2012-02-20
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---


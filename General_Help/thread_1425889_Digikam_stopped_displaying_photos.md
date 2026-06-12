---
title: "Digikam stopped displaying photos"
date: 2010-03-09
forum: General Help
---

### Post by TheSqueak on 2010-03-09
Has anybody else run across this issue - my installation of Digikam has suddenly stopped showing any photos at all.

(Digikam 1.1 on KDE 4.4.1)

When I run it from the console, I get the following output:

```
digikam(17026)/digikam (core) main: Database Path:  "/home/james/Important/Photos/"
digikam(17026)/digikam (core) Digikam::SchemaUpdater::update: SchemaUpdater update 
digikam(17026)/digikam (core) Digikam::SchemaUpdater::startUpdates: Have a database structure version  "5"
digikam(17026)/digikam (core) Digikam::SchemaUpdater::makeUpdates: makeUpdates  5  to  5                  
digikam(17026)/digikam (core) Digikam::AlbumRootLocation::AlbumRootLocation: Creating new Location  "/"  uuid  "volumeid:?path=%2Fhome%2Fjames%2FImportant%2FPhotos"
digikam(17026)/digikam (core) Digikam::CollectionManager::updateLocations: location for  "/home/james/Important/Photos"  is available  true                         
digikam(17026)/digikam (core) Digikam::ThumbnailLoadThread::initializeThumbnailDatabase: Thumbnail db ready for use                                                 
digikam(17026)/digikam (core) Digikam::AlbumManager::checkNepomukService: digikamnepomukservice is not available in NepomukServer                                   
digikam(17026)/digikam (core) Digikam::IccSettingsPriv::scanDirectories: ()                                                                                         
digikam(17026)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-james/ksycoca4"                                      
Time elapsed: 21 ms                                                                                                                                                 
Time elapsed: 8 ms                                                                                                                                                  
Model: Time elapsed: 63 ms                                                                                                                                          
TextureColorizer: Time elapsed: 15 ms                                                                                                                               
Time elapsed: 6 ms                                                                                                                                                  
Time elapsed: 6 ms                                                                                                                                                  
Model: Time elapsed: 22 ms                                                                                                                                          
digikam(17026)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-james/digikamG17026.slave-socket"                      
digikam(17026)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///usr/share/kde4/apps/kdeui/about/kde_infopage.css")                         
digikam(17026)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-james/digikamj17026.slave-socket"                      
digikam(17026)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///usr/share/kde4/apps/digikam/about/digikam.css")                            
digikam(17026)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-james/digikamm17026.slave-socket"                      
digikam(17026)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///usr/share/kde4/apps/digikam/about/main.html")                              
digikam(17026)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-james/digikamH17026.slave-socket"                      
digikam(17026)/digikam (core) Digikam::AlbumManager::startScan: KDirWatch method =  "INotify"                                                                       
digikam(17026)/kio (Slave) KIO::Slave::createSlave: createSlave "digikamdates" for KUrl("digikamdates:?databaseType=QSQLITE&databaseName=/home/james/Important/Photos/digikam4.db")
digikam(17026)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-james/digikamt17026.slave-socket"                                     
digikam(17026): couldn't create slave: "Unable to create io-slave:                                                                                                                 
klauncher said: Error loading 'kio_digikamdates'.                                                                                                                                  
"                                                                                                                                                                                  
digikam(17026)/digikam (core) Digikam::AlbumManager::slotDatesJobResult: Failed to list dates                                                                                      
digikam(17026)/kio (Slave) KIO::Slave::createSlave: createSlave "digikamalbums" for KUrl("digikamalbums:/John and Burley Wedding/?albumRoot=/home/james/Important/Photos&albumRootId=1&databaseType=QSQLITE&databaseName=/home/james/Important/Photos/digikam4.db")                                                                                                                                                                     
digikam(17026)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-james/digikamJ17026.slave-socket"                                                                      
digikam(17026): couldn't create slave: "Unable to create io-slave:                                                                                                                                                  
klauncher said: Error loading 'kio_digikamalbums'.                                                                                                                                                                  
"                                                                                                                                                                                                                   
digikam(17026)/digikam (core) Digikam::ImageAlbumModel::slotResult: Failed to list url:  "Could not start process Unable to create io-slave:                                                                        
klauncher said: Error loading 'kio_digikamalbums'.

{snip rest}
```

---

### Post by cjhabs on 2010-03-09
I would start by going to Settings -> Configure DigiKam -> Collections and make sure it is still pointing to the correct folders.

---

### Post by TheSqueak on 2010-03-09
It's still pointing at the correct place.

I should have added that I can still see all of the folders/albums in my collection, it's just not showing any of the photos in them.

---

### Post by TheSqueak on 2010-03-10
And a reboot has apparently fixed it ...

---


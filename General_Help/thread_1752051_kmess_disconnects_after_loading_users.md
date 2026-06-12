---
title: "kmess disconnects after loading users"
date: 2011-05-07
forum: General Help
---

### Post by arbosis on 2011-05-07
:confused:
When I try to login into kmess, just after it loads the conntact list it disconnects and tries again (the same account works on other msn clients)
I'm using kubuntu 11.04 64b, and kmess 2.0.6

konsole output:
```
0.000> CRITICAL: kmess(2447)/kdeui (kdelibs): Attempt to use QAction "status" with KXMLGUIFactory! 
0.053> WARNING: QObject::connect: Incompatible sender/receiver arguments
        ChatMaster::addContact(QString) --> MsnNotificationConnection::addNewContact(QString,QStringList)
0.191> kmess(2447) RoamingService::updateDisplayPicture: Missing profileResourceId, not updating display picture 
7.799> kmess(2447) AddressBookService::parseAddressBook: Skipped 'messenger@microsoft.com' contact! 
7.805> kmess(2447) AddressBookService::parseAddressBook: Skipped 'messenger@microsoft.com' contact! 
7.829> kmess(2447) AddressBookService::parseAddressBook: Skipped 'messenger@microsoft.com' contact! 
7.835> kmess(2447) AddressBookService::parseAddressBook: Skipped 'messenger@microsoft.com' contact! 
7.842> kmess(2447) AddressBookService::parseAddressBook: Skipped 'messenger@microsoft.com' contact! 
7.851> kmess(2447) AddressBookService::parseAddressBook: Skipped 'messenger@microsoft.com' contact! 
7.883> kmess(2447) AddressBookService::parseAddressBook: Skipped 'messenger@microsoft.com' contact! 
8.711> kmess(2447) RoamingService::updateProfile: Missing profileResourceId, not updating profile 
8.711> kmess(2447) RoamingService::updateProfile: Missing profileResourceId, not updating profile 
9.188> kmess(2447) MsnNotificationConnection::slotError: MSN Notification Connection error type 4 : "The remote host closed the connection" 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
9.202> WARNING: QFileSystemWatcher: failed to add paths: /home/arbosis/.config/ibus/bus

```

I've search similar problems but I haven't found any usefull answer. Help please

---


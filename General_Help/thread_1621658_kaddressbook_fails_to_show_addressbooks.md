---
title: "kaddressbook fails to show addressbooks"
date: 2010-11-14
forum: General Help
---

### Post by fbusse on 2010-11-14
kadressbook, first started after LogOn, shows two seeming empty addressbooks: 
[LIST]
[*]"Personal Contacts" (/home/user/.local/share/contacts/) and 
[*]"akonadi_vcard_resource_1" (/home/user/.kde/share/apps/kabc/std.vcf)
[/LIST]

After closing/restarting kadressbook, no addressbook at all is shown any more. Same problem with the Address module in kontact. After Reboot, the above two seeming empty addressbooks are back again.

In KDE-Ressources, there are three addressbooks installed and active: 
[LIST]
[*]/home/user/.kde/share/apps/kabc/std.vcf (vcard),
[*]/home/user2/.kde/share/apps/kabc/std.vcf (vcard, read only) and
[*]akonadi-resource
[/LIST]
In the both vcards, there are indeed addresses, that User and User2 have kept from KDE3.

Starting kadressbook from konsole, I receive the following: 
```
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/user/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon
```
... I begin to despair of using KDE4: A system that even fails with the most basic functions for eMail-communication, probably isn't for the simple user that I am.

[Launchpad-Bugreport #676173]("https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/676173")

---


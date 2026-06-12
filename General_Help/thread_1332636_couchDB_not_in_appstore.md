---
title: "couchDB not in appstore?"
date: 2009-11-20
forum: General Help
---

### Post by sanderj on 2009-11-20
Hi,

I can't find couchDB in the Karmic 9.10 app.store. See screendump.

I *can* install couchdb via "sudo apt-get install couchdb".

What's going on? Am I searching for the wrong app in the appstore?

```

sander@quirinius:~$ sudo apt-get install couchdb
[sudo] password for sander: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tcl8.3
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  couchdb
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,002B of archives.
After this operation, 81.9kB of additional disk space will be used.
Get:1 http://nl.archive.ubuntu.com karmic/universe couchdb 0.10.0-0ubuntu3 [9,002B]
Fetched 9,002B in 0s (18.6kB/s)
Selecting previously deselected package couchdb.
(Reading database ... 133047 files and directories currently installed.)
Unpacking couchdb (from .../couchdb_0.10.0-0ubuntu3_all.deb) ...
Processing triggers for sreadahead ...
sreadahead will be reprofiled on next reboot
Setting up couchdb (0.10.0-0ubuntu3) ...
Installing new version of config file /etc/logrotate.d/couchdb ...
 * Starting database server couchdb                                      [ OK ] 

sander@quirinius:~$ 

```

---

### Post by P4man on 2009-11-20
I guess they dont consider it an app. If all packages from synaptic show up in the software center most users wouldnt even be able to install a desktop calculator anymore as they would drown in the huge and cryptic list.
 
You can install it through synaptic package manager though. And I guess at some point that functionality will be merged in the software center.

---

### Post by sanderj on 2009-11-20
It's indeed in Synaptic. And not in the old Add/Remove Programs.

OK. Clear. Thanks.

---


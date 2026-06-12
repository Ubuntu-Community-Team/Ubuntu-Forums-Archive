---
title: "Akonadi Errors on Resource Configuration."
date: 2010-02-28
forum: General Help
---

### Post by Bornabe on 2010-02-28
I recently started making the move to Kubuntu 32bit and would like to take advantage of it's many integrated features for eMail, Contacts, etc... and found using a Google account may be best, so I set one of those up too so I can keep my Desktop, my InterWeb and my iPhone all on the same page with everything.  I learned about Akonadi and setup the Google resources but noticed the following error in the Akonadi Error Log after receiving an error 'Failed getting last updated contact.' just after adding an Akonadi GoogleData Resource for both the Contact and Calendar resources.

```
100228 19:50:15 [Note] Plugin 'FEDERATED' is disabled.
100228 19:50:16  InnoDB: Started; log sequence number 0 125001
100228 19:50:16 [Warning] Can't open and lock time zone table: Table 'mysql.time_zone_leap_second' doesn't exist trying to live without them
100228 19:50:16 [ERROR] Can't open and lock privilege tables: Table 'mysql.servers' doesn't exist
100228 19:50:16 [ERROR] Cannot open mysql.db
100228 19:50:16 [ERROR] Cannot open mysql.user
100228 19:50:16 [ERROR] Cannot open mysql.event
100228 19:50:16 [ERROR] Event Scheduler: An error occurred when initializing system tables.
100228 19:50:16 [Note] /usr/sbin/mysqld-akonadi: ready for connections.
Version: '5.1.37-1ubuntu5-log'  socket: '/home/cj/.local/share/akonadi/db_misc/mysql.socket'  port: 0  (Ubuntu)
```

I went as far as wiping and fresh-installing Kubuntu v9.10, openSuSe v11.2 and now am on LinuxMint 8 KDE, based on Kubuntu v9.10.

---

### Post by Bornabe on 2010-02-28
I gave up trying and just went with Thunderbird, Lightning for Thunderbird & Zindus to sync the Calendar and Contacts inside Thunderbird.  Less is More, right?  Removing Akonadi, Kmail, Kontact, etc... and just using Thunderbird might actually be better on stability and performance overall.

---


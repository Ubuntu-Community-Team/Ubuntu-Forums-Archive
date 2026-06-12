---
title: "Libre office base"
date: 2012-08-13
forum: General Help
---

### Post by QsoftStudios on 2012-08-13
Not sure if i'm posting in the right thread but o well. I was doing some work on a Libre Office base database when my router lost power due to a breaker trip. I  re-opened the database and I get the error The connection to the data source "data" could not be established, the driver class" cloud not be loaded. The database is located on a file server in my rack, and it works fine. I restarted it everything and still no go. I think the database has become corrupted. Any thoughts on recovering it would be amazing since its a business database. I have backups but the nearest one is from last week and douse not have the recent changes on it.

---

### Post by cbanakis on 2012-08-13
If your pulling data from a server on your network, and libre can't see the file...

Is there a chance that your equipment is set to DHCP AUTOMATIC?

In which case, the servers IP address may have changed when your router was reset.

Can you connect to the server via nautilus, and access files on the server that way?

---

### Post by QsoftStudios on 2012-08-13
The Ip adress has stayed the same, and yes I can access the  file via natilus, the file opens fine but when I click tables it gives me that error. I even pulled the database file off the server and on to my desktop and tried to access the tables and I still got the error.

---

### Post by cbanakis on 2012-08-13
You may be correct assuming the file is corrupted then.

Thats outside my knowledge base.

Figured I'd take a shot in the dark, and maybe we'd get lucky with the IP.

---


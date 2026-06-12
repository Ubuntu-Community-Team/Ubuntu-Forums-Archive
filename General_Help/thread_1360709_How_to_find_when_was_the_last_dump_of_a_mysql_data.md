---
title: "How to find when was the last dump of a mysql database?"
date: 2009-12-21
forum: General Help
---

### Post by milindras on 2009-12-21
Hi,
 
On my web server there are lots of mysql databases. How to find the last sqldump of a selected database? 
 
Thanks

---

### Post by DaithiF on 2009-12-21
Probably from the timestamp of the latest dump file you can find for that database.

Unlike (for example) Microsoft SQL Server, the MySQL database server itself is not aware of when/what backups are taken.  So you can't run some sql to ask the system database for any history on backups (again, unlike MSSQL).

Usually MySQL databases are backed up using the mysqldump utility -- this creates a file (or can be piped to another mysql server).  So assuming backups are being taken, find where they're being written to, and pick the latest file from there.

---

### Post by milindras on 2009-12-22
Sorry I should have expliain about this more.
 
I have a suspect somebody who has database user name & password has taken a dump of the database illegally (one of web sites of my server). Is there anyway to track this? Somehting like a mysql log to IP or when?
 
Im sure that any of user doest have access to the server (ssh). But that perticular database user & database name was exposed to them. So they can connect to the database remotely to take a dump.
 
Another question is, If the database user has no permission to connect to the perticular database from **any** host, So they shoudn't be able to connect remotely isnt it? (it only has permission for local host connection)
 
Many thanks for the reply.

---


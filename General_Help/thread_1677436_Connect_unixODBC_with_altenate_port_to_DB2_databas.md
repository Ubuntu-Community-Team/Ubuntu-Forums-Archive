---
title: "Connect unixODBC with altenate port to DB/2 database"
date: 2011-01-28
forum: General Help
---

### Post by spamking2000 on 2011-01-28
Hey Folks,
 
Question for the community out there. I imagine someone has run into this maybe more likely on the server side in pulling DB/2 data reports.

I'm trying to use ODBCConfig for unixODBC to connect to a DB2 database. I think I've got everything in there right, but there's no place to input the port. The DB2 database in question uses a different port than the default 50000. I just can't find a way to make UnixODBC call up the address of the server that the DB2 databases are on with its alternative port... so the server is rejecting the connection.
 
unixODBC is trying to use port 50000. The server that I'm connecting to uses 5031... I just can't figure out how to override the default 50000 to 5031.

I'm using the iSeries Access driver (AS400/DB2) from IBM, on Ubuntu 10.04LTS

I can't imagine that I'm the only one who's ever run into this problem.... but I also can't seem to figure out how to fix it.
 
Any help is appreciated!

Thanks!

---

### Post by spamking2000 on 2011-02-01
bump.... I still haven't figured this one out. Hoping someone else out there knows the trick.

---


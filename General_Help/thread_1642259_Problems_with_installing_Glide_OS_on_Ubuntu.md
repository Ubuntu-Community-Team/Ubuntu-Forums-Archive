---
title: "Problems with installing Glide OS on Ubuntu"
date: 2010-12-10
forum: General Help
---

### Post by jazzperm on 2010-12-10
I am trying to get Glide OS Desktop run on Ubintu 10.10 (tried 10.04 too btw) [http://www.glideos.com/downloads.html]("http://www.glideos.com/downloads.html")

When I download and try to install the deb file in both ubuntu 10.04 and 10.10 I get this message before installing: "Fout: Aan de volgende afhankelijkheid kon niet voldaan worden: libical (>= 0.43)" translated: "Error: The following dependencies could not be met: libical (> = 0.43)".

When I use alien to convert the rpm file to a deb file I get this output when trying to activate the software:
~$ /usr/share/glide/glide
"2010-12-08 14:31:43             Glide Desktop 3.3.4 Linux i686 #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 2.6.32-26-generic 2 CPUS"
"2010-12-08 14:31:43             Installation dir = /usr/share/glide"
"2010-12-08 14:31:43             Launching with forceNewDb = false"
glide::gui::GuiBoot::init()
Using default preferences
"2010-12-08 14:31:43             Intitializing Sync DB force new = no"
"2010-12-08 14:31:43             Sync DB is /home/jasper/.glide/sync.2.0.db"
"2010-12-08 14:31:43             Creating Sync database /home/jasper/.glide/sync.2.0.db, version 2.0, without old version"
QSqlDatabase: QSQLITE driver not loaded
QSqlDatabase: available drivers: QMYSQL3 QMYSQL
"2010-12-08 14:31:43   ERROR     Could not open the sync db /home/jasper/.glide/sync.2.0.db for creation -- Driver not loaded Driver not loaded"
"2010-12-08 14:31:43   ERROR     Could not open the sync database for creation/schema!"

I hope someone can hekp me out with this, because I think Glide OS is a perfect way to backup my files online and organise them.

thanks so far!

---

### Post by sealed on 2010-12-28
Try:

sudo apt-get install libqt4-qt3support libqt4-sql-sqlite

---


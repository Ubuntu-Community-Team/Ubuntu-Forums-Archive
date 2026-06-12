---
title: "QT-sql issue possibly?"
date: 2010-09-25
forum: General Help
---

### Post by clievers on 2010-09-25
Hi,
I am trying to get transcoding working in mythtv and am getting an error. I tried posting on mythtvtalk forums, since I thought it was related to mythtv, but the poster thought maybe it was an issue with qt-sql? So, I thought I'd post here too to see if someone can help. When I try to run the mythcommflag with the --gencutlist argument (step prior to then running an honorcutlist), I get the following:


[INDENT][COLOR="DarkRed"]2010-09-24 20:32:06.835 Using configuration directory = /home/cory/.mythtv
2010-09-24 20:32:06.836 Empty LocalHostName.
2010-09-24 20:32:06.846 New DB connection, total: 1
2010-09-24 20:32:06.850 Closing DB connection named 'DBManager0'
2010-09-24 20:32:06.855 ProgramInfo(): Updated pathname '':'' -> '1007_20100923223000.mpg'
QSqlDatabasePrivate::removeDatabase: connection 'DBManager0' is still in use, all queries will cease to work.
2010-09-24 20:32:06.912 MSqlDatabase::OpenDatabase(), db object is not valid!
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-24 20:32:06.962 Driver error was [1/-1]:
Driver not loaded
Database error was:
Driver not loaded

2010-09-24 20:32:07.013 Database not open while trying to load setting: idletimeoutsecs
2010-09-24 20:32:07.013 MSqlDatabase::OpenDatabase(), db object is not valid!
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-24 20:32:07.063 Driver error was [1/-1]:
Driver not loaded
Database error was:
Driver not loaded

2010-09-24 20:32:07.113 Database not open while trying to load setting: masterserverip
2010-09-24 20:32:07.113 MSqlDatabase::OpenDatabase(), db object is not valid!
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-24 20:32:07.164 Driver error was [1/-1]:
Driver not loaded
Database error was:
Driver not loaded

2010-09-24 20:32:07.214 Database not open while trying to load setting: masterserverport
2010-09-24 20:32:07.214 MSqlDatabase::OpenDatabase(), db object is not valid!
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-24 20:32:07.264 Driver error was [1/-1]:
Driver not loaded
Database error was:
Driver not loaded

2010-09-24 20:32:07.314 Database not open while trying to load setting: wolbackendcommand
2010-09-24 20:32:07.315 MSqlDatabase::OpenDatabase(), db object is not valid!
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-24 20:32:07.365 Driver error was [1/-1]:
Driver not loaded
Database error was:
Driver not loaded

2010-09-24 20:32:07.415 Database not open while trying to load setting: backendconnectretry
2010-09-24 20:32:07.418 Using protocol version 56[/COLOR][/INDENT]



Thanks in advance for any advice and suggestions,
Cory

---


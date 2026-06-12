---
title: "KRecipies database problems"
date: 2006-01-25
forum: General Help
---

### Post by BobSongs on 2006-01-25
Krecipes is installed but is complaining about its database choices. Any suggestions?

**installed apps**
krecipies
libmysqlclient12
libmysqlclient14
mysql-common
openoffice.org2-base
python2.4-mysqldb
python2.4-pysqlite2
python-mysqldb
python-pysqlite2

**error messages**
Simple Local File (SQLite):
"Krecipies could not open the SQLite database. You may not have the necessary permissions." 

Local or remote MySQL Database:
"The QT database plug-in (QMYSQL3) is not installed. This plug-in is required for using this database backend."

Do I need more of the MySQL components installed?

Thanks.

---

### Post by BobSongs on 2006-01-26
Okay; problem solved.

Everyone can go home.

Thanks

---

### Post by munralamun on 2006-04-28
Can you tell us what you did?

I'm having the same probem especially with the Qmysql3 not found error.

Thanks!

---

### Post by BobSongs on 2006-06-14
[QUOTE=munralamun]Can you tell us what you did?

I'm having the same probem especially with the Qmysql3 not found error.

Thanks![/QUOTE]```
sudo apt-get install libqt3-mt-mysql
```

---


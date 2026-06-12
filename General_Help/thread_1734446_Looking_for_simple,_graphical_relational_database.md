---
title: "Looking for simple, graphical relational database"
date: 2011-04-20
forum: General Help
---

### Post by Lars Noodén on 2011-04-20
I'm looking for a simple to use relational database with a graphical front-end. What are the options on Ubuntu?

For those that know Filemaker, I'm looking for something like that and I'd like not to have to build one in Qt.

---

### Post by SeijiSensei on 2011-04-20
There are web-based managers for both [PostgreSQL]("http://phppgadmin.sourceforge.net/doku.php?id=start") and [MySQL]("http://www.phpmyadmin.net/home_page/index.php").  These require a server running Apache+PHP with whichever database you'd like in the back end.

Personally, if I really want to use a graphical manager, I use MS Access with ODBC connections to my PostgreSQL databases.  Otherwise I just type SQL commands into the command-line clients, psql or mysql.

---

### Post by oldfred on 2011-04-20
I used dbase2 thru 4, then MS Access. Have not found anything but I think kexi was the closest. I am working on using SQLite & python, but it is a lot of detail.

Databases:
[http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL](http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL)
OpenOffice database
MDB Viewer
Glom - design is loosely based on FileMaker Pro
[http://www.glom.org/wiki/index.php?title=Main_Page](http://www.glom.org/wiki/index.php?title=Main_Page)
[http://www.kexi-project.org/](http://www.kexi-project.org/)
[http://www.koffice.org/kexi/](http://www.koffice.org/kexi/)
[http://www.knoda.org/](http://www.knoda.org/)
[http://www.gnome-db.org/](http://www.gnome-db.org/)
[http://www.0d.be/projects/gaby/](http://www.0d.be/projects/gaby/)
Microsoft Access in Wine - some success older version
[http://ubuntuforums.org/showthread.php?t=1113065](http://ubuntuforums.org/showthread.php?t=1113065)
[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)

---

### Post by Lars Noodén on 2011-04-21
> **oldfred said:**
> I think kexi was the closest. I am working on using SQLite & python, but it is a lot of detail.

Thanks. I will look at kexi again.

---


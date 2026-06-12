---
title: "Akonadi Broken"
date: 2012-01-28
forum: General Help
---

### Post by Orcris on 2012-01-28
I just upgraded to KDE 4.8, and when I opened Kontact I got a message saying Akonadi had had a fatal error. The log said that Akonadi is not registered as a Dbus. How do I fix this?

I looked for the database (/usr/sbin/mysqld-akonadi), and it's nonexistent. How do I create it?

EDIT:
mysql wasn't installed, so I ran ```
sudo aptitude install mysql-server mysql-client
``` and installed mysql. After that, I ran ```
sudo /usr/sbin/mysqld-akonadi
``` and it generated another error. I ran ```
 sudo mysql_upgrade --password=(my password) --force
``` and the table Akonadi needs still doesn't exist.

---


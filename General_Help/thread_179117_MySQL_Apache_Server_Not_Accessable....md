---
title: "MySQL Apache Server Not Accessable..."
date: 2006-05-19
forum: General Help
---

### Post by woodyrew on 2006-05-19
I'm trying to move our Company Database over to a Ubuntu system to get away from MS.  The database is currently an Access DB which is pretty rubbish tbh which is why we want to put it into MySQL.

I've installed MySQL and an Apache server on my Ubuntu system, however I need to use it as a Database server on a network.  I can't get access to the MySQL databases from anywhere else on the network.  We just want it accessible from the local network.

I've searched about for answers but I've not gained a solution yet.

Any hints tips or advice would be greatly welcome.

Thanks, Woody.

---

### Post by savas on 2006-05-19
Hi. As default you can only access mysql from local machine. You have to give permission to access from network. Below link can help you.

[http://www.trustix.org/wiki/index.php/MySQL_network_access](http://www.trustix.org/wiki/index.php/MySQL_network_access)

---

### Post by woodyrew on 2006-05-19
That's great thanks, I now need to find out how to reset my MySQL root password or Reset the whole MySQL Server installation.

---

### Post by savas on 2006-05-19
You can change root pasword using SQL ALTER statement. But there is a easy way.

```
mysqladmin -u root password PaSsWoRd
```

If you want to reset all settings. Remove mysql and reinstall.

```
sudo apt-get remove mysql-server
sudo apt-get install mysql-server
```

Good Luck!

---


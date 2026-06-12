---
title: "mysql restore backup"
date: 2012-05-22
forum: General Help
---

### Post by bill-lancaster on 2012-05-22
Before re-installing Ubuntu 12.04 I dumped my sql data using mysqldump.
Now I come to restore using 

 mysqldump -u root -pxxxxx calendar < /home/bill/Documents/calendar.sql

I get:-
 -- MySQL dump 10.13  Distrib 5.5.22, for debian-linux-gnu (i686)
--
-- Host: localhost    Database: calendar
-- ------------------------------------------------------
-- Server version	5.5.22-0ubuntu1

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;
/*!40103 SET TIME_ZONE=@OLD_TIME_ZONE */;

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;


 Dump completed on 2012-05-22 11:29:03

but there is no data in 'calendar'

Any help would be appreciated

---

### Post by phaemon on 2012-05-22
mysqldump dumps the database. To restore it just use mysql. Command is:

```

mysql -u root -p calendar < /home/bill/Documents/calendar.sql

```(that will prompt for a password; it's best not to leave passwords in your history)

If you have a big database, it's nicer to use pv with it to show the progress. You can do:
```

pv calendar.sql | mysql -u root -p calendar

```"sudo apt-get install pv" to get it.

---

### Post by bill-lancaster on 2012-05-22
That worked a treat! Thanks

---


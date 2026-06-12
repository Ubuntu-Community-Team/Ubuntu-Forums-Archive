---
title: "Mysql downgrade"
date: 2011-03-03
forum: General Help
---

### Post by bender1 on 2011-03-03
Hi ,i installed ubuntu 10.10 so i can make a mmo private server,but i  have a problem .my mysql database is too new i need mysql-client15 ,how  do i install it?i used this command apt-get install mysql-server mysql-client php5-mysql but it installs me the latest apt-get install libmysqlclient15-dev,can someone tell me how to do it?

---

### Post by bender1 on 2011-03-03
no one can help me?

---

### Post by bender1 on 2011-03-04
no one can help me?

---

### Post by bender1 on 2011-03-04
c'mon people no one knows?

---

### Post by TeoBigusGeekus on 2011-03-04
Find a machine that supports your database.
Use mysql administrator to create a backup.

Create a tiny test database on maverick's mysql version.
Use mysql admin again to create a backup from it.

Open the two backups (they're actually text files-scripts to create and populate the dbs from scratch) and compare them. Make the necessary changes to your first backup according to what you see in the second one.

I had an almost similar problem when I had to load a db created on 5.0.18 to mysql 5.1.something. I just opened the .sql file and it was just a matter of a single command preventing it from working properly.

---

### Post by TeoBigusGeekus on 2011-03-04
> this is one of the sql files ,can u modify it ? so it works in libmysqlclient16?please to have an example.[http://uploading.com/files/c3826933/db_account.sql/](http://uploading.com/files/c3826933/db_account.sql/)

Please don't pm for support - use the forums so that others can contribute to or benefit from the discussion.

I downloaded your .sql file but it wouldn't load cause there was no command for the creation of the database.

Change the first lines of the sql file to

```
# MySQL-Front 3.2  (Build 6.2)

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET CHARACTER SET 'utf8' */;

# Host: 192.168.52.128    Database: db_account
# ------------------------------------------------------
# Server version 5.0.45-log
CREATE DATABASE /*!32312 IF NOT EXISTS*/ db_account;
USE db_account;
#
# Table structure for table t_account
#
```

and try to load it with administrator again.

---

### Post by bender1 on 2011-03-04
I modified the .sql and executed them and when i m trying to start the db this is what is says.[http://img46.imageshack.us/i/screenshotdvt.png/]("http://img46.imageshack.us/i/screenshotdvt.png/")Do it matter that i m using navicat?

---

### Post by TeoBigusGeekus on 2011-03-04
> **bender1 said:**
> I modified the .sql and executed them and when i m trying to start the db this is what is says.[http://img46.imageshack.us/i/screenshotdvt.png/]("http://img46.imageshack.us/i/screenshotdvt.png/")Do it matter that i m using navicat?

No idea. Can you try it with mysql administrator?

By the way, I should tell you that I don't use ubuntu. The versions installed in my system are
```
libmysqlclient 5.5.9-1
mysql 5.5.9-1
mysql-clients 5.5.9-1
mysql-gui-tools 5.0r14-4
```

Could you please post yours?
```
dpkg -l|grep sql
```

---

### Post by bender1 on 2011-03-04
this is a SS with all that i got when i wrote that command.[http://img219.imageshack.us/i/screenshot1jk.png/]("http://img219.imageshack.us/i/screenshot1jk.png/")

---

### Post by TeoBigusGeekus on 2011-03-04
Ok, so your sql packages are old. Never mind that.
Install administrator and try from there as I'm more familiar with it (I abandoned mysql administration from command line a long time ago).

---

### Post by bender1 on 2011-03-04
i installed mysql admin,now?

---

### Post by TeoBigusGeekus on 2011-03-04
Open it, give password and go to Restore Backup.
Click change path and select the path where your db lies.
The .sql file will appear in the box - choose it and press restore backup.

---

### Post by bender1 on 2011-03-04
it keeps loading i put the ip from navicat and username and pass and it wont connect.[http://img651.imageshack.us/i/screenshotvf.png/]("http://img651.imageshack.us/i/screenshotvf.png/")
found it,had to put localhost instead of IP ,silly me

---

### Post by TeoBigusGeekus on 2011-03-04
Put localhost in the server hostname.

---

### Post by bender1 on 2011-03-04
i restored them now what?

---

### Post by TeoBigusGeekus on 2011-03-04
No error messages?
If not, you're done - the db was successfully loaded into mysql.

---

### Post by bender1 on 2011-03-04
yes ,but when i'm trying to run the ./db_server i get the same error.
you wrote that line in .sql and it didnt needed libmysqlclient15 ,can you write other so that it doesnt need libssl.so.7?

---

### Post by TeoBigusGeekus on 2011-03-04
Install mysql query browser and open it.
Give the same credentials you gave in administrator.
Once in, check to see if the name of your db is in the schemata tab.
If it is, double click it. You should be able to navigate through all the tables.

---

### Post by TeoBigusGeekus on 2011-03-04
As for the libssl.so problem, see [this]("http://forum.teamspeak.com/showthread.php/58241-Solution-for-unable-to-load-database-plugin-library-quot-libts3db_mysql.so-quot").

---

### Post by bender1 on 2011-03-04
I installed libssl and removed mysql admin and query ,and now i have this error ,and i do not know how to fix it ,can you help me?[http://img217.imageshack.us/i/screenshotyct.png/]("http://img217.imageshack.us/i/screenshotyct.png/")

---

### Post by TeoBigusGeekus on 2011-03-04
Might I suggest a purging and reinstallation of everything mysql related?

---


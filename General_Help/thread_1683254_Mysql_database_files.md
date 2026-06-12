---
title: "Mysql database files"
date: 2011-02-07
forum: General Help
---

### Post by kantor on 2011-02-07
I'm new to the ensemble Mysql-PHP-Apache on Linux, but i'm not a newbie of linux.

I use ubuntu to create a little client to manage a database, i can create and select database without errors, but i can't see the sql files in the working directory of php script. 

There are some trouble about persistence or the sql files created by Mysql are in a esotic directory? ^^

:confused:

---

### Post by ahsan101 on 2011-02-07
I missed your point, what are you actually looking for ? you are looking for .sql file in which directory? Can you clearify it a bit more? May be i can help you out, because i have experienced MySql,apache and php etc.

---

### Post by kantor on 2011-02-07
My point is: 
I've got a php script that creates, selects and works on a database in the directory /var/www/. I get no errors.

I expected to find a name_db.sql file in /var/www/ but i there isn't any kind of .sql file. 
I missed something about Mysql on linux?

---

### Post by SeijiSensei on 2011-02-07
If the database is running, you connect to it with a mysql_connect() command in PHP.  That opens a connection to the DB that you can use with other mysql_ commands.

There's no "file" created; just a connection to the database server mysqld.

The actual database is stored in /var/lib/mysql, but you don't access that directly, only via the server instance.  If you want a complete backup of the database, look into mysqldump.  You'll get a plain-text backup as a set of SQL commands.

---

### Post by kantor on 2011-02-07
> **SeijiSensei said:**
> If the database is running, you connect to it with a mysql_connect() command in PHP.  That opens a connection to the DB that you can use with other mysql_ commands.

There's no "file" created; just a connection to the database server mysqld.

The actual database is stored in /var/lib/mysql, but you don't access that directly, only via the server instance.  If you want a complete backup of the database, look into mysqldump.  You'll get a plain-text backup as a set of SQL commands.

So it's how i suspected. Many thanks for the clarification, i was just wondering if i was right. However i use Mysqli extension, but in this case i guess it's the same.

---


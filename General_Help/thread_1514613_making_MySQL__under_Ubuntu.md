---
title: "making MySQL  under Ubuntu"
date: 2010-06-21
forum: General Help
---

### Post by klaasvg on 2010-06-21
Hi all,

I am following a Linux course from a book and use my Ubuntu PC for it. But despite a few attempts I do not succeed in making MySQL working.
There appears to be a problem with permissions. I also consulted the manual of My SQL itself and carried out the following steps:

-MySQL is installed, the packages are:
mysql-client-5.1
mysql-server-5.1
mysql-server-core-5.1

-Initialise the data directory and create grant tables
cd /usr/bin
sudo mysql-install-db --user=mysql
This generates some messages, but no errors still

-Starting the server
/usr/bin/mysqld_safe --user=mysql &
Tells that the server is already started

-Call sudo mysqladmin version
This gives an error message: 
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

I tries some different things but it keeps giving this error messages. Actually I am not sure what the issued statement do exactly and how/where it creates tables and how permissions work.

Maybe I am missing something simple? Anybody has ideas?
Regards, Klaas

---

### Post by Ryan Dwyer on 2010-06-21
You don't need to do any of that. Just run sudo apt-get install mysql-server to install it from the repositories.

MySQL has its own user system. By default there's an account called root with no/blank password. However, it looks like you configured it differently.

---

### Post by klaasvg on 2010-06-21
I think those packages were already installed. but maybe I messed something. IS it better to re-isntall the packages? Can I maek the MySQL server "clean" again?
I udnerstand that there is a default user root with no password. My tutorial advices to make a user mysql with a password. But maybe the tutorial is a bit outdated. 
I have really no idea how to set up thing an on the command line or where the db is located. Is there some good tutorial available? Or has anybody experience with it?

---

### Post by Ryan Dwyer on 2010-06-21
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

You can uninstall MySQL and purge your existing config (MySQL users etc) by running sudo apt-get purge mysql-server, then install again with sudo apt-get install mysql-server.

The database files are in /var/lib/mysql, but you shouldn't have to ever touch those files manually.

When installing MySQL I believe it prompts you to set a password for the root account. You don't need to set a password for a development/test machine, but for a production server it's highly recommended.

You can install phpMyAdmin (web based database manager) to manage almost all aspects of MySQL including user creation.

---

### Post by zevans on 2010-07-05
klaasvg - You are not going mad. :-)

There is a bug in here somewhere. I've seen a few people ask the question in the past but I've never run into the problem myself before. Now I have.

Last week I installed mysql on a server, and everything went as you would expect. This week I have a problem, on my netbook, yet I haven't done anything different.

- dpkg-reconfigure mysql-server-5.1 asks if I want to set a root password as you would expect. This password doesn't work - but I don't get an error message during reconfigure.

- I've tried the purge and reinstall method (which is quite a pain in lucid, because parts of KDE now depend on the mysql-server package.) This doesn't seem to work either, whether I choose to set a password or leave it blank.

- The official method of resetting SQL root password doesn't work. I can start the database without the permissions framework, but the problem seems to be that THERE IS NO ROOT USER AT ALL. No wonder none of the other methods can set a password. There is a debian-sys-maint password and NO other usernames. Look:

```

root@vademecum:~# mysql -u root
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.1.41-3ubuntu12.3 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> SELECT User, Host, Password FROM mysql.user;
+------------------+-----------+-------------------------------------------+
| User             | Host      | Password                                  |
+------------------+-----------+-------------------------------------------+
| debian-sys-maint | localhost | *9A7137A8B2C7AB710FD15DF98E5D3EFB130AF432 |
+------------------+-----------+-------------------------------------------+
1 row in set (0.00 sec)

```

Anyone have any idea why this is happening, and more importantly, how I fix it?

---

### Post by zevans on 2010-07-05
As usual, as soon as I post I have a brainwave...

For some reason, and I still don't know why, the default databases had not been set up correctly.

As advised in
[http://dev.mysql.com/doc/refman/5.1/en/mysql-install-db-problems.html]("http://dev.mysql.com/doc/refman/5.1/en/mysql-install-db-problems.html")

I renamed the existing database out of the way and ran the separate script that (luckily) comes with mysql to create the initial databases.

```
# stop mysql
service mysql stop

# This is where the databases are by default in Ubuntu
cd /var/lib/sql
mv mysql.old

# recreates all the system tables
mysql_install_db --user=mysql

service mysql start
```

---

### Post by klaasvg on 2010-07-20
Hi Zevans,

SO still many problems with MySQL... I have partly solved the problem now. I installed MySQL fresly on a new LL installation, during the installation of the package it asked for the root password. 
After installing I can easily turn on and off the database using 
service mysql start|stop|restart|status

And to get into the MySQL interface, I just type:
mysqladmin -u root -p

and it asks for the My SQL root user password (not the system root password) and it sees to work fine.

I still wonder whether it is good to use the root as primary mysql user. I remember a tutorial where user and group mysql were set up...

---

### Post by porchrat on 2010-07-20
> **klaasvg said:**
> Hi Zevans,

SO still many problems with MySQL... I have partly solved the problem now. I installed MySQL fresly on a new LL installation, during the installation of the package it asked for the root password. 
After installing I can easily turn on and off the database using 
service mysql start|stop|restart|status

And to get into the MySQL interface, I just type:
mysqladmin -u root -p

and it asks for the My SQL root user password (not the system root password) and it sees to work fine.

I still wonder whether it is good to use the root as primary mysql user. I remember a tutorial where user and group mysql were set up...

I normally create another user with less privileges for day-to-day work. Also if you have some app running off the MySQL server that doesn't need to create databases but only needs to read them why let it login using root? All it needs is read privileges.

What other problems are you having?

---

### Post by Wim Sturkenboom on 2010-07-20
```
mysql> grant all privileges on mydb.* to 'wim'@'localhost' identified by 'my password';
Query OK, 0 rows affected (0.00 sec)

mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)

mysql> exit

```
This creates a user 'wim' that can fully manipulate the database 'mydb'.

If my login (in Linux) is 'wim', I can access it with '*mysql mydb -p*'

---

### Post by porchrat on 2010-07-20
> **Wim Sturkenboom said:**
> ```
mysql> grant all privileges on mydb.* to 'wim'@'localhost' identified by 'my password';
Query OK, 0 rows affected (0.00 sec)

mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)

mysql> exit

```
This creates a user 'wim' that can fully manipulate the database 'mydb'.

If my login (in Linux) is 'wim', I can access it with '*mysql mydb -p*'

You know I actually had never realised that but it makes perfect sense.

When I forget to specify a user for myqsl I often get told something like:

> Access denied for user 'porchrat'@'localhost' (using password NO)

---


---
title: "mySQL on Ubuntu"
date: 2011-01-08
forum: General Help
---

### Post by john77eipe on 2011-01-08
Hi, 

I wanted to support my website with mySQL database. So I installed the following on my Ubuntu machine. 
mysql-admin 
mysql-server 
mysql-client 
mysql-query-browser 


root@eipe-john:~# service mysql start 
mysql start/running, process 2678 

Does this start the server? Do I need both client and server to support my website? (I thinks server alone will do as I'm the only user here) 

root@eipe-john:~# mysqladmin status 
mysqladmin: connect to server at 'localhost' failed 
error: 'Access denied for user 'root'@'localhost' (using password: NO)' 

??? How do I proceed from here to creating a database?

---

### Post by lykeion on 2011-01-08
You need the mysql-client to connect to the mysql-server when you create databases, make queries, etc.

Read the [ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP") page of the Ubuntu Documentation to find out how to:
[LIST]
[*]Set mysql bind address
[*]Set mysql root password
[*]Create a mysql database
[*]Create a mysql user
[/LIST]
To learn more about SQL, queries, etc I would recommend [W3 Schools SQL Tutorial]("http://www.w3schools.com/sql/default.asp").

---

### Post by john77eipe on 2011-01-08
@lykeion

Thanks. 
I was worried if I would get any reply as this has to do more with mySQL than Ubuntu :)

---

### Post by john77eipe on 2011-01-08
root@eipe-john:/# mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
:(

---

### Post by john77eipe on 2011-01-08
```
root@eipe-john:/etc/init.d# mysqld_safe --skip-grant-tables &
[1] 7332
root@eipe-john:/etc/init.d# 110108 20:16:34 mysqld_safe Logging to syslog.
110108 20:16:34 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
root@eipe-john:/etc/init.d# mysql -u root
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.1.49-1ubuntu8.1 (Ubuntu)

```

And it's working now. But could someone explain the error and what "mysqld_safe --skip-grant-tables &" does?

---

### Post by lykeion on 2011-01-08
You can read the manual for most commands/applications using *man*:
```
man mysqld_safe
```
I think the default root password for MySQL is blank, but trying to login as root *without* using a password will give you access denied. You should however be able to login with:
```
mysql -u root -p
```and pressing Enter when prompted for password.

---


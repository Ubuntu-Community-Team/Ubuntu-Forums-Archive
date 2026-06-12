---
title: "Configurating MySQL Database Server"
date: 2012-08-14
forum: General Help
---

### Post by Medialeakz on 2012-08-14
Hello,  i dont know if anyone can help me resolve this problem i am having. 
i have installed mySql database server on my Ubuntu server, create the user and database 
now when i try to connect to the mysql server, its NOT connecting.

Btw I am using Webmin web interface.

---

### Post by Habitual on 2012-08-14
is mysqld started?

terminal > 
```
pidof mysqld
```

if not, ```
sudo service mysqld start
```

---

### Post by Cheesemill on 2012-08-14
I'm not sure what configurating means but you can test if MySQL is working by using the command line.
```
mysql -u root -p
```
This should prompt you for the mysql root password and then open up a mysql shell like so:
```
root@arch:/usr# mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 10
Server version: 5.5.27-log Source distribution

Copyright (c) 2000, 2011, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 
```If this works then MySQL is functioning correctly (type quit to exit the MySQL shell).

---


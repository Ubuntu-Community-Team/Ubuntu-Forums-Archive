---
title: "mysql privileges missing"
date: 2010-06-03
forum: General Help
---

### Post by james182 on 2010-06-03
hi i installed LAMP and also mysql administrator.
the problem is when i click User Administration within mysql administrator i get this error " could not retrieve user privilege information".

[B]SYSTEM DETAILS
Connected to mysql server instance:[/B]
User: phpmyadmin
Host: 127.0.0.1
Port: 3306

**Server Info**
MySQL Version: 5.1.41
Network Name: localhost


please help...:confused:

---

### Post by james182 on 2010-06-03
Polite bump 

I need to grant permissions to my root user but can't get mysql access.  
Please help. I have googled but no joy.

---

### Post by james182 on 2010-06-04
i have tried:

james@james-laptop:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysqld.sock' (2)

james@james-laptop:~$ sudo  mysql -u phpmyadmin mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysqld.sock' (2)

and get the above errors. but i can login into phpmyadmin but have no privileges any help would be much appreciated. :confused:

---

### Post by Andy Moon on 2010-09-11
Maybe have a look at mysql "debian" user credentials in file */etc/mysql/debian.cnf*

You shall be able to use the user called *debian-sys-maint* for login into your admin tool.

Not sure if that's a "proper" way of logging in mysql though.

I'm currently finishing my LAMP config. Did it before, and didn't remember struggling with mysql users as Ive been struggling today.

---


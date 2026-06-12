---
title: "mysql problem"
date: 2006-06-07
forum: General Help
---

### Post by sc30317 on 2006-06-07
when I try use the code 

 mysql -u root mysql

to setup my mysql account, i get


ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)

What should I do to get mysql working?

---

### Post by giants_fan on 2006-06-08
[QUOTE=sc30317]when I try use the code 

 mysql -u root mysql

to setup my mysql account, i get


ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)

What should I do to get mysql working?[/QUOTE]
Uh...is MySQL running?

I suspect it isn't.  In the terminal, try typing "telnet localhost 3306".  If you get a "Connection Refused" message, it's not running.  To turn it on, go to System->Administration->Services and "Database" server.

---

### Post by adamkane on 2006-06-09
It's always good to learn mysql from the command line, but you may want to use phpmyadmin to make things easier:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by mlind on 2006-06-09
sudo /etc/init.d/mysqld restart ?

---


---
title: "PHP cannot connect to MySQL server"
date: 2006-05-26
forum: General Help
---

### Post by mesh2005 on 2006-05-26
I installed PHP,MySQL using the ap-get. I wrote a php script to connect the MySQL but it failed to connect although all my settings are true.
I hope you can help. thanks

---

### Post by lkagan on 2006-05-26
First ensure mysql is running with
```
ps auxw | grep mysql
```
Then ensure you can connect manually with
```
 mysql -u root
```
Then try your script again.
If it fails, post your mysql_connect() or similar function as a reply to this forum (ensure you change the password) and also post the message the PHP displays or logs.

---

### Post by mesh2005 on 2006-05-26
it worked thanks :)

---

### Post by brickbat on 2006-05-27
Sorry to hijack this but I have the same problem.

When I ran the grep command it replied with

brickbat 28840  0.0  0.2   2524   608 pts/0    R+   15:51   0:00 grep mysql

and when i did mysql -u root it replied wth command not found.

---

### Post by lkagan on 2006-05-27
The results of grep means that mysql is not running. The failed mysql command means that mysql is not in your path (probably not installed). If you used the package manager (Synaptic) to install mysql as most people on Ubuntu would, it would be located at /usr/bin/mysql. So typing the following would simply spit back the path to mysql:
```
larry@foxxy:~$ ls /usr/bin/mysql
/usr/bin/mysql
```
If you get 
```
larry@foxxy:~$ ls /usr/bin/mysql
ls: /usr/bin/mysql: No such file or directory
```
Then mysql is not installed (at least not by the package manager).
The below command will install MySQL. MySQL comes in two parts: the server and the client.  There is also a module that plugs into php that tells it how to talk to MySQL which is also included in the following command:
```
 sudo apt-get install mysql-client mysql-server php4-mysql
```
The above makes a couple of assumptions.  The version of PHP will be 4 and the version of MySQL will also be 4.0.

Good luck!

Larry

---

### Post by brickbat on 2006-05-27
For some reason, mysql didnt install with apt-get with the other programs.  Maybe i mistyped it or something.  Anyway, I installed it with Synaptic. Done.

Thanks Larry.

---

### Post by adamkane on 2006-05-27
Easy Apache/MySQL/PHP install:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

---


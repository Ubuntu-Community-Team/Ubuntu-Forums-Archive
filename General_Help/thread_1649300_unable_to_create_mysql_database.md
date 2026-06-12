---
title: "unable to create mysql database"
date: 2010-12-20
forum: General Help
---

### Post by zenji agamotto on 2010-12-20
Hey all thanks for the help in advance! 
right now i am having a tough time creating a mysql database for snort 
when i enter:   $ cat /etc/group |grep -i mysql 
i get: mysql:x:126:
 
when i enter: /usr/share/doc/snort-mysql$ sudo zcat create_mysql.gz | mysql -u (myusername) -h localhost -p snortdb
Enter password: 
ERROR 1045 (28000): Access denied for user '(myusername)'@'localhost' (using password: YES)

and i tried both the original mysql password as well as my root password to no avail what am i doing wrong?

when i check out: cat /etc/passwd |grep -i mysql
mysql:x:117:126:MySQL Server,,,:/nonexistent:/bin/false

have i set something up wrong or just missed a major step somewhere?

---

### Post by wojox on 2010-12-20
What happens when you open a terminal and enter

```
mysql -u root -p <Enter>

```

---

### Post by zenji agamotto on 2010-12-20
mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 55
Server version: 5.1.49-1ubuntu8.1 (Ubuntu)

---

### Post by wojox on 2010-12-20
Okay now your logged in as root, so set up your user or database. Read [MySQL Documentation]("http://dev.mysql.com/doc/")

---

### Post by scott_tiger on 2010-12-20
[http://www.howtogeek.com/howto/ubuntu/install-mysql-server-5-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-mysql-server-5-on-ubuntu/)
SEE THE ABOVE URL..IT WILL SOLVE YOUR PROBLEM

---

### Post by zenji agamotto on 2010-12-20
those are the very directions i used to get up and running! but originally i am trying to set up a database for snort and when i compiled snort it told me that i needed to : zcat create_mysql.gz | mysql -u <user> -h <host> -p <databasename>
 and when i do that or even throw in a sudo i still get the ERROR 1045 (28000): Access denied for user 'xxxxxxxx'@'localhost' (using password: YES)

---

### Post by zenji agamotto on 2010-12-20
So to re-cap: when I:  ps ax | grep mysql
 6002 ?        Ssl    0:27 /usr/sbin/mysqld
 8383 pts/0    S+     0:00 grep --color=auto mysql

so its definitely running i can even log into myql server and issue commands
i checked out the MySQL reference guide before I even posted the query, and essentially my question remains maybe i should have been more specific: How would i create a database from command line ?
i am assuming i must create some user in mysql then grant it all privileges of root and then flush privileges?
the thread @ [http://www.howtogeek.com/howto/ubuntu/install-mysql-server-5-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-mysql-server-5-on-ubuntu/) alludes to this at the very end but is not conclusive.

again the command im trying to run is zcat create_mysql.gz | mysql -u <user> -h <host> -p <databasename>
 
but its giving me a permission error how do i create the proper environment in mysql server for this to work?

---


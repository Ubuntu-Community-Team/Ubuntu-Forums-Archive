---
title: "ERROR on mysql"
date: 2011-01-21
forum: General Help
---

### Post by Rakeshvijayan on 2011-01-21
I am trying to install library system , at the point granting permission  for "root" user and " koha " named user system sows some error ...am  confused now ...expect help with your help I can go forward
This is the Note that I used
[
* mysqladmin -u root -p create koha

Enter Password: your mysql root password

koha is the name of my db in this case.

* mysql -uroot –p

Enter Password: your mysql root password

Grant Permissions for MySQL Database:

Now because this is a tutorial, I used simple passwords. Of course on  your production system, it is advised that you use difficult passwords.  Kindly don’t criticize

koha is the database name.

* mysql> grant all on koha.* to 'root'@'localhost' identified by 'rootpassword’;

Query OK, 0 rows affected (0.00 sec)

* mysql> grant all on koha.* to 'koha'@'localhost' identified by 'koha';

Query OK, 0 rows affected (0.00 sec)

* mysql> flush privileges;

Query OK, 0 rows affected (0.00 sec)

* mysql> quit;

Bye ]

THIS IS THE RESULT FOR THAT STEP .IS THERE ANY MISTAKE IN THERE

library@mct:~$ mysql -u root -p
Enter password:
Welcome to the MySQL monitor. Commands end with ; or \g.
Your MySQL connection id is 37
Server version: 5.0.75-0ubuntu10.5 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> grant all on koha.* to 'root'@'localhost'
-> grant all on koha.* to 'root'@'localhost' identified by 'password';
ERROR 1064 (42000): You have an error in your SQL syntax; check the  manual that corresponds to your MySQL server version for the right  syntax to use near 'grant all on koha.* to 'root'@'localhost' identified  by 'password'' at line 2
mysql> grant all on koha.* to 'root'@'localhost' grant all on koha.* to 'root'@'localhost' identified by 'password';
ERROR 1064 (42000): You have an error in your SQL syntax; check the  manual that corresponds to your MySQL server version for the right  syntax to use near 'grant all on koha.* to 'root'@'localhost' identified  by 'password'' at line 1
mysql>:popcorn:

---


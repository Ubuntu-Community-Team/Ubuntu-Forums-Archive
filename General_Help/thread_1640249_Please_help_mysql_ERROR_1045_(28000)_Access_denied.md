---
title: "Please help: mysql ERROR 1045 (28000): Access denied for user  (using password: YES)"
date: 2010-12-07
forum: General Help
---

### Post by getmizanur on 2010-12-07
elloo,

i have tried to follow some the tutorials on google to setup mysql for remote access however, cannot seem to do it. am i missing something.

i have edited /etc/mysql/my.cnf bind-address directive to a static ip address. then, i grant user@'%' access to database and restart mysql

after doing all that, when i try to remote access mysql i get "Access denied for user"

Please help

---

### Post by Habitual on 2010-12-08
I don't believe /etc/mysql/my.cnf bind-address has anything to do with remote connection permissions.

I'd remark any addition you made out and bounce mysql.

Can you access that mysql_user FROM the mysql server?

Example Grant (for comparison purposes)
Login to mysql
mysql > grant all privileges on dbNAME.* to guest@% identified by 'getmizanur'; <-- WhatEVER password you use here BECOMES guest's new mysql password.

mysql > flush privileges; 
mysql > exit;

in a terminal prompt on the MySQL server type
mysql -uguest -p (enter)
"Enter Password:" getmizanur <-- use this password, or whatever you set it to on the 'grant all' statement.

No need to restart mysql, AFAIK.

You should get in.

---


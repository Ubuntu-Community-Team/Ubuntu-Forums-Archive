---
title: "i need someone trustworthy to install openbiblio on a web server."
date: 2011-11-12
forum: General Help
---

### Post by t120 on 2011-11-12
Hello,

I'm banging my head against a wall here trying to install OpenBiblio on a subdomain of a particular website I am running. I have created a MySQL Database, as well as a user, and assigned all privileges to this user. I then edited the database_constants.php file to include this information. Still, no go. / displayed this message:

-----

Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'your OpenBiblio '@'localhost' (using password: YES) in /home/strawbe1/public_html/(MYDOMAIN)/catalog/classes/Query.php on line 36
Database Query Error - You've Probably Found a Bug

Cannot connect to database server.

Please give all the information on this page to your support personnel.

Query Connecting to database server... failed. The DBMS said this:

Access denied for user 'your OpenBiblio '@'localhost' (using password: YES)
Debug Backtrace (most recent call first):

/home/strawbe1/public_html/(MYDOMAIN)/catalog/classes/Error.php:100 FatalHandler->printBackTrace()
/home/strawbe1/public_html/(MYDOMAIN)/catalog/classes/Error.php:68 FatalHandler->dbError('Connecting to database server...', 'Cannot connect to database server.', 'Access denied for user \'your OpenBiblio \'@\'localhost\' (using password: YES)')
/home/strawbe1/public_html/(MYDOMAIN)/catalog/classes/Query.php:18 Fatal->dbError('Connecting to database server...', 'Cannot connect to database server.', 'Access denied for user \'your OpenBiblio \'@\'localhost\' (using password: YES)')
/home/strawbe1/public_html/(MYDOMAIN)/catalog/shared/read_settings.php:21 Query->Query()
/home/strawbe1/public_html/(MYDOMAIN)/catalog/shared/common.php:81 require_once('/home/strawbe1/public_html/(MYDOMAIN)/catalog/shared/read_settings.php')
/home/strawbe1/public_html/(MYDOMAIN)/catalog/home/index.php:6 require_once('/home/strawbe1/public_html/(MYDOMAIN)/catalog/shared/common.php')

(Please note: I have replaced my domain name with "(MYDOMAIN)" to insure privacy)
-----

I became frustrated and removed both the database and the OpenBiblio files. The subdomain's root directory is now empty. 

What I am looking for is a trustworthy person who is able to install this script. If anyone would be willing to install this for me, I will PM you FTP and database details. The OpenBiblio files can be downloaded from obiblio.sourceforge.net. 

Would anybody be willing to help me? I am floundering... :)

---


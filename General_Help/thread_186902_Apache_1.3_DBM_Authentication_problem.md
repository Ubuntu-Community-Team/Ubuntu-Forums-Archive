---
title: "Apache 1.3 DBM Authentication problem"
date: 2006-06-02
forum: General Help
---

### Post by dimlerb on 2006-06-02
There are several types of DB file formats. It appears that our dbm_auth_module expects DB file to have extension of .PAG and .DIR, however dbmmanage comand creates DB file without any extensions. Therefore, web server doesn't find the files. The web server reports that it cannot find or open file.

DBM File and a user is created with the following command
+++++++++++
sh-3.00# /usr/bin/dbmmanage /var/www/users adduser mark
User mark added with password encrypted to V2xu4ZWJeB1hk using crypt
+++++++++++

Users are checked and verified

+++++++++++
sh-3.00# /usr/bin/dbmmanage /var/www/users view
mark:V2xu4ZWJeB1hk
++++++++++++

 
User cannot login. The following error is recorded in Apache error log
++++++++++++
[Wed May 31 15:13:01 2006] [error] [client 127.0.0.1] (2)
No such file or directory: could not open dbm auth file: /var/www/users
[Wed May 31 15:13:01 2006] [error] [client 127.0.0.1] 
DBM user mark not found: /var/www/protected1
++++++++++++

**Please share any experience with this setup...**

---


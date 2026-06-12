---
title: "how to take mysqldump from a remote mysql host ?"
date: 2012-04-22
forum: General Help
---

### Post by winzip on 2012-04-22
How to dump  database from a remote mysql host ?

I am not sure whats the correct syntax ...but I guess it   is  like this .

*mysqldump -u root -p root  Test_Database  -h 192.168.2.18  *

where  Test_Database  is a database in remote mysql host 192.168.2.18 with  dbuserid=root and dbpassword=root.


Could you please tell what would be the correct syntax here  ?

---

### Post by Habitual on 2012-04-23
IF the db is on 192.168.2.18
```
ssh root@192.168.2.18 "mysqldump Test_Database > /path/to/file.sql"
``` will export the db.

IF the mysql_root_user (in mysql) password is NOT the same as root user Linux account then
```
ssh root@192.168.2.18 "mysqldump -uroot -ppassword Test_Database > /path/to/file.sql"
``````
-h 192.168.2.18 
```should not be necessary.

If you are trying to dump the db to your local host, there is a method that can do that (I don't remember off the top of my head but it involves a "-" operation in the command, otherwise you will have to scp/[s]ftp the remote /path/to/file.sql to your local host.

HTH.

---


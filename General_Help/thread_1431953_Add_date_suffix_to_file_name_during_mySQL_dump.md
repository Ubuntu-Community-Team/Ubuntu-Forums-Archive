---
title: "Add date suffix to file name during mySQL dump"
date: 2010-03-17
forum: General Help
---

### Post by ojobson on 2010-03-17
I have a script (below) which works ok, but I have tried to modify it as I want to keep the older files for a restore if needed. I have tried adding a date suffix to the newly created files (second lump of code), but it doesn't seem to work.
 
I get the error: 
[INDENT]$SOURCEDIR/p1db_$DATEVAR.sql: ambiguous redirect
[/INDENT]The working original script:
```

#!/bin/bash
# mysql dump of wordpress website db's and export to a destination machine
#These first commands set the variables for the destination of the dumped db, an optional date extension to the file and the password for the host server.
SOURCEDIR=/home/wordpress/backups/dump
PASS=password
#This section controls the dumps from the mysql database, parsing the above variables. You can edit the commands below to include all the mySQL options or just the tables you require.
/opt/lampp/bin/mysqldump --opt -u root -p$PASS --add-drop-table --lock-tables --databases DBNAME1 > $SOURCEDIR/p1db.sql
/opt/lampp/bin/mysqldump --opt -u root -p$PASS --add-drop-table --lock-tables --databases DBNAME2 > $SOURCEDIR/jtdb.sql
/opt/lampp/bin/mysqldump --opt -u root -p$PASS --add-drop-table --lock-tables --databases DBNAME2 > $SOURCEDIR/ppdb.sql
/opt/lampp/bin/mysqldump --opt -u root -p$PASS --add-drop-table --lock-tables --databases DBNAME3 > $SOURCEDIR/pfdb.sql
/opt/lampp/bin/mysqldump --opt -u root -p$PASS --add-drop-table --lock-tables --databases DBNAME4 > $SOURCEDIR/pcdb.sql
#The following command activates rsync to talk to the destination backup over SSH
#You can use this to export a backup to a remote machine or,
#..you can use this command to send the mysql databases to a mirrored server. A second script will need to be run on the destination server to import the transfered db into mysql.
rsync -rtlzv --ignore-errors -e ssh /home/wordpress/backups/dump/ root@OTHERHOSTIP:/home/wordpress/backups/import

```
 
Then when trying to add date suffix with variable:
 
```

#!/bin/bash
# mysql dump of wordpress website db's and export to a destination machine
#These first commands set the variables for the destination of the dumped db, an optional date extension to the file and the password for the host server.
SOURCEDIR=/home/wordpress/backups/dump
DATEVAR='date +%d_%m_%y'
PASS=password
#This section controls the dumps from the mysql database, parsing the above variables. You can edit the commands below to include all the mySQL options or just the tables you require.
/opt/lampp/bin/mysqldump --opt -u root -p$PASS --add-drop-table --lock-tables --databases pageone > $SOURCEDIR/p1db_$DATEVAR.sql
/opt/lampp/bin/mysqldump --opt -u root -p$PASS --add-drop-table --lock-tables --databases pageonejanettxt > $SOURCEDIR/jtdb_$DATEVAR.sql
/opt/lampp/bin/mysqldump --opt -u root -p$PASS --add-drop-table --lock-tables --databases pageonepager > $SOURCEDIR/ppdb_$DATEVAR.sql
/opt/lampp/bin/mysqldump --opt -u root -p$PASS --add-drop-table --lock-tables --databases pageoneflare > $SOURCEDIR/pfdb_$DATEVAR.sql
/opt/lampp/bin/mysqldump --opt -u root -p$PASS --add-drop-table --lock-tables --databases pageonecontact > $SOURCEDIR/pcdb_$DATEVAR.sql
#The following command activates rsync to talk to the destination backup over SSH
#You can use this to export a backup to a remote machine or,
#..you can use this command to send the mysql databases to a mirrored server. A second script will need to be run on the destination server to import the transfered db into mysql.
rsync -rtlzv --ignore-errors -e ssh /home/wordpress/backups/dump/ root@OTHERHOSTIP:/home/wordpress/backups/import

```
 
Any ideas? Bit stumped and I can't seem to make any of the examples I've found from googling work in the scenario.
 
Cheers,

---

### Post by ojobson on 2010-03-17
Had the date surrounded by quotes '' instead of backticks ``.
 
All working like a dream now!

---


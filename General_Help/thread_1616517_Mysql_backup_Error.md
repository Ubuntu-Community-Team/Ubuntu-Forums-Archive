---
title: "Mysql backup Error"
date: 2010-11-08
forum: General Help
---

### Post by suresh_vandiyur on 2010-11-08
Hi i have used the below script for the backup of the mysql database

i got to error am new for the shell script

Errors:
sh /home/blaze/backupmysql.sh 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
/home/blaze/backupmysql.sh: 54: Syntax error: "then" unexpected (expecting "done")


                     Mysql Database backup using the Shell Script

#!/bin/bash

MyUSER="root"  #USERNAME
MyPASS="XXX"               #PASSWORD
MyHOST="localhost"                            # HOSTNAME


MYSQL="$(which mysql)"
MYSQLDUMP="$(which mysqldump)"
CHOWN="$(which chown)"
CHMOD="$(which chmod)"
GZIP="$(which gzip)"

# Backup Dest directory,change this if you have some other location
 DEST="/backup"

#Main directory where backup will be stored
MBD="$DEST/mysql"

# Get hostname
HOST="$(hostname)"

# Get data in dd-mm-yyyy format

 NOW="$(date+"%d-%m-%y")"
 
# File to store current backup file
 FILE=""

#store list of databases
 DBS=""

# DO Not BACKUP these databases
IGGY="test"

[ ! -d $MBD ] && mkdir -p $MBD | | :

#Only root can access it!
$CHOWN 0.0 -R $DEST
$CHMOD 0600 $DEST

# Get all database list first

DBS="$(MYSQL -u $MyUSER -h $MyHOST -p$MyPASS -Bse 'show databases')"

for db in $DBS

do

    skipdb=-1
     if["$IGGY" != ""];
then
       for i in $IGGY
       do
           ["$db" =="$i] && skipdb=1 | | :
       done
fi

  if[ "skipdb" =="-1"] ; then
  FILE="$MBD/$db.$HOST.$NOW.gz"

    $MYSQLDUMP -u $MyUSER -h $MyHOST -p$MyPASS $db | $GZIP -9 > $FILE

fi
done

---

### Post by Hippytaff on 2010-11-08
> 
if["$IGGY" != ""];

 
do you need a space
```

if[ "$IGGY" != "" ];

```
and double brackets may work better
```

if [[ "$IGGY" != "" ]];

```
just a thought :-)

---


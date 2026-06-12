---
title: "mysql script from cron"
date: 2011-01-16
forum: General Help
---

### Post by afrazin on 2011-01-16
I'm trying to run a mysql script from a cron job.  Here's the relevant lines that get the error:
# Get all database list first
DBS="$($MYSQL -u$MyUSER -h$MyHOST -p$MyPASS -Bse 'show databases')"

# Get all tables list first
TBLAdmin="$($MYSQL -u$MyUSER -h$MyHOST -p$MyPASS -Dadmindb -Bse 'show tables')"

The error I'm getting is:
./mysql-production-backup.sh: line 59: -u: command not found

I don't know why -u would be giving me a problem.  Earlier in the script I defined the user.  I tried it with a space after -u and without and neither works.  Any suggestions?

Thanks!

---


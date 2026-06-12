---
title: "Permissions error with PostgreSQL psql process"
date: 2011-08-13
forum: General Help
---

### Post by gargoyle60 on 2011-08-13
Need help please!
 
I have installed PostgreSQL 9.0 in Ubuntu 11.04.

The following is a bit long-winded and cross-relates to PostgreSQL, but I'm sure others are using it on Ubuntu so might offer help.
 
I ran the PostgreSQL installation thus:
```
sudo su
./postgresql-9.0.4-1-linux.bin

```
accepting all the installer defaults except specifying the Data Directory
as "/home/gary/PostgreSQL/9.0/data/gjd_data/gjd_sentinel_data"
(NB. quotes shown here for emphasis only, not entered to the installer)
 
Beforehand I manually created a data directory structure to isolate my personal data files (as myself, not using sudo):
```
mkdir /home/gary/PostgreSQL/
mkdir /home/gary/PostgreSQL/9.0
mkdir /home/gary/PostgreSQL/9.0/data/
mkdir /home/gary/PostgreSQL/9.0/data/gjd_data
mkdir /home/gary/PostgreSQL/9.0/data/gjd_data/gjd_sentinel_data

```
 
I have a personal project database script file (copied from my Windows installation) that I know works perfectly under Windows. It has been modified for the correct paths/locations, etc. for Linux. When run this should create my entire project database, including loading sample data. This script file is called "Z_Build_DB_Linux.sql"
 
I am trying to run psql in batch mode as follows (long command, line wrapped here):
```
/opt/PostgreSQL/9.0/bin/psql --dbname postgres --host localhost --port 5432 --username postgres --file /home/gary/PostgreSQL/9.0/data/gjd_data/Z_Build_DB_Linux.sql --log-file /home/gary/PostgreSQL/9.0/data/gjd_data/Z_Build_DB_Linux.log --output /home/gary/PostgreSQL/9.0/data/gjd_data/Z_Build_DB_Linux_query_output.log --expanded

```
 
This is where I hit a wall! It doesn't matter if I run this as user "gary" or "root".
I have tried different combinations/variations, including having "chowned" directory "gjd_sentinel_data" to user postgres. Similarly with chgrp.
 
This is my environment (sorry, lines may wrap again):
```
root@GJDPC2:~$ export PGHOME=/opt/postgres/9.0
[EMAIL="root@GJDPC2:~$"]root@GJDPC2:~$[/EMAIL] export PGDATA=/home/gary/PostgreSQL/9.0/data/gjd_data
...snip...
[EMAIL="root@GJDPC2:/home/gary/PostgreSQL/9.0/data/gjd_data"]root@GJDPC2:/home/gary/PostgreSQL/9.0/data/gjd_data[/EMAIL]# ls -l
total 48
drwxrwxrwx 13 postgres postgres  4096 2011-08-12 15:21 gjd_sentinel_data
-rw-r--r--  1 root     root     10701 2011-08-12 16:46 Z_Build_DB_Linux.log
-rw-r--r--  1 root     root       231 2011-08-12 16:46 Z_Build_DB_Linux_query_output.log
-rwxr--r--  1 gary     gary     20808 2011-08-12 16:32 Z_Build_DB_Linux.sql*
[EMAIL="root@GJDPC2:/home/gary/PostgreSQL/9.0/data/gjd_data"]root@GJDPC2:/home/gary/PostgreSQL/9.0/data/gjd_data[/EMAIL]# /opt/PostgreSQL/9.0/
bin/psql --dbname postgres --host localhost --port 5432 --username postgres --file /home/gary/PostgreSQL/9.0/data/gjd_data/Z_Build_DB_Linux.sql --log-file /home/gary/PostgreSQL/9.0/data/gjd_data/Z_Build_DB_Linux.log --output /home/gary/PostgreSQL/9.0/data/gjd_data/Z_Build_DB_Linux_query_output.log --expanded
Password:
...
psql:/home/gary/PostgreSQL/9.0/data/gjd_data/Z_Build_DB_Linux.sql:48:
ERROR:  could not set permissions on directory "/home/gary/PostgreSQL/9.0/data/gjd_data/gjd_sentinel_data": Permission denied

```
 
For info the statement in the script that is causing the problem:
```
CREATE TABLESPACE sentinel_data OWNER sentinel
     LOCATION E'/home/gary/PostgreSQL/9.0/data/gjd_data/gjd_sentinel_data';

```
 
The problem, obviously, is the "Permission denied" error. What/where am I going wrong?
 
From my directory listing I can see that the permissions for gjd_sentinel_data are drwxrwxrwx with owner/group of postgres. On that basis I can't see why there is the problem.
I am wondering if it has something to do with the psql process running as, or owned by, user postgres? Or that I am running as the wrong user? Or something else beyond my experience?
---
Ubuntu 11.04 with GNOME2 classic desktop
Single user.
Dual boot with Windows XP Home

---

### Post by gargoyle60 on 2011-08-18
Solved.
For info: abandoned the previous approach in favour of...

```
sudo apt-add-repository ppa:pitti/postgresql
sudo apt-get update
sudo apt-get install postgresql-9.0
sudo apt-get install postgresql-client-9.0
sudo apt-get install postgresql-contrib-9.0
sudo apt-get install pgadmin3

```Now everything working.

---


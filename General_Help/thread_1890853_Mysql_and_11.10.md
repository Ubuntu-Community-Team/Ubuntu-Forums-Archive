---
title: "Mysql and 11.10"
date: 2011-12-04
forum: General Help
---

### Post by jacknet52 on 2011-12-04
I downloaded a dump from my host site and the file looks like a source file with all the commands for setting up the database and all the data. however when I try to run it in Mysql to put it on my localhost I get this:
 mysql> source /home/downloads/rustic.sql;
ERROR: 
Failed to open file '/home/downloads/rustic.sql', error: 2

Someone on another site suggested I drop the ; terminator but it didn't matter. I've tried various combinations to my home/download/file.sql and none work. I'm using Ubuntu 11.10 as localhost. 
Any suggestions please?
Thanks

---

### Post by The Cog on 2011-12-04
Firstly, I think you probably have the file path wrong - I would expect it to have your username in it, e.g. '/home/jacknet52/downloads/rustic.sql'.

Secondly, I think that the sql process might not have read access to your home directory anyway. In which case, you might have to copy the sql file to /tmp and tell mysql to source from /tmp/rustic.sql.

---

### Post by jacknet52 on 2011-12-05
thanks Cog: I think I got the path right this time, also spelled my filename right. /home/jacknet/Downloads/rusticdb.sql and I changed permissions to rwx for owner and user and ran:
mysql> source /home/jacknet/Downloads/rusticdb.sql; and got 
ERROR 1046 (3D000): No database selected
ERROR 1046 (3D000): No database selected
ERROR 1046 (3D000): No database selected
ERROR 1046 (3D000): No database selected
 The first line in the script file is "Create database 'xxxxxxxxx'"
So I'm still not sure it ran the .sql file or if it did why didn't it find a database when the first line says to create one?

---

### Post by The Cog on 2011-12-05
That sounds like a problem in the script to me. I would expect that after CREATE DATABASE XXX it would say USE DATABASE XXX. Or would refer to all tables as 'database.table' rather than just using the table name.

---

### Post by jacknet52 on 2011-12-06
Just to let you know Cog that I ran the Create Database 'database' command on the command line, ran Use database 'database' from the command line then commented them out and ran the rest of the dump.sql file and it populated the database ok. Thanks.

---


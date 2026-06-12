---
title: "Why does a wildcard work at the command line, but not in a .sh file?"
date: 2011-01-22
forum: General Help
---

### Post by Fynn on 2011-01-22
Hi, and thanks in advance for the help here :)

I have a dump of a database called **myDatabase_2011-01-22.sql.gz**.  (The numbers change as they represent the date).

If I run the following from the command line everything works fine and my database is loaded.

```
gunzip < myDatabase_*.sql.gz | mysql -u root -pPASSWORD myDatabase;
```

BUT...  I'm trying to put this into a .sh script to run as a cron job and receive the error:

```
getMyDatabases: 6: cannot open myDatabase_*.sql.gz: No such file
```

Any ideas?

---

### Post by tredegar on 2011-01-22
Please post the cronjob line and the script it is calling.

Hint: cron doesn't have a proper $PATH and you may need to specify /full/pathnames/to_executables

---

### Post by dcottingham on 2011-01-22
In addition to giving a full path to the executables, it also helps to give a full path to any data files. I'm guessing you got that error message because cron is not executing it in the directory you expected.

---

### Post by Fynn on 2011-01-22
Hi, thanks for the reply.  Here's my .sh file, I've tried changing the DB name from **mydatabase_*.sql.gz** to **mydatabase_2011-01-22.sql.gz** and that works.  (Not what I'm after though).

```

cd /home/myuser/mysql_backups/
mkdir `date '+%Y-%m-%d'`
scp backup@myserver.co.uk:mysql_backups/*.gz `date '+%Y-%m-%d'`/
chown myuser `date '+%Y-%m-%d'`/
cd `date '+%Y-%m-%d'`/
gunzip < mydatabase_*.sql.gz | mysql -u root -pMYPASSWORD mydatabase

```

---

### Post by ajgreeny on 2011-01-22
What about then first line of the .sh file?
```
#!/bin/bash
cd /home/myuser/mysql_backups/
mkdir `date '+%Y-%m-%d'`
scp backup@myserver.co.uk:mysql_backups/*.gz `date '+%Y-%m-%d'`/
chown myuser `date '+%Y-%m-%d'`/
cd `date '+%Y-%m-%d'`/
gunzip < mydatabase_*.sql.gz | mysql -u root -pMYPASSWORD mydatabase
```I agree about the other suggestions, as full paths are always needed in my experience in cron jobs.

---

### Post by Fynn on 2011-01-22
Thanks, I've added that first line.  No, it just doesn't seem to like it (even with explicit paths defined).

Strange.

It's easy enough to rename the file (using a wildcard) to something definite, and then perform the gunzip and load operation.

---

### Post by dcstar on 2011-01-22
Cron environments are different from user shell environments. If you want things to behave in similar manners then you may have to explicitly set various options:

[http://www.gnu.org/software/bash/manual/html_node/Filename-Expansion.html](http://www.gnu.org/software/bash/manual/html_node/Filename-Expansion.html)

---


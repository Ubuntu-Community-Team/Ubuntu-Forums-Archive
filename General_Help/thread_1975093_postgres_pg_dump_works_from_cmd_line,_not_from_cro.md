---
title: "postgres pg_dump works from cmd line, not from crontab"
date: 2012-05-06
forum: General Help
---

### Post by robinnelu on 2012-05-06
I am trying to do auto backups of postgresql database using pg_dump, but this command only works from command line, not in crontab. Here is the command:

**command line (works):**
/usr/bin/sudo -u postgres /usr/bin/pg_dump dbasename > /root/dbasebak.sql

in crontab I'm setting it every 5 minutes just for testing:

**crontab (does not work):**
*/5 * * * * /usr/bin/sudo -u postgres /usr/bin/pg_dump dbasename > /root/dbasebak.sql

**The error in syslog is:**
Error: bad username; while reading /etc/crontab

If it is related, I do have local postgres ident = trust in pg_hba.conf, like this:
local   all         postgres                          trust


thanks.

---

### Post by SeijiSensei on 2012-05-07
Whose crontab did you put this in?

If you want to have it be run by the postgres user, the easiest solution is to put the entry in /etc/crontab like this:

```
*/5 * * * * postgres /usr/bin/pg_dump dbasename > /root/dbasebak.sql
```

In /etc/crontab, the username under which the job is run appears immediately after the stars. You could alternatively create a crontab for the postgres user by using

```

sudo su postgres
crontab -e

```

but I don't see much value to that approach unless you expect to be setting up a number of cron jobs for the postgres user to execute.  If you do choose this method, you'd use the same job definition as above but omit the username "postgres".

I also prefer to use pg_dumpall so all the databases get backed up with a single command.

Backing up the database every five minutes seems a bit excessive unless you have a really high-traffic system or have a very unstable machine or power situation. (If the latter, get a UPS.)  PostgreSQL is a very stable daemon; I can't recall the last time I saw one fall over under normal loads, and I've used Postgres pretty much exclusively for years now.  I run nightly backups myself.

You don't want to use sudo in an unattended setting, unless you've set up sudo permissions to not require a password.  Otherwise running sudo in a cron job will cause it to hang waiting for the password to be typed.  If you want to enable the root user to run a command as another user, you can use "su -c 'command' username", but it's a lot easier just assigning the command to the correct user in crontab.

---

### Post by robinnelu on 2012-05-07
I am logged in as root and the crontab is /etc/crontab.

I have changed the cron command to:

*/5 * * * * postgres /usr/bin/pg_dump dbasename > /root/dbasebak.sql

Still not working. Syslog shows that it ran:

May  7 12:55:01 PostgresqlDBServer CRON[23525]: (postgres) CMD (/usr/bin/pg_dump dbasename > /root/dbasebak.sql)

but no backup file. How can postgres write to /root, is this maybe a permission error?

---

### Post by albandy on 2012-05-07
Postgres should not write to root I recomend you to create a new folder in /root and add the correct permissions:

sudo mkdir /root/db
sudo chown root.postgres /root/db
sudo chmod 770 /root/db

and then modify crontab:

*/5 * * * * postgres /usr/bin/pg_dump dbasename > /root/db/dbasebak.sql

---

### Post by robinnelu on 2012-05-07
thank you, that is now working. One more question, what is the syntax for adding the current date to the filename. I have found examples but I don't seem to be getting it right.

---

### Post by SeijiSensei on 2012-05-08
You can create a date string with the bash command date.  For instance, the bash construct "$(date +%Y%M%d)" returns a strong like "20120508".  However I don't know if you can just put this in crontab entry or not.  Give this a try and see if it works for you:

```
*/5 * * * * postgres /usr/bin/pg_dump dbasename > /root/dbasebak-$(date +%Y%m%d).sql
```

An easier solution might be to add an configuration file to /etc/logrotate.d/ and let the logrotate program handle the task for you.  By default it now uses the "-YYYYMMDD" format on the files it backs up.  To use logrotate, create a file in an editor as root with sudo called /etc/logrotate.d/pgbackup and enter this:

```

/root/db/dbasebak.sql {
     daily
     rotate 30
}

```

Now each day's backup will be renamed to dbasebak.sql-YYYYMMDD and kept for thirty days.

---

### Post by robinnelu on 2012-05-15
thank you. I tried this and it did not work.

0 1 * * * postgres /usr/bin/pg_dump productiondatabase > /root/dbbaks/prod_database_fullbackup$(date +%d).sql

it left blank in filename where date should go. That's ok, one day of backup is fine, I don't need a date.

---

### Post by albandy on 2012-05-16
> **robinnelu said:**
> thank you. I tried this and it did not work.

0 1 * * * postgres /usr/bin/pg_dump productiondatabase > /root/dbbaks/prod_database_fullbackup$(date +%d).sql

it left blank in filename where date should go. That's ok, one day of backup is fine, I don't need a date.

It will be easier using an script:

create a file called pgbackup in /usr/local/sbin :

sudo gedit /usr/local/sbin/pgbackup

and add the following contents:
```

#! /bin/bash
TODAY=$(date +%d)  #if you want full date change to this: TODAY=$(date +%Y%m%d)
OUTPUT="/root/dbbaks/prod_database_fullbackup_$TODAY.sql"
/usr/bin/pg_dump productiondatabase > $OUTPUT

```

then add execute permision:
sudo chmod 755 /usr/local/sbin/pgbackup

and modify crontab:

0 1 * * * postgres /usr/local/sbin/pgbackup

---


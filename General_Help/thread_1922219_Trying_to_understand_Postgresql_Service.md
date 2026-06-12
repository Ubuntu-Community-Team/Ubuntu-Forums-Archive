---
title: "Trying to understand Postgresql Service"
date: 2012-02-08
forum: General Help
---

### Post by ratcheer on 2012-02-08
I am having trouble understanding exactly how to manage the service postgresql.

When I want to start my user database, I always have to terminate the root server, first. I do this by "sudo service postgresql stop". Then I su to my user account and run "pg_ctl <my_db_name>". If I do not terminate the root server first, this will fail. But, it works the way I do it.

So, I decided to eliminate the need to terminate the root server by not starting it in the first place. I went through all the /etc/init.d/rc?.d directories, renaming Snnpostgresql to Knnpostgresql. When I rebooted, the root service did not come up. However, when I then tried to start my user server, it failed. I put the K links back to their S names, rebooted, and everything was working, as before.

So, why is it that I can kill the root service and start the user database, but if I do not allow the root service to start, the user database will not start?

Thank you,
Tim

---

### Post by drdos2006 on 2012-02-08
I see you are running 11.10. It sounds like PostgreSQL did not install properly or that something has changed between 10.04 LTS and 11.10.

Have you tried an earlier distro, have you backed up the database, purged PostgreSQL and re-installed ?

regards

---

### Post by SeijiSensei on 2012-02-08
I've used PostgreSQL for over a dozen years and have never encountered the problems you describe.
> **ratcheer said:**
> I am having trouble understanding exactly how to manage the service postgresql.  When I want to start my user database, I always have to terminate the root server, first.

There should be just one instance of the PG daemon running.  It will start as root, but then it will become the "postgres" user.  That user owns the entire database system in /var/lib.  There's never a need to run a separate instance of PG for each individual user.  All the user-specific management services are provided in the one daemon listening on port 5432.

If you want to create a database for an existing Unix user (e.g, "harry" below), then you need only do this:

```
sudo su
su postgres
createuser harry
[answer questions]
exit

```

When finished, harry should be able to run the command "createdb harry" (assuming you answered the question about whether harry can create databases in the affirmative).  Now user harry should be able to run the command "psql harry" from the prompt and see an empty database awaiting tables, etc. Harry can, in fact, create and own a multitude of databases with different names.

If you try to connect to the database remotely (e.g., "psql -U harry -h someserver harry") you'll probably get a connection refused.  By default, only local users can connect via localhost, and only then if the user's name matches. Take a look at pg_hba.conf for more details.

---

### Post by ratcheer on 2012-02-08
Thanks for your advice. But the user account I am using is postgres. It ***cannot*** start a database while the root server is running.

I can reboot and come back to show exactly what happens.

Tim

---

### Post by ratcheer on 2012-02-08
Ok, I rebooted and went through the sequence. Everything here was done immediately after rebooting, even before starting this web browser.

```
tim@tim-oneiric:~$ su - postgres
Password: 
postgres@tim-oneiric:~$ pg_ctl start
server starting
postgres@tim-oneiric:~$ LOG:  could not bind IPv4 socket: Address already in use
HINT:  Is another postmaster already running on port 5432? If not, wait a few seconds and retry.
WARNING:  could not create listen socket for "localhost"
FATAL:  could not create any TCP/IP sockets

postgres@tim-oneiric:~$ logout
tim@tim-oneiric:~$ ps -ef|grep postgres
postgres  1114     1  0 17:12 ?        00:00:00 /usr/lib/postgresql/9.1/bin/postgres -D /var/lib/postgresql/9.1/main -c config_file=/etc/postgresql/9.1/main/postgresql.conf
postgres  1137  1114  0 17:12 ?        00:00:00 postgres: writer process                                                                                                    
postgres  1138  1114  0 17:12 ?        00:00:00 postgres: wal writer process                                                                                                
postgres  1139  1114  0 17:12 ?        00:00:00 postgres: autovacuum launcher process                                                                                       
postgres  1140  1114  0 17:12 ?        00:00:00 postgres: stats collector process                                                                                           
tim       1986  1795  0 17:13 pts/0    00:00:00 grep --color=auto postgres
tim@tim-oneiric:~$ sudo service postgresql stop
[sudo] password for tim: 
 * Stopping PostgreSQL 9.1 database server                                                                                    [ OK ] 
tim@tim-oneiric:~$ su - postgres
Password: 
postgres@tim-oneiric:~$ pg_ctl start
server starting
postgres@tim-oneiric:~$ LOG:  database system was shut down at 2012-02-08 14:35:14 CST
LOG:  database system is ready to accept connections
LOG:  autovacuum launcher started

postgres@tim-oneiric:~$ 
```Maybe I am doing something wrong, but I have no idea what it could be.

Tim

---

### Post by SeijiSensei on 2012-02-09
You're trying to start another instance of the server daemon when it's already running.  Why are you doing that?

As I said, there should be only one running instance.  If you want to create multiple users or databases you need to use the "createuser" and "createdb" commands from the command prompt.  You need to run createuser as the postgres user, but any user that you create can run createdb if you give that user permission to create databases during the createuser dialog.

---

### Post by ratcheer on 2012-02-09
Thank you, again. But I still seem to be missing something.

First, the main PostgreSQL documentation specifies that the database should not be started by root. It tells you how to wrap the database start command in "su -c" systax so it can be started by the postgres user at bootup. But, the way it got installed on my system, it seems to be being started by root. And I have looked through all the init scripts and cannot find where to make this change.

If I run psql as user postgres, then do \l, it lists the system tables but not postgresql's tables. If I stop the root instance and start postgres's instance, postgres can access everything.

The way I want things to be is exactly the way I ran Oracle as a DBA for 14 years. The UNIX administrator would always install and start things as root, and I always redid them completely to be started by user oracle.

I am apparently still missing something here. If I could use the server that is started by init at bootup, it would be ok, but since I cannot access postgres's user tables, it does not work for me. This, coupled with the fact that the documentation even says not to let the server be started by root.

Again, thank you for your help.

Tim

---

### Post by SeijiSensei on 2012-02-09
> **ratcheer said:**
> Thank you, again. But I still seem to be missing something.

The postgresql service is managed by the "service" command, "sudo service postgresql start".  That will launch an instance of the server running as the postgres user.  If you want to talk to the database as that user use "su postgres" then psql.

You should never need to start the service with the pg_ctl command.  All that is required is handled by the script in /etc/init.d that is run by the service command.  Also when you install postgresql from the Ubuntu repositories, it will be configured to start the postgresql service on each reboot.

> If I run psql as user postgres, then do \l, it lists the system tables but not postgresql's tables. If I stop the root instance and start postgres's instance, postgres can access everything.

The postgres user doesn't have any tables by default, so I'm not sure what you're looking for.  In most cases the only role the postgres user serves is to manage the overall instance.  All the actual databases should be owned by individual users as I've described twice now.  Create one or more users with createuser, use 'createdb -U username dbname' to make an empty database, then connect to the database as that user and fill it with tables, etc., using whatever method you choose (including ODBC).

Other than creating new users, it's very rare to do anything in PG as the postgres user.

I had only a brief unpleasant experience with connecting to Oracle from a PHP application so I can't compare the two.  MySQL works similarly to PostgreSQL though it has a more convoluted method of creating new users and databases.  Still doesn't Oracle support multiple users and multiple databases within a single server instance, too?

---

### Post by ratcheer on 2012-02-09
Ok, here is what might be going on. I "over" read the documentation and created a new, extra database instance as user postgres. It is a separate instance from the default one created when I installed PostgreSQL. I must have just assumed that the default instance is owned by root and thought I needed one created by postgres.

I will see what I can do about migrating the tables and views in my "extra" instance to the default instance.

In Oracle, I could have several database instances running on the same machine at the same time. PostgreSQL is obviously a little different. I need to get used to the differences.

Thank you for patiently helping me with my questions.

Tim

---

### Post by SeijiSensei on 2012-02-10
You can run separate instances of the server daemon as long as each one listens on a different TCP port.  I've done that sometimes when I've built a more recent version of the server from source for testing.  You assign the port in postgresql.conf and, in this case, start the server with pg_ctl.  (I usually put this command in /etc/rc.local.)  

You then need to use "psql -U user -h host *-p port* dbname" to connect to the other instance (or change the value of the PGDATA environment variable which is usually more work than using "-p").

Migration is pretty simple if you use the pg_dump command.  It will create a plain-text file with the commands needed to recreate the database using psql.  Something like this:

```

sudo su
su postgres
pg_dump -p 5432 mydb > mydb.sql
createdb -p 54321 mynewdb
psql -p 54321 mynewdb < mydb.sql

```

That assumes I'm running the new instance on port 54321 instead of the default port 5432, and that user postgres owns mydb and will own mynewdb.  You can obviously create mynewdb as a different user from postgres as well.  You'd need to exit from the postgres shell and su into the new user before running the createdb and psql commands.

If you want to back up an entire instance, run the command pg_dumpall as the postgres user instead of pg_dump.  For details, see their man pages.  I run a script with cron each night that uses pg_dumpall to create daily backups with date-stamped filenames.

---

### Post by ratcheer on 2012-02-10
Again, thank you very much, @SeijiSensei

Tim

---

### Post by ratcheer on 2012-02-11
[http://forums.postgresql.com.au/viewtopic.php?f=36&t=5858](http://forums.postgresql.com.au/viewtopic.php?f=36&t=5858)

I thought the info in that link would help me straighten things out.

Tim

---

### Post by ratcheer on 2012-02-12
Ok, I believe I am pretty much where I want to be with all this. Sort of. The new thing I learned is that Debian/Ubuntu provide what seem to be additional facilities outside or beyond vanilla PostgreSQL. They provide something called clusters.

So I ran pg_createcluster to create something new on my /home filesystem. It is not exactly a database, but it seems to contain something like a database. So, I now have two clusters, one named main in the /var directory and another one under /home. I was able to export all my data from my database I had outside this structure and import it into my new cluster.

I can start and stop the two clusters, independently. I specify which cluster I connect to by specifying the port.

I still don't understand all the implications of this.

Tim

---


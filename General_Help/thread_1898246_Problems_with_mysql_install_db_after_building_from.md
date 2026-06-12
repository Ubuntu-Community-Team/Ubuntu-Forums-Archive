---
title: "Problems with mysql_install_db after building from source."
date: 2011-12-20
forum: General Help
---

### Post by TheCommander on 2011-12-20
I've installed PHP and Apache from source and now I've moved onto installing MySQL from source.

**Note: I had installed MySQL from apt-get but then I removed it via 'apt-get autoremove mysql-server'**

I downloaded the tar.gz, unpacked, then did the following:

```
cmake .
make
sudo make install DESTDIR="/usr/local/mysql"
```

It appears to have installed correctly.

I've created the user and group 'mysql' and moved ownership of everything inside /usr/local/mysql to mysql.

So next I try to run mysql_install_db like so:

```
sudo /usr/local/mysql/scripts/mysql_install_db --user=mysql --basedir=/usr/local/mysql
```

I get the following error: 
```
Installing MySQL system tables...

Installation of system tables failed!  Examine the logs in
/var/lib/mysql for more information.

You can try to start the mysqld daemon with:

    shell> /usr/local/mysql/bin/mysqld --skip-grant &

and use the command line tool /usr/local/mysql/bin/mysql
to connect to the mysql database and look at the grant tables:

    shell> /usr/local/mysql/bin/mysql -u root mysql
    mysql> show tables

Try 'mysqld --help' if you have problems with paths.  Using --log
gives you a log in /var/lib/mysql that may be helpful.

Please consult the MySQL manual section
'Problems running mysql_install_db', and the manual section that
describes problems on your OS.  Another information source are the
MySQL email archives available at http://lists.mysql.com/.

Please check all of the above before mailing us!  And remember, if
you do mail us, you MUST use the /usr/local/mysql/scripts/mysqlbug script!
```


The contents of /var/log/mysql/error.log shows:
```
111221  4:34:59 [ERROR] Incorrect definition of table mysql.proc: expected column 'comment' at position 15 to have$
ERROR: 1136  Column count doesn't match value count at row 1
111221  4:35:00 [ERROR] Aborting

111221  4:35:00 [Note] /usr/local/mysql/bin/mysqld: Shutdown complete
```

I've tried doing what the error message says to do but nothing seems to complete, I just get other errors!

Anyway, I'm completely stumped, my best guess is that it's something to do with me installing MySQL through the package manager first and when I removed it it didn't remove some of the old data.

Has anyone experienced this before, could do with a point in the right direction! Many thanks

EDIT: And apologies if this is in the wrong forum, I'm unfamiliar with the Ubuntu forums :(

---

### Post by TheCommander on 2011-12-21
So I fixed my problem (within minutes of making a thread after being stuck on it for a few days, typical). Posting the solution incase this comes up on Google for someone with a similar problem.

I believe my old install was an older version from apt-get so the installed database structure was incorrect. 

I deleted the folder /var/lib/mysql, did a reinstall (just to make sure) and then ran mysql_install_db and it seems to have worked.

I did have some strange issues on reinstalling though, instead of going into /usr/local/mysql it was going into /usr/local/mysql/usr/local/mysql/

I ended up running the sudo make install without the DESTDIR command in the end (defaults to /usr/local/mysql anyway).

---


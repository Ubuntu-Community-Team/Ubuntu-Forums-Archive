---
title: "MediaTomb"
date: 2010-03-12
forum: General Help
---

### Post by jessy722 on 2010-03-12
Hey,
Trying to build the mysql database manually for my mediatomb server,
I just need some pointing in the right direction as far as what my tables should include for the database.

I'm also receiving an error when I try and start mediatomb, mysql_error 1045 access denied for user 'root'@'localhost' the user i created is judmedia
the database judmediatomb and gave the user all permissions.
The judmedia user aswell has no password attached because i thought that was the issue since the mediatomb config doesn't ask for the mysql user password
here is my mediatomb config file:

<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchem$
  <!--
     Read /usr/share/doc/mediatomb-common/README.gz section 6 for more
     information on creating and using config.xml configration files.
    -->
  <server>
    <ui enabled="yes" show-tooltips="yes">
      <accounts enabled="yes" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>Judmedia's MediaTomb</name>
    <udn>uuid:6f0e2103-c925-4c8d-9623-7f4df69c2855</udn>
    <home>/var/lib/mediatomb</home>
    <webroot>/usr/share/mediatomb/web</webroot>
    <storage>
      <sqlite3 enabled="no">
        <database-file>mediatomb.db</database-file>
      </sqlite3>
      <mysql enabled="yes">
        <host>localhost</host>
        <username>judmedia</username>
        <database>judmediatomb</database>
      </mysql>



Thanks in advance!

---

### Post by tgalati4 on 2010-03-12
By default mediatomb uses sqlite3, which is what I am running, so I can't really help.

I presume you have installed phpmyadmin:

sudo apt-get install phpmyadmin

I find it helpful to browse the database, settings and permissions when I'm having mysql problems.

I presume that mysqld is running?

tgalati4@washme:~$ ps -ef | grep mysql
tgalati4  1436  1419  0 15:42 pts/0    00:00:00 grep mysql
root      4329     1  0 Jan04 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     4371  4329  0 Jan04 ?        03:42:13 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      4373  4329  0 Jan04 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld

If not, then:

sudo /etc/init.d/mysql restart

According to:

man mediatomb

You can run it in a terminal, in the foreground, and messages will go to the console. You can also give it a logfile switch so it will dump its randomness to a logfile.  That might be helpful.

cat /var/log/mediatomb.log

Of course, it could be a bug in mediatomb or lack of documentation for how the mysql user and password is to be specified.

---

### Post by jessy722 on 2010-03-12
Thanks for the tip!
installed phpadmin which wouldn't allow me to log in with judmedia because it won't allow accounts to have no passwords but noticed I was able to still log through the terminal the mysql way. Then I opened up phpmyadmin under root, added the only check box that wasn't unchecked for judmedia to the database and boom she works.

though now it seems to be hanging here(web ui accessible while hanging) :




[EMAIL="judmedia@judmedia:%7E/.mediat"]judmedia@judmedia:~/.mediat[/EMAIL]omb$ mediatomb

MediaTomb UPnP Server version 0.12.0 - [http://mediatomb.cc/](http://mediatomb.cc/)

===============================================================================
Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2010-03-12 23:31:51    INFO: Loading configuration from: /home/judmedia/.mediatomb/config.xml
2010-03-12 23:31:51    INFO: Checking configuration...
2010-03-12 23:31:51    INFO: Setting filesystem import charset to UTF-8
2010-03-12 23:31:51    INFO: Setting metadata import charset to UTF-8
2010-03-12 23:31:51    INFO: Setting playlist charset to UTF-8
2010-03-12 23:31:51    INFO: Configuration check succeeded.
2010-03-12 23:31:51    INFO: database doesn't seem to exist. automatically creating database...
2010-03-12 23:31:51    INFO: database created successfully.
2010-03-12 23:31:51    INFO: Initialized port: 49152
2010-03-12 23:31:51    INFO: Server bound to: 192.168.2.20
2010-03-12 23:31:52    INFO: MediaTomb Web UI can be reached by following this link:
2010-03-12 23:31:52    INFO: [http://192.168.2.20:49152/](http://192.168.2.20:49152/)
2010-03-12 23:32:21    INFO: thread cleanup; thread_id=-1251435664



Would this be because I didn't create any tables in the database? Or if I  scan with the web ui will it create the database tables for me? I don't   mind manually creating the tables.(its for a class anyway)

I left this going while I typed this post added a few more thread cleanups will they end any thoughts?


2010-03-12 23:36:41    INFO: thread cleanup; thread_id=-1251435664
2010-03-12 23:36:45    INFO: thread cleanup; thread_id=-1259828368
2010-03-12 23:36:46    INFO: thread cleanup; thread_id=-1303921808
2010-03-12 23:38:51    INFO: thread cleanup; thread_id=-1303921808
2010-03-12 23:39:06    INFO: thread cleanup; thread_id=-1243042960
2010-03-12 23:39:06    INFO: thread cleanup; thread_id=-1287128208

---

### Post by tgalati4 on 2010-03-13
Realize that when your database is first created, mediatomb has to scan your collection of media files.  This is a background process and it could take a while.  That's my guess as to where the thread cleanups are coming from.

Let it run for a while then try to access it later.

---


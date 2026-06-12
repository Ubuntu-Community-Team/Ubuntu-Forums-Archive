---
title: "Can't connect to mysql (socket file vanishing act)"
date: 2010-03-30
forum: General Help
---

### Post by ffrr on 2010-03-30
Hi,

I posted the following on "Networking and Wireless" and received no response. I suppose that was the wrong group. So here I try again on "General Help":

**Can't connect to mysql (socket file vanishing act)**             
[LEFT]
Hi all,
[/LEFT]
 
Here's what I get when trying to connect to mysql:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Sure enough the file has disappeared over night. Yesterday it was still there and everything was working fine. About one hour of scouring archives I came upon an excellent piece of advice by one Ack99 who recommended (about four years ago) to 'simply' recreate the file, stating that it worked for him. He doesn't say how one simply recreates the file. I'm dying to know.

Thanks for suggestions

Frederic

---

### Post by rudy.b on 2010-03-31
Hi Frederic,

It sounds to me like your mysql server is not running, the socket file disappears when the server stops.  Try starting your server and it should be ok for you to connect.  

The larger question is:  why did the server go down?  If you didn't shut it down yourself, it may have gone down under an error condition.  You may want to check your mysql log to see if you can find anything suspicious.

---

### Post by nemilar on 2010-03-31
Definitely take a look at your mysql error logs (in /var/log) to see if there is a clue about what happened.

---

### Post by ffrr on 2010-03-31
rudy.b, nemilar, thank you both for your help.

The server isn't running is exactly right. If I try to start it with the command "mysqld" the "Can't connect..." error occurs. 

There's nothing in the logs I could make out. They are empty:

root@hatchbox-one:/home/fr# ls -l /var/log | grep mysql
drwxr-s--- 2 mysql             adm       4096 2010-02-28 21:07 mysql
-rw-r----- 1 mysql             adm          0 2010-03-15 09:02 mysql.err
-rw-r----- 1 mysql             adm          0 2010-03-31 08:28 mysql.log
-rw-r----- 1 mysql             adm         20 2010-03-30 08:49 mysql.log.1.gz
-rw-r----- 1 mysql             adm         20 2010-03-29 08:37 mysql.log.2.gz
root@hatchbox-one:/home/fr# ls -l /var/log/mysql
total 0
root@hatchbox-one:/home/fr# 

Frederic

---

### Post by ffrr on 2010-03-31
Here I'm again with more details: 

root@hatchbox-one:/home/fr# mysqld
100331  9:24:07 [Note] Plugin 'FEDERATED' is disabled.
mysqld: Can't find file: 'plugin' (errno: 2)
100331  9:24:07 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
100331  9:24:07  InnoDB: Started; log sequence number 0 44243
100331  9:24:07 [ERROR] Fatal error: Can't open and lock privilege tables: Can't find file: 'host' (errno: 2)

root@hatchbox-one:/home/fr# mysql_upgrade
Looking for 'mysql' as: mysql
Looking for 'mysqlcheck' as: mysqlcheck
Running 'mysqlcheck' with connection arguments: '--port=3306' '--socket=/var/run/mysqld/mysqld.sock' 
mysqlcheck: Got error: 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) when trying to connect
FATAL ERROR: Upgrade failed
root@hatchbox-one:/home/fr#

Frederic

---

### Post by rudy.b on 2010-04-03
You'll have to repair your host table.  To do this, issue the following command to start your server bypassing the privilege system:
```
$ sudo mysqld --skip-grant-tables
```Then, open another terminal and do the following to repair the host table:
```
$ mysql
mysql> use mysql
mysql> repair table host use_frm;
mysql> exit

```Now try restarting your server.

---

### Post by ffrr on 2010-04-03
Thank you very much for your advice. I walked through the steps you recommend. They didn't fix the problem directly but generated error messages that got me on the right track. With some embarrassment I admit that all *.MY? files are gone from /var/lib/mysql/mysql. It must have been a malformed command line attempt of the one-line-does-it-all kind that blew the files away. Migrating a Windows system to Linux takes some doing straightening out the upper-lower-case mess. So, I'll just reinstall MySQ.

Thanks again.

Frederic

(I'll remember the --skip-grant-tables trick. It might come in handy some other time!)

---

### Post by rudy.b on 2010-04-03
Cool, glad you were able to identify your problem. O:)

---

### Post by ffrr on 2010-04-04
My embarrassment grows in proportion to my display of ignorance. The optimism I expressed in my last post was premature, I'm afraid. I thought reinstalling mysql would restore the missing files. Either it doesn't or I am looking in the wrong place. I reinstalled these six packages:

libmysqlclient15off
   Status: install ok installed
   Version: 5.1.30really5.0.83-0ubuntu3
   Depends: mysql-common (>= 5.1.30really5.0.83-0ubuntu3), libc6 (>= 2.4), zlib1g (>= 1:1.1.4)

mysql-server-core-5.1
   Status: install ok installed
   Version: 5.1.37-1ubuntu5.1
   Provides: mysql-server-core
   Depends: libc6 (>= 2.7), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.1.1), libwrap0 (>= 7.6-4~), zlib1g (>= 1:1.1.4), libmysqlclient16 (>= 5.1.37-1ubuntu5.1)

mysql-server-5.1
   Status: install ok half-configured
   Version: 5.1.37-1ubuntu5.1
   Provides: mysql-server, virtual-mysql-server
   Depends: mysql-client-5.1 (>= 5.1.37-1ubuntu5.1), libdbi-perl, perl (>= 5.6), libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libmysqlclient16 (>= 5.1.21-1), libstdc++6 (>= 4.1.1), zlib1g (>= 1:1.1.4), debconf (>= 0.5) | debconf-2.0, psmisc, passwd, lsb-base (>= 3.0-10), mysql-server-core-5.1 (>= 5.1.37-1ubuntu5.1)

mysql-common
   Status: install ok installed
   Version: 5.1.37-1ubuntu5.1
   Provides: mysql-common-4.1

mysql-client-5.1
   Status: install ok installed
   Version: 5.1.37-1ubuntu5.1
   Provides: mysql-client, mysql-client-4.1, virtual-mysql-client
   Depends: debianutils (>= 1.6), libdbi-perl, libdbd-mysql-perl (>= 1.2202), mysql-common (>= 5.1.37-1ubuntu5.1), libmysqlclient16 (>= 5.1.37-1ubuntu5.1), perl, libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libncurses5 (>= 5.6+20071006-3), libstdc++6 (>= 4.1.1), libwrap0 (>= 7.6-4~), zlib1g (>= 1:1.1.4)

libmysqlclient16
   Status: install ok installed
   Version: 5.1.37-1ubuntu5.1
   Depends: mysql-common (>= 5.1.37-1ubuntu5.1), libc6 (>= 2.4), zlib1g (>= 1:1.1.4)

Each install ended with closing the mysql server and failing to restart it. Sure enough, none had restored the missing files. (/var/lib/mysql/mysql/*.MY?)

Next I scanned all my *.deb files with dpkg-deb -c for file names ending with .MYD or .MYI and found none. Where the hell did they have come from in the first place I wonder. Ideas are definitely most welcome as I have seriously exhausted my own.

Puzzled and stunned

Frederic

---

### Post by ffrr on 2010-04-07
I found a solution in the MySQL's on-line documentation. ([http://dev.mysql.com/doc/refman/5.1/en/installing-binary.html](http://dev.mysql.com/doc/refman/5.1/en/installing-binary.html)). It is a very extensive, very detailed and intelligible manual that explains, step by step, how to select, download and manually install a binary edition.

First I removed the mysql-server-5.1 and all its dependencies (apt-get autoremove mysql-server-5.1) Then I followed the MySQL doc. The server started right away. Setting up accounts required reinstalling mysql-client-5.1 with apt-get. It had apparently been autoremoved as a dependency of the server package.

This closes the thread with many thanks to my helpers.

Frederic

---


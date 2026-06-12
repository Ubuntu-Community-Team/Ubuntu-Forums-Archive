---
title: "Can't connect to my sql server"
date: 2010-05-24
forum: General Help
---

### Post by alexlesuper on 2010-05-24
I'm trying to install a mysql server in my 9.10 linux server, but once I download the packages and install them it's supposed to ask me for a password to authenticate into the server, but it doesn't do that and just continues installing.

Once its finished installing I try to access it but it gives me an error message.

Here's what I did to install it:


> alex@alex-server:~$ sudo apt-get install mysql-server
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libdbi-perl libhtml-template-perl libnet-daemon-perl libplrpc-perl mysql-client-5.1 mysql-server-5.1 mysql-server-core-5.1
Suggested packages:
  dbishell libipc-sharedcache-perl tinyca
The following NEW packages will be installed:
  libdbd-mysql-perl libdbi-perl libhtml-template-perl libnet-daemon-perl libplrpc-perl mysql-client-5.1 mysql-server mysql-server-5.1 mysql-server-core-5.1
0 upgraded, 9 newly installed, 0 to remove and 87 not upgraded.
Need to get 20.3MB/20.4MB of archives.
After this operation, 48.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libnet-daemon-perl 0.43-1 [46.9kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libplrpc-perl 0.2020-2 [36.0kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libdbi-perl 1.609-1 [800kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libdbd-mysql-perl 4.011-1ubuntu1 [136kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main mysql-client-5.1 5.1.37-1ubuntu5.1 [8,202kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main mysql-server-core-5.1 5.1.37-1ubuntu5.1 [3,839kB]                                                                          
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main mysql-server-5.1 5.1.37-1ubuntu5.1 [7,186kB]                                                                               
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libhtml-template-perl 2.9-1 [65.8kB]                                                                                               
Fetched 20.3MB in 1min 25s (238kB/s)                                                                                                                                              
Preconfiguring packages ...
Selecting previously deselected package libnet-daemon-perl.
(Reading database ... 145649 files and directories currently installed.)
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.43-1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2020-2_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.609-1_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.011-1ubuntu1_i386.deb) ...
Selecting previously deselected package mysql-client-5.1.
Unpacking mysql-client-5.1 (from .../mysql-client-5.1_5.1.37-1ubuntu5.1_i386.deb) ...
Selecting previously deselected package mysql-server-core-5.1.
Unpacking mysql-server-core-5.1 (from .../mysql-server-core-5.1_5.1.37-1ubuntu5.1_i386.deb) ...
Selecting previously deselected package mysql-server-5.1.
Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.37-1ubuntu5.1_i386.deb) ...
 * Stopping MySQL database server mysqld
   ...done.
Selecting previously deselected package libhtml-template-perl.
Unpacking libhtml-template-perl (from .../libhtml-template-perl_2.9-1_all.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.1.37-1ubuntu5.1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up libnet-daemon-perl (0.43-1) ...
Setting up libplrpc-perl (0.2020-2) ...
Setting up libdbi-perl (1.609-1) ...
Setting up libdbd-mysql-perl (4.011-1ubuntu1) ...
Setting up mysql-client-5.1 (5.1.37-1ubuntu5.1) ...

Setting up mysql-server-core-5.1 (5.1.37-1ubuntu5.1) ...
Setting up mysql-server-5.1 (5.1.37-1ubuntu5.1) ...
 * Stopping MySQL database server mysqld
   ...done.
 * Starting MySQL database server mysqld
   ...done.
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

Setting up libhtml-template-perl (2.9-1) ...
Setting up mysql-server (5.1.37-1ubuntu5.1) ...
alex@alex-server:~$ clear

alex@alex-server:~$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld
   ...done.
alex@alex-server:~$ mysql -u alex -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'alex'@'localhost' (using password: YES)

If I try to simply access without a password using just 'mysql', I get the following error:


> alex@alex-server:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I've been looking in the forums on how to solve this for a while but I can't find anything relevant. Can anyone help?

---

### Post by alexlesuper on 2010-05-24
bump

---

### Post by SlidingHorn on 2010-05-24
Please give it some time before bumping a thread.  It's usually recommended to wait about 24 hours.

There's a lot of posts to get to, and someone will assist you as soon as they can

---

### Post by Ahadiel on 2010-05-24
Try:
```
sudo dpkg-reconfigure mysql-server
```

Also IIRC, MySQL users are different than regular users. The above command should prompt you to set a MySQL root password, and then from there you can create the appropriate user accounts.

---

### Post by alexlesuper on 2010-05-25
> alex@alex-server:~$ sudo dpkg-reconfigure mysql-server
[sudo] password for alex: 
alex@alex-server:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I still can't access the server. I can't find the solution to this problem online.

---

### Post by WorMzy on 2010-05-25
Try looking at this webpage: [https://help.ubuntu.com/community/MysqlPasswordReset]("https://help.ubuntu.com/community/MysqlPasswordReset"), it might help.

In particular, this part:

> ```
mysqladmin -u root password your-new-password
sudo /etc/init.d/mysql restart
```

```
mysql -u root -p
```

You should now be logged in as root. Make sure to notedown your password! Thanks to Illuvator for posting this method in the ubuntu forum.

---

### Post by alexlesuper on 2010-05-27
I don't think the password is the problem. I think, rather, that the SQL is not installed correctly. I keep running into this error in particular:


> alex@alex-server:~$ mysqladmin -u root password abcpass
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

Anyone had this error before?

---

### Post by threepwood960 on 2011-02-01
Please, was it solved? I am with this problem from yesterday. Thanks,

Iam.

---

### Post by Habitual on 2011-02-01
```
grep "bind-address" /etc/mysql/my.cnf
```
shows what value?

and 
```
sudo pidof mysqld
```
does it return a PID?

if not, start the mysqld server with ```
sudo service mysql start
```

then try mysql -uroot -p<password> again.

Let us know.

---

### Post by threepwood960 on 2011-02-01
Thanks for the answer:
# grep "bind-address" /etc/mysql/my.cnf
bind-address		= 127.0.0.1

# sudo pidof mysqld
(nothing)

# sudo service mysql start
mysql start/running

# mysql -uroot -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

---

### Post by Habitual on 2011-02-01
try this please...

```
mysql -h 127.0.0.1 -uroot -p<password>

```
Lemme know...

---

### Post by threepwood960 on 2011-02-02
```
# sudo start mysql
[sudo] password for user: 
start: Job is already running: mysql
# mysql -h 127.0.0.1 -uroot -p
Enter password: 
ERROR 2003 (HY000): Can't connect to MySQL server on '127.0.0.1' (111)

```

---

### Post by Habitual on 2011-02-02
bind-address = 127.0.0.1 <-- Change this to the actual IP of the machine.
in /etc/mysql/my.cnf

```

sudo service mysql stop
sudo service mysql start
pidof mysqld
mysql -uroot -p<pass>
```

NOTE: if pidof mysqld doesn't return a PID then mysql is NOT running.
**That needs to happen** first.

---

### Post by threepwood960 on 2011-02-02
I have the yesterday problem again. When I run:
sudo service mysql start

It get hang up...

I think that I will remove everything, reinstall and try to recover de DBs.

---

### Post by Habitual on 2011-02-03
```
sudo cp -p /var/lib/mysql/mysql /var/lib/mysql/mysql.org
```

---

### Post by threepwood960 on 2011-02-03
Solved: Installed mysql-server-5.1 from a bug-fixed repository, and moved my old databases from /home to /var/lib/mysql. Thanks.

---

### Post by Habitual on 2011-02-03
Great news!

Glad it worked out.

---


---
title: "apt-get install mysql-server doesn't install the mysql db"
date: 2012-06-27
forum: General Help
---

### Post by abatie on 2012-06-27
I accidentally toasted my mysql db while setting it up, so did an apt-get remove mysql-server and then reinstalled it.  It looked like it left /var/lib/mysql alone, so I removed it and tried again.  No /var/lib/mysql re-appeared.  I tried --reinstall and purging and autoremove and autoclean and nothing I can do will get mysql to reinstall its own database?!?

---

### Post by astraljava on 2012-06-27
> **abatie said:**
> I accidentally toasted my mysql db while setting it up, so did an apt-get remove mysql-server and then reinstalled it.  It looked like it left /var/lib/mysql alone, so I removed it and tried again.  No /var/lib/mysql re-appeared.  I tried --reinstall and purging and autoremove and autoclean and nothing I can do will get mysql to reinstall its own database?!?

Hi, is this on precise? I just did this myself while tampering with wordpress installation. I got fairly dependable results with it. Can you show the output of the commands:

$ sudo ls -l /var/lib/mysql
$ dpkg -l | grep mysql
$ ps -ef | grep mysqld

I only had a little trouble initially as there seemed to be a left-over process listening in the same port where a new one is attempted to be set to listen. I accidentally had removed the installation of mysql at that point, so couldn't properly stop the process, either. A reboot finally fixed that problem.

---

### Post by abatie on 2012-06-27
It's 10.04

ls -l /var/lib/mysql gets "no such file or directory"

there's no mysql running obviously


ii  libdbd-mysql-perl                          4.012-1ubuntu1                                  A Perl5 database interface to the MySQL data
rc  libmysqlclient15off                        5.1.30really5.0.83-0ubuntu3                     MySQL database client library
ii  libmysqlclient16                           5.1.41-3ubuntu12                                MySQL database client library
ii  mysql-client-5.1                           5.1.41-3ubuntu12                                MySQL database client binaries
ii  mysql-client-core-5.1                      5.1.41-3ubuntu12                                MySQL database core client binaries
ii  mysql-common                               5.1.41-3ubuntu12                                MySQL database common files (e.g. /etc/mysql
ii  mysql-server                               5.1.41-3ubuntu12                                MySQL database server (metapackage depending
ii  mysql-server-5.1                           5.1.41-3ubuntu12                                MySQL database server binaries
ii  mysql-server-core-5.1                      5.1.41-3ubuntu12                                MySQL database core server files
ii  php5-mysql                                 5.3.2-1ubuntu4                                  MySQL module for php5

---

### Post by astraljava on 2012-06-27
> **abatie said:**
> It's 10.04

ls -l /var/lib/mysql gets "no such file or directory"

there's no mysql running obviously


Ok. As you have the packages still there, might be best to purge them, make sure the package database is up-to-date, and then try to re-install them. Can you paste the output of:

$ sudo apt-get purge mysql-server-5.1

(let's make sure the packages are being fetched again)
$ sudo apt-get clean

$ sudo apt-get update

$ sudo apt-get install mysql-server

---

### Post by abatie on 2012-06-27
I basically already did that but... I'm upgrading to 10.10 at the moment (needed for another package I need on this system), so if that doesn't fix it (I doubt it will), I'll try wiping every package with mysql in its name and reinstalling tomorrow...

---

### Post by astraljava on 2012-06-27
> **abatie said:**
> I basically already did that but... I'm upgrading to 10.10 at the moment (needed for another package I need on this system), so if that doesn't fix it (I doubt it will), I'll try wiping every package with mysql in its name and reinstalling tomorrow...

I understand, but without the output of apt it's hard to help you further. So if it continues to happen tomorrow, do share. :) Good luck!

---


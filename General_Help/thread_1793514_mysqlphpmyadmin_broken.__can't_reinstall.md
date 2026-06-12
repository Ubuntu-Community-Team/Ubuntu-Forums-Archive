---
title: "mysql/phpmyadmin broken.  can't reinstall"
date: 2011-06-29
forum: General Help
---

### Post by sneakyimp on 2011-06-29
In an uber-tired haze at 3am, I mistakenly mis-clicked and deleted all the tables in the 'mysql' database that gets installed with mysql.  My attempts to remove it completely and reinstall it failed to remedy the problem and so I got gradually bolder, removing things manually.

I've apparently corrupted either my APT database or removed a critical file and now i cannot either fully install or uninstall mysql at all.  Some help would be much appreciated lest I have to reinstall ubuntu for the 3rd time this week.

```

root@jaith-GA-880GM-USB3:/# apt-get install mysql-server mysql-client libmysqlclient-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libmysqlclient-dev mysql-client mysql-server
0 upgraded, 3 newly installed, 0 to remove and 15 not upgraded.
1 not fully installed or removed.
Need to get 0 B/3,187 kB of archives.
After this operation, 10.0 MB of additional disk space will be used.
Selecting previously deselected package libmysqlclient-dev.
(Reading database ... 143370 files and directories currently installed.)
Unpacking libmysqlclient-dev (from .../libmysqlclient-dev_5.1.54-1ubuntu4_amd64.deb) ...
Selecting previously deselected package mysql-client.
Unpacking mysql-client (from .../mysql-client_5.1.54-1ubuntu4_all.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.1.54-1ubuntu4_all.deb) ...
Processing triggers for man-db ...
Setting up phpmyadmin (4:3.3.10-1) ...
.: 12: Can't open /usr/share/dbconfig-common/internal/mysql
dpkg: error processing phpmyadmin (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up libmysqlclient-dev (5.1.54-1ubuntu4) ...
Setting up mysql-client (5.1.54-1ubuntu4) ...
Setting up mysql-server (5.1.54-1ubuntu4) ...
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---


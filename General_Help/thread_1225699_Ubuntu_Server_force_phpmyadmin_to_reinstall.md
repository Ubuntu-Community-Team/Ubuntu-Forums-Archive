---
title: "Ubuntu Server force phpmyadmin to reinstall?"
date: 2009-07-28
forum: General Help
---

### Post by justin10ec on 2009-07-28
Something went wrong with my phpmyadmin installtion. When I try to remove it via: ```
sudo apt-get remove phpmyadmin
```

This is what goes on

```


root@4:~# apt-get remove phpmyadmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libx11-data php5-gd libmcrypt4 libxcb1 libxau6 libt1-5 libxdmcp6 libxpm4
  libgd2-xpm php5-mcrypt libjpeg62 x11-common libx11-6 php5-mysql
  dbconfig-common libapache2-mod-php5 php5-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  phpmyadmin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 13.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 25203 files and directories currently installed.)
Removing phpmyadmin ...
dbconfig-common: dumping mysql database phpmyadmin to /var/tmp/phpmyadmin.phpmyadmin.2009-07-29-03.39.mysql.XUhTKT.
/usr/share/dbconfig-common/internal/common: fork: Cannot allocate memory
Could not open required defaults file:
Fatal error in defaults handling. Program aborted.
unable to connect to mysql server.
error encountered dumping database:
Could not open required defaults file: Fatal error in defaults handling. Program aborted
dbconfig-common: phpmyadmin remove: retrying.
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf
/usr/share/dbconfig-common/dpkg/common: fork: Cannot allocate memory
/usr/share/dbconfig-common/dpkg/common: fork: Resource temporarily unavailable
/usr/share/dbconfig-common/dpkg/common: fork: Resource temporarily unavailable
/usr/share/dbconfig-common/dpkg/common: fork: Cannot allocate memory
dpkg: error processing phpmyadmin (--remove):
 subprocess pre-removal script returned error exit status 128
/usr/share/dbconfig-common/dpkg/common: fork: Cannot allocate memory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 128
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by DaithiF on 2009-07-29
Hi,
looks like your system ran out of memory.  maybe run top and see if there are some processes consuming large amounts of memory and stop them before trying again.

---


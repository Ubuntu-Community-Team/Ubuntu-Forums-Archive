---
title: "dpkg: cannot move  `/etc/gconf/2/path' to `/ETC/GCONF/2/PATH' et. al"
date: 2010-10-21
forum: General Help
---

### Post by DDM on 2010-10-21
I've searched for this problem on here so sorry if it's been addressed, but it's one that has plagued me since 9.10, even after many reinstalls and over two different computers. 
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lzma libnspr4-0d mame-common xdg-utils libxss1 libnss3-1d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gconf2-common (2.31.91-0ubuntu3.1) ...
mv: cannot move `/usr/share/gconf/default.path' to `/USR/SHARE/GCONF/DEFAULT.PATH': No such file or directory
mv: cannot move `/etc/gconf/2/path' to `/ETC/GCONF/2/PATH': No such file or directory
dpkg: error processing gconf2-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libapache2-mod-php5 (5.3.3-1ubuntu9.1) ...
mv: cannot move `/usr/share/php5/php.ini-production' to `/USR/SHARE/PHP5/PHP.INI-PRODUCTION': No such file or directory
mv: cannot move `/etc/php5/apache2/php.ini' to `/ETC/PHP5/APACHE2/PHP.INI': No such file or directory
dpkg: error processing libapache2-mod-php5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libgconf2-4:
 libgconf2-4 depends on gconf2-common (>= 2.31); however:
  Package gconf2-common is not configured yet.
 libgconf2-4 depends on gconf2-common (<< 2.32); however:
  Package gconf2-common is not configured yet.
dpkg: error processing libgconf2-4 (--configure):
 dependency problems - leaving unconfigured
Setting up php5-cli (5.3.3-1ubuntu9.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          mv: cannot move `/usr/share/php5/php.ini-production.cli' to `/USR/SHARE/PHP5/PHP.INI-PRODUCTION.CLI': No such file or directory
mv: cannot move `/etc/php5/cli/php.ini' to `/ETC/PHP5/CLI/PHP.INI': No such file or directory
dpkg: error processing php5-cli (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of php-pear:
 php-pear depends on php5-cli; however:
  Package php5-cli is not configured yet.
dpkg: error processing php-pear (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 gconf2-common
 libapache2-mod-php5
 libgconf2-4
 php5-cli
 php-pear
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So it's clear what the errors are, but the only way I know how to fix them is to rm the gconf2-common.postinst file. I've also had this happen with grub2, samba, and a few other fairly important packages. I've also tried to sudo aptitude remove --purge each item and reinstall them one by one, and I still get the same errors.

---


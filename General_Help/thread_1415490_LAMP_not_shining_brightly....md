---
title: "LAMP not shining brightly..."
date: 2010-02-24
forum: General Help
---

### Post by alphapup on 2010-02-24
EDIT --- solved scroll down for solution

I'm having  a strange problem with a LAMP installation.

apache serves up local pages for me just fine.  PHP is working.  MySQL is up and running and I've created databases and users with it.

I thought all was fine until I tried to use it with a drupal install.  At that point I discovered that PHP/Apache seem to have no notion that MySQL is available.

<?php phpinfo(); ?>

only shows that it is consulting mysql ini files, but nowhere in the page does it actually show output for mysql.

/etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini  

What am I missing?

What I've installed

dpkg --get-selections | grep php
libapache2-mod-php5                install
php5                        install
php5-common                    install
php5-mysql                    install

dpkg --get-selections | grep apache
apache2                        install
apache2-mpm-prefork                install
apache2-utils                    install
apache2.2-bin                    install
apache2.2-common                install
libapache2-mod-auth-mysql            install
libapache2-mod-php5                install

dpkg --get-selections | grep mysql
libapache2-mod-auth-mysql            install
libdbd-mysql-perl                install
libmysqlclient15off                install
libmysqlclient16                install
libqt4-sql-mysql                install
mysql-admin                    install
mysql-client                    install
mysql-client-5.1                install
mysql-common                    install
mysql-gui-tools-common                install
mysql-query-browser                install
mysql-server                    install
mysql-server-5.1                install
mysql-server-core-5.1                install
php5-mysql                    install

SOLUTION --------------

This is a cautionary tale about messing with your standard distro's structure.

I messed with the /usr/lib/php5 structure (added an ext subdirectory) then set that as the extension dir in php.ini

Days later I decided to just go with the standard configuration and *thought* I'd completely uninstalled php and removed all config files and just cleaned everything up... not so.

A subsequent re-install kept the old structure... sort of.  As I added new php modules, all the new .so files were stored not in the ext folder but a numbered folder at the same level and the php.ini still pointed to the ext directory.  

PHP never seemed to load the .so files even though the packages with PHP extensions seemed to be installing.

Oops.

---


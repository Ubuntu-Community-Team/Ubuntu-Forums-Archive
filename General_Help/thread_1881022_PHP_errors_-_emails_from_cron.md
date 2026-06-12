---
title: "PHP errors - emails from cron"
date: 2011-11-14
forum: General Help
---

### Post by sammcj on 2011-11-14
Hi all,

I'm getting the following emails every hour or so from cron, however I can't see anything in my crontab or /etc/cron.whatever relating to this.


Subject:

Cron <root@nas> [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete

Body:

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/pdo_sqlite.so' - /usr/lib/php5/20090626/pdo_sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/sqlite.so' - /usr/lib/php5/20090626/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/sqlite3.so' - /usr/lib/php5/20090626/sqlite3.so: cannot open shared object file: No such file or directory in Unknown on line 0


Ubuntu 11.10 x64 Server, latest updates installed.

---


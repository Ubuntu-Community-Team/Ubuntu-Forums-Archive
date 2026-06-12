---
title: "cron godaddy dedicated setting"
date: 2010-07-05
forum: General Help
---

### Post by sunward on 2010-07-05
I have having problems with setting up a cron job (for a drupal installation) running on a godaddy dedicated server.  Plesk does work, and even crontab shows an error.

I could list all errors, but does anyone have the correct command?

---

### Post by clrg on 2010-07-05
What did you do exactly in order to define the cron job? Post any scripts, commands, and configuration files, please.

---

### Post by sunward on 2010-07-06
at root in with crontab -e command

(time)  /usr/bin/curl /var/www/vhosts/sunward1.com/httpdocs/cron.php
gave error as curl: (3) <url> malformed

(time)  /usr/bin/php /var/www/vhosts/sunward1.com/httpdocs/cron.php
gave error as:
> Warning: include_once(./includes/bootstrap.inc): failed to open stream: No such  file or directory in /var/www/vhosts/sunward1.com/httpdocs/cron.php on line  9

Warning: include_once(): Failed opening './includes/bootstrap.inc' for  inclusion (include_path='.:/usr/share/php:/usr/share/pear') in  /var/www/vhosts/sunward1.com/httpdocs/cron.php on line 9

Fatal error:  Call to undefined function drupal_bootstrap() in  /var/www/vhosts/sunward1.com/httpdocs/cron.php on line 10

(time) is the time and frequency - set every day early in the morning

---

### Post by sunward on 2010-07-11
Finally got it to work.

I used crontab command at the root level.  For more information
 [http://drupal.org/node/36678#comment-69418](http://drupal.org/node/36678#comment-69418)
 the thread contains more details on using the crontab command

---


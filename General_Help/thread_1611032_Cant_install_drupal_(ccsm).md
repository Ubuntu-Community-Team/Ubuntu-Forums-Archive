---
title: "Cant install drupal (ccsm)"
date: 2010-11-01
forum: General Help
---

### Post by Verbeck on 2010-11-01
I don't know where this is most appropriate to post, but here goes:

after completing the form for entering the database name,  user-name/password, the installer just resets all the fields when i press 'save and continue'. no error is displayed. 

so what might be the problem and how can i fix it?

ps.wordpress installed without a hitch

---

### Post by eric_1982 on 2010-11-01
What are the permissions on the drupal dir? Who is the owner? www-data

ls -la

Also what version of drupal are you installing? (6 or 7?) Have you enable redirects?

---

### Post by Verbeck on 2010-11-01
i'm using /home/www as the document root
the only permission changes i did so far are for sites/default and sites/default/settings.php. for both i did chmod o+w (it was in the readme)
```

verbeck@Vector-Sigma:~$ cd /home/www
verbeck@Vector-Sigma:/home/www$ ls -la
total 236
drwxr-xr-x 10 verbeck verbeck  4096 2010-11-01 21:27 .
drwxr-xr-x  6 root  root   4096 2010-11-01 16:13 ..
drwxr-xr-x  5 verbeck verbeck  4096 2010-11-01 21:52 blog
-rw-r--r--  1 verbeck verbeck 44869 2010-08-12 01:35 CHANGELOG.txt
-rw-r--r--  1 verbeck verbeck   988 2010-08-06 15:58 COPYRIGHT.txt
-rw-r--r--  1 verbeck verbeck   262 2006-08-09 12:42 cron.php
drwxr-xr-x  2 verbeck verbeck  4096 2010-08-12 01:41 includes
-rw-r--r--  1 verbeck verbeck   980 2007-12-26 13:46 index.php
-rw-r--r--  1 verbeck verbeck  1308 2007-11-20 00:53 INSTALL.mysql.txt
-rw-r--r--  1 verbeck verbeck  1075 2007-11-26 21:36 INSTALL.pgsql.txt
-rw-r--r--  1 verbeck verbeck 47150 2010-05-09 19:13 install.php
-rw-r--r--  1 verbeck verbeck 15646 2008-07-10 00:15 INSTALL.txt
-rw-r--r--  1 verbeck verbeck 18048 2009-01-06 22:27 LICENSE.txt
-rw-r--r--  1 verbeck verbeck  1924 2009-04-29 22:15 MAINTAINERS.txt
drwxr-xr-x  3 verbeck verbeck  4096 2010-08-12 01:41 misc
drwxr-xr-x 35 verbeck verbeck  4096 2010-08-12 01:41 modules
drwxr-xr-x  3 verbeck verbeck  4096 2010-08-12 01:41 profiles
-rw-r--r--  1 verbeck verbeck  1590 2008-12-11 01:12 robots.txt
drwxr-xr-x  2 verbeck verbeck  4096 2010-08-12 01:41 scripts
drwxr-xr-x  4 verbeck verbeck  4096 2010-11-01 21:33 sites
drwxr-xr-x  7 verbeck verbeck  4096 2010-08-12 01:41 themes
-rw-r--r--  1 verbeck verbeck 25457 2009-03-30 16:15 update.php
-rw-r--r--  1 verbeck verbeck  4926 2010-05-11 14:39 UPGRADE.txt
-rw-r--r--  1 verbeck verbeck   352 2005-12-11 00:26 xmlrpc.php

```

---

### Post by eric_1982 on 2010-11-01
what version of Drupal are you installing?

have you enabled clean URLs?

sudo a2enmod rewrite


Take a quick look at this

[http://www.linuxbasement.com/content/customizing-drupal-part-1](http://www.linuxbasement.com/content/customizing-drupal-part-1)

---

### Post by Verbeck on 2010-11-01
yep.

its version 6

---

### Post by Verbeck on 2010-11-01
fixed it : added the database info manually to sites/default/settings.php (must have been a permission issue after all :D) 

edit ; 
> Unable to send e-mail. Please contact the site administrator if the problem persists.now need a fix for this

---

### Post by Verbeck on 2010-11-08
bump.

edit : found it again [http://drupal.org/project/smtp](http://drupal.org/project/smtp) and [http://sourceforge.net/projects/phpmailer/files/phpmailer%20for%20php5_6/]("http://sourceforge.net/projects/phpmailer/files/phpmailer%20for%20php5_6/")

guess i should have googled it first :|

---


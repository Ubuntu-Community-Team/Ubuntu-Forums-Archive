---
title: "re-drupal problem"
date: 2010-04-05
forum: General Help
---

### Post by nischalinn on 2010-04-05
Can anyone tell me how to  install **drupal5** in Ubuntu9.04.I've installed it but when I tried to open it through Run Application,it can not locate the file.

My terminal shows:


[B]XXX@XXX-desktop:~$ sudo apt-get install drupal5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
drupal5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up drupal5 (5.10-1ubuntu1.1) ...
dbconfig-common: writing config to /etc/dbconfig-common/drupal5.conf
*** WARNING: ucf was run from a maintainer script that uses debconf, but
             the script did not pass --debconf-ok to ucf. The maintainer
             script should be fixed to not stop debconf before calling ucf,
             and pass it this parameter. For now, ucf will revert to using
             old-style, non-debconf prompting. Ugh!

             Please inform the package maintainer about this problem.
Replacing config file /etc/drupal/5/sites/default/dbconfig.php with new version
dbconfig-common: flushing administrative password
www-data www-data 0750 /var/lib/drupal5/files
[/B]

---

### Post by djoxyk on 2010-04-05
why you install it from repository? its a common php script. Download it, put into your server folder (for example var/www/drupal), set up database connection and run from browser like
[http://localhost/drupal/](http://localhost/drupal/)

---


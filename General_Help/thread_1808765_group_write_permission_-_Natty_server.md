---
title: "group write permission - Natty server"
date: 2011-07-20
forum: General Help
---

### Post by RoyB (Aus) on 2011-07-20
On my server there is a directory; /var/www/garland/app_logs.
In this directory is a file garland.log.
garland.log permissions are 664, owner is garland and group is garlandrw

I want to allow a php script that is run by users via a web url to write an entry into garland.log.
I've tried everything I can think of to make this work but no matter what I do the user receives an error in their browser.
This has driven me mad for 24 hours.  I suspect the problem is simple, trivial and obvious but I can't see it.  Assistance appreciated.

The php script is owned by garland:
```
4 -rw-rw-r-- 1 garland garland 2650 2011-07-21 08:41 garlandWrite.php

```
Within the php script is:
```
$FileHandle = fopen("/var/www/garland/app_logs/garland.log",'w') or die("can't open file");
fwrite($FileHandle,"This is a test");
fclose ($FileHandle);
``````
Warning: fopen(/var/www/garland/app_logs/garland.log): failed to open stream: Permission denied in /var/www/garland/scripts/garlandWrite.php on line 44 can't open file
```
extract from ls -las /var/www/garland/app_logs```
 4 -rw-rw-r-- 1 garland garlandrw      15 2011-07-21 08:42 garland.log
```
In /etc/group is:
```
garlandrw:x:1001:garland,www-data

```
in /etc/apache2/sites-available/default is the following section:
```
        <Directory /var/www/garland/app_logs>
                Options FollowSymLinks
                Options +Indexes
                AllowOverride All
                Order allow,deny
                allow from all
        </directory>

```

---


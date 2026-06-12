---
title: "Durpal 6 Install :  Stalled in Config"
date: 2010-10-26
forum: General Help
---

### Post by mikeincousa on 2010-10-26
[SIZE=3]**Stalled at Drupal Database Configuration Page, What have I missed?  :(**[/SIZE]
 ===========================================================
Stuck Here...

**[http://localhost/drupal-6.19/install.php?profile=default&locale=en](http://localhost/drupal-6.19/install.php?profile=default&locale=en)**

Database configuration
 Type; mysqli
 name: drupal
 user name; None of the combinations in the PHP adm (following) worked.
  Password: N.A.  

=====================================================
[B]
About....[/B]You are using Ubuntu 10.04 LTS the Lucid Lynx  
________

 From CL....
 [B]
Starting [/B]XAMPP for Linux 1.7.3a...  
 XAMPP: Starting Apache with SSL (and PHP5)...  
 XAMPP: Starting MySQL...  
 XAMPP: Starting ProFTPD...  
  XAMPP for Linux started.  

____________________________________________________________________________________________________________

 **[http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)**
**database: **drupal, No tables found in database**.**

[B]Column Headings....
 [/B]User,Host,Password,Global Privileges,Grant,
 
[B]Data...  
 [/B]Any,%,--,,No,  ,
 Any,linux,No,
 ALL PRIVILEGES ,Yes,  ,
 Any,localhost,No,ALL PRIVILEGES ,Yes,  ,
 mike,,No,ALL PRIVILEGES ,Yes,  ,
 mike,%,No,ALL PRIVILEGES ,Yes,  ,
 pma,localhost,No,ALL PRIVILEGES ,Yes,  ,
 root,linux,No,ALL PRIVILEGES ,Yes,  ,
 root,localhost,No,ALL PRIVILEGES ,Yes,  
 __________________________________________________________________________________________________
[B]
/opt/lampp/htdocs/drupal-6.19/sites/default
[/B]
From GUI, Properties>Permissions
Owner: 6226-user #6226 create and delete
Group: 6226 create and delete
folder access: create and delete.
allow executing program, unchecked

CL
-rw-rw-r-- 1   6226    6226 9485 2009-09-14 06:59 default.settings backup.php
drwxrwxrwx 2 nobody nogroup 4096 2010-10-25 19:45 files
-rw-rw-rw- 1 mike   mike    9485 2009-09-14 06:59 settings.php

settings.php
GUI: owner, mike; group, mike; executing un-checked
CL: -rw-rw-rw- 1 mike   mike    9485 2009-09-14 06:59 settings.php

---

### Post by mikeincousa on 2010-10-27
I worked more on this. 
The problem seems to be in the link between Drupal and mysql. 
I'm confused as to how to specify which one of the ones (under the PHP adm heading) to use.
I am thinking I should junk all of them and start over?

---


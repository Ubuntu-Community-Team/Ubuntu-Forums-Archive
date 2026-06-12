---
title: "Zabbix GUI Install problem"
date: 2010-12-23
forum: General Help
---

### Post by saphil on 2010-12-23
I installed the server and client from the repositories. I got version 1.8:
```
wolf@telcontar:~$ zabbix_server -V
Zabbix Server (daemon) v1.8.1 (revision 9702) (27 January 2010)
Compilation time:  Apr  6 2010 01:48:34

```Patiently followed the install instructions in the 1.8 manual

Got everything running, apparently normally, but then I noticed the GUI Installation tab.  This helped me optimize the php.ini file so the pretty front end could be used.

I got the step 7 where it says
```

 7. Install    
[LIST]
[*] 1. Introduction
[*] 2. Licence Agreement
[*] 3. Check of pre-requisites
[*] 4. Configure DB connection
[*] 5. Zabbix server details
[*] 6. Pre-Installation Summary
[*] 7. Install
[*] 8. Finish
[/LIST]
     Configuration file:   Fail   
  
 
 Please install configuration file manualy, or fix permissions on conf directory.
 
 Press "Save configuration file" button, download configuration file and save it as 
 "/usr/share/zabbix/conf/zabbix.conf.php"
 
  
 
 When done, press the "Retry" button
```and when I attempted to save the file, I got the error:
```

[LIST]
[*] Incorrect configuration file[/usr/share/zabbix/conf/zabbix.conf.php]
[/LIST]

```I am acting as admin on the PHP GUI frontend.  I checked the zabbix.conf.php file and it is a soft link to /etc/zabbix/dbconfig.php

I copied the file I had been working on to another location and ran diff against /etc/zabbix/dbconfig.php

```
wolf@telcontar:~$ sudo diff /etc/zabbix/dbconfig.php bin/zabbix.conf.php 
2,11c2,19
< global $DB;
< 
< $DB["TYPE"]      = "mysql";
< $DB["SERVER"]    = "localhost";
< $DB["PORT"]      = "0";
< $DB["DATABASE"]  = "zabbix";
< $DB["USER"]      = "zabbix";
< $DB["PASSWORD"]  = "PASSWORD";
< $ZBX_SERVER      = "127.0.0.1";
< $ZBX_SERVER_PORT = "10051";
---
> /*
> ** ZABBIX
> ** Copyright (C) 2000-2005 SIA Zabbix
> **
> ** This program is free software; you can redistribute it and/or modify
> ** it under the terms of the GNU General Public License as published by
> ** the Free Software Foundation; either version 2 of the License, or
> ** (at your option) any later version.
> **
> ** This program is distributed in the hope that it will be useful,
> ** but WITHOUT ANY WARRANTY; without even the implied warranty of
> ** MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
> ** GNU General Public License for more details.
> **
> ** You should have received a copy of the GNU General Public License
> ** along with this program; if not, write to the Free Software
> ** Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
> **/
13c21
< $IMAGE_FORMAT_DEFAULT    = IMAGE_FORMAT_PNG;
---
> global $DB;
14a23,30
> $DB["TYPE"]        = "MYSQL";
> $DB["SERVER"]        = "localhost";
> $DB["PORT"]        = "0";
> $DB["DATABASE"]        = "zabbix";
> $DB["USER"]        = "root";
> $DB["PASSWORD"]        = "PASSWORD";
> $ZBX_SERVER        = "192.168.0.102";
> $ZBX_SERVER_PORT    = "10051";
16,19d31
< ## dont remove this!
< ## This is a work-around for dbconfig-common
< if($DB["TYPE"] == "mysql") 
<     $DB["TYPE"] = "MYSQL";
21,24c33,34
< if($DB["TYPE"] == "pgsql")
<     $DB["TYPE"] = "POSTGRESQL";
< ##
< ?>
---
> $IMAGE_FORMAT_DEFAULT    = IMAGE_FORMAT_PNG;
> ?>
\ No newline at end of file

```Why is this a soft link?  Would it be safe to 
```
sudo mv /usr/share/zabbix/conf/zabbix.conf.php /usr/share/zabbix/conf/zabbix.conf.php.test
sudo cp zabbix.conf.php /usr/share/zabbix/conf/zabbix.conf.php 
```or would it make more sense to keep the linked behaviour and:
```
sudo cp zabbix.conf.php /etc/zabbix/dbconfig.php
```

---

### Post by saphil on 2010-12-23
I was impatient so I tried it this way:
```
wolf@telcontar:/etc/zabbix$ sudo mv dbconfig.php dbconfig.php.old
[sudo] password for wolf: 
wolf@telcontar:/etc/zabbix$ sudo cp /home/wolf/bin/zabbix.conf.php /etc/zabbix/dbconfig.php
wolf@telcontar:/etc/zabbix$ sudo service apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
```
since the main differences in the 2 files were the username #could really be the whole difference!
and some detail about the choice of db, if the db might be postgre # which it isn't

```
Configuration file:   Ok   
 When done, press the "Next" button
```

---


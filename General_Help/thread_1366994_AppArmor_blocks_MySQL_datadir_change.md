---
title: "AppArmor blocks MySQL datadir change?"
date: 2009-12-29
forum: General Help
---

### Post by mrpaint on 2009-12-29
*The title is just my guess

Hi,

I'm trying to change the datadir for MySQL (installed via Package Manager). I changed the **/etc/mysql/my.cnf** and updated the **/etc/apparmor.d/usr.sbin.mysqld** to match my new directory: **/media/data/www/__mysql_data/** (which is in a FAT32 partition, mounted at **/media/data/**)

Basically, I want to move the datadir to the same directory with the MySQL installation in Windows so I can access to my databases and tables without any problem. Sounds simple but it keeps saying failed when I run **/etc/init.d/mysql start**

Here is the last 10 lines in syslog

```
Dec 29 13:02:35 pon-dell1510 kernel: [ 1081.354241] type=1503 audit(1262066555.758:175): operation="open" pid=4579 parent=4578 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Dec 29 13:02:36 pon-dell1510 kernel: [ 1082.381834] type=1503 audit(1262066556.786:176): operation="open" pid=4589 parent=4588 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Dec 29 13:02:37 pon-dell1510 kernel: [ 1083.406886] type=1503 audit(1262066557.809:177): operation="open" pid=4599 parent=4598 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Dec 29 13:02:38 pon-dell1510 kernel: [ 1084.437810] type=1503 audit(1262066558.841:178): operation="open" pid=4609 parent=4608 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Dec 29 13:02:38 pon-dell1510 kernel: [ 1084.465526] type=1503 audit(1262066558.869:179): operation="open" pid=4618 parent=4617 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Dec 29 13:02:38 pon-dell1510 /etc/init.d/mysql[4625]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Dec 29 13:02:38 pon-dell1510 /etc/init.d/mysql[4625]: #007/usr/bin/mysqladmin: connect to server at 'localhost' failed
Dec 29 13:02:38 pon-dell1510 /etc/init.d/mysql[4625]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Dec 29 13:02:38 pon-dell1510 /etc/init.d/mysql[4625]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Dec 29 13:02:38 pon-dell1510 /etc/init.d/mysql[4625]: 

```

I surfed around the Internet and most of people get denied error message from AppArmor when mysqld tries to access the new datadir but I don't know why mysqld tried to access **/sys/devices/system/cpu/**? Hmm, I'm stucked, please help :(

---


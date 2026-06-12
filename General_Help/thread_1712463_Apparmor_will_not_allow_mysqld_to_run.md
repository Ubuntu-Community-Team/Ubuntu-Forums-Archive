---
title: "Apparmor will not allow mysqld to run"
date: 2011-03-22
forum: General Help
---

### Post by Qu4rk on 2011-03-22
Mysql will not start.  I found this in the syslog.  Can someone help me resolve this issue?

```
[   53.219630] type=1400 audit(1300835573.999:23): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2364 comm="apparmor_parser"
[   83.470764] type=1400 audit(1300835604.250:24): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3043 comm="apparmor_parser"
[  113.691579] type=1400 audit(1300835634.469:25): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3648 comm="apparmor_parser"
[  143.884699] type=1400 audit(1300835664.668:26): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4202 comm="apparmor_parser"
[  174.088291] type=1400 audit(1300835694.868:27): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4277 comm="apparmor_parser"
[  204.283724] type=1400 audit(1300835725.064:28): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4354 comm="apparmor_parser"
[  234.540474] type=1400 audit(1300835755.324:29): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4432 comm="apparmor_parser"
[  264.739401] type=1400 audit(1300835785.520:30): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4516 comm="apparmor_parser"
[  294.938488] type=1400 audit(1300835815.720:31): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4596 comm="apparmor_parser"
[  325.135247] type=1400 audit(1300835845.916:32): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4681 comm="apparmor_parser"
[  355.348197] type=1400 audit(1300835876.132:33): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4766 comm="apparmor_parser"
[  385.538900] type=1400 audit(1300835906.320:34): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4840 comm="apparmor_parser"
[  415.729900] type=1400 audit(1300835936.512:35): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4914 comm="apparmor_parser"
[  445.920447] type=1400 audit(1300835966.700:36): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4988 comm="apparmor_parser"

```

---

### Post by drevicko on 2011-08-25
Bump...\
I'm getting the same problem..

---

### Post by Qu4rk on 2011-08-25
I ended up having to reinstall.  Hope someone can help you with this issue.

---

### Post by drevicko on 2011-08-26
Thanks for the reply (:

For people reading this, my problem was generated when I tried to move the mysql data directory, and evidently stuffed it up..

I eventually got it working - after "removing completely" 'mysql-server' and 'mysql-server-5.1', reloading the apt package information (ctrl-r in the synaptic gui - without this synaptic refuses to reinstall mysql-server..), checking that i had 'datadir=/var/lib/mysql' in  /etc/mysql/my.cnf, reinstalling 'mysql-server' then carefully following the 

[instructions to move mysql's data directory]("http://ubuntuforums.org/showpost.php?p=5220182&postcount=2")

I got it working (:

I suspect my problem was caused by copying the data directory /var/lib/mysql without the -p option. This meant that permissions and ownership weren't set up right.

---


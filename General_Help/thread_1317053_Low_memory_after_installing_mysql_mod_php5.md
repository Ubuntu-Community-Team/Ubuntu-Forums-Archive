---
title: "Low memory after installing mysql mod php5"
date: 2009-11-06
forum: General Help
---

### Post by ghadamyari on 2009-11-06
Hi there,

I have a VPS.
I have installed "Lighttpd, php5cgi, mysql-server, mysql-client, 
libmysqlclient15-dev"

I have optimized the MySQL Server (/etc/mysql/my.cnf).
All these together just take 30 mb Memory.
Lighttpd use just 12mb memory And everything is very good.

But,
When I install php5 mod MySQL :
apt-get install php5-mysql
Then the Lighttpd memory increases to 90mb !!!

Any Solutions?
I am using updated Debian Lenny, MySQL5, php5.

Thanks!

---

### Post by ghadamyari on 2009-11-06
Before Installing php5-mysql :
Mem:    458752k total,    43940k used,   414812k free,        0k buffers
Swap:        0k total,        0k used,        0k free,        0k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
    1 root      15   0  1980  684  588 S  0.0  0.1   0:00.61 init
 9514 root      15   0  2256 1068  872 R  0.0  0.2   0:00.00 top
10109 www-data  18   0  7532 1176  504 S  0.0  0.3   0:00.00 lighttpd
10110 www-data  25   0 14132 4416 3000 S  0.0  1.0   0:00.00 php5-cgi
10113 www-data  25   0 14132 1728  312 S  0.0  0.4   0:00.00 php5-cgi
10119 www-data  25   0 14132 4412 3000 S  0.0  1.0   0:00.00 php5-cgi
10121 www-data  25   0 14132 1724  312 S  0.0  0.4   0:00.00 php5-cgi
10122 www-data  25   0 14132 4420 3000 S  0.0  1.0   0:00.00 php5-cgi
10123 www-data  25   0 14132 1732  312 S  0.0  0.4   0:00.00 php5-cgi
10124 www-data  25   0 14132 4420 3000 S  0.0  1.0   0:00.00 php5-cgi
10125 www-data  25   0 14132 1732  312 S  0.0  0.4   0:00.00 php5-cgi
11972 root      25   0  2692 1304 1076 S  0.0  0.3   0:00.00 mysqld_safe
12011 mysql     25   0 22464 5020 4208 S  0.0  1.1   0:00.02 mysqld
12013 root      25   0  1628  528  456 S  0.0  0.1   0:00.00 logger
18122 daemon    18   0  1764  508  408 S  0.0  0.1   0:00.00 portmap
18247 root      15   0  1692  596  488 S  0.0  0.1   0:00.02 syslogd
18264 root      21   0  1644  396  324 S  0.0  0.1   0:00.00 klogd

After installing php5-mysql :

Mem:    458752k total,   138980k used,   319772k free,        0k buffers
Swap:        0k total,        0k used,        0k free,        0k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
    1 root      15   0  1980  684  588 S  0.0  0.1   0:00.61 init
11833 www-data  18   0  7532 1180  504 S  0.0  0.3   0:00.00 lighttpd
11834 www-data  25   0 38512 8080 5476 S  0.0  1.8   0:00.01 php5-cgi
11837 www-data  25   0 38460 2912  316 S  0.0  0.6   0:00.00 php5-cgi
11843 www-data  25   0 38512 8088 5476 S  0.0  1.8   0:00.01 php5-cgi
11845 www-data  25   0 38460 2920  316 S  0.0  0.6   0:00.00 php5-cgi
11846 www-data  25   0 38512 8088 5476 S  0.0  1.8   0:00.01 php5-cgi
11848 www-data  25   0 38460 2920  316 S  0.0  0.6   0:00.00 php5-cgi
11849 www-data  21   0 38512 8084 5476 S  0.0  1.8   0:00.01 php5-cgi
11852 www-data  21   0 38512 2924  316 S  0.0  0.6   0:00.00 php5-cgi
11972 root      25   0  2692 1304 1076 S  0.0  0.3   0:00.00 mysqld_safe
12001 root      15   0  2256 1072  872 R  0.0  0.2   0:00.03 top
12011 mysql     25   0 22464 5020 4208 S  0.0  1.1   0:00.02 mysqld
12013 root      25   0  1628  528  456 S  0.0  0.1   0:00.00 logger
18122 daemon    18   0  1764  508  408 S  0.0  0.1   0:00.00 portmap
18247 root      15   0  1692  596  488 S  0.0  0.1   0:00.02 syslogd
18264 root      21   0  1644  396  324 S  0.0  0.1   0:00.00 klogd

---

### Post by ghadamyari on 2010-06-03
Hello,

I have found the solution.
edit
```
/etc/apache2/apache2.conf
```
Find :
```
<IfModule mpm_prefork_module>
    StartServers       8
    MinSpareServers    5
    MaxSpareServers   20
    ServerLimit      256
    MaxClients       256
    MaxRequestsPerChild  4000
</IfModule>
```

And change it to this one :
```

<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>
```
Then restart apache2 server :
```
/etc/init.d/apache2 restart
```

---


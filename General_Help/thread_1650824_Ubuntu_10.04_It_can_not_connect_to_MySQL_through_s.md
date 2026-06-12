---
title: "Ubuntu 10.04: It can not connect to MySQL through socket"
date: 2010-12-22
forum: General Help
---

### Post by Nuria on 2010-12-22
Hi all!!!

I am in the process of installing a genome brower on an ubuntu 10.04 (lucid). I achieved to see the browser once. Then, the mysql.sock disappeared and to solve this I tried first, to reboot the server with no results. Then I removed and reinstalled the MySQL server installing mysql-server-5.1. Now, I have a socket  and MySQL is running (checked these out) but when I try to see the browser that is what I obtain:

 Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (13)

Any ideas, please?

Núria

---

### Post by Ubu_Fester on 2011-01-01
I am having the very same issue.

Within my mythbackend.log I am getting the following errors:

> 2011-01-01 11:10:32.434 mythbackend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2011-01-01 11:10:32.838 Using runtime prefix = /usr
2011-01-01 11:10:33.069 Using configuration directory = /home/mythtv/.mythtv
2011-01-01 11:10:33.431 Empty LocalHostName.
2011-01-01 11:10:33.512 Using localhost value of HTPC
2011-01-01 11:10:33.828 New DB connection, total: 1
2011-01-01 11:10:33.987 Unable to connect to database!
2011-01-01 11:10:34.309 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

2011-01-01 11:10:34.604 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2011-01-01 11:10:34.750 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.2011-01-01 11:10:35.004 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error

SSDP::PerformSearch - did not write entire buffer.
...............................................................................
2011-01-01 11:10:37.799 UPnPautoconf() - No UPnP backends found
2011-01-01 11:10:37.847 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']

---


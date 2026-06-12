---
title: "Processes not showing"
date: 2010-05-06
forum: General Help
---

### Post by eXDee on 2010-05-06
We have a 9.10 VPS on the OpenVZ platform, and for some reason now its decided not to show what processes are running.

The only thing that shows is a process which is started by CRON on a schedule.

```
$ sudo ps aux
USER        PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
user    32747  0.5  0.4  15104 12056 ?        S    09:00   0:14 /usr/bin/perl .script.pl

```
nmon and top have the same result.

Yet stuff is running:
```
$ sudo service mysql status
 * /usr/bin/mysqladmin  Ver 8.42 Distrib 5.1.37, for debian-linux-gnu on i486
Copyright 2000-2008 MySQL AB, 2008 Sun Microsystems, Inc.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license

Server version          5.1.37-1ubuntu5
Protocol version        10
Connection              Localhost via UNIX socket
UNIX socket             /var/run/mysqld/mysqld.sock
Uptime:                 1 hour 22 min 50 sec

Threads: 25  Questions: 73114  Slow queries: 0  Opens: 1324  Flush tables: 1  Open tables: 96  Queries per second avg: 14.711
```

This doesn't make any sense. Ideas?

---

### Post by dcstar on 2010-05-07
> **eXDee said:**
> We have a 9.10 VPS on the OpenVZ platform, and for some reason now its decided not to show what processes are running.

The only thing that shows is a process which is started by CRON on a schedule.

```
$ sudo ps aux
USER        PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
user    32747  0.5  0.4  15104 12056 ?        S    09:00   0:14 /usr/bin/perl .script.pl

```
nmon and top have the same result.

Yet stuff is running:
```
$ sudo service mysql status
 * /usr/bin/mysqladmin  Ver 8.42 Distrib 5.1.37, for debian-linux-gnu on i486
Copyright 2000-2008 MySQL AB, 2008 Sun Microsystems, Inc.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license

Server version          5.1.37-1ubuntu5
Protocol version        10
Connection              Localhost via UNIX socket
UNIX socket             /var/run/mysqld/mysqld.sock
Uptime:                 1 hour 22 min 50 sec

Threads: 25  Questions: 73114  Slow queries: 0  Opens: 1324  Flush tables: 1  Open tables: 96  Queries per second avg: 14.711
```

This doesn't make any sense. Ideas?

```
ps -ef
```

---


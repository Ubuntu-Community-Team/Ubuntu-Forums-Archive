---
title: "Zabbix on Ubuntu"
date: 2009-10-21
forum: General Help
---

### Post by jimmyjean on 2009-10-21
Hello,

I have installed Zabbix Server via Synaptic on Ubuntu Server 9.04.

I see from the forum that it is common to have to tweak the installation but I can't find a complete guide. If i start zabbix_agent it runs fine. However, zabbix_server does not seem to want to run.

Here is the output from the server log:

7494:20091020:133501 Starting zabbix_server. ZABBIX 1.6.1.
7494:20091020:133501 **** Enabled features ****
7494:20091020:133501 SNMP monitoring: YES
7494:20091020:133501 WEB monitoring: YES
7494:20091020:133501 Jabber notifications: YES
7494:20091020:133501 ODBC: NO
7494:20091020:133501 IPv6 support: YES
7494:20091020:133501 **************************
7494:20091020:133501 ZABBIX semaphores already exist, trying to recreate.
7500:20091020:133501 server #6 started [Trapper]
7501:20091020:133501 server #7 started [Trapper]
7502:20091020:133501 server #8 started [Trapper]
7504:20091020:133501 server #9 started [Trapper]
7506:20091020:133501 server #10 started [Trapper]
7508:20091020:133501 server #11 started [ICMP pinger]
7510:20091020:133501 server #12 started [Alerter]
7495:20091020:133501 server #1 started [Poller. SNMP:YES]
7512:20091020:133501 server #13 started [Housekeeper]
7512:20091020:133501 Executing housekeeper
7496:20091020:133501 server #2 started [Poller. SNMP:YES]
7515:20091020:133501 server #14 started [Timer]
7497:20091020:133502 server #3 started [Poller. SNMP:YES]
7519:20091020:133502 server #16 started [Node watcher. Node ID:0]
7521:20091020:133502 server #17 started [HTTP Poller]
7498:20091020:133502 server #4 started [Poller. SNMP:YES]
7523:20091020:133502 server #18 started [HTTP Poller]
7525:20091020:133502 server #19 started [HTTP Poller]
7527:20091020:133502 server #20 started [HTTP Poller]
7529:20091020:133502 server #21 started [HTTP Poller]
7494:20091020:133502 server #0 started [Watchdog]
7494:20091020:133502 In main_watchdog_loop()
7499:20091020:133502 server #5 started [Poller. SNMP:YES]
7531:20091020:133502 server #23 started [Escalator]
7517:20091020:133502 server #15 started [Poller for unreachable hosts. SNMP:YES]
7530:20091020:133502 server #22 started [Discoverer. SNMP:YES]
7512:20091020:133506 Deleted 0 records from history and trends
7494:20091020:133615 One child process died. Exiting ...
7494:20091020:133617 Failed to connect to database: Error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) [2002]
/usr/sbin/zabbix_server [2280]: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
/usr/sbin/zabbix_server [2280]: ERROR: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [3350]: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [3350]: ERROR: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [4351]: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [4351]: ERROR: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
/usr/sbin/zabbix_server [2338]: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
/usr/sbin/zabbix_server [2338]: ERROR: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [5662]: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [5662]: ERROR: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [8153]: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [8153]: ERROR: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [8174]: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [8174]: ERROR: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [8177]: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [8177]: ERROR: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [8931]: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [8931]: ERROR: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [8957]: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [8957]: ERROR: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [8970]: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [8970]: ERROR: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [9141]: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [9141]: ERROR: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
./zabbix_server [32332]: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
./zabbix_server [32332]: ERROR: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
./zabbix_server [32354]: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
./zabbix_server [32354]: ERROR: Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]
zabbix_server [32617]: Cannot open PID file [/var/run/mysqld/mysqld.pid] [Permission denied]
zabbix_server [32617]: ERROR: Cannot open PID file [/var/run/mysqld/mysqld.pid] [Permission denied]
zabbix_server [435]: Cannot open PID file [/var/run/mysqld/mysqld.pid] [Permission denied]
zabbix_server [435]: ERROR: Cannot open PID file [/var/run/mysqld/mysqld.pid] [Permission denied]

The following are the notable variables of the mysql database:

pid_file: /var/run/mysqld/mysqld.pid
port: 3306
socket /var/run/mysqld/mysqld.sock


I would very much appreciate any help in getting this working.

Thanks

Jim

---

### Post by kushal.kumaran on 2009-10-25
The error messages of the form "Cannot create PID file [/var/run/zabbix-server/zabbix_server.pid] [No such file or directory]" indicate that you might have to create the /var/run/zabbix-server directory before you try to run it.

---


---
title: "Oracle-xe Apex interface not connecting with 9.10"
date: 2010-04-22
forum: General Help
---

### Post by ybbon66 on 2010-04-22
Hey,

I've read through many of the posts on this and other sites and I still can't seem to get this to work. Just to be sure I haven't missed anything I'll post what I have done:

91 bash: server$> sudo /etc/init.d/oracle-xe force-reload
Shutting down Oracle Database 10g Express Edition Instance.
Stopping Oracle Net Listener.

Starting Oracle Net Listener.
Starting Oracle Database 10g Express Edition Instance.

93 bash: server$> lsnrctl status

LSNRCTL for Linux: Version 10.2.0.1.0 - Production on 22-APR-2010 09:31:28

Copyright (c) 1991, 2005, Oracle.  All rights reserved.

Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC_FOR_XE)))
STATUS of the LISTENER
------------------------
Alias                     LISTENER
Version                   TNSLSNR for Linux: Version 10.2.0.1.0 - Production
Start Date                22-APR-2010 09:25:17
Uptime                    0 days 0 hr. 6 min. 10 sec
Trace Level               off
Security                  ON: Local OS Authentication
SNMP                      OFF
Default Service           XE
Listener Parameter File   /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/admin/listener.ora
Listener Log File         /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/log/listener.log
Listening Endpoints Summary...
  (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC_FOR_XE)))
  (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=127.0.0.1)(PORT=1521)))
Services Summary...
Service "PLSExtProc" has 1 instance(s).
  Instance "PLSExtProc", status UNKNOWN, has 1 handler(s) for this service...
The command completed successfully

94 bash: server$> lsnrctl service

LSNRCTL for Linux: Version 10.2.0.1.0 - Production on 22-APR-2010 09:31:58

Copyright (c) 1991, 2005, Oracle.  All rights reserved.

Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC_FOR_XE)))
Services Summary...
Service "PLSExtProc" has 1 instance(s).
  Instance "PLSExtProc", status UNKNOWN, has 1 handler(s) for this service...
    Handler(s):
      "DEDICATED" established:0 refused:0
         LOCAL SERVER
The command completed successfully

95 bash: server$> cat network/admin/listener.ora 
# listener.ora Network Configuration File:

SID_LIST_LISTENER =
  (SID_LIST =
    (SID_DESC =
      (SID_NAME = PLSExtProc)
      (ORACLE_HOME = /usr/lib/oracle/xe/app/oracle/product/10.2.0/server)
      (PROGRAM = extproc)
    )
  )

LISTENER =
  (DESCRIPTION_LIST =
    (DESCRIPTION =
      (ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC_FOR_XE))
      (ADDRESS = (PROTOCOL = TCP)(HOST = localhost )(PORT = 1521))
    )
  )

DEFAULT_SERVICE_LISTENER = (XE)

96 bash: server$> cat network/admin/tnsnames.ora 
# tnsnames.ora Network Configuration File:

XE =
  (DESCRIPTION =
    (ADDRESS = (PROTOCOL = TCP)(HOST = localhost )(PORT = 1521))
    (CONNECT_DATA =
      (SERVER = DEDICATED)
      (SERVICE_NAME = XE)
    )
  )

EXTPROC_CONNECTION_DATA =
  (DESCRIPTION =
    (ADDRESS_LIST =
      (ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC_FOR_XE))
    )
    (CONNECT_DATA =
      (SID = PLSExtProc)
      (PRESENTATION = RO)
    )
  )

7 bash: server$> cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    nobrien-ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I am on my home network via wireless so I only connect via VPN and have no static IP. I have wondered if this is the issue as I also have a problem with KPvnc which connects but then can't ping or see any internal sites but I use Cisco VPN Anywhere client.

I have also tried using localhost and hostname in the tnsnames  but that doesn't make a difference. The port is 9999 to not interfere with JBoss but I have tried 127.0.0.1, localhost and nobrien-ubuntu:9999/apex without success.

I unistalled and reinstalled to no effect. Although I can use sqlplus this won't help as I need to set up JDBC connections and DBVisualiser won't connect so neither will the JBoss connections.

Interestingly, I just noticed that tnsping doesn't return...

01 bash: server$> tnsping nobrien-ubuntu 10

TNS Ping Utility for Linux: Version 10.2.0.1.0 - Production on 22-APR-2010 09:35:57

Copyright (c) 1997, 2005, Oracle.  All rights reserved.

Used parameter files:

Used HOSTNAME adapter to resolve the alias
Attempting to contact (DESCRIPTION=(CONNECT_DATA=(SERVICE_NAME=))(ADDRESS=(PROTOCOL=TCP)(HOST=127.0.1.1)(PORT=1521)))


Any ideas? Sorry for the long post. anyone needs any other info I can get it.

[Solution]
Check your VPN! I was using VPN Anywhere, for some reason it interferes with this. When disabled I had no problems.

---


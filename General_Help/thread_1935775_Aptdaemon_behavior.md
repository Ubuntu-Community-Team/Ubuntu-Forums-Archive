---
title: "Aptdaemon behavior"
date: 2012-03-05
forum: General Help
---

### Post by begage1 on 2012-03-05
I was going through the syslog1 file and saw the the aptdaemon, about every 5 minutes would go through a cycle of 'Shutting Down Due to Inactivity' followed by 'Shutdown Was Requested' and 'Initializing daemon'.

Example pasted from logfile;

Mar  4 00:20:51 BriansNemesis AptDaemon: INFO: Quiting due to inactivity
Mar  4 00:20:51 BriansNemesis AptDaemon: INFO: Shutdown was requested
Mar  4 00:20:54 BriansNemesis AptDaemon: INFO: Initializing daemon
Mar  4 00:25:55 BriansNemesis AptDaemon: INFO: Quiting due to inactivity
Mar  4 00:25:55 BriansNemesis AptDaemon: INFO: Shutdown was requested
Mar  4 00:25:58 BriansNemesis AptDaemon: INFO: Initializing daemon
Mar  4 00:31:58 BriansNemesis AptDaemon: INFO: Quiting due to inactivity
Mar  4 00:31:58 BriansNemesis AptDaemon: INFO: Shutdown was requested
Mar  4 00:32:01 BriansNemesis AptDaemon: INFO: Initializing daemon
Mar  4 00:38:01 BriansNemesis AptDaemon: INFO: Quiting due to inactivity
Mar  4 00:38:01 BriansNemesis AptDaemon: INFO: Shutdown was requested
Mar  4 00:38:08 BriansNemesis AptDaemon: INFO: Initializing daemon
Mar  4 00:43:09 BriansNemesis AptDaemon: INFO: Quiting due to inactivity
Mar  4 00:43:09 BriansNemesis AptDaemon: INFO: Shutdown was requested
Mar  4 00:43:10 BriansNemesis AptDaemon: INFO: Initializing daemon

Can anyone tell me if this is normal behavior?  I don't know enough about 'aptdaemon' to know what it is supposed to be doing or if this indicates a problem in my system.  Any information or suggestions would be greatly appreciated.

Brian Gage

---


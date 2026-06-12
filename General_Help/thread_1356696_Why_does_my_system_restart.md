---
title: "Why does my system restart?"
date: 2009-12-16
forum: General Help
---

### Post by kempy1000 on 2009-12-16
Hi

I have an ubuntu 9.10 machine, on startup mythwelcome runs.

If i leave the timeout to count down from 120 to 0 the system shuts down.

If i press 'm' then 'shutdown now' the system reboots!

I have checked these commands:
In mythtv-setup: shutdown command sudo shutdown -h now
In mythfrontend: shutdown command sudo shutdown -h now
In mythwelcome --setup: shutdown command sudo shutdown -h now

I am confused to why it reboots?!

If the user mythtv runs ```
 sudo shutdown -h now 
``` the system shuts down like it should.

mythbackend.log (Cleared then rebooted till auto restart (Should be auto shutdown))
```

2009-12-16 16:47:35.812 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-12-16 16:47:36.039 Using runtime prefix = /usr
2009-12-16 16:47:36.122 Using configuration directory = /home/mythtv/.mythtv
2009-12-16 16:47:36.284 Empty LocalHostName.
2009-12-16 16:47:36.380 Using localhost value of chimera
2009-12-16 16:47:36.553 New DB connection, total: 1
2009-12-16 16:47:36.773 Connected to database 'mythconverg' at host: localhost
2009-12-16 16:47:36.824 Closing DB connection named 'DBManager0'
2009-12-16 16:47:36.917 Connected to database 'mythconverg' at host: localhost
2009-12-16 16:47:37.559 Current MythTV Schema Version (DBSchemaVer): 1244
2009-12-16 16:47:39.223 MythBackend: Starting up as the master server.
2009-12-16 16:47:39.454 New DB connection, total: 2
2009-12-16 16:47:39.508 Connected to database 'mythconverg' at host: localhost
2009-12-16 16:47:39.839 New DB connection, total: 3
2009-12-16 16:47:40.023 Connected to database 'mythconverg' at host: localhost
2009-12-16 16:47:40.836 New DB scheduler connection
2009-12-16 16:47:40.950 Connected to database 'mythconverg' at host: localhost
2009-12-16 16:47:41.427 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-12-16 16:47:41.573 Main::Registering HttpStatus Extension
2009-12-16 16:47:41.698 Enabled verbose msgs:  important general
2009-12-16 16:47:41.955 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-12-16 16:47:44.140 Reschedule requested for id -1.
2009-12-16 16:47:44.931 Scheduled 2 items in 0.8 = 0.45 match + 0.34 place
2009-12-16 16:47:45.017 Seem to be woken up by USER
2009-12-16 16:47:46.064 I'm idle now... shutdown will occur in 120 seconds.
2009-12-16 16:47:47.015 MainServer::ANN Monitor
2009-12-16 16:47:47.087 adding: chimera as a client (events: 0)
2009-12-16 16:47:47.130 MainServer::ANN Monitor
2009-12-16 16:47:47.197 adding: chimera as a client (events: 1)
2009-12-16 16:49:01.504 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
SSH: Ok to shutdown
MPD: Ok to shutdown
Failed 0 Checks
Shutting down....
2009-12-16 16:49:50.493 CheckShutdownServer returned - OK to shutdown
2009-12-16 16:49:50.671 Running the command to set the next scheduled wakeup time :-
                                                sudo sh -c "/usr/bin/setwakeup.sh 1260991280"
2009-12-16 16:49:52.103 Running the command to shutdown this computer :-
                                                sudo shutdown -h now


```

Thanks
Chris

---

### Post by kempy1000 on 2009-12-16
I fixed this so just incase someone needs to know:

I changed all the 3 shutdown command values to:
```
 /home/mythtv/mythscript/shutdownpc.sh 
```

shutdownpc.sh
```

#!/bin/bash

sudo shutdown -h now

exit 0

```

not sure why it worked but it did!

---


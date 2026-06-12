---
title: "DB2 and Ubuntu 10.04"
date: 2012-02-21
forum: General Help
---

### Post by Triton46 on 2012-02-21
Hi All, 

I installed DB2 enterprise edition on an Ubuntu 10.04 server.  Everything works fine, however it's the automated startup that is giving me fits.  Now, before you reply...yes I RTFM all over google, here is what I tried:


[LIST]
[*]BUM
[*]init.d/update-rc.d
[*]init.d/chkconfig
[*]init.d/rc.local
[/LIST]

DB2 just won't startup after a reboot...however after bootup I can manually start/stop DB2 everytime.  I have tried two different scripts, one directly staring the DB manager (dbadmin start) and then the instance (db2start) and one list [here]("http://www.ibm.com/developerworks/forums/message.jspa?messageID=13941864#13941864") which starts DB2HOME/instance/db2istrt.

I've tried everything...literally! :confused:

Collecting a log, this is what I get back from trying to start DB Admin then the instance on reboot with update-rc.d set to default:

First Script:
> #!/bin/sh
su - dasusr1 -c "dbadmin start"
su - db2init1 -s "db2start"SQL1032N No start database manager command was issued.
SQL4410W The DB2 Administration Server is not active.

For some reason, the DB2 Admin Server does not get started on reboot..works fine if you run the script manually.

Second Script (from link):
> #!/bin/sh
#

[LIST=1]
[*]Script to start DB2 instance on bootup.
[/LIST]
 #
set -e

. /lib/lsb/init-functions

case "$1" in
start)
        /opt/ibm/db2exc/V9.1/instance/db2istrt 
        ;;
stop|restart|reload)
        ;;
esac

exit 0I have not tried to gather a log from this yet.

---

### Post by Triton46 on 2012-02-22
I added an append to log ">> /var/log/db2.log" to each call.

The call to "dbadmin start" from dasusr1 does not appear to run at all on reboot.  I commented out the call to "db2start" from db2inst1 and received no information from the logs.

Also, the call to db2istrt does not produce a log entry.

Again, all of these work when logged in and kicked off by root.

---

### Post by Triton46 on 2012-02-22
Still no joy...the script does fire (as seen by adding an echo of date) but produces nothing and starts nothing for DB2.

---

### Post by Triton46 on 2012-02-27
Anyone have some things to try to troubleshoot?

---

### Post by Triton46 on 2012-02-27
Finally!

It turns out there was not enough memory on startup but DB2 allows it if you click db2start or db2istart a second time.  This was the key:

[http://publib.boulder.ibm.com/infocenter/db2luw/v9r5/index.jsp?topic=/com.ibm.db2.luw.qb.server.doc/doc/t0008238.html](http://publib.boulder.ibm.com/infocenter/db2luw/v9r5/index.jsp?topic=/com.ibm.db2.luw.qb.server.doc/doc/t0008238.html)

I increased memory to the VM and reset the kernel memory parameters in /etc/sysctl.conf to what they listed.  Works on reboot now!

---


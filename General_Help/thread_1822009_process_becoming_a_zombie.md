---
title: "process becoming a zombie"
date: 2011-08-09
forum: General Help
---

### Post by Nubstar on 2011-08-09
Hello All,

My system specs are the following:
Ubuntu 11.04 - installed from CD
tranmission
sendEmail


When logging in the motd is indicating that I have 4 zombie processes. I ran ps -aux to list my processes and I can kill them based on PID.

I am using tranmission and it has the ability to run a script upon completion of a torrent download. ps -aux shows the following:

USER         PID   %CPU   %MEM      VSZ     RSS   TTY        STAT   START     TIME   COMMAND
104         6313    0.0    0.0        0       0   ?          Z      23:20     0:00   [torrent_complet] <defunct>

here is the script that is running upon completion of a torrent download:




#!/bin/bash

SUBJECT="Torrent Download Complete"

FROM_ADDR="email@localhost.localdomain"
TMPFILE=`mktemp -t transmission.XXXXXXXXXX`

echo "Transmission finished downloading \"$TR_TORRENT_NAME\", completed on: $TR_TIME_LOCALTIME" >$TMPFILE

sendEmail -t [email]email@address.com[/email] -f $FROM_ADDR -u $SUBJECT -m < "$TMPFILE"

rm $TMPFILE






Is there anything within this script that requires modification to stop it from becoming a zombie? If not, anything outside of the script that requires modifying?

I have read a bit on <defunct> processes and sort-of understand the parent-child relationship and storing of PID's.


Thank you in advance for any assistance provided!
-Nubstar

---

### Post by dcstar on 2011-08-10
> **Nubstar said:**
> Hello All,

My system specs are the following:
Ubuntu 11.04 - installed from CD
tranmission
sendEmail


When logging in the motd is indicating that I have 4 zombie processes. I ran ps -aux to list my processes and I can kill them based on PID.

I am using tranmission and it has the ability to run a script upon completion of a torrent download. ps -aux shows the following:

USER         PID   %CPU   %MEM      VSZ     RSS   TTY        STAT   START     TIME   COMMAND
104         6313    0.0    0.0        0       0   ?          Z      23:20     0:00   [torrent_complet] <defunct>

here is the script that is running upon completion of a torrent download:

```
#!/bin/bash

SUBJECT="Torrent Download Complete"

FROM_ADDR="email@localhost.localdomain"
TMPFILE=`mktemp -t transmission.XXXXXXXXXX`

echo "Transmission finished downloading \"$TR_TORRENT_NAME\", completed on: $TR_TIME_LOCALTIME" >$TMPFILE

sendEmail -t [email]email@address.com[/email] -f $FROM_ADDR -u $SUBJECT -m < "$TMPFILE"

rm $TMPFILE
```

Is there anything within this script that requires modification to stop it from becoming a zombie? If not, anything outside of the script that requires modifying?

I have read a bit on <defunct> processes and sort-of understand the parent-child relationship and storing of PID's.


Thank you in advance for any assistance provided!
-Nubstar

Try putting an **exit** command at the end.

---


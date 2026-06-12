---
title: "Tail log files to syslog?"
date: 2011-03-23
forum: General Help
---

### Post by nigelenki on 2011-03-23
Is there a way to tail a log file and send each line as a syslog event to a remote server?

---

### Post by gmargo on 2011-03-23
Here's a basic loop to do a line-by-line tail.  Netcat (**nc**) is used to send to the remote system.
```

#!/bin/sh
tail -F -q /path/to/log/file | \
while read -r line ; do
    # send to remote syslog daemon
    echo "<0>$line" | nc -w 1 -u destination.system.name 514
done

```The destination system must be configured to listen on udp port 514. It may only be listening for local connections (which is the **rsyslog** default.)

---


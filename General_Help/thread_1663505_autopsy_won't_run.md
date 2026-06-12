---
title: "autopsy won't run"
date: 2011-01-09
forum: General Help
---

### Post by COKEDUDE on 2011-01-09
Can someone tell me why autopsy won't run? 

```
~ $ autopsy

============================================================================

                       Autopsy Forensic Browser 
                  http://www.sleuthkit.org/autopsy/
                             ver 2.24 

============================================================================
Evidence Locker: /var/lib/autopsy
Start Time: Sun Jan  9 18:16:04 2011
Remote Host: localhost
Local Port: 9999

Open an HTML browser on the remote host and paste this URL in it:

    http://localhost:9999/autopsy

Keep this process running and use <ctrl-c> to exit
Can't open log: autopsy.log at /usr/share/autopsy/lib//Print.pm line 383.

```

---

### Post by piovisqui on 2011-01-09
you should run it as root

---

### Post by COKEDUDE on 2011-01-10
> **piovisqui said:**
> you should run it as root

Thank you. That was the problem.

---


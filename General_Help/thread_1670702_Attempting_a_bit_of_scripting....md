---
title: "Attempting a bit of scripting..."
date: 2011-01-19
forum: General Help
---

### Post by HarryTruman on 2011-01-19
I apologize if this is in the wrong thread.  I've never performed any bash scripting but I'm really interested in learning and figuring it all out.  The only problem is that I have NO idea where to start.  All of the tutorials I've checked out don't really explain why things are they way there are.  

I have something in mind for a script I'm wanting to create but I have no idea where to even start to get this doing what I want it to do.  If someone could provide a good link to learn from, or if they want to go all out with their own examples, that would be awesome!

1.	Auto-config
2.	Stop services
3.	Grep for running netbackup services.  If none are running, proceed.  If all services haven’t stopped, repeat 2.
4.	Start services

Here are the commands:
```
# Automatically reconfigures the backup drives; no input
/usr/openv/volmgr/bin/tpautoconf –a		

# Usually hangs for a second and requires a “y” input to continue stopping services
/usr/openv/netbackup/bin/bp.kill_all

# Needs to skip to repeat the above service stop unless ‘grep netbackup’ is the only running command
ps -aef | grep netbackup

# Doesn’t normally fail, no input
/usr/openv/netbackup/bin/bp.start_all
```

---

### Post by dracayr on 2011-01-19
```

#!/bin/bash
/usr/openv/volmgr/bin/tpautoconf –a
while ps -aef|grep netbackup|grep -v grep
do
yes|/usr/openv/netbackup/bin/bp.kill_all
sleep 5 #you may not need this, it just delays before repeating the bp.kill_all command.
done
/usr/openv/netbackup/bin/bp.start_all

```

---

### Post by HarryTruman on 2011-01-19
Well, that certainly does what I need it to do.  Thanks!

---


---
title: "custom init script w/ sleep command"
date: 2009-07-28
forum: General Help
---

### Post by AwkwardSilence on 2009-07-28
I have installed csync2 for file replication and need it set up to check for file updates every 5 seconds. This will be faster than a cron job should handle, so I've set up a simple init script that continuously runs with a 5 second sleep interval. I've added it to run at boot time with "update-rc.d csync2monitor defaults".

Everything works fine and the script begins running at boot time. However, when I go to reboot the computer it does not kill the process and the script continues to run. As soon as I manually kill the process the computer then reboots.

How do I get this to stop when I reboot?

Here is the script:
```

#!/bin/sh
while [ 1 ]
        do
                sleep 5
                csync2 -xvt
        done

```

---

### Post by AwkwardSilence on 2009-07-29
Any ideas?

I tried writing an LSB init script with start/stop functions, but that made some other services not start on bootup.

---

### Post by AwkwardSilence on 2009-08-14
This script is still stopping my server from rebooting.
Any suggestions would be appreciated.

Thanks

---

### Post by DaithiF on 2009-08-14
Hi,
I think you should start with the /etc/init.d/skeleton file -- make a copy & edit it to call your script.  this should give you most of the boilerplate you need for an init script.

---

### Post by sdennie on 2009-08-14
The key is to not have your infinite loop in the init script itself.  As said above, use an init script to call your script as if it were a daemon.  That should do the proper bookkeeping and allow you to properly start/stop/restart/etc your script.

---

### Post by Slim Odds on 2009-08-14
> **sdennie said:**
> The key is to not have your infinite loop in the init script itself.  As said above, use an init script to call your script as if it were a daemon.  That should do the proper bookkeeping and allow you to properly start/stop/restart/etc your script.

Or you can also use the trap command to catch the proper signals and deal with them. SIGTERM is the one you should look at.

---


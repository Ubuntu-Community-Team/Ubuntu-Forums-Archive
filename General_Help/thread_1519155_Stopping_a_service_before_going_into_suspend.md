---
title: "Stopping a service before going into suspend"
date: 2010-06-27
forum: General Help
---

### Post by allanlewis on 2010-06-27
I believe that my PC, running Lucid, is hanging when trying to go into suspend because of mythtv-backend. If I stop the service and then suspend, it works fine and comes back up fine, and then I have to start the service again. I tried putting the following script into /etc/pm/sleep.d but it isn't working:
```
#!/bin/sh

# Arguments can be:
#    "suspend suspend"
#    "resume suspend"
#    "thaw hibernate"

case "$1" in
        "suspend"
                stop mythtv-backend
                ;;
        "resume"
                start mythtv-backend
esac
```
Is there something wrong with this script (courtesy [Zorael]("http://ubuntuforums.org/showpost.php?p=8437073&postcount=2")) or is there something else I need to do? Perhaps it's because MythTV keeps a connection to my USB TV tuner open and that's what's blocking suspend?

---


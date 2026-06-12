---
title: "Run a script after resuming from suspend _and_ network is back online?"
date: 2011-01-31
forum: General Help
---

### Post by sexcopter on 2011-01-31
Hi, this may seem daft, but I'd like a simple command to run when I open my laptop. However, the command is wget, and it needs an internet connection in order to succeed. Don't really know bash, but I put together the following in /etc/pm/sleep.d/99-update-wallpaper.sh

```

#!/bin/bash

case "$1" in
        thaw|resume)
                ping -c 1 ibm-lucid
                foo=$?
                echo $foo >> /home/james/foo.log

                while [ "$foo" -ne "0" ] ; do
                   sleep 5
                   ping -c 1 ibm-lucid
                   foo=$?
                   echo $foo >> /home/james/foo.log
                done

                /usr/bin/wget -U Mozilla/5.0 -O /home/james/wallpaper.jpg http://static.die.net/earth/mercator/1600.jpg
                ;;
        *)
                ;;
esac
exit $?

```

So, this seems to work, but there's a problem. Whatever deals with connecting the wifi (network manager?) seems to be waiting for the script to exit before doing its thing. Thus we seem to get stuck in a loop.

So... it looks like this _isn't_ the way to go about what I'm trying to do. I'm wondering if there's another place for this script that won't hold up network manager (or other stuff) while it's pinging every 5 seconds waiting for a connection.

Make sense? Please let me know if there's an entirely different and much simpler way to achieve this... my current approach seems very convoluted.

Thanks,
James

---


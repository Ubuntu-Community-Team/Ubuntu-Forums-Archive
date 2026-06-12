---
title: "Irexec not exceuting kill commands"
date: 2010-01-17
forum: General Help
---

### Post by kempy1000 on 2010-01-17
Hi,

Irexec will not execute any kill commands.

I am trying to kill the process mplayer with my remote.

This is the script i have:
```

#!/bin/sh

if ps ax | grep -v grep | grep mplayer > /dev/null
then
        echo "Stopping mplayer..."
        #sudo pkill mplayer
        #sudo killall mplayer
        sudo kill `pidof mplayer`
else
        echo "Starting mplayer..."
        sudo mplayer -playlist http://media-ice.musicradio.com/GalaxyYorkshire.m3u
fi

exit 0

```
(I have tried all commented out code)

I am trying to make the same button that starts the radio kill the radio too.

However when i press the button the radio starts fine. Press it again then another process of mplayer starts? But doesn't kill the original process.

Thanks
Chris

---


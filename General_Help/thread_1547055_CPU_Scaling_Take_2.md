---
title: "CPU Scaling Take 2"
date: 2010-08-06
forum: General Help
---

### Post by _h_ on 2010-08-06
In reference to this [thread]("http://ubuntuforums.org/showthread.php?t=1542203"), sort of.

I just did a complete fresh install of ubuntu last night after I broke something, and now whenever I boot up into ubuntu my cpu scaling is stuck into performance rather than ondemand as it should be. I've started to use my battery on my Gateway ML6732 again, and ubuntu starting into performance mode for scaling is a really unnessecary waste of battery life.

What's funny is, my /etc/init.d/ondemand file has ondemand set, and not performance.

/etc/init.d/ondemand;

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          ondemand
# Required-Start:    $remote_fs $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Set the CPU Frequency Scaling governor to "ondemand"
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

case "$1" in
    start)
        start-stop-daemon --start --background --exec /etc/init.d/ondemand -- background
        ;;
    background)
    sleep 60 # probably enough time for desktop login

   [B] for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
    do
        [ -f $CPUFREQ ] || continue
        echo -n ondemand > $CPUFREQ
    done
    ;;[/B]
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```

---

### Post by _h_ on 2010-08-06
Think this might have been a bug, as it seems to be working correctly now and upon reboot is now set to ondemand as it should be for both AC power and battery power.

---


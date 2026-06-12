---
title: "Easily change between &quot;performance&quot; and &quot;ondemand&quot; frequency governors"
date: 2010-06-18
forum: General Help
---

### Post by Asmodai on 2010-06-18
Hey,

I'm looking for an easy way to quickly switch between these two modes. I'm currently using four separate Gnome panel applets (one for each core), but I'd like to change the setting for all cores at the same time.
I tried a script that runs cpufreq-selector for each core, but for some odd reason cpufreq-selector does not terminate after having changed the frequency, so the script never finishes its job.

Any other ideas?

---

### Post by dcstar on 2010-06-19
> **Asmodai said:**
> Hey,

I'm looking for an easy way to quickly switch between these two modes. I'm currently using four separate Gnome panel applets (one for each core), but I'd like to change the setting for all cores at the same time.
I tried a script that runs cpufreq-selector for each core, but for some odd reason cpufreq-selector does not terminate after having changed the frequency, so the script never finishes its job.

Any other ideas?

This is the /etc/init.d script that 10.04 runs to change things, edit to suit:

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

	for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
	do
		[ -f $CPUFREQ ] || continue
		echo -n ondemand > $CPUFREQ
	done
	;;
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


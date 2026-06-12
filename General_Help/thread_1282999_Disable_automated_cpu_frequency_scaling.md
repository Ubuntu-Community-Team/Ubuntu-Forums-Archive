---
title: "Disable automated cpu frequency scaling?"
date: 2009-10-05
forum: General Help
---

### Post by orange_roughy on 2009-10-05
Hi,

There are lots of existing posts about this. I've read many (all?) of them, and tried all suggestions I could find. None of the solutions in those threads work.

Ubuntu 9.04 Jaunty Jackalope doesn't scale my CPU frequency correctly. It is very often set to the lowest setting--800 MHz (Intel 2.27 GHz Core2 Duo in a Dell Latitude E6400). Trying to change it from the command-line or from CPU Frequency Scaling Monitor 2.26.1 has no effect. For this reason, I want to manually scale the CPU frequency or completely disable it to remain at max.

In my case, 99.999% of the time CPU freq. scaling isn't necessary since I'm running on AC power, and my CPU core temps are very cool (40 degree C or under). Yet Unbuntu insists on running at 800 MHz. This happens from cold boot as well as resume from suspend and hibernate.

Disabling SpeedStep in the BIOS forces the CPU cores to operate at their lowest frequency. None of the config file mucking around I've done has helped.

The governor settings (Conservative, OnDemand, Performance, Powersave) appear to "stick" in CPU Frequency Scaling Monitor, but there is no actual change in performance when they are selected. Selecting any of the actual frequencies (800 MHz, 1.60 GHz, 2.27 GHz) has no effect--the monitor still shows 800 MHz.

What can I do? I am at my wits' end.

Thank you,
orange roughy

---

### Post by gidyeo on 2009-11-06
Orange_roughy,

Sorry i didn't see your reply to me previous post on the other thread on similar topic.

Did you try to follow the instructions and disable "ondemand" cpu governor?
[http://ubuntuforums.org/showpost.php...65&postcount=7](http://ubuntuforums.org/showpost.php...65&postcount=7)

If not can you please post your /etc/init.d/ondemand here?

---

### Post by orange_roughy on 2009-11-06
Hi gidyeo,

that link doesn't bring up a forum topic.

output of /etc/init.d/ondemand is:

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

Note I've since upgraded to Karmic.

---

### Post by gidyeo on 2009-11-07
try change:
echo -n ondemand > $CPUFREQ
to:
echo -n performance > $CPUREQ

i did this in Jaunty and it works. Think Karmic is more or less the same.

---


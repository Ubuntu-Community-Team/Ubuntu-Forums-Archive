---
title: "Set default CPU speed and governor?"
date: 2010-09-29
forum: General Help
---

### Post by Bazirker on 2010-09-29
While the CPU Frequency Scaling Monitor is an excellent tool for selecting my notebook's CPU speed and governor on the fly, it's irritating that it doesn't remember my settings on rebooting.  How do I change the default CPU scaling settings?  (It currently defaults to ondemand which gives me poor performance in virtual machines and during video playback.)

---

### Post by mc4man on 2010-09-29
You haven't really mentioned what you actually want. In the past I do remember installing and running something that changes the values - wasn't that thrilled.

In my case I like  ondemand but did see issues with some videos and certain other 'situations' where ondemand resulted in poor performance, mainly because it stayed at min or close to min. freq.

What I decided to do was work with what does happen and alter it to suit my needs.
By default you boot to performance (full freq.) and after 60 secs drop to ondemand.
What controls this is a script - /etc/init.d/ondemand

So in my case I felt the default upscaling threshold was set to high - where that's defined I couldn't find ( the default value is 95

So instead edited the ondemand script to lower the value making upscaling more likely and 'quicker' and it's made a demonstrable difference here. 

I guess I'm mentioning for 2 reasons - you may want to try lowering the threshold or I can see ways to use the ondemand script to do other things if desired. (a matter of the obvious or trial & error -  the script can adjust some of what you see in /sys/devices/system/cpu/

Here's my current ondemand - blue section was added to lower the up value

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
[COLOR="Blue"]
	for CPU_THRESHOLD in /sys/devices/system/cpu/cpufreq/ondemand/up_threshold
	do
		[ -f $CPU_THRESHOLD ] || continue
		echo -n 65 > $CPU_THRESHOLD
	done[/COLOR]
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

### Post by Bazirker on 2010-09-29
> **mc4man said:**
> You haven't really mentioned what you actually want. In the past I do remember installing and running something that changes the values - wasn't that thrilled.

Yes, I suppose I didn't mention what I wanted.  As of my initial post, I wanted to set the CPU scaling to default to performance (i.e. to not scale at all but run full tilt all the time) but you actually have made a very good suggestion about adjusting the ondemand governor.  After all, it's what I use on my phone, why not on my laptop?  I'm trying out reducing the up threshold and might adjust sampling rate too, although it looks like the default should be plenty fast.

Thanks!

---


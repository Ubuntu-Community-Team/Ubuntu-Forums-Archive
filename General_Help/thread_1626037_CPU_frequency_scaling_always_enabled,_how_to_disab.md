---
title: "CPU frequency scaling always enabled, how to disable"
date: 2010-11-19
forum: General Help
---

### Post by suzumeuta on 2010-11-19
When I boot my machine (using a dual core 2ghz CPU) I always find myself out of "performance" mode (which I need), using only 1ghz per core.
While this is easily fixable with "sudo cpufreq-set -g performance", I don't seem to be able to do it before having control of the machine. I would like to be able to boot with my CPU at full power.
I would prefer to disable whatever is scaling down my CPUs to having to inject cpufreq-set to change governor. Anyone has any hint?

I use default Ubuntu but I boot into a KDE4 desktop. But the same issue happens booting into the Gnome desktop.

---

### Post by Ocxic on 2010-11-19
there is a panel applet that will let you control that, no terminal required. 

as for your question about setting a default, there is a way to do it, i just don't know how.

---

### Post by suzumeuta on 2010-11-19
Yeah, there is a gnome-panel applet, but that only works in gnome. That applet is actually what made me notice I was running at half-power :P
I also know it must be possible to make that before the DE loads, but I don't remember where either...hope someone else does.

---

### Post by mc4man on 2010-11-19
If you don't find a way to change otherwise - 

Edit: this applies to lucid and maverick - see you list hardy, no idea there if the same

I actually prefer ondemand but, at least here, don't think it always scales up when needed.
To adjust that added a section to /etc/init.d/ondemand

Anyway, looking at the script (which switches from performance at boot to ondemand after 60 sec.'s) I suppose a simple one word edit will do what you wish.
Change the blue in the line in this section line to performance
(you may wish to first ck. in /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors to make sure it's avail., though should be
```
for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
	do
		[ -f $CPUFREQ ] || continue
		echo -n [COLOR="Blue"]ondemand[/COLOR] > $CPUFREQ
```

Or if you first wish to try lowering the up_threshold value let me know.. I find it does make a difference in certain areas

---

### Post by sdennie on 2010-11-20
mc4man has given some really great advice on this.  Your info says you are running 8.04 but, you state you are running KDE4 so, I have to assume you are running a later version of Ubuntu.  If you are indeed running 8.04, you should be able just put your cpufreq-set command in /etc/rc.local.  But, as mc4man alluded to, ondemand really is the better governor for most cases.  It's just that by default the up_threshold is set to a very poor value in newer versions of Ubuntu.

---

### Post by psusi on 2010-11-20
You realize that the default policy only slows down the cpu when you AREN'T USING IT?

---

### Post by sdennie on 2010-11-20
> **psusi said:**
> You realize that the default policy only slows down the cpu when you AREN'T USING IT?

That's not quite true.  It used to be the case that the ondemand governor would, by default, shoot the CPU to max speed with very little provocation and keep it there.  When that was true, it was difficult to notice the difference between ondemand and performance.  However with more recent versions of Ubuntu, the up_threshold for the ondemand governor has been set so high that using ondemand can cause noticeable performance problems for anything that can't keep the CPU usage above like 95%.

So, to re-quote you: "You realize that the default policy only speeds up the CPU when you are REALLY USING IT?"

---

### Post by mc4man on 2010-11-20
> You realize that the default policy only slows down the cpu when you AREN'T USING IT?
While that's true I have demonstable instances where performance is affected by the default up_threshold value(95).

The way I adjust (value used is personal preference, added blue section
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

	[COLOR="Blue"]for CPU_THRESHOLD in /sys/devices/system/cpu/cpufreq/ondemand/up_threshold
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

Because I'm not sure if the formatting actually matters (tab, half tab indents on some lines) I may not copy directly from here, just a guide

---

### Post by suzumeuta on 2010-11-20
> **psusi said:**
> You realize that the default policy only slows down the cpu when you AREN'T USING IT?

Yes I do, the problem is that it refuses to scale *up* for some reason. I can only get it to full speed when firefox hangs up or something. Otherwise it doesn't even scale while gaming or compiling!

Anyway, your solution worked fine, mc4man. Thanks a lot!

EDIT: Also, using Maverick, forgot to update that!

---

### Post by psusi on 2010-11-20
Oh, I didn't realize it had been changed.  95 does seem a little too high.

---


---
title: "Ondemand vs Performance"
date: 2010-07-31
forum: General Help
---

### Post by request_another on 2010-07-31
I just wanted to know if having my laptop set to ondemand, will this affect performance in any way? I realize it increases the clock speed to performance when the CPU is under load, but does the time it take to go from ondemand to performance affect speed? Will there be any noticeable difference between the two setups?

I have a dual core intel at 2.2GHz when in performance. When ondemand is set with no load it downclocks to 800Mhz.

---

### Post by x-shaney-x on 2010-07-31
In general I don't notice any major differences.
However, if you like your desktop affects then you might (I do).

For example, something you could do as a little experiment:

On performance, open a window and just leave it there and do nothing for a few moments then minimize it.

Then do exactly the same with on-demand.
You will likely notice the animation jumps.

Basically I assume there has to be that tiny delay where whatever wants to use that bit more power has to tell the computer and the computer has to respond accordingly and allocate that extra power.

We are talking milliseconds here but it does seem to be the case.

---

### Post by Sylslay on 2010-07-31
Main diffrence is power use by CPU, You Heat more CPU when use only Perfomnace mode, And on speed CPU, made after 2007 You don't see much diffrents on ordn:oary softwere, exept games.

---

### Post by 3rdalbum on 2010-07-31
Pretty much as soon as your CPU hits real load, the OnDemand governor increases the speed of the CPU to handle it. Intel did some tests and concluded that you should just use OnDemand - it'll save power and be pretty much as fast in real life. I'd tend to trust Intel on this as they DO make the CPUs :-)

---

### Post by request_another on 2010-07-31
im trying out ondemand and i like it  alot cause my system runs a lot cooler too. i think i'll keep it for the day to test it.

---

### Post by mc4man on 2010-07-31
The only issue I had in lucid with the ondemand, and this may certainly be subjective, is the default up_threshold seemed too high  - 95

Adjusted it down to 75  or 65 (atm 65) and I thought performance was a bit 'snappier' in certain area's, - some web pages, playback of hd video's ect.

Did so here by editing /etc/init.d/ondemand - adding the blue section
(if trying probably best to back up current ondemand, though it is an easy edit - I'd just save a copy of the orig. script somewhere - 
Ex.
cp /etc/init.d/ondemand ~/Documents/


```
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

[COLOR="Blue"]        for CPU_THRESHOLD in /sys/devices/system/cpu/cpufreq/ondemand/up_threshold
	do
		[ -f $CPU_THRESHOLD ] || continue
		echo -n 65 > $CPU_THRESHOLD
	done[/COLOR]
	;;
    restart|reload|force-reload)
```

---

### Post by request_another on 2010-07-31
what is the up_threshold exactly?

---

### Post by mc4man on 2010-07-31
> what is the up_threshold exactly?
Well "exactly" you'll need to research - I've read about how it works some - not enough to say.

In use the value of the up_threshold affects when and how much your cpu scales up.
I don't think there is a perfect value for everyone - I found the 65-75 range best here for my use, others may find a different value or the default more suitable.

A lower threshold would reduce  battery life by small amount, - not an issue here.

I looked but didn't find anywhere to set this in a gui, though there should be, even better would be separate for ac and battery if that was a concern.

---


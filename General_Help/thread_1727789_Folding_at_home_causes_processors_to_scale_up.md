---
title: "Folding at home causes processors to scale up"
date: 2011-04-12
forum: General Help
---

### Post by Pollox on 2011-04-12
I would like to run folding at home on my laptop again. It used  to run great (a few years ago), and not cause the cpu to scale up, but now I have to enter ```
echo 1 | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/ondemand/ignore_nice_load
``` each time I reboot to keep the cpu cores at their lowest frequencies (otherwise the machine gets very hot, which I don't like).

I have tried the instructions I found on:
[https://help.ubuntu.com/community/FoldingAtHome#Folding%20on%20a%20Notebook](https://help.ubuntu.com/community/FoldingAtHome#Folding%20on%20a%20Notebook) and [https://wiki.edubuntu.org/FoldingAtHomeTeamUbuntu/HowTo#CPU%20Frequency%20Scaling%20Issues](https://wiki.edubuntu.org/FoldingAtHomeTeamUbuntu/HowTo#CPU%20Frequency%20Scaling%20Issues),
which say to either add
```
echo 1 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/ignore_nice_load
echo 1 > /sys/devices/system/cpu/cpu1/cpufreq/ondemand/ignore_nice_load
```
or
```
echo 1 | tee /sys/devices/system/cpu/cpu*/cpufreq/ondemand/ignore_nice_load > /dev/null
```
to /etc/rc.local, but neither worked for me.

---

### Post by Pollox on 2011-05-03
Bump. Anyone have any ideas?

---

### Post by sbraz on 2011-08-27
yes i do. :)

by default on ubuntu there's a script on runlevel 5 which sets the governor to ondemand 60 seconds after the script is called.
**/etc/init.d/ondemand** (i've added some things, written in [COLOR="Red"]red[/COLOR] to try to fix your problem without rc.local)

```
root@sbraz-netbook:/etc/init.d# cat ondemand 
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
	**sleep 60 # probably enough time for desktop login**

	for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
	do
		[ -f $CPUFREQ ] || continue
		[B]echo -n ondemand > $CPUFREQ
                [COLOR="red"]sleep 2
                echo 1 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/ignore_nice_load
                echo 1 > /sys/devices/system/cpu/cpu1/cpufreq/ondemand/ignore_nice_load[/COLOR][/B]
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
recent kernels are compiled with the default governor set to performance.
basically your rc.local runs before the 60 seconds delay specified in /etc/init.d/ so it fails to apply the setting since the governor is still on performance mode (by kernel).

btw, i don't get why this script has to be hid like that... it took me hours to figure out why the os were "randomly" switching to ondemand while the kernel were set to conservative. :confused:



if you need help running folding@home only when you are on ac power just tell me. :)

---

### Post by dcstar on 2011-08-28
> **Pollox said:**
> I would like to run folding at home on my laptop again. It used  to run great (a few years ago), and not cause the cpu to scale up.

Simply install the **powernowd** package.

It ignores "niced" processes by default and I use it for my BOINC for just this issue.

---


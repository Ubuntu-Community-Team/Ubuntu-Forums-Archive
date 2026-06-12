---
title: "Script won't run from cron - tried everything"
date: 2011-04-21
forum: General Help
---

### Post by GameboyRMH on 2011-04-21
I'm pulling my hair out trying to get this script, which normally works fine, to run from cron. This is far from my first custom cron script, but it's the first to give trouble! I've added PATH directives (never had to do that before) but it still didn't work. I also tried setting absolute paths, that didn't help either. If I add a line that echoes a string to a file as a test at the end of the script, the file appears, so I know the script is executing, it just looks like the cpufreq-set commands aren't working.

The purpose of this script is to adjust the maximum SpeedStep setting on my now passively-cooled home server to keep the CPU from getting too toasty.

```
#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/games:/usr/local/sbin:/usr/local/bin

# set temp above which to drop the maximum frequency
scaledowntemp=`echo -n "62"`
# set temp below which to reset the maximum frequency
scaleuptemp=`echo -n "59"`
# get cpu temperature
cputemp=`sensors | grep "Core 0" | gawk '{print $3 }' | sed -e 's/+//g' | sed 's/....$//'`
if [ $cputemp -lt $scaleuptemp ] # if temp is in acceptable range, set max frequencies free
then
    cpufreq-set -c 0 -u 2.81Ghz
    cpufreq-set -c 1 -u 2.81Ghz
fi
if [ $cputemp -gt $scaledowntemp ] # if temp is too high, limit cores to 1.6Ghz
then
    cpufreq-set -c 0 -u 1.61Ghz
    cpufreq-set -c 1 -u 1.61Ghz
fi
```

---

### Post by GameboyRMH on 2011-04-21
Tried another version that sets the frequencies using echo instead of cpufreq-set:

```
#! /bin/sh


PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/games:/usr/X11R6/bin:/usr/local/sbin:/usr/local/bin:/$HOME/bin:/usr/local/scripts

# set temp above which to drop the maximum frequency
scaledowntemp=`echo -n "62"`
# set temp below which to reset the maximum frequency
scaleuptemp=`echo -n "59"`
# get cpu temperature
cputemp=`sensors | grep "Core 0" | gawk '{print $3 }' | sed -e 's/+//g' | sed 's/....$//'`
if [ $cputemp -lt $scaleuptemp ] # if temp is in acceptable range, set max frequencies free
then
    echo 2803000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
    echo 2803000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq
fi
if [ $cputemp -gt $scaledowntemp ] # if temp is too high, limit cores to 1.6Ghz
then
    echo 1610000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
    echo 1610000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq
fi
```

Again, works fine if I run it from a terminal, but frequencies don't change if cron runs it :confused:

---

### Post by DaithiF on 2011-04-22
Hi, capture output from the cron job to check for errors.
```
* * * * * /path/to/your/script** > /path/to/some/logfile 2>&1**

```

also add an echo statement to output the value of the cputemp variable, since that drives what gets executed.

also, (though i don't think this is the problem), the way you set the scaleup/down variables seems a bit bizarre to me ... why not just **scaledowntemp=62**?

---

### Post by GameboyRMH on 2011-04-23
Alright, getting somewhere! Here's what I got from the log file:

```

CPUtemp=
[: 20: -lt: unexpected operator
[: 27: -gt: unexpected operator

```So CPUtemp isn't being set (if I run the script from a terminal it says CPUtemp=40 or whatever) and cron doesn't like the -lt and -gt operators. 

Also the scaleup/down thing is intentional. I want the CPU temperature to drop to that temperature before it scales up again, otherwise the temp could climb too high again in under 1 minute. I'm using a burnP6 thread for each core in testing to simulate a worst-case scenario in terms of CPU usage.

Edit: OK what's causing the cputemp variable to go blank when run through cron is this:

```
sed 's/....$//'
```If I take that out, CPUtemp shows up but with a trailing decimal digit, and I need to trim those last two characters to turn it into a plain integer.

---

### Post by GameboyRMH on 2011-04-23
YES got the script working! Here is the final script, I've left the cpufreq-set lines in there but commented out:

```

#! /bin/sh

MAILTO=""

# set temp above which to drop the maximum frequency
scaledowntemp=62
# set temp below which to reset the maximum frequency
scaleuptemp=59
# get cpu temperature
cputemp=`sensors | grep "Core 0" | awk '{print $3}' | sed -e 's/+//g' | head --bytes=-3`
echo CPUtemp=$cputemp
if [ $cputemp -lt $scaleuptemp ] # if temp is in acceptable range, set max frequencies free
then
    echo 2803000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
    echo 2803000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq
    #cpufreq-set -c 0 -u 2.81Ghz
    #cpufreq-set -c 1 -u 2.81Ghz
fi
if [ $cputemp -gt $scaledowntemp ] # if temp is too high, limit cores to 1.6Ghz
then
    echo 1610000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
    echo 1610000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq
    #cpufreq-set -c 0 -u 1.61Ghz
    #cpufreq-set -c 1 -u 1.61Ghz
fi

```

---

### Post by DaithiF on 2011-04-23
Hi, glad you got it working.  just for the record, my point about the scaleup/down variables was not about what you use them for, but the way you set their values.  there is no need to do it the way you do with the echo command, you can just assign their values directly:
[B]scaleuptemp=62
[/B]

---

### Post by GameboyRMH on 2011-04-23
> **DaithiF said:**
> Hi, glad you got it working.  just for the record, my point about the scaleup/down variables was not about what you use them for, but the way you set their values.  there is no need to do it the way you do with the echo command, you can just assign their values directly:
[B]scaleuptemp=62
[/B]

Oh right, that is unnecessary, I was testing something earlier and forgot to change it back :redface:

---


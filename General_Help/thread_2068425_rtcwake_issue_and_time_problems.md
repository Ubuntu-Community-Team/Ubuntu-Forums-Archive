---
title: "rtcwake issue and time problems"
date: 2012-10-09
forum: General Help
---

### Post by blind0wl on 2012-10-09
Hi All, hoping I can get some advice on an issue I am having with the rtcwake command to suspend my server during business hours (I only use it out of hours and like to preserve electricity!)

I have been using a script that I found on google as per below:

[http://askubuntu.com/questions/61708/automatically-sleep-and-wake-up-at-specific-times]("http://askubuntu.com/questions/61708/automatically-sleep-and-wake-up-at-specific-times")

```
#!/bin/bash

# Auto suspend and wake-up script
#
# Puts the computer on standby and automatically wakes it up at specified time
#
# Written by Romke van der Meulen <redge.online@gmail.com>
# Minor mods fossfreedom for AskUbuntu
#
# Takes a 24hour time HH:MM as its argument
# Example:
# suspend_until 9:30
# suspend_until 18:45

# ------------------------------------------------------
# Argument check
if [ $# -lt 1 ]; then
    echo "Usage: suspend_until HH:MM"
    exit
fi

# Check whether specified time today or tomorrow
DESIRED=$((`date +%s -d "$1"`))
NOW=$((`date +%s`))
if [ $DESIRED -lt $NOW ]; then
    DESIRED=$((`date +%s -d "$1"` + 24*60*60))
fi

# Kill rtcwake if already running
sudo killall rtcwake

# Set RTC wakeup time
# N.B. change "mem" for the suspend option
# find this by "man rtcwake"
sudo rtcwake -l -m mem -t $DESIRED &

# feedback
echo "Suspending..."

# give rtcwake some time to make its stuff
sleep 2

# then suspend
# N.B. dont usually require this bit
#sudo pm-suspend

# Any commands you want to launch after wakeup can be placed here
# Remember: sudo may have expired by now

# Wake up with monitor enabled N.B. change "on" for "off" if 
# you want the monitor to be disabled on wake
xset dpms force on

# and a fresh console
clear
echo "Good morning!"
```

It has worked great on my other machines but for some reason it just never wakes up at the expected time.

I did some investigation and found that if I just pull out the rtcwake portion of the script the time it actually says it will wake up is great deal longer than when I asked it to.  So in fact the script is fine, I think its purely a time based issue on the server.  I have checked date, hwclock and the both come up with the same time:

```
$date
Tue Oct  9 17:37:16 EST 2012

$sudo hwclock
Tue 09 Oct 2012 17:37:22 EST  -0.460623 seconds

```

I've used rtcwake -t (Absolute time) and worked out the time required for the console input...so:

```
$date +s%
$1349768392

$sudo rtcwake -l -m mem -t 1349771992
```

This should take the current time and add 1 hour to it (3600 seconds) so the wake up time will be 18:42 EST.  If I run this I get:

```
rtcwake: wakeup from "mem" using /dev/rtc0 at Wed Oct 10 04:39:52 2012
```

The clock seems to be out 10 hours...forward...which isnt possible according to the timezone Im in (+10).

Not only that but when I send this command the server sleeps...for a few seconds and wakes up straight away...

Sorry for the long winded post, but wanted to make sure I gave as much detail as possible.

Cheers

Blindy

---

### Post by cryptotheslow on 2012-10-09
What timezone is your hardware (BIOS) set to?

I find hwclock is a bit odd when trying to determine that.

For example, this machine's BIOS is set to UTC yet hwclock returns a BST time (my local zone):
```
crypto@ubulaptop1204:~$ sudo hwclock
[sudo] password for crypto: 
Tue 09 Oct 2012 20:18:47 BST  -0.322582 seconds

```This is a script I cobbled together to make sure a server was powered up at a given time, it writes directly to the RTC wakealarm rather than using rtcwake:
```

#!/bin/bash
# Script to set RTC wakeup time to make sure ubuserver is awake when remote backup arrives.
# Need to make sure ubuserver is up at 21:00 every day.
# So we set RTC wakeup to 21:00 UTC for today if time now is <21:00 and for 21:00 tomorrow if later on.
# This script will be called at ubuserver shutdown and set the next wakeup time.

# Let's find what the UTC hour is now
utchournow=$(date -u +%H)
echo UTC Hour now is: $utchournow

# Is it before 21:00?
if [ ! $utchournow -ge 21 ]; then
    before21=1
    echo before21: $before21
else
    before21=0
    echo before21: $before21
fi

if [ $before21 -eq 1 ]; then
    # Earlier than 21:00 let's get UTC 21:00 for today and put it in a var
    waketime=$(date -u --date="today 21:00:00" +%s)
    echo waketime - secs since epoch utc: $waketime
else
    # Later than 21:00 let's get UTC 21:00 for tomorrow and put it in a var
    waketime=$(date -u --date="tomorrow 21:00:00" +%s)
    echo waketime - secs since epoch utc: $waketime
fi

# Let's clear and then write the RTC wake event
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo $waketime > /sys/class/rtc/rtc0/wakealarm

```Save something like that in /etc/init.d and symlink to it in /etc/rc0.d/ and /etc/rc6.d so it gets called everytime the server is shutdown or restarted.

You can then just use a really simple cron entry to shutdown the server at your desired time.

The short answer would have been - I suspect the BIOS time on your current machine is on UTC whilst the others were on localised time (or vice versa) which is throwing your script out by your local timezone offset from UTC.

Your script calls rtcwake with the -l flag (localised time), so your fix might be as simple as changing that for the -u flag (utc). Might be a more sensible approach to fix it rather than changing the BIOS clock which could have knock on effects.

---


---
title: "Server wakes automatically at set time - how to disable"
date: 2009-10-14
forum: General Help
---

### Post by JustGus on 2009-10-14
For some reason my server has taken to waking at the same time every evening.  I had a look around at various scripts (crontab, hwclock, acpid) to see if there was a setting that enables this, but can't find anything that would seem to explain it.  

Can anyone out there point me in the right direction to fix this and get my machine to enjoy a quiet sleep.  I've got a four year old who frequently wakes me in the middle of the night, so the last thing I want is something else waking up when it should be resting. :)

Thanks in advance for any help!

---

### Post by Aearenda on 2009-10-14
It should be possible to disable timed wake-up in the machine's BIOS settings available at start-up.

---

### Post by JustGus on 2009-11-30
I'm still trying to figure out how to make this stop and would be grateful for any tips.  
Had a look at the BIOS settings, but not sure what the command is that specifically disables waking at a set time (I've got one of the setting "Wake on Ring" enabled, as this allows me to use Wake On LAN, which I need).  
I've done a hunt around to try and find some command (e.g. in the CRON settings) that would explain why every evening the machine wakes at 8:24, but I've not been able to find anything.
Thanks in advance for any advice!

---

### Post by Aearenda on 2009-12-01
Timed wake-up is controlled by the BIOS, and the time can be updated by ACPI settings in place as the operating system shuts down, [as described here]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake"). You can see what time is set on Ubuntu 8.04 by```
cat /proc/acpi/alarm
```
On kernel 2.6.22 and later (eg Ubuntu 9.10) it has moved to /sys/class/rtc/rtc0/wakealarm.

On 8.04 you can set the time like this:```
sudo -i
echo "+00-00-00 06:35:00" > /proc/acpi/alarm
exit
```
Note that this sets the wake time to be 6 hours and 35 minutes from the moment of running the command. Using this, you could at least set the wake to a sensible time!

Setting the time on later systems is harder. [This link]("http://www.mythtv.org/wiki/ACPI_Wakeup") explains more about the whole setup.

Unfortunately, setting a wake time is one thing, turning it off is another. That's why I suggested you look for a way to disable it in the BIOS. Unfortunately BIOS setup screens vary a lot, so I can't tell you exactly what to look for; but if it has a "wake time" setting, there should be a disable setting too. 

Another idea is to look for this line in /etc/default/rcS, and remove it if it is there: ```
HWCLOCKACCESS=no
```

By the way, have you ever modified /etc/init.d/hwclock.sh? By default, code in here in 8.04 defeats the wake-on-alarm process.

Does the machine wake if disconnected from the LAN? I wonder if something else is sending a WOL command.

If the worst comes to the worst, maybe a BIOS reset would clear it, but make sure you have noted down all the customised settings before you try that.

---

### Post by JustGus on 2009-12-04
Thanks so much for the suggestions, Aearenda.  You figured it out: some time ago I had to make a mod to the HWCLOCK script (can't even remember what it was for) and it turns out that was the root of the problem.  I've restored the original script and it no longer does the mystery bootup.  
Thanks!

---

### Post by Aearenda on 2009-12-04
That's great! Thanks for letting us know - and please mark the thread 'solved' when you get a moment.

---

### Post by JustGus on 2009-12-11
Thanks again, Aearenda.  Just saw your note and have looked around and done a search to try and find how to mark this as "solved."  Sorry - can you let me know how?  Cheers!

---

### Post by Aearenda on 2009-12-11
It should be on the 'Thread Tools' link in red near the top of the page :-)

---

### Post by JustGus on 2009-12-11
Thanks a mill. You've been a [SIZE="7"]huge[/SIZE] help!

---


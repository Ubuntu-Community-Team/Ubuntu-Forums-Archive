---
title: "Running cpufreq-selector with crontab doesn't work"
date: 2010-10-22
forum: General Help
---

### Post by Glaucous on 2010-10-22
I'm creating a scripts which changes the CPU Freq if some specific applications are running, however, this doesn't work with crontab.

First I tried my script, everything worked except the actual cpufreq-selector.

So I created this crontab job as user (as well as root).
* * * * * /usr/bin/cpufreq-selector -c 0 -g performance

However, it doesn't work.

Is there anything I can do? My only other alternative right now is to make the script an infinite while loop (with sleep).

---

### Post by sriramoman on 2010-12-01
BUMP!
Same problem here. The script runs standalone, though!
I want my laptop to run in full scale, but nasty gnome power savers dont allow them to do so!

---

### Post by wamanning on 2011-01-29
same problem here.  even adding the full path to cpufreq-selector to the crontab doesnt help.  same commands run in terminal work fine.

ideas/suggestions?

---

### Post by wamanning on 2011-10-01
anyone find a resolution to this yet?

script works fine interactively, but nothing from cron.

---

### Post by sriramoman on 2011-10-16
I found a good quick method. It is a bit crooked, but it works.
Open /etc/init/ondemand

Find the line where "ondemand" lies. Change it to "performance". It works!

---

### Post by wamanning on 2011-10-23
in order for this to work using cpufreq-selector from a script, [FONT="Courier New"]/usr/bin/cpufreq-selector[/FONT] must have Cmnd_Alias and priveliges defined appropriately in [FONT="Courier New"]/etc/sudoers[/FONT]

i was driven to create this DIY scaling because my system is older and the cpu switching apparently isnt fast enough for ubuntu to reliably use the desireable ondemand governor.  system latency can cause problems with math computations if the cpu speed change in the middle of an operation.  in these systems, ondemand is not usable and the system defaults to performance (can be manually switched to powersave).  this script toggles performance/powersave based on the screensaver being active/inactive.  below is the system message that indicates the problem with the ondemand governor.

[FONT="Courier New"][INDENT]kernel: [  399.418242] ondemand governor failed, too long transition latency of HW, fallback to performance governor[/INDENT][/FONT]

also, i modded a python script to monitor your screensaver to automatically toggle between powersave and performance cpu setting automatically, no need for a crontab when you can have your system react to user-activity.  

this was inspired by this guy's work:  [http://blog.troyastle.com/2011/06/run-scripts-when-gnome-screensaver.html](http://blog.troyastle.com/2011/06/run-scripts-when-gnome-screensaver.html)

the difference is that i call cpufreq-selector directly instead of putting something in separately callable script.  1 script instead of 3.

[FONT="Courier New"][INDENT]#!/usr/bin/env python

# for this script to work, make sure that Cmnd_Alias and privileges
# are defined appropriately for cpufreq-selector in /etc/sudoers

from gobject import MainLoop
from dbus import SessionBus
from dbus.mainloop.glib import DBusGMainLoop
from subprocess import Popen
import os
import logging


class toggleCPUFREQ:
    def __init__(self):
        DBusGMainLoop(set_as_default=True)
        self.mem='ActiveChanged'
        self.dest='org.gnome.ScreenSaver'
        self.bus=SessionBus()
        self.loop=MainLoop()
        self.bus.add_signal_receiver(self.catch,self.mem,self.dest)
    def catch(self,ssOn):
        if ssOn == 1: #Screensaver turned on
            os.system("/usr/bin/cpufreq-selector -g powersave")
        else: #Screensaver turned off
            os.system("/usr/bin/cpufreq-selector -g performance")

toggleCPUFREQ().loop.run()[/INDENT][/FONT]

also, i wrote a little bash script you can use for testing.  open up a terminal window, run this and it echos back a log of the active cpu speed so you can double-check to see the speed changing as the screensaver toggles on/off.

[FONT="Courier New"][INDENT]#!/bin/bash

# this script displays the current cpufreq
# in a continuous loop

while [ 1 ]
do
    OUT=$(/usr/bin/cpufreq-info -f)
    echo "$(date) | CURRENT CPUFREQ= $OUT"
    sleep 10
done[/INDENT][/FONT]

---


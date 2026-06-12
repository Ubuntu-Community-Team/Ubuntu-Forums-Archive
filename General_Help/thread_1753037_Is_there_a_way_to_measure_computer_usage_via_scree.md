---
title: "Is there a way to measure computer usage via screensaver activity?"
date: 2011-05-08
forum: General Help
---

### Post by jkcunningham on 2011-05-08
I'm looking for a simple way to determine the rough amount of time per day I spend on a computer. This can be a difficult task if you try to monitor processes, key presses, mouse clicks and the like, because one can be doing anything from thinking about a coding problem, reading a web article, talking on the phone, or off walking the dog. The computer cannot read my mind. Since I leave computers on 24/7 monitoring log-ins won't work.

I hit on the idea of logging how much time the computer spends in screensaver mode. My error would then be no greater than the product of the idle-time-to-screensaver with the number of times it goes into screensaver mode. Subtracting this from 24 hours would give me an estimate which would be reasonable for my purposes.

The problem is: I don't know how to log when the screensaver turns on and off. I am running Ubuntu 10.10 at the moment on most machines, about to start upgrading to 11.04 on some of them.

After lots of googling I hit upon the dbus-monitor which looked like it might work, but is missing an important ingredient. Here's the script I am running which launches the monitor as a daemon:

```
#!/bin/bash
RUNNING=`ps -A | grep "dbus-monitor"`
if [ ! $RUNNING  ]; then
    echo "(Re)starting dbus-monitor daemon"
    nohup dbus-monitor "--profile" "type='signal',interface='org.gnome.ScreenSaver'" >> ${HOME}/sc.log &
fi
```

Here is the output it produces after locking and unlocking the screen a couple times:

```
sig     1304860712      153829  2       /org/freedesktop/DBus   org.freedesktop.DBus    NameAcquired
sig     1304860717      318732  462     /org/gnome/ScreenSaver  org.gnome.ScreenSaver   ActiveChanged
sig     1304860725      547928  463     /org/gnome/ScreenSaver  org.gnome.ScreenSaver   ActiveChanged
sig     1304861018      17      464     /org/gnome/ScreenSaver  org.gnome.ScreenSaver   ActiveChanged
sig     1304862919      403523  466     /org/gnome/ScreenSaver  org.gnome.ScreenSaver   ActiveChanged

```
The second column is obviously unix UTC in seconds. The missing ingredient is it doesn't identify whether the screensaver is on or off! I suppose I could assume they toggle from the time NameAcquired happens, but it makes me queasy that there might be a missing or extra event I can't anticipate which would throw everything out of sync.

Much obliged for ideas.

jkcunningham

---


---
title: "CPU use has shot up after using gconf-editor"
date: 2011-06-19
forum: General Help
---

### Post by John Krow on 2011-06-19
I'm running 10.04 on a Dell. I'm using a Samsung SyncMaster 172v as the monitor.
I had what appears to be the common problem that changing the setting for the time the screensaver takes to kick in using System>Preferences>Screensaver doesn't actually change anything on some systems. BTW, as a side issue there are two identical menu items with that name which open different but similar tools - some kind of update which hasn't removed the previous tool I imagine.

Anyway, to try and resolve this I ran 
```
gconf-editor
```. Under Apps/gnome-screensaver I noticed that 
'idle_delay' was set to 10 (minutes). I changed it to 100. On a whim i also changed the setting for 'power_management_delay' to a higher value in case it was conflicting - I didn't notice this was in seconds not minutes, which should have tipped me off to leave well alone. Now CPu usage (according to the AWN applet to monitor it) is at about 54% when the system isn't being used, ie my default desktop without anything extra running, and up to between 70-99% when running one or two programs. Changing the 'power_management_delay' setting back doesn't seem to restore the CPu usage to anything like the minimal levels seen before I started messing about here.

Any advice? I will of course post further information as requested.

Edited to add: a simple reboot seemed to solve this problem and set CPU usage back to normal, plus I forgot I had some screenlets running which may have accounted for the extra usage (even though they were re-loaded with the reboot). 
Still like some advice about the duplicate menu item tho.

---


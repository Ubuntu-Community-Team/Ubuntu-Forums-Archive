---
title: "config file for Sysmonitor screenlet?"
date: 2009-09-09
forum: General Help
---

### Post by rbc on 2009-09-09
I have set up the SysMonitor screenlet. Very useful information, all in one place, and I like it very much, but.....one of the sensors is for the battery, which is showing BAT1 0%, which makes perfect sense, because the acpi command, in terminal shows that my laptop battery is recognized as BAT0. This is obviously not a "help me fix this or I am going back to Windows" problem, but still rather annoying. Is there some config file that I can alter, so that the SysMonitor screenlet will check BAT0 instead of BAT1?

---

### Post by GoDamN on 2010-07-18
Seems on Lucid that the array index for the bat_list is incorrect or unexpected. Changing
self.bat_data = sensors.bat_get_data(self.bat_list[0])
to 
self.bat_data = sensors.bat_get_data(self.bat_list[1])
in 
/usr/share/screenlets/Sysmonitor/SysmonitorScreenlet.py

gave me the correct charge data (compared to the ACPI battery screenlet). Still shows as BAT1 but im not too fussed about that really.

---

### Post by rbc on 2010-09-27
It had been so long I had stopped checking this thread to see if anyone had responded. Your suggestion worked like a charm. You're right, it still shows BAT1, but I'm not bothered by that either. Thanks much

---


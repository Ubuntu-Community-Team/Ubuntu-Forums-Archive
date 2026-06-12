---
title: "Alarm clock?"
date: 2009-07-05
forum: General Help
---

### Post by Cam42 on 2009-07-05
Is there any way to use my Ubuntu machine as an alarm clock? I'd like it to play some harder music in the morning to wake me up. How would I do this?

---

### Post by matrixblue on 2009-07-05
Use Kalarm

---

### Post by cmost on 2009-07-05
Kalarm is really nice but is designed for use in KDE.  If you want something for Gnome, then I would recommend Alarm Clock.

"Alarm Clock is designed to provide user with simple interface for creating alarms, reminding him about birthdays, appointments, important dates. Alarm Clock can be configured very easily even by a non-power user and fits perfectly into the GNOME Desktop."

[https://launchpad.net/alarmclock](https://launchpad.net/alarmclock)

You could also try gnome-applet-alarm-clock, which is a extremely versatile alarm clock applet for your Gnome panel.  I couldn't locate a deb file for this (maybe you'll have better luck) but it's put out by Red Hat.  You can always download the appropriate RPM for your system and convert it to a DEB with Alien.  More info here:

[http://rpmfind.net/linux/rpm2html/search.php?query=gnome-applet-alarm-clock](http://rpmfind.net/linux/rpm2html/search.php?query=gnome-applet-alarm-clock)

**Edit** Converted the Fedora Core 11 RPM package to a DEB file with Alien and it works perfectly in Ubuntu 9.04

---

### Post by t4thfavor on 2009-07-05
Cron jobs are nice too, a simple alarm that wakes you up m-f at 6AM would look something like this.

```

crontab -e
# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)  OR sun,mon,tue,wed,thu,fri,sat 
# |  |  |  |  |
# *  *  *  *  *   command to be executed
  0  6  *  *  1-5 /usr/bin/mplayer hardmusic.pls

```

Let me know if it wirks out :)

---

### Post by matrixblue on 2009-07-05
I just downloaded and tried alarm-clock and it really is awesome and hs a better interface in my opinion.

---

### Post by Cam42 on 2009-07-05
I actually found a rhythmbox plugin [http://nedrebo.org/code/rhythmbox/alarm_clock/](http://nedrebo.org/code/rhythmbox/alarm_clock/) that'll work

---

### Post by credobyte on 2009-07-05
+1 for Alarm Clock ( tiny & awesome ) :)

---


---
title: "Crontab not executing hddtemp"
date: 2011-05-05
forum: General Help
---

### Post by chrisbay90 on 2011-05-05
I have this very very quick and dirty script to pull temperature  information and log it. The script is in the root crontab to run every  hour. ```
#!/bin/bash

log=/root/scripts/temps.log

echo `date`,`hddtemp /dev/sda` >> $log
echo `date`,`hddtemp /dev/sdb` >> $log
echo `date`,`sensors | grep 'Core 0'` >> $log
echo `date`,`sensors | grep 'Core 1'` >> $log
echo `date`,`sensors | grep temp1` >> $log
echo `date`,`sensors | grep temp2` >> $log
echo `date`,`sensors | grep temp3` >> $log
echo `whoami` >> $log
```When run from a root shell it outputs to the file correctly.
```
Thu May 5 14:17:56 EST 2011,/dev/sda: ST31500341AS: 35°C
Thu May 5 14:17:56 EST 2011,/dev/sdb: ST31000528AS: 32°C
Thu May 5 14:17:56 EST 2011,Core 0: +45.0°C (high = +74.0°C, crit = +100.0°C)
Thu May 5 14:17:56 EST 2011,Core 1: +43.0°C (high = +74.0°C, crit = +100.0°C)
Thu May 5 14:17:56 EST 2011,temp1: +27.0°C (high = -1.0°C, hyst = -13.0°C) ALARM sensor = thermistor
Thu May 5 14:17:56 EST 2011,temp2: +19.0°C (high = +85.0°C, hyst = +85.0°C) sensor = diode
Thu May 5 14:17:56 EST 2011,temp3: +37.5°C (high = +80.0°C, hyst = +75.0°C) sensor = thermistor
root
```When run from crontab the it does not execute the hddtemp command.
```
Thu May 5 14:17:01 EST 2011,
Thu May 5 14:17:01 EST 2011,
Thu May 5 14:17:01 EST 2011,Core 0: +46.0 C (high = +74.0 C, crit = +100.0 C)
Thu May 5 14:17:01 EST 2011,Core 1: +44.0 C (high = +74.0 C, crit = +100.0 C)
Thu May 5 14:17:01 EST 2011,temp1: +27.0 C (high = -1.0 C, hyst = -13.0 C) ALARM sensor = thermistor
Thu May 5 14:17:01 EST 2011,temp2: +17.5 C (high = +85.0 C, hyst = +85.0 C) sensor = diode
Thu May 5 14:17:01 EST 2011,temp3: +37.5 C (high = +80.0 C, hyst = +75.0 C) sensor = thermistor
root
```Any idea's why? As a first step of debug i added the whoami line. I can't seee any clues there.

---

### Post by georgemc on 2011-05-05
When I make scripts for crontab I assume no environment.  I would  suggest to check the real locations of your commands with "whereis" and  add the full path for each command.

Hope this helps.

George

---

### Post by chrisbay90 on 2011-05-05
> **georgemc said:**
> When I make scripts for crontab I assume no environment.  I would  suggest to check the real locations of your commands with "whereis" and  add the full path for each command.

Hope this helps.

George

Thanks for your reply george, that did the trick.

```
$ whereis hddtemp
hddtemp: /usr/sbin/hddtemp /etc/hddtemp.db /usr/share/man/man8/hddtemp.8.gz
```

changed
```
..
echo `date`,`hddtemp /dev/sda` >> $log
echo `date`,`hddtemp /dev/sdb` >> $log
..
```

to
```
..
echo `date`,`/usr/sbin/hddtemp /dev/sda` >> $log
echo `date`,`/usr/sbin/hddtemp /dev/sdb` >> $log
..
```

Is there a way to tell a bash script to inherit or load the same environment as a users prompt. Something to do with .bashrc i would presume?

---


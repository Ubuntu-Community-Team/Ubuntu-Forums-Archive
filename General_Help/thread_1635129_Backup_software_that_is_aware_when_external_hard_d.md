---
title: "Backup software that is aware when external hard drives are plugged in"
date: 2010-12-01
forum: General Help
---

### Post by altonbr on 2010-12-01
Because a lot of users are using laptops now, and many want externals hard drives for backups, is there a program in Ubuntu (cross-platform with Windows would be nice) that backs up files to an external hard drive when the external drive is plugged in or on a timely basis? All backup systems seem to have a timed system, but these systems have annoying pop ups if your backup location is non-existant (e.g. Deja Dup).

Use case 1: I plug in my external, the program recognizes that and starts a backup.

Use case 2: I leave my external in all day and every 6 hours, my laptop backs up my files to it.

Any suggestions?

---

### Post by Hawkoon on 2010-12-01
I use a udev rule to initiate mounting of my encrypted drives as soon as I plug them in. Would that be an option? You could trigger your backup software that way or an rsync script to do the backup for you. It wouldn't cover Windows though.

---

### Post by altonbr on 2010-12-02
> **Hawkoon said:**
> I use a udev rule to initiate mounting of my encrypted drives as soon as I plug them in. Would that be an option? You could trigger your backup software that way or an rsync script to do the backup for you. It wouldn't cover Windows though.

That would work. I wonder why a developer hasn't integrated that into their backup suite yet.

How did you go about doing it?

---

### Post by Hawkoon on 2010-12-02
> **altonbr said:**
> 
How did you go about doing it?

Once I figured out that udev is responsible for handling devices, I found this site [HTML]http://www.reactivated.net/writing_udev_rules.html[/HTML]It has all the info on how to utilise udev to manipulate device nodes and trigger custom actions when drives are attached/removed. You will have to start with finding out the match criteria for the CONNECTION of your DRIVE.

The DRIVE can be identified by its UUID which you can get from ```
udevadm info -a -p `udevadm info -q path -n /dev/sdx` | grep ATTRS{serial}
```You will have to combine the UUID with some criteria from  the property tree of the drive's device path 
```
udevadm info -q all -a -n /dev/sdx
``` otherwise your udev rule will be triggered more than once.

Combining this info you create a rule in /etc/udev/user.rules, in my case it was
```
SUBSYSTEM=="block", ATTRS{serial}=="57434434394", SYMLINK+="Data", RUN+="/usr/bin/mounttruecrypt -u william /dev/Data"
```

Close of with making a symlink to /etc/udev/rules.d/80-user.rules and restart udev (/etc/init.d/udev reload) or reboot

---

### Post by altonbr on 2010-12-04
Amazing. Thank you very much!

---


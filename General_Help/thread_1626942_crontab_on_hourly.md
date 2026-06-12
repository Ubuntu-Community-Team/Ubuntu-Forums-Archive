---
title: "crontab on hourly"
date: 2010-11-20
forum: General Help
---

### Post by muhdazmilug on 2010-11-20
hi

i have this script that i want to run every hour, add the command in crontab but it not running. when i test the crontab to write something on the log file,it running.. When i try to run the script using commandline,it running.

i hv go through the forum, and but still in the same.

here the script :
```

#!/bin/bash
#script change background desktop from Linux desktop hacks
export DIR='/home/muhdazmilug/Pictures/Wallpaper/' #set directory for wallpaper
export NUMBER=$RANDOM  #build in variable
export TOTAL=0 # 
#count the the total of file in dir
for f in `ls $DIR`
do
let "TOTAL +=1"
done
let "NUMBER %=TOTAL" # select the image to be use
export CURRENT=0
for f in `ls $DIR`
do
if [ $CURRENT = $NUMBER ]
then
/usr/bin/gconftool-2 -t string -s /desktop/gnome/background/picture_filename $DIR/$f
break
fi
let "CURRENT += 1"
done

```

i use sudo crontab -e to add the crontabs command

```

1 * * * * bash /home/muhdazmilug/changeWallpaper.sh
1 * * * * echo "wallpaper Successful: $(date)" >> /tmp/crontabsLog.log

```

thank in advance

---

### Post by dcstar on 2010-11-20
> **muhdazmilug said:**
> hi

i have this script that i want to run every hour, add the command in crontab but it not running. when i test the crontab to write something on the log file,it running.. When i try to run the script using commandline,it running.
........
```

1 * * * * bash /home/muhdazmilug/changeWallpaper.sh
1 * * * * echo "wallpaper Successful: $(date)" >> /tmp/crontabsLog.log

```

thank in advance

Cron jobs do not run in **your** user Gnome environment, they run in their own system environment.

Run the script from System-Preferences-Startup Applications.

---

### Post by lsatenstein on 2010-11-21
> **dcstar said:**
> Cron jobs do not run in **your** user Gnome environment, they run in their own system environment.

Run the script from System-Preferences-Startup Applications.

From root

crontab -u user 

is supposed to allow creating a user crontab.

---

### Post by muhdazmilug on 2010-11-22
when i sudo cat /var/log/syslog | grep CRON

this appear..

```

Nov 22 23:44:01 muhdazmilugAspire3810T CRON[4202]: (root) CMD (   cd   /home/muhdazmilug/ScriptHelp/changeWallpaper.sh )
Nov 22 23:44:01 muhdazmilugAspire3810T CRON[4200]: (CRON) error (grandchild #4202 failed with exit status 2)
Nov 22 23:44:01 muhdazmilugAspire3810T CRON[4200]: (CRON) info (No MTA installed, discarding output)


```

i search the exit status 2 say that Misuse of shell builtins..
what Misuse of shell builtins mean?

---

### Post by muhdazmilug on 2010-11-22
after searching in this forum,the problem had be solve...thank here

here my new script look like..

```

#!/bin/bash

# Get the pid of nautilus
nautilus_pid=$(pgrep -u $LOGNAME -n nautilus)

# If nautilus isn't running, just exit silently
if [ -z "$nautilus_pid" ]; then
  exit 0
fi

# Grab the DBUS_SESSION_BUS_ADDRESS variable from nautilus's environment
eval $(tr '\0' '\n' < /proc/$nautilus_pid/environ | grep '^DBUS_SESSION_BUS_ADDRESS=')

# Check that we actually found it
if [ -z "$DBUS_SESSION_BUS_ADDRESS" ]; then
  echo "Failed to find bus address" >&2
  exit 1
fi

# export it so that child processes will inherit it
export DBUS_SESSION_BUS_ADDRESS


export DIR='/home/muhdazmilug/Pictures/Wallpaper/' 
export NUMBER=$RANDOM  #build in variable
export TOTAL=0 # 
for f in `ls $DIR`
do
let "TOTAL +=1"
done
let "NUMBER %=TOTAL" 
export CURRENT=0
for f in `ls $DIR`
do
if [ $CURRENT = $NUMBER ]
then
/usr/bin/gconftool-2 -t string -s /desktop/gnome/background/picture_filename $DIR/$f
break
fi
let "CURRENT += 1"
done
exit

```

---


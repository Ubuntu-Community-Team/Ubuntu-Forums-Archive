---
title: "trying to record uptime"
date: 2011-10-10
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-10-10
i managed to make this but it has issues if the computer is on over 1 day or on under 1 hour is there a more script friendly way to get the system uptime?
shutdown script:
```
#!/bin/bash
LAST_UT=`cat /var/uptime`
CURRENT_UT=`uptime | awk '{ split($3,a,":"); print (a[1]*60+a[2]+$UT) }'`
echo $(($LAST_UT+$CURRENT_UT)) > /var/uptime
exit 0
```
login script:
```
#!/bin/sh
UT=`cat /var/uptime`
if [ $UT -gt 43200 ]; then
    zenity --info --title="Clean Me" --text="I have been running for 30 days, it is time to clean the dust bunnies out.\nPlease remove the side panel on the tower and blow them out with a can of air.\nPlease do one quick squirt into the air out side of the computer to ensure there is no moisture in the nozzle."
    echo 0 > /var/uptime #/var/uptime is chmoded to 777
fi
```

---

### Post by sisco311 on 2011-10-10
The first number in /proc/uptime is the current uptime in seconds. I'd try something like:
```
#!/bin/bash

if ! [[ -f "/var/uptime" ]]
then
    echo 0 > "/var/uptime" || exit 1
fi

cut=$(cut -f 1 -d '.' /proc/uptime)
lut=$(< /var/uptime)

echo $(( cut + lut )) > /var/uptime || exit 2

```

```
#!/bin/bash

if ! [[ -f /var/uptime ]]
then
   exit 1
fi

if (( $(< /var/uptime) > 30*24*60*60 ))
then
    whatever
fi
```

---

### Post by pqwoerituytrueiwoq on 2011-10-10
thanks

---


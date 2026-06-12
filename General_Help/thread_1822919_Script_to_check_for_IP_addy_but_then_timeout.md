---
title: "Script to check for IP addy but then timeout"
date: 2011-08-11
forum: General Help
---

### Post by dardack on 2011-08-11
OK the same issue that I've had since 9.04 is happening to this day.  The mount command is done before my laptop get's an IP address.  So this is what I add to my rc.local file back in 9.04 (right now I just do sudo mount -a once i'm logged in, but want to automate it again).

```
while ! ifconfig wlan0 | grep "inet addr" ; do
    sleep 1
done
mount -a
```

What I want here is a timeout after 60 seconds.  Is that possible?

---

### Post by amauk on 2011-08-11
Bit messy, but this should do

```
COUNT=0
DO_MOUNT=1
while ! ifconfig wlan0 | grep "inet addr" ; do
    if [ "$COUNT" -ge 60 ]; then
        DO_MOUNT=0
        break
    fi
    sleep 1
    COUNT=$(expr "$COUNT" + 1)
done
if [ "$DO_MOUNT" -eq 1 ]; then
    mount -a
fi
```

---


---
title: "Display sleep timer script"
date: 2011-08-13
forum: General Help
---

### Post by Auxao on 2011-08-13
Hi,

I followed a tutorial here on how to instantly lock and sleep my display, however I would like to add an additional line that changes the timer for which the display sleeps on its own.

I normally have the sleep timer set to a fairly long duration, however I would like the script to change that since I only plan on running it when I know I'll be away from my desk for a long period of time.  That way if the display is awoken unexpectedly (i.e. someone bumps my desk) it will return to sleep asap.

For reference, this is what I have so far:
```
#!/bin/bash
gnome-screensaver-command  --lock
xset dpms force off
```

Thank you!

---

### Post by Basher101 on 2011-08-13
why do you even need a script for that? In the Screensaver settings and Power manager you have all the things you need - when the screensaver comes, the screen locks, or sleeps. Just look in your system settings. And if you isntantly want to lock your screen press ctrl+alt+L

---

### Post by Auxao on 2011-08-13
I like the script for it because I change those settings just about every other day. This way, instead of having to go through the menus each time, I can just shortcut this script, and then another to change the sleep timer back to a longer duration.

---

### Post by Auxao on 2011-08-22
/bump

Still looking for help please.

Thank you!

---

### Post by fdrake on 2011-08-22
```

cat > lock.sh
#!/bin/bash
while : do 
gnome-screensaver-command  --lock
xset dpms force off
sleep 5  #sleep in 5 sec
done
<press Control+D>
chmod + x lock.sh
./lock.sh

```

---


---
title: "Blue proximity help"
date: 2010-04-04
forum: General Help
---

### Post by nexx892 on 2010-04-04
So BP executes to lock my computer if my phone is more than 10 feet away and to unlock it if its 5 feet away using 
gnome-screensaver-command -l
and gnome-screensaver-command -d



But if I manually locked it before somebody could just put my phone out of the 10 feet and back in to unlock my computer without knowing a password.


How would I go about making a script that will not unlock it if something else other than BP locked it?
Because I can choose what to execute when it is in and out of the area.

---

### Post by AldenIsZen on 2011-01-23
Not a programmer, just a "little hacker" of things I need. [This link]("http://art.ubuntuforums.org/showthread.php?p=10390179#post10390179") may interest you and give you some ideas.


 Perhaps you can switch or add other "[cases]("http://ss64.com/bash/case.html")" (conditions) to the script, and add commands to BP like the "rfkill block bluetooth" in the locking commad? I know that alone should make it where you have to enter in the password period after it is locked. At any rate, I am sure it can be done.
```

#!/bin/bash
#Code from [http://ubuntuforums.org/showthread.php?t=1387211](http://ubuntuforums.org/showthread.php?t=1387211)

. /usr/lib/pm-utils/functions

case "$1" in
    hibernate|suspend)
    rfkill block bluetooth
    ;;
    thaw|resume)
    rfkill unblock bluetooth
    ;;
    *)
    ;;
esac

exit
```

---


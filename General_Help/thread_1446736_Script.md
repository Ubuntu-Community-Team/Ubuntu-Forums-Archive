---
title: "Script"
date: 2010-04-04
forum: General Help
---

### Post by pedrom169 on 2010-04-04
Is there anyway of making this?

I want a loop of the:
cursor moving to one place clicking
Waiting a second
cursor moving to another place clicking
Waiting a second

But also with a e.g. F1 turning it on and off?

Could someone help me or point me in the right direction?

Thanks

---

### Post by iponeverything on 2010-04-04
googling around for "gnome automation"

I found this:

[http://ubuntuforums.org/showthread.php?t=392686](http://ubuntuforums.org/showthread.php?t=392686)

---

### Post by sisco311 on 2010-04-04
```

#!/bin/bash

#Coordinate of the first click location
X1=100
Y1=100

#Coordinate of the second click location
X2=200
Y2=200

#Time in seconds to wait between clicks
TIME=1

NAME=$0
NAME=${NAME//*\//}

ISRUNNING="$(pidof -x $NAME | awk '{print $3}')"

if [ $ISRUNNING ]; then
  killall $NAME
else
  while true; do
    xdotool mousemove $X1 $Y1
    xdotool click 1
    sleep $TIME
    xdotool mousemove $X2 $Y2
    xdotool click 1
    sleep $TIME
  done
fi

```

---


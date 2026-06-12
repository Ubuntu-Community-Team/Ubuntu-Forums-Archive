---
title: "Script helped needed to kill one app then launch another"
date: 2011-09-11
forum: General Help
---

### Post by CDNdevil on 2011-09-11
Hi everybody, I was needing help with making a simple script that will let me basically toggle between two apps, the apps are Boxee and XBMC. I wanna have it kill XMBC and launch Boxee and vise versa. I could make a script that'll kill one and launch the other, but I wanna basically make it a toggle the I could execute via LIRC using my remote. Any help would be appreciated.

---

### Post by toupeiro on 2011-09-11
Something like this might get you there.  Debugging needed:

```

#!/bin/bash

PROGRAM1=&#8221;/usr/bin/boxee&#8221;
PROGRAM2="/usr/bin/xbmc"

APPCHK=$(ps aux | grep -c $PROGRAM1)


if [ $APPCHK = '0' ];

then

Echo "Nothing running, starting $PROGRAM1"
/usr/bin/boxee  &

fi

else

if [ $APPCHK = '$PROGRAM1' ];

then

killall $PROGRAM1

Echo "Killing $PROGRAM1 and starting $PROGRAM2"

/usr/bin/xbmc &

fi

else

if [ $APPCHK = '$PROGRAM2' ];

then

killall $PROGRAM2

Echo "Killing $PROGRAM2 and starting $PROGRAM1"

/usr/bin/boxee  &

fi

exit
```

---

### Post by CDNdevil on 2011-09-11
Thank you very much, that's much better then what I wrote, basically I have two scripts to kill one then launch the other.

---


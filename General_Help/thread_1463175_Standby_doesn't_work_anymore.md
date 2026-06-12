---
title: "Standby doesn't work anymore"
date: 2010-04-26
forum: General Help
---

### Post by Ferux on 2010-04-26
Hello


I'm using Karmic since November and standby/sleep has always worked fine. Some weeks ago, it stopped working fine.

After a reboot, I can put the system in standby only once. If I try standby after that, the system seems to do a normal standby, but it resumes at the moment the fans would normally stop working.

I tried different things like the s2ram program, pmi action sleep, etc. No help. I went to the BIOS and tried a number of things, one was succesfull: disable USB. When USB is disabled I can go into standby every time. When I enable USB again (even with no devices connected), standby only works once again.

So, **how can I disable USB at the moment I go into standby**? I'm not sure whether that would help.

Any other ideas? I have no idea what might have changed at the moment the problem came...


Thank you

---

### Post by Ferux on 2010-04-30
OK, i found out it was indeed the USB which caused me troubles. I made 2 scripts to shutdown all the USB ports before going into standby. The scripts are made executable and put in the /etc/pm/sleep.d directory so they get executed on suspend/resume.


This one is called first (by giving it a name starting with a lower number). It unmounts my drive called 'LACIE' so this drive doesn't give errors on resume.
```

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    hibernate|suspend)
    if [test -d /media/LACIE]; then
    umount /media/LACIE
    rm /media/LACIE
    fi
    ;;
    thaw|resume)
    ;;
    *)
    ;;
esac

exit
```


The next script shuts down all the USB ports. I found the correct numbers in the /sys/bus/usb/devices directory.
```

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    hibernate|suspend)
    echo suspend >/sys/bus/usb/devices/1-0:1.0/power/level
    echo suspend >/sys/bus/usb/devices/1-8/power/level
    echo suspend >/sys/bus/usb/devices/1-8.1/power/level
    echo suspend >/sys/bus/usb/devices/1-8.1.1/power/level
    echo suspend >/sys/bus/usb/devices/1-8.1.1:1.0/power/level
    echo suspend >/sys/bus/usb/devices/1-8.1.2/power/level
    echo suspend >/sys/bus/usb/devices/1-8.1.2:1.0/power/level
    echo suspend >/sys/bus/usb/devices/1-8.1.3/power/level
    echo suspend >/sys/bus/usb/devices/1-8.1.3:1.0/power/level
    echo suspend >/sys/bus/usb/devices/1-8.1.3:1.1/power/level
    echo suspend >/sys/bus/usb/devices/1-8.1.3:1.2/power/level
    echo suspend >/sys/bus/usb/devices/1-8.1.3:1.3/power/level
    echo suspend >/sys/bus/usb/devices/1-8.1:1.0/power/level
    echo suspend >/sys/bus/usb/devices/1-8.3/power/level
    echo suspend >/sys/bus/usb/devices/1-8.3:1.0/power/level
    echo suspend >/sys/bus/usb/devices/1-8:1.0/power/level
    echo suspend >/sys/bus/usb/devices/2-0:1.0/power/level
    echo suspend >/sys/bus/usb/devices/usb1/power/level
    echo suspend >/sys/bus/usb/devices/usb2/power/level
    ;;
    thaw|resume)
    echo auto >/sys/bus/usb/devices/1-0:1.0/power/level
    echo auto >/sys/bus/usb/devices/1-8/power/level
    echo auto >/sys/bus/usb/devices/1-8.1/power/level
    echo auto >/sys/bus/usb/devices/1-8.1.1/power/level
    echo auto >/sys/bus/usb/devices/1-8.1.1:1.0/power/level
    echo auto >/sys/bus/usb/devices/1-8.1.2/power/level
    echo auto >/sys/bus/usb/devices/1-8.1.2:1.0/power/level
    echo auto >/sys/bus/usb/devices/1-8.1.3/power/level
    echo auto >/sys/bus/usb/devices/1-8.1.3:1.0/power/level
    echo auto >/sys/bus/usb/devices/1-8.1.3:1.1/power/level
    echo auto >/sys/bus/usb/devices/1-8.1.3:1.2/power/level
    echo auto >/sys/bus/usb/devices/1-8.1.3:1.3/power/level
    echo auto >/sys/bus/usb/devices/1-8.1:1.0/power/level
    echo auto >/sys/bus/usb/devices/1-8.3/power/level
    echo auto >/sys/bus/usb/devices/1-8.3:1.0/power/level
    echo auto >/sys/bus/usb/devices/1-8:1.0/power/level
    echo auto >/sys/bus/usb/devices/2-0:1.0/power/level
    echo auto >/sys/bus/usb/devices/usb1/power/level
    echo auto >/sys/bus/usb/devices/usb2/power/level
    ;;
    *)
    ;;
esac

exit
```


The scripts work perfect and I'm not annoyed by the lights of the USB devices anymore when the device is in standby.

The only problem is that I cannot connect my mouse to USB (use PS/2 instead). For some reason, the scirpt hangs when I use a USB mouse. If you want to check-out a script, you can check the suspend log at 'System --> Administration --> Logs --> pm-suspend.log'.

OK, problem solved!

---


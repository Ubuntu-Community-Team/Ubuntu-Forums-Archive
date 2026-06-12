---
title: "why does the fan run constantly when I return from suspend?"
date: 2006-04-25
forum: General Help
---

### Post by harty83 on 2006-04-25
Hello,

I have a dell inspiron 5150 and whenver I return from suspend, the fan runs constantly for well over an hour.  Any clue why this is?  It doesn't do that when I do a fresh start or return from hibernation; only from suspend.

Thanks!
Alan

---

### Post by lobner on 2007-07-27
I have the same problem with a Thinkpad x60.

The problem is related to the wireless network card not going back into the power mode it was in, before suspension.
I fixed this with a shellscript setting the power back to what it was supposed to be.
What I don't know how to do though, is how to automatically run this (or any other for that matter) when I return from suspend?

How do I execute a shell script each time I return from suspend-mode?
Could anybody tell me that? Please??

Well, my script is pasted below, see if it works for you. ( I realize it has been some time since you wrote this post, but never the less... )

```

#!/bin/sh
#
# PowerLevelAjustmentShellScript
# ethPower.sh
#

F="eth1      get_power:Power save level: 6 (AC) OFF"
T="eth1      get_power:Power save level: 7 (BATTERY)"

MODE=`iwpriv eth1 get_power`

if [ "$MODE" != "$T" ]; then  #if iwpriv mode isn't level 7
    logger "IWPRIV: Power level is: 6"
    logger "Setting to 7..."
    gksudo iwpriv eth1 set_power 7
    sudo -K
    logger "IWPRIV: New power level: 7"
else
    logger "IWPRIV: Power level already: 7"
fi

```

---

### Post by lobner on 2007-07-27
Fixed it!

Place *yourScript.sh* file in */etc/acpi/resume.d/* with the code pasted below.

It functions on an Lenovo ThinkPad X60 with the standard NIC.

```

#!/bin/sh
#
# PowerLevelAjustmentShellScript
#

F="eth1      get_power:Power save level: 6 (AC) OFF"
T="eth1      get_power:Power save level: 7 (BATTERY)"

MODE=`iwpriv eth1 get_power`

if [ "$MODE" != "$T" ]; then  #if iwpriv mode isn't level 7
    logger "IWPRIV: Power level: 6"
    #Sleep to wait for network interface to initialize
    logger "IWPRIV: Sleeping for 45 secs, then set: 7"
    sleep 45
    logger "IWPRIV: Setting to 7..."
    iwpriv eth1 set_power 7
    if [ "$MODE" != "$T" ]; then    
	logger "IWPRIV: New power level: 7"
    else
	logger "IWPRIV: Failed to set power level!"
    fi
else
    logger "IWPRIV: Power level: 7"
fi

```

---


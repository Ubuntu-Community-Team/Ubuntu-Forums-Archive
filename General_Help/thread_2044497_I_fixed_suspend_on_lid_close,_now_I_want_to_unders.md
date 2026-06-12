---
title: "I fixed suspend on lid close, now I want to understand..."
date: 2012-08-19
forum: General Help
---

### Post by Bazon on 2012-08-19
Hello,

on my girlfriends netbook (Samsung NC10), suspend on closing the lid worked only sometimes. that really bothered me (more than her...;-)), because that didn't make linux look good... 

So I tried several things, and finally, I got it working 100% of the time: I edited /etc/acpi/lid.sh, commented everything in the lid-close-case out and entered something that works. it only led to two small problems:
1. an error message after resume saying suspend didn't work because another suspend was going on. [happened only one time]
2. going to suspend immediately after resume again. [happend only one time, another time than 1.]


**so I want now:**
(a) understand the initial script: how should it cause suspend in the first place? what's about that strang last line containing the path /etc/acpi/local, which I can't found on the disk?
(b) and i want to know whether it's made good now or how it could be done better. (it would be interesting to know what went wrong before...) how can the two small problems be eliminated? 

maybe you know and can tell me? :-)

here is the old /etc/acpi/lid.sh:
```
#!/bin/bash
# TODO:  Change the above to /bin/sh

test -f /usr/share/acpi-support/state-funcs || exit 0

. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

if [ `CheckPolicy` = 0 ]; then exit; fi

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"	    
	    . /usr/share/acpi-support/screenblank
	fi
    done
else
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"
	    grep -q off-line /proc/acpi/ac_adapter/*/state
	    if [ $? = 1 ]
		then
		if pidof xscreensaver > /dev/null; then 
		    su $user -c "xscreensaver-command -unthrottle"
		fi
	    fi
	    if [ x$RADEON_LIGHT = xtrue ]; then
		[ -x /usr/sbin/radeontool ] && radeontool light on
	    fi
	    if [ `pidof xscreensaver` ]; then
		su $user -c "xscreensaver-command -deactivate"
	    fi
	    su $user -c "xset dpms force on"
	fi
    done
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post
```

my edited version (comment before each edit. my comments in CAPITAL letters to see them better):

```
#!/bin/bash
# TODO:  Change the above to /bin/sh

test -f /usr/share/acpi-support/state-funcs || exit 0

. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

# COMMENTED OUT, BECAUSE "EXIT" COULD STOP SUSPEND
# if [ `CheckPolicy` = 0 ]; then exit; fi


grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
# PLAY A SOUND AS A SIGN OF REACHING THAT CASE 
    aplay /usr/share/sounds/alsa/Noise.wav;

# LOCK THE SCREEN (XFCE4) AND SUSPEND
    xflock4 && dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend;

# I DIDN'T UNDERSTOOD AND IT DIDN'T SEEM TO WORK, SO i COMMENTED OUT:
#    for x in /tmp/.X11-unix/*; do
#	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
#	getXuser;
#	if [ x"$XAUTHORITY" != x"" ]; then
#	    export DISPLAY=":$displaynum"	    
#	    . /usr/share/acpi-support/screenblank
#	fi
#   done
else
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"
	    grep -q off-line /proc/acpi/ac_adapter/*/state
	    if [ $? = 1 ]
		then
		if pidof xscreensaver > /dev/null; then 
		    su $user -c "xscreensaver-command -unthrottle"
		fi
	    fi
	    if [ x$RADEON_LIGHT = xtrue ]; then
		[ -x /usr/sbin/radeontool ] && radeontool light on
	    fi
	    if [ `pidof xscreensaver` ]; then
		su $user -c "xscreensaver-command -deactivate"
	    fi
	    su $user -c "xset dpms force on"
	fi
    done
fi

# WHAT DOES THIS MEAN? THERE IS NO SUCH PATH /ETC/ACPI/LOCAL! WHAT DOES THE X MEAN? COULD IT CAUSE TROUBLE?
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post
```

---


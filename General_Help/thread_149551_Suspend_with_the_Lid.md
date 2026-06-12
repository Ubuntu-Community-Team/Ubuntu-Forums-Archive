---
title: "Suspend with the Lid"
date: 2006-03-24
forum: General Help
---

### Post by trent dillman on 2006-03-24
Howdy all,

I've had great success with Griffin3's tut on Suspend2 [here]("http://ubuntuforums.org/showthread.php?t=75443"), and I'd really like to suspend when I close the lid. Any ideas?

edit: sorry for the new post, but with 19 pages, I figured I'd be lost in the weight of it all.

edit 2: here's my event scripts:

```

cat /etc/acpi/powerbtn.sh
#!/bin/sh
# /etc/acpi/powerbtn.sh
# Initiates a shutdown when the power putton has been
# pressed.

[ -f /var/lock/acpisleep ] && exit 0

# If PowerManager is running, let it handle policy
if [ `pidof PowerManager` ]; then
  exit
fi

if ps -Af | grep -q '[k]desktop' && test -f /usr/bin/dcop
then
    dcop --all-sessions --all-users ksmserver ksmserver logout 0 2 0 && exit 0
else
    /sbin/shutdown -h now "Power button pressed"
fi

```
```

cat /etc/acpi/lid.sh
#!/bin/sh

. /usr/share/acpi-support/power-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

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
                su $user -c "xscreensaver-command -unthrottle"

            fi
            if [ x$RADEON_LIGHT = xtrue ]; then
                [ -x /usr/sbin/radeontool ] && radeontool light on
            fi
            su $user -c "xscreensaver-command -deactivate"
            su $user -c "xset dpms force on"
        fi
    done
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post

```

---

### Post by trent dillman on 2006-03-28
Solved.

---

### Post by John.Michael.Kane on 2006-03-28
@trent dillman If you please post how you fixed this issue. so that other users with the same problems can see if it helps them.


Thanks.

---

### Post by trent dillman on 2006-03-28
[http://ubuntuforums.org/showthread.php?t=150864](http://ubuntuforums.org/showthread.php?t=150864)

---


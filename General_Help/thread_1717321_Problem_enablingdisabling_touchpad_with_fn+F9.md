---
title: "Problem enabling/disabling touchpad with fn+F9"
date: 2011-03-29
forum: General Help
---

### Post by bdoe on 2011-03-29
I'm not entirely sure where to post this, so please forgive me if I got it wrong. I am having a problem using my laptop's special keys to toggle my touchpad on and off on my ASUS G73JH laptop, running Ubuntu 10.10 (2.6.35-28-generic-pae).

First, some preliminaries:

My touchpad works just fine, but it does not respond to my laptop's special key, Fn+F9.

In /etc/acpi/events I have the following script, "asus-touchpad":
```
# /etc/acpi/events/asus-touchpad
# This is called when the user presses the touchpad button and calls
# /etc/acpi/asus-touchpad.sh for further processing.

event=hotkey (ATKD|HOTK) 0000006[ab]
action=/bin/sh /etc/acpi/asus-touchpad.sh
```

In /etc/acpi I have the script, "asus-touchpad.sh":
```
#!/bin/sh
[ -f /usr/share/acpi-support/state-funcs ] || exit 0

. /usr/share/acpi-support/power-funcs

# if this is the right behavior, then this should be moved out of acpi-support
# to hal (or whatever is replacing hal for such events)
getXconsole

XINPUTD="SynPS/2 Synaptics TouchPad"

# get the current state of the touchpad
tpstate=`xinput list-props "$XINPUTD" | grep "Device Enabled" | cut -d: -f2`

# if getting the status failed, exit
test -z $tpstate && exit 1

if [ $tpstate -eq 0 ]; then
   xinput set-int-prop "$XINPUTD" "Device Enabled" 8 1
   
else
   xinput set-int-prop "$XINPUTD" "Device Enabled" 8 0
   
fi
```

Now, here's the kicker: By inserting logger statements into asus-touchpad.sh, I was able to determine that my Fn+F9 keypresses are being detected, and my scripts are being executed. The problem is with:
```
tpstate=`xinput list-props "$XINPUTD" | grep "Device Enabled" | cut -d: -f2`
```
That statement is not being executed at all. For that matter, neither are the other xinput statements. Logging the value of $tpstate after this statement shows that the variable is null. However, if I go into a terminal and type "sh /etc/acpi/asus-touchpad.sh", the script executes perfectly and toggles my touchpad on or off; just not when executed from the keypress event handler, and it only seems to be the xinput command that is affected.

Can anyone shed some light on this problem?

---

### Post by bdoe on 2011-05-07
*bump*

---


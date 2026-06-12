---
title: "Ubuntu 10.04 warcom bamboo can't toggle touch"
date: 2010-11-21
forum: General Help
---

### Post by davidvandoren on 2010-11-21
Hi I followed[ these instructions]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") for installing the drive software for the wacom bamboo cth-460/ko-c
everything works pretty much. I can't however turn off the touch function. the indicator works. And I think it worked the first time I set it up. 

When running the script through the terminal I get this.

**sh /home/david/.toggle-touch.sh**
```
desktop:~$ sh /home/david/.toggle-touch.sh
[: 23: off: unexpected operator
Touch is OFF, turning ON.

```**sh /home/david/.xsetwacom.sh**
```
desktop:~$ sh /home/david/.xsetwacom.sh
Unknown parameter name 'ClickForce'.
Property 'Wacom Sample and Suppress' does not exist on device.
Property 'Wacom Sample and Suppress' does not exist on device.
Unknown parameter name 'ClickForce'.
Property 'Wacom Pressurecurve' does not exist on device.
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (XInputExtension)
  Minor opcode of failed request:  5 (X_SetDeviceMode)
  Serial number of failed request:  15
  Current serial number in output stream:  15
Segmentation fault

```Is there any other way to turn the touch off. Or can anyone help me to fix this.

Thanks a lot

---

### Post by Favux on 2010-11-21
Hi davidvandoren,

When did you compile xf86-input-wacom?  If you just did it then you have 0.10.9, which just came out, and it has renamed ClickForce to Threshold.  See the Edit at the bottom of the HOW TO.  Also there are some other problems with 0.10.9 right now that have to be dealt with.

---

### Post by davidvandoren on 2010-11-21
Thanks for the reply.

Is there another way disable the touch in general?
I don't need to grab that thing with my fingers anyway. I just need to use it for the Chinese handwriting input. 

Thanks

---

### Post by Favux on 2010-11-21
Yes, assuming the xsetwacom commands are working.  In the xsetwacom script change:
```
xsetwacom set 11 Touch "on"
xsetwacom set 11 Gesture "on"
```
to
```
xsetwacom set 11 Touch "off"
xsetwacom set 11 Gesture "off"
```
Using your ID # or "Device name" if you're hot plugging.  You probably don't need to do Gesture but might as well.

---

### Post by davidvandoren on 2010-11-21
Thanks but does not work either.

---

### Post by Favux on 2010-11-21
Well what you could do is download the 0.10.8 xf86-input-wacom tar and compile it.  Then everything should pretty much work.

---

### Post by davidvandoren on 2010-11-21
Solved


In terminal run
**xinput --list**
```
xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SIGMACHIP Usb Mouse                         id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Pen eraser          id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Pen cursor          id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Pen touch           id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Pen pad             id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Pen stylus          id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Finger eraser       id=14    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Finger cursor       id=15    [slave  pointer  (2)]
&#9116;   &#8627;[COLOR=Red] Wacom BambooFun 2FG 4x5 Finger touch        id=16 [/COLOR]   [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Finger pad          id=17    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Finger stylus       id=18    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; sonixj                                      id=19    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=20    [slave  keyboard (3)]

```

Finger touch is id=16

Now open the toggle-touch.sh and change the value I marked in red to 16 
save and that's it now it works

```
TOUCH_STATE=`xsetwacom get [COLOR=Red]11[/COLOR] Touch`
if [ "$TOUCH_STATE" == "on" ]
  then
    echo "Touch is ON, turning OFF."
    notify-send -t 1500 "Bamboo P&T touch OFF"
    xsetwacom set [COLOR=Red]11[/COLOR] Touch off
  else
    echo "Touch is OFF, turning ON."
    notify-send -t 1500 "Bamboo P&T touch ON"
    xsetwacom set [COLOR=Red]11[/COLOR] Touch on
fi
```

Thanks

and how do I mark this thread as solved?

---

### Post by Favux on 2010-11-21
Good!  Nice work.

Your xinput list is incorrect by the way.  Extra non-existent devices.  That's one of the three problems with 0.10.9.  That got fixed yesterday, but the fix isn't in the repository yet.  So you've worked around it.

Solved is above your first post in Thread Tools.

---

### Post by mlitty on 2011-01-07
Thanks so much.  This is exactly what I needed!

---

### Post by cnr_roxx on 2011-04-12
Big thanx, guys!

BTW: **Favux_wacom.conf_.toggle-touch.sh** works well in 10.10 (Maverick) too, although comment in script mentions only Lucid.

---

### Post by cnr_roxx on 2011-04-12
I've noticed that my "Finger touch" device sometimes gets different ID number after rebooting the system. So I modified **Favux_wacom.conf_.toggle-touch.sh** to automatically detect actual ID number of device:

```

#!/bin/bash

## Use with Lucid wacom.conf.  Get the
## "Device name" or ID number for touch
## from 'xinput --list'. 
##
## For touch state notification use:
##  sudo apt-get install libnotify-bin
## Otherwise comment (#) out the two
## notify-send lines.  If installed
## see 'man notify-send'.

XID=`xinput --list | grep "Wacom.*Finger touch" | sed 's/.*=\([^\t]*\).*/\1/'`

TOUCH_STATE=`xsetwacom get $XID Touch`
if [ "$TOUCH_STATE" == "on" ]
  then
    echo "Touch is ON, turning OFF."
    notify-send -t 1500 "Bamboo P&T touch OFF"
    xsetwacom set $XID Touch off
  else
    echo "Touch is OFF, turning ON."
    notify-send -t 1500 "Bamboo P&T touch ON"
    xsetwacom set $XID Touch on
fi

```

Have fun :)

---

### Post by alpha-buntu on 2011-08-09
Thank you. worked for me too!

---


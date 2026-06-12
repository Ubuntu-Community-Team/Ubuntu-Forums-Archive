---
title: "Touchpad Not Registered/Usable"
date: 2012-01-30
forum: General Help
---

### Post by smc170 on 2012-01-30
Hello, 'Nix users,

I've been using different distro's for some time now, and recently got a new laptop and eagerly dual booted Windows 7 and Ubuntu 11.10, my shiny new machine is a Samsung Series 7 Chronos.

I love everything about the setup except these two major problems:

1.) The touch-pad doesn't seem to be recognized in the settings manager, leading to and unusable, extremely annoying touch-pad that registers almost anything as a click. Since i cant access the touchpad settings, i cant turn off touch-pad click, (or two finger scrolling). I know it has been talked about before, but haven't found and actual answer. 

2.) less minor, but my ATI Radeon HD 6490m graphics card driver seems to keep thinking its not updated? I go to additional drivers and it always says that the driver is not installed when it is(?).

I would really love help on the first question, as it is EXTREMELY annoying. Any help and info is greatly appreciated.

---

### Post by smc170 on 2012-01-31
Ill try to revive it! No-one has this issue? Anyone?

---

### Post by pbrane on 2012-01-31
What kind of touch pad do you have? In a terminal run this command,
```

xinput --list

```

Once you find out what kind it is you *may* be able to disable tapping. The Cypress touch pads don't seem to be supported in linux yet.

Where are you getting your ATI drivers?

---

### Post by smc170 on 2012-01-31
> **pbrane said:**
> What kind of touch pad do you have? In a terminal run this command,
```

xinput --list

```Once you find out what kind it is you *may* be able to disable tapping. The Cypress touch pads don't seem to be supported in linux yet.

Where are you getting your ATI drivers?

Ive got a PS/2 Elantech Touchpad... Don't know if it's supported or not...

I'm getting my ATI drivers from the "Additional Drivers" applet, although i remember a post somewhere about getting the ATI interface in Ubuntu. Will check.

---

### Post by pbrane on 2012-01-31
If you can list your touchpad with xinput you should be able to control it as well.
```

xinput set-int-prop "**<the name of your touchpad in xinput>**" "Device Enabled" 8 0
/usr/bin/synclient MaxTapTime=0

```

If you add the name of the touchpad from xinput --list where the bold text is in the command you can issue those commands to see if they work. the second one using synclient will disable tapping. you might need to install synclient first.

---

### Post by smc170 on 2012-01-31
> **pbrane said:**
> If you can list your touchpad with xinput you should be able to control it as well.
```

xinput set-int-prop "**<the name of your touchpad in xinput>**" "Device Enabled" 8 0
/usr/bin/synclient MaxTapTime=0

```If you add the name of the touchpad from xinput --list where the bold text is in the command you can issue those commands to see if they work. the second one using synclient will disable tapping. you might need to install synclient first.

Hmm, accidentally entered synclient TouchpadOff=0 by misinterpreting another users suggestions, and now the touchpad is Off completely, no use... Anyone can help? I know i'm making a total fool of myself.

[EDIT]: Oops, restarted and all is good, in terms of the touchpad "working". Still no ability to turn off click :(

---

### Post by pbrane on 2012-02-01
> **smc170 said:**
> 
... in terms of the touchpad "working". Still no ability to turn off click :(
so setting MaxTapTime to zero doesn't work?

Try 
```

synclient

```

this will list available properties and settings for your touchpad.

---

### Post by smc170 on 2012-02-01
> **pbrane said:**
> so setting MaxTapTime to zero doesn't work?

Try 
```

synclient

```this will list available properties and settings for your touchpad.


When i enter that, i get this message:
```

Couldn't find synaptics properties. No synaptics driver loaded?
```

I've got synaptic touch-pad driver installed via software center though... Maybe it's just not working?

---

### Post by smc170 on 2012-02-01
Here's another useful piece of info... I went into /etc/x11/xorg.conf, And this is all i found:
```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

```

I feel like there should be more in there, but i dont know how to change it?

---

### Post by pbrane on 2012-02-01
> **smc170 said:**
> Here's another useful piece of info... I went into /etc/x11/xorg.conf, And this is all i found:
```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

```

I feel like there should be more in there, but i dont know how to change it?

xorg does configuration automatically now. My xorg.conf has even less in it. You don't want to make any changes unless you know specifically that you have to. 

I don't know how you managed to turn off the touchpad with synclient, it doesn't seem to recognize your device. I would think that using xinput would work if there is an xorg driver loaded for your touchpad. Try ```
 xinput --list-props "**<device name>**"
``` using the same device syntax as the **--list** argument.

EDIT: I was able to use this command to disable tapping on my AlpsPS/2 ALPS GlidePoint:
```

xinput set-prop 14 "Synaptics Tap Time" 0

```
the number 14 is my device number determined by **xinput --list**. The property "Synaptics Tap Time" comes from **xinput --list-props 14**. You would need to change the device number/name and the property to match yours. Might be worth a try.

---

### Post by smc170 on 2012-02-01
> **pbrane said:**
> xorg does configuration automatically now. My xorg.conf has even less in it. You don't want to make any changes unless you know specifically that you have to. 

I don't know how you managed to turn off the touchpad with synclient, it doesn't seem to recognize your device. I would think that using xinput would work if there is an xorg driver loaded for your touchpad. Try ```
 xinput --list-props "**<device name>**"
``` using the same device syntax as the **--list** argument.

EDIT: I was able to use this command to disable tapping on my AlpsPS/2 ALPS GlidePoint:
```

xinput set-prop 14 "Synaptics Tap Time" 0

```the number 14 is my device number determined by **xinput --list**. The property "Synaptics Tap Time" comes from **xinput --list-props 14**. You would need to change the device number/name and the property to match yours. Might be worth a try.

Hmm, more and more problems:

```
spencer@Smc-Ubuntu:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Laser Wheel Mouse                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; Mouseemu virtual mouse                      id=14    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Elantech Touchpad                      id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; WebCam SC-13HDL11431N                       id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Mouseemu virtual keyboard                   id=15    [slave  keyboard (3)]
spencer@Smc-Ubuntu:~$ xinput set-prop 13 "Synaptics Tap Time" 0
property Synaptics Tap Time doesn't exist, you need to specify its type and format
```

It seems my touchpad isn't recognized as a synaptic device, but a "PS/2" touchpad. Is it possible to change that to get synaptics to work?

---

### Post by pbrane on 2012-02-01
You need to run 
```

xinput --list-props "PS/2 Elantech Touchpad"

```
to see what your properties are called. Then you may be able to run
```

xinput set-prop "PS/2 Elantech Touchpad" "**YOUR DEVICE TAPPING PROPERTY NAME**" 0

``` to disable tapping.

---

### Post by smc170 on 2012-02-01
> **pbrane said:**
> You need to run 
```

xinput --list-props "PS/2 Elantech Touchpad"

```to see what your properties are called. Then you may be able to run
```

xinput set-prop "PS/2 Elantech Touchpad" "**YOUR DEVICE TAPPING PROPERTY NAME**" 0

``` to disable tapping.

Thank you so much for your support pbrane

I'm making progress, i did the Xinput --list-props "PS/2 Elantech Touchpad" command, and came up with this info:

```
spencer@Smc-Ubuntu:~$ xinput --list-props "PS/2 Elantech Touchpad"
Device 'PS/2 Elantech Touchpad':
    Device Enabled (132):    1
    Coordinate Transformation Matrix (134):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (254):    0
    Device Accel Constant Deceleration (255):    1.000000
    Device Accel Adaptive Deceleration (256):    1.000000
    Device Accel Velocity Scaling (257):    10.000000
    Evdev Axis Inversion (258):    0, 0
    Evdev Axes Swap (260):    0
    Axis Labels (261):    "Rel X" (142), "Rel Y" (143)
    Button Labels (262):    "Button Left" (135), "Button Middle" (136), "Button Right" (137), "Button Wheel Up" (138), "Button Wheel Down" (139)
    Evdev Middle Button Emulation (263):    0
    Evdev Middle Button Timeout (264):    50
    Evdev Wheel Emulation (265):    0
    Evdev Wheel Emulation Axes (266):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (267):    10
    Evdev Wheel Emulation Timeout (268):    200
    Evdev Wheel Emulation Button (269):    4
    Evdev Drag Lock Buttons (270):    0
spencer@Smc-Ubuntu:~$ 
```

I'm not sure what the device tapping property name is...

---

### Post by pbrane on 2012-02-01
It doesn't look like there is a property for tapping. I'll keep looking to see if there is another solution. In the meantime are you using a USB mouse? If so you can disable the touch-pad altogether with this
```

xinput set-prop "PS/2 Elantech Touchpad" "Device Enabled" 0

```
This will disable the touch-pad until you reboot. You can re-enable the touch-pad with 
```

xinput set-prop "PS/2 Elantech Touchpad" "Device Enabled" 1

```

---

### Post by smc170 on 2012-02-02
> **pbrane said:**
> It doesn't look like there is a property for tapping. I'll keep looking to see if there is another solution. In the meantime are you using a USB mouse? If so you can disable the touch-pad altogether with this
```

xinput set-prop "PS/2 Elantech Touchpad" "Device Enabled" 0

```This will disable the touch-pad until you reboot. You can re-enable the touch-pad with 
```

xinput set-prop "PS/2 Elantech Touchpad" "Device Enabled" 1

```

Yup yup, it's wiered, cause this computer, you can automatically disable the touchpad (Ctrl+F5), so ubuntu recognizes the touchpad because the little alert comes up. Odd.

---

### Post by sportfreak2020 on 2012-02-06
i have similar questions towards the same topic .. i m trying to set the xinput value for my virtual pointer ... this is for a remote linux server(cloud server) with tigerVNC running on it .. 
here is the output for xinput list 

```
xinput list
""	id=0	[XExtensionPointer]
""	id=1	[XExtensionKeyboard]
"Virtual core keyboard"	id=2	[XKeyboard]
"Virtual core pointer"	id=3	[XPointer]
```

I am trying to set the value for my right click = left click for my virtual pointer .. so that users who log in into this machine should NOT be able to get the right click menu at all .. 

so when i try to get list props for id =0 or 3 i get this error:
```
xinput list-props 0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  131 (XInputExtension)
  Minor opcode of failed request:  36 (X_ListDeviceProperties)
  Serial number of failed request:  15
  Current serial number in output stream:  15
```

```
xinput list-props 3
X Error of failed request:  XI_BadDevice (invalid Device parameter)
  Major opcode of failed request:  131 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Device id in failed request: 0x17
  Serial number of failed request:  14
```

any suggestions ????

---

### Post by sportfreak2020 on 2012-02-06
nevermind .. found out an alternative solution .. tint2 ( available in the repos ) offers much more customization .. its auth file 'tint2rc' is present in the ~/.config/tint2/  .. 

might help someone lookig for a similar solution .. 
Link: [http://code.google.com/p/tint2/wiki/Configure](http://code.google.com/p/tint2/wiki/Configure)

now i go and :popcorn:

---


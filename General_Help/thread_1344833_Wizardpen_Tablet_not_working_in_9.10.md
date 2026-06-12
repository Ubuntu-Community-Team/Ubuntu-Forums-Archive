---
title: "Wizardpen Tablet not working in 9.10"
date: 2009-12-03
forum: General Help
---

### Post by Black Don on 2009-12-03
Hi there,
I have a Genius G-Pen 340 tablet and have loaded the 0.7.0-alpha2 wizardpen drivers for it and it does not  work.  The system detects it and I seem to be able to click the buttons to do some things but I can not move the cursor around with the tablet.  I have searched for anything on-line that might help and have tried the fixes found at [http://www.jpbouza.com.ar/ESP2/tutoriales/gnulinux/genius-tablet/id/en](http://www.jpbouza.com.ar/ESP2/tutoriales/gnulinux/genius-tablet/id/en)
and from this forum
[http://ubuntuforums.org/showthread.php?t=1309953](http://ubuntuforums.org/showthread.php?t=1309953)

I have tried all the fixes that seem appropriate from these URL's but still have not resolved my issues.  It seems that is issue is beyond my abilities to fix with the resources I have found.  Some help would be much appreciated.

---

### Post by Favux on 2009-12-03
Hi Black Don,

Welcome to Ubuntu Forums!

Let's start by looking at:
```
xinput --list
```
and
```
grep -i name /proc/bus/input/devices

```

---

### Post by Black Don on 2009-12-04
xinput --list
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"ETPS/2 Elantech Touchpad"    id=2    [XExtensionPointer]
    Type is TOUCHPAD
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 8
        Max_value is 1144
        Resolution is 1
    Axis 1 :
        Min_value is 8
        Max_value is 760
        Resolution is 1
"CNF7129"    id=3    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Asus EeePC extra buttons"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=5    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Sleep Button"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=7    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=8    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=9    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=10    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"UC-LOGIC Tablet WP4030U"    id=11    [XExtensionPointer]
    Type is TOUCHPAD
    Num_buttons is 14
    Num_axes is 5
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 8000
        Resolution is 10000
    Axis 1 :
        Min_value is 0
        Max_value is 6000
        Resolution is 10000
    Axis 2 :
        Min_value is 0
        Max_value is 32767
        Resolution is 10000
    Axis 3 :
        Min_value is 0
        Max_value is 32767
        Resolution is 10000
    Axis 4 :
        Min_value is 0
        Max_value is 1023
        Resolution is 10000

grep -i name /proc/bus/input/devices
[FONT=monospace][/FONT]N: Name="Power Button"
N: Name="Lid Switch"
N: Name="Sleep Button"
N: Name="Power Button"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="Video Bus"
N: Name="Asus EeePC extra buttons"
N: Name="CNF7129"
N: Name="HDA Digital PCBeep"
N: Name="ETPS/2 Elantech Touchpad"
N: Name="UC-LOGIC Tablet WP4030U"

There you go.

---

### Post by drpjkurian on 2009-12-04
Hi you can give a try to my thread
[http://ubuntuforums.org/showthread.php?t=1337260](http://ubuntuforums.org/showthread.php?t=1337260)

All the best

---

### Post by Black Don on 2009-12-05
That worked Thanks.  :)

Even though your instructions are almost identical to those I had done from one of the other web sites I had mention I guess manually compiling from the source you provided in your thread made all the difference in the world.

---

### Post by Favux on 2009-12-05
Hi Black Don,

Great!  Nice job.

---

### Post by drpjkurian on 2009-12-06
> **Black Don said:**
> That worked Thanks.  :)

Even though your instructions are almost identical to those I had done from one of the other web sites I had mention I guess manually compiling from the source you provided in your thread made all the difference in the world.

Hi Black don

Thats great

---


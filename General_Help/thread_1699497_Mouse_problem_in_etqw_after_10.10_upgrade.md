---
title: "Mouse problem in etqw after 10.10 upgrade"
date: 2011-03-03
forum: General Help
---

### Post by davery on 2011-03-03
Hi,

I recently upgraded to 10.10.  Since the upgrade, when i start Enemy Territory: Quake Wars, everything works fine until i get into a mission, where i find myself automatically spinning uncontrollably, and i cannot move the mouse fast enough to compensate for it.  When i hit the voice chat button, it stops, and i can control my direction as normal, but then it comes back when i close that.  The mouse works fine in the game's menu system.

Possibly relevant points:
1. As i said, the mouse works fine in the game's menu system, which suggests a problem with the game.
2. I never had this problem in 10.04.
3. Unplugging usb devices and replugging them (all i have now are keyboard, mouse, and wireless adapter) and rmmod/modprobing usbhid sometimes makes it work.  It's like rolling the dice.
4. It once happened that i started a mission against the cpu to test it, then connected to a server to play, and it worked in the first case but started spinning in the second.
5. xorg.conf has no InputDevice listed.
6. Playing with xinput --list and moving things up or down the list (as suggested in a thread related to a stuck left mouse button) had the same effect as #3.  xinput --list output is: 

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft  Microsoft Basic Optical Mouse v2.0     id=8    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Wired Keyboard 600                id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Microsoft Wired Keyboard 600                id=9    [slave  keyboard (3)]
```I don't know what XTEST pointer is, and i don't know why the keyboard is listed under the virtual core pointer.
7. I don't have unclutter installed.

It seems to me that etqw thinks there is another input device controlling the pointer.  What about 10.10 might cause this?  Does anyone have any other suggestions?

Any help is greatly appreciated.

---

### Post by turtle153 on 2011-03-03
Theres a chance the keyboard is interfering. Try unplugging it and playing.

---

### Post by davery on 2011-03-05
I had tried that with mixed results, see #3.

I did follow the beginning of this thread: [http://www.howtoforge.com/how-to-auto-disable-the-touchpad-when-the-mouse-is-plugged-in-fedora-13](http://www.howtoforge.com/how-to-auto-disable-the-touchpad-when-the-mouse-is-plugged-in-fedora-13) to disable the keyboard as a pointing device the other day, and it worked after that.  I haven't had time to try again or to attempt automating it though.  Why would 10.10 have the keyboard automatically set as a pointing device?

---

### Post by davery on 2011-03-27
[LEFT]OK, after a couple weeks playing with it, i've had success most of the time with

```
$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft  Microsoft Basic Optical Mouse v2.0     id=8    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Wired Keyboard 600                id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Microsoft Wired Keyboard 600                id=9    [slave  keyboard (3)]
$xinput xinput list-props 10
Device 'Microsoft Wired Keyboard 600':
    Device Enabled (121):    1
    Coordinate Transformation Matrix (123):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (240):    0
    Device Accel Constant Deceleration (241):    1.000000
    Device Accel Adaptive Deceleration (242):    1.000000
    Device Accel Velocity Scaling (243):    10.000000
    Evdev Reopen Attempts (238):    10
    Evdev Axis Inversion (244):    0, 0
    Evdev Axis Calibration (245):    0, 0, 0, 0
    Evdev Axes Swap (246):    0
    Axis Labels (247):    "Abs X" (258), "Abs Y" (259), "Abs Z" (260), "Abs Rotary X" (261), "Abs Rotary Y" (262), "Abs Rotary Z" (263), "Abs Throttle" (264), "Abs Rudder" (265), "Abs Wheel" (266), "Abs Hat 0 X" (267), "Abs Hat 0 Y" (268), "Abs Hat 1 X" (269), "Abs Volume" (270), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
    Button Labels (248):    "Button 0" (257), "Button Unknown" (239), "Button Unknown" (239), "Button Wheel Up" (127), "Button Wheel Down" (128), "Button Horiz Wheel Left" (129), "Button Horiz Wheel Right" (130)
    Evdev Middle Button Emulation (249):    2
    Evdev Middle Button Timeout (250):    50
    Evdev Wheel Emulation (251):    0
    Evdev Wheel Emulation Axes (252):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (253):    10
    Evdev Wheel Emulation Timeout (254):    200
    Evdev Wheel Emulation Button (255):    4
    Evdev Drag Lock Buttons (256):    0
$xinput set-prop 10 "Device Enabled" 0

```As myself....  Yesterday, it didn't work until i did the same thing as root.  Today, neither is working.  That is, after doing these, i still get the spinning problem.  Any ideas on what else might be causing this?  How can i turn this off automatically?
[/LEFT]

---

### Post by davery on 2011-04-07
After the last post, i changed /usr/share/x11/xkb/compat/complete from 

```
// $XKeyboardConfig$
// $Xorg: complete,v 1.3 2000/08/17 19:54:34 cpqbld Exp $
default xkb_compatibility "complete"  {
    include "basic"
    augment "iso9995"
    augment "mousekeys"
    augment "accessx(full)"
    augment "misc"
    augment "xfree86"
    augment "level5"
};
```

to

```
// $XKeyboardConfig$
// $Xorg: complete,v 1.3 2000/08/17 19:54:34 cpqbld Exp $
default xkb_compatibility "complete"  {
    include "basic"
    augment "iso9995"
//    augment "mousekeys"
//   augment "accessx(full)"
    augment "misc"
    augment "xfree86"
    augment "level5"
};
```

and haven't had problems since.

---


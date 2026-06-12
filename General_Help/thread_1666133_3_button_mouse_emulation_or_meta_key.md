---
title: "3 button mouse emulation or meta key"
date: 2011-01-13
forum: General Help
---

### Post by pulven on 2011-01-13
Hi I have a problem getting Xfig working on my Xubuntu 10.10
First the setup, it's all virtual:
Dell Latitude
  |-->windows XP
         | --> virtualbox
                 | --> Xubuntu 10.10

Now Xfig needs the middle click, or the Meta_key. The problem is, I have neither.
First I looked at xinput
[INDENT]VirtualBox:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImExPS/2 Generic Explorer Mouse             id=9    [slave  pointer  (2)]
&#9116;   &#8627; (unnamed)                                   id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=8    [slave  keyboard (3)]

By testing with xinit test 9 I can see the buttons press values on screen
lover right,upper right and touchpad click produces 1
lover left,upper left click produces 3
scroll up produces 4
scroll down produces 5

VirtualBox:~$ xinput list-props 9  
Device 'ImExPS/2 Generic Explorer Mouse':
    Device Enabled (114):    1
    Coordinate Transformation Matrix (116):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (235):    0
    Device Accel Constant Deceleration (236):    1.000000
    Device Accel Adaptive Deceleration (237):    1.000000
    Device Accel Velocity Scaling (238):    10.000000
    Evdev Reopen Attempts (231):    10
    Evdev Axis Inversion (239):    0, 0
    Evdev Axes Swap (241):    0
    Axis Labels (242):    "Rel X" (124), "Rel Y" (125)
    Button Labels (243):    "Button Left" (117), "Button Middle" (118), "Button Right" (119), "Button Wheel Up" (120), "Button Wheel Down" (121), "Button Horiz Wheel Left" (122), "Button Horiz Wheel Right" (123), "Button Side" (233), "Button Extra" (234), "Button Unknown" (232), "Button Unknown" (232), "Button Unknown" (232), "Button Unknown" (232)
    Evdev Middle Button Emulation (244):    2
    Evdev Middle Button Timeout (245):    50
    Evdev Wheel Emulation (246):    0
    Evdev Wheel Emulation Axes (247):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (248):    10
    Evdev Wheel Emulation Timeout (249):    200
    Evdev Wheel Emulation Button (250):    4
    Evdev Drag Lock Buttons (251):    0

I've tried different xinput set-int-prop 9 "Evdev Middle Button Emulation" but I can't figure out how it should work
[/INDENT]
I've also been trying to remap the keyboard, with xmodmap, to get the Meta_L on the windows key, but had no luck here neither.
Overall I'm stuck and need help or pointers.
Which programs are used on startup? and where can I configure them? (Hal,X.X11,xmodmap,xinput)
Or can someone come with a solution?

all help are appreciated

-Rune 
 
In both cases, which order do the config files get loaded /etc/... ~/. ... ?

---


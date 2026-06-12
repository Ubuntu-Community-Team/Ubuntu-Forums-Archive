---
title: "Synaptics touchpad vertical scrolling problem"
date: 2011-01-21
forum: General Help
---

### Post by void00 on 2011-01-21
Well, I've got a Dell Inspiron N4010 14R laptop and has got Ubuntu 10.04  Installed and running.

My problem is that my Synaptics touchpad does not  have vertical or horizontal scrolling 
when using Ubuntu. In Win7, it  is ok and works perfect.
The Mouse preferences does not show any  Touchpad tab
I searched and read almost all the threads here but  still have not got a solution.

here is the output of **xinput  -list**
```

&#9121; Virtual core pointer                         id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST  pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB+PS/2  Optical Mouse                      id=11    [slave  pointer  (2)]
&#9116;    &#8627; PS/2 Synaptics TouchPad                     id=13    [slave  pointer   (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14     [slave  pointer  (2)]
&#9123; Virtual core keyboard                        id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST  keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power  Button                                id=6    [slave  keyboard (3)]
     &#8627; Video Bus                                   id=7    [slave  keyboard  (3)]
    &#8627; Power Button                                id=8     [slave  keyboard (3)]
    &#8627; Sleep Button                                 id=9    [slave  keyboard (3)]
    &#8627;  Laptop_Integrated_Webcam_1.3M               id=10    [slave  keyboard  (3)]
    &#8627; AT Translated Set 2 keyboard                id=12     [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys   

```It  detects the PS/2 Synaptics touchpad.

also the output of **xinput list-props "PS/2 Synaptics TouchPad"** is given below.
Is it possible to get the scrolling feature by setting the WheelEmulation to 1 using
**xinput set-int-props** **"PS/2 Synaptics TouchPad" **?
If so, please give me the command.

```

    Device Accel Constant Deceleration (241):    1.000000
    Device Accel Adaptive Deceleration (243):    1.000000
    Device Accel Velocity Scaling (244):    10.000000
    Evdev Reopen Attempts (238):    10
    Evdev Axis Inversion (245):    0, 0
    Evdev Axes Swap (247):    0
    Axis Labels (248):    "Rel X" (131), "Rel Y" (132)
    Button Labels (249):    "Button Left" (124), "Button Middle" (125), "Button Right" (126), "Button Wheel Up" (127), "Button Wheel Down" (128)
    Evdev Middle Button Emulation (250):    2
    Evdev Middle Button Timeout (251):    50
    Evdev Wheel Emulation (252):    0
    Evdev Wheel Emulation Axes (253):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (254):    10
    Evdev Wheel Emulation Timeout (255):    200
    Evdev Wheel Emulation Button (256):    4
    Evdev Drag Lock Buttons (257):    0
```

I installed and tried both  gsynaptics and gpointing-device-settings, but they say
to turn on  SHMConfig. 
Another thing is that once I changed "Protocol" to "alps"  in xorg.conf, both the above
work but has no effect when I change  the settings.The Mouse preferences also shows
Touchpad tab once the  protocol is changed to alps. So should I install alps driver
or  something?

Can someone please point me towards the solution. I would really like to use the
vertical scroll as I prefer the touchpad to a usb mouse.

---


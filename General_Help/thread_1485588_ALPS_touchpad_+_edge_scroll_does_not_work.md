---
title: "ALPS touchpad + edge scroll does not work"
date: 2010-05-17
forum: General Help
---

### Post by Vladimir Hidalgo on 2010-05-17
I've got an PCG-71311U (VPCEB15EL) which is a Vaio serie "E" laptop with an ALPS touchpad.

It came with Windows 7, in which I could use the right edge of the touchpad as a vertical scrollbar and bottom edge as the horizontal.

I think it's multitouch capable, as I tested in Google Chrome to make zoom out/zoom in by using two fingers and a "expanding from the center" gesture and it succeeded.

I don't mind about the multitouch, but I can't get the scroll thing.

Moreover I can't disable the touchpad while typing with Syndaemon. Can't do any configuration with the Mouse preferences window.

It's just like everything were hardcoded for my touchpad. What can I do?.

This is Xorg.0.log info about my touchpad: ```

:~$ cat /var/log/Xorg.0.log | grep -i alps
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event8)
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
(**) AlpsPS/2 ALPS GlidePoint: App
```

Synclient info:

```
:~$ synclient -l
Parameter settings:
    LeftEdge                = 153
    RightEdge               = 870
    TopEdge                 = 115
    BottomEdge              = 652
    FingerLow               = 12
    FingerHigh              = 14
    FingerPress             = 127
    MaxTapTime              = 180
    MaxTapMove              = 56
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 1
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 139
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 25
    HorizScrollDelta        = 25
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 1
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.4
    MaxSpeed                = 1
    AccelFactor             = 0.207
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 14
    EdgeMotionMaxZ          = 79
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 102
    EdgeMotionUseAlways     = 0
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 1
    GuestMouseOff           = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 1
    CircularScrolling       = 0
    CircScrollDelta         = 0.01
    CircScrollTrigger       = 8
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 99
    CoastingSpeed           = 0
    PressureMotionMinZ      = 14
    PressureMotionMaxZ      = 79
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    JumpyCursorThreshold    = 0
```

---

### Post by Vladimir Hidalgo on 2010-05-17
tpconfig package also does not work :(

---

### Post by Vladimir Hidalgo on 2010-05-20
Good news!, it works with 2.6.34 kernel!

I just updated my kernel to:

> Linux protecsal 2.6.34-020634-generic #020634 SMP Mon May 17 20:34:55 UTC 2010 i686 GNU/Linux

To my surprise scroll does work now!.

I can't use GSynaptics at all now (complains about SHMconfig not enabled in xorg.conf) neither syndaemon or synclient (now it reports no synaptics device) but hey, at least I have scroll!

I hope gnome/ubuntu updates the touchpad utilities to properly support configuration of ALPS touchpads!.

Also it seems now Xorg identifies some "Vaio Jogdial" but it's ignoring it. As it seems there's hope to have good support for 10.10, the perfect 10!.

> (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event7)
(**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event7"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Found relative axes
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/event4)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)


---

### Post by Vladimir Hidalgo on 2010-08-28
Bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543")

---

### Post by Sojurner on 2010-10-01
i have a similar issue. However my edge scroll worked form the beginning, but as soon as i scroll up the screen scrolls all the way to the bottom... any idea how to fix this?

---

### Post by bel3atar on 2010-10-18
same problem

---

### Post by kennethadammiller on 2010-12-09
I too have the same problem. Only I have an aspire 5740, with an Alps and it has the same edge scroll problem as well.

The symptom is this: i can scroll down with it, but I can not scroll up. If I do, it tries to scroll very fast downward. So I can only use it to scroll down. Also, I do not have horizontal scroll.

---


---
title: "Samsung N150 touchpad"
date: 2010-08-01
forum: General Help
---

### Post by SushiR on 2010-08-01
My netbook has a synaptics touchpad. I just want to do the following:

1.) smooth (!) two-finger scrolling (horiz/vert)
2.) a 3-finger-tap as middle click and 2-finger-tap as right click

From dmesg I got this:
```
[   14.485738] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000
[   14.539778] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
``` 
I've tried various recommendations I've found via Google and I got it working somehow, but it was far away from being usable or smooth.

This is the output of "synclient -l"
```
Parameter settings:
    LeftEdge                = 1752
    RightEdge               = 5192
    TopEdge                 = 1620
    BottomEdge              = 4236
    FingerLow               = 24
    FingerHigh              = 29
    FingerPress             = 255
    MaxTapTime              = 180
    MaxTapMove              = 221
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 280
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 100
    HorizScrollDelta        = 100
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 1
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.4
    MaxSpeed                = 0.7
    AccelFactor             = 0.00995223
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 29
    EdgeMotionMaxZ          = 159
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 401
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
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 199
    CoastingSpeed           = 0
    PressureMotionMinZ      = 29
    PressureMotionMaxZ      = 159
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

If someone somehow managed to work out a decent configuration for N150 (or maybe N220, that obviously suffers from the same problem), please let me know. I'm somewhat frustrated...

---

### Post by SushiR on 2010-08-02
Hmmm, seems like my idea of a working touchpad is somewhat exotic...

---

### Post by SushiR on 2010-08-03
Anyone?

---

### Post by SushiR on 2010-08-18
Two weeks - and nobody has an idea. Well, obviously my topic is too advanced for the masses...?!

---

### Post by generics on 2010-12-12
Hi SushiR,
My touchpad was switched off for years, until...
Got a new Samsung N150 and read the instructions on how to use the touchpad. Stopped using a mouse instantly! Replaced Windows7 by Ubuntu 10.10 after 1 month. But now touchpad is so basic.
Did you ever get yours working?

I got 2 finger scroll working, but not smoothly (it was only other touchpad help I could find)

I really miss:
Pinch in and out...
Rotate
Single finger vertical/horizontal scroll using side/bottom of touchpad

Thanks for any help you /others can give

---

### Post by Ge64 on 2011-06-21
Allow me to revive this ancient thread for i have not found a decent source of information on the matter:

I've enabled two-finger scrolling through the Mouse settings window but it just jumps around and is completely unusable (in fact it may cause serious damage to your netbook, your surroundings, or your fists). I've tried messing around with the synclient settings to no avail, if anybody has got it working please post your settings here!

Pinch-to-zoom would be nice but i don't expect much from this touchpad. It works nicely in Windows though so it's not a hardware issue.

---

### Post by hit on 2012-02-07
[http://ubuntuforums.org/showpost.php?p=11141211&postcount=1](http://ubuntuforums.org/showpost.php?p=11141211&postcount=1)

Try this one, worked for me.

---


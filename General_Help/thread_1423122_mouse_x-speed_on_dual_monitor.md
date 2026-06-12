---
title: "mouse x-speed on dual monitor"
date: 2010-03-06
forum: General Help
---

### Post by Eraemaajaervi on 2010-03-06
hi, 
I'm using two monitors, they're virtually placed next to each other so the virtual screen resolution is (1024+1280) x 800px. 
Now my mouse speed on the x-axis is automatically set higher, which is good if you permanently switch between both monitors all the time. But I don't need it, so how do I turn it off? It's kinda annoying if you're used to your "normal" mouse speed.
Y-axis speed is still fine.

also, is there a way do display the gnome-do dock on the right handed monitor? it places itself always on the left monitor....

thanks

[edit]
oh by the way, I'm using Mint 8 which is Ubuntu 9.10 with gnome 2.28.1

---

### Post by steve_d on 2010-12-15
I have the same issue: Enabling dual monitors makes the touchpad x-axis speed much higher than the y-axis speed.

Lenovo T410, lspci shows:

VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

10.10 32bit, Gnome.

I believe its using the synaptics driver.

synclient output:

```

steve@T410:~$ synclient -l
Parameter settings:
    LeftEdge                = 1781
    RightEdge               = 5579
    TopEdge                 = 1646
    BottomEdge              = 4582
    FingerLow               = 24
    FingerHigh              = 29
    FingerPress             = 255
    MaxTapTime              = 180
    MaxTapMove              = 245
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 280
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 111
    HorizScrollDelta        = 111
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.4
    MaxSpeed                = 0.7
    AccelFactor             = 0.00896057
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 29
    EdgeMotionMaxZ          = 159
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 446
    EdgeMotionUseAlways     = 0
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 0
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


Anyone have ideas? I go from single head to dual head on a daily basis, so I would prefer not to adjust the settings manually everytime.

---


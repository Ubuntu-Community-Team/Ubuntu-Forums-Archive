---
title: "Touchpad Mouse incorrectly mapped"
date: 2011-04-14
forum: General Help
---

### Post by skydiver|goose on 2011-04-14
Hey folks,

My touchpad mouse is incorrectly mapped. I've tried fooling with the general "mouse" options, but it won't work right.

In short, because the left and right click buttons are also a part of the touch pad, they're being mapped as a part of the touch pad itself and not as button; therefore, I have no right click, and if I had one finger on the left click and one finger on the touchpad, the mouse freaks out.

Thanks.

---

### Post by skydiver|goose on 2011-04-15
bump

---

### Post by skydiver|goose on 2011-04-15
I hate to keep bumping, but a working mouse is kinda one of those things you need...

cat /proc/bus/input/devices reveals this about the mouse, if it means anything to anyone:
I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input10
U: Uniq=
H: Handlers=mouse1 event10 
B: PROP=d
B: EV=b
B: KEY=6420 10000 0 0 0 0
B: ABS=260800011000003

---

### Post by rummy77 on 2011-04-18
Try running this and see what happens. It's going to set parameters for the synclient program which is running your touchpad. If it works we can set it up to run at each boot.

```
PROG=synclient
echo edges
$PROG LeftEdge=1750
$PROG RightEdge=5200
$PROG TopEdge=1620
$PROG BottomEdge=3500
echo Finger Press
$PROG FingerLow=24
$PROG FingerHigh=29
$PROG FingerPress=255
echo taps time
$PROG MaxTapTime=180
$PROG MaxTapMove=220
$PROG MaxDoubleTapTime=180
$PROG SingleTapTimeout=180
$PROG ClickTime=100
$PROG FastTaps=1
echo emulate
$PROG EmulateMidButtonTime=75
$PROG EmulateTwoFingerMinZ=280
$PROG EmulateTwoFingerMinW=7
echo scrolling
$PROG VertScrollDelta=100
$PROG HorizScrollDelta=0
$PROG VertEdgeScroll=1
$PROG HorizEdgeScroll=0
$PROG CornerCoasting=0
$PROG VertTwoFingerScroll=0
$PROG HorizTwoFingerScroll=0
echo Pointer speed
$PROG MinSpeed=0.1
$PROG MaxSpeed=1
$PROG AccelFactor=1
$PROG TrackstickSpeed=0
$PROG EdgeMotionMinZ=29
$PROG EdgeMotionMaxZ=159
$PROG EdgeMotionMinSpeed=1
$PROG EdgeMotionMaxSpeed=401
$PROG EdgeMotionUseAlways=0
echo scrolling flags
$PROG UpDownScrolling=1
$PROG LeftRightScrolling=1
$PROG UpDownScrollRepeat=1
$PROG LeftRightScrollRepeat=1
$PROG ScrollButtonRepeat=100
echo Touchpad Mouse one/off
$PROG TouchpadOff=0
$PROG GuestMouseOff=0
echo dragging
$PROG LockedDrags=0
$PROG LockedDragTimeout=5000
echo corners
$PROG RTCornerButton=2
$PROG RBCornerButton=3
$PROG LTCornerButton=0
$PROG LBCornerButton=1
echo tap
$PROG TapButton1=1
$PROG TapButton2=2
$PROG TapButton3=3
echo click
$PROG ClickFinger1=1
$PROG ClickFinger2=3
$PROG ClickFinger3=2
echo Circular
$PROG CircularScrolling=0
$PROG CircScrollDelta=0.1
$PROG CircScrollTrigger=0
$PROG CircularPad=0
echo Palm
$PROG PalmDetect=1
$PROG PalmMinWidth=10
$PROG PalmMinZ=199
$PROG CoastingSpeed=0
echo Grab
$PROG GrabEventDevice=1
$PROG TapAndDragGesture=1
echo Area
$PROG AreaLeftEdge=0
$PROG AreaRightEdge=0
$PROG AreaTopEdge=0
$PROG AreaBottomEdge=0
echo Jumpy
$PROG JumpyCursorThreshold=120

```

---

### Post by skydiver|goose on 2011-04-18
Just run it in a .sh script? Sudo, or regular user?

---

### Post by rummy77 on 2011-04-19
If you just copy all of that and paste it in the terminal, it should set all of those variables in synclient.

You can change any of the variables you need to get the touchpad to work the way you want.  More info is at [http://manpages.ubuntu.com/manpages/hardy/en/man5/synaptics.5.html](http://manpages.ubuntu.com/manpages/hardy/en/man5/synaptics.5.html).

If you get some settings that work, then you can just copy all of the above, with your own changes, into gedit and save it as a .sh, then make it executable, and have it run at boot.  Good luck, and post back if you need to.

---

### Post by skydiver|goose on 2011-04-19
Unfortunately, it didn't resolve my issues. My right click still doesn't work, and the mouse still hops all over the screen when I try and have my thumb on the left click button and pointer finger on the touchpad.

---


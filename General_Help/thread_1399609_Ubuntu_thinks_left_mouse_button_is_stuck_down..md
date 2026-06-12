---
title: "Ubuntu thinks left mouse button is stuck down."
date: 2010-02-05
forum: General Help
---

### Post by nevdelap on 2010-02-05
I found a post describing apparently the same problem in a closed forum where I couldn't reply - [http://ubuntuforums.org/showthread.php?t=1297928]("http://ubuntuforums.org/showthread.php?t=1297928")

I have the same issue, and have had it since about the time that post was made - October last year.

Ubuntu will occasionally think that the left mouse button is pressed, when it is not. Moving the mouse will move a selection over the text of the page or edit control where it thinks the selection is being made by clicking and holding the left button.

The mouse works fine in Windows and the mouse button is not stuck down. When it is this way further clicks are ignored.

The difference between my issue and that described previously is that if I left click on the touchpad left button things will go back to normal and the mouse will continue working.

Anyone else had this issue? Any ideas on how to fix it?

Thanks,

Nev

Ubuntu 9.10 with all updates on Asus EEE 1000H.

---

### Post by myurko on 2010-06-15
I am having the same issue on both 9.10 and 10.04. However, I have been unable to find any easy way to get it unstuck. This essentially renders the OS useless to me.

---

### Post by Basotang on 2010-07-06
I do have the exact same problem. Sometimes I manage to get out it by clicking randomly, sometimes no. Going to a console out of X (CTRL+ALT+F1) and coming back (CTRL+ALT+F7) does not cure it. 
Pretty annoying indeed.

Basotang.

---

### Post by demvin on 2011-03-23
Getting the same thing here on 10.10 amdx64.

When it happens, even if I unplug my mouse to use the trackpad I still get the problem.  

Very very annoying.

---

### Post by tredegar on 2011-03-23
An observation: Only 4 people with this problem in the last year. No solutions offered or found.

Maybe you have accidentally enabled some "disability" feature for people with disabilities, who cannot use a mouse in the usual way. Eg try pressing the SHIFT key five times. 

Meanwhile check out System - Preferences - Assistive Technologies.  There may be other places where this "assistive" stuff hides. If you fix it, please let us know what it was that was mis-set.

---

### Post by shangas on 2011-04-05
I'm getting this same issue intermittently on a fresh Ubuntu 10.10-x86 install. It's definitely not an "assistive" feature, and once it triggers, I haven't found any way to get the mouse button functionality back except by rebooting.

---

### Post by demvin on 2011-05-31
Same problem here.  Natty amd64 dell E6510 with usb mouse.

Very annoying and so basic.

---

### Post by xpluto on 2011-06-02
same problem here and  after  suspension my keyboard freezes too

---

### Post by mannyweb.ca on 2011-06-25
Exactly same issue here.  Using ubuntu 10.04 (LTS version) on my new netbook  Aspire One 522.  It is hell of annoying.  Please I need a solution or only option seems back to windows which I do not want!

---

### Post by mannyweb.ca on 2011-06-26
Is it possible that it might be a hardward issue; atleast for me.  I say because I thought upgrading might be the solution.  So I went from 10.04 to 10.10 and then to 11.04.  All had the same issues, finally decided to do a clean install of 10.04 and this happened during the install.  I mean from the very beginning.

Unfortunately I don't have windows to prove this theory.

---

### Post by wafflesausage on 2011-06-26
Try unplugging the keyboard, if that doesn't work, try a different mouse.

---

### Post by mannyweb.ca on 2011-06-26
Actually I kind of fixed this.  The problem is coming from the touchpad.  My netbook allows me to disable it with FN-F7.  Mouse works correctly now.

Personally this is not one of the greatest set-ups, but at least it lets me figure out what the problem is and configure ubuntu on this netbook.

---

### Post by mannyweb.ca on 2011-06-26
Ok so by going to the terminal and typing in:  synclient -l  it lists what I believe to be my touchpad configurations.  Anything in there that may indicate why my touchpad is out of it's mind?


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
    HorizEdgeScroll         = 0
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
    TouchpadOff             = 0
    GuestMouseOff           = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 0
    RBCornerButton          = 0
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 0
    TapButton2              = 0
    TapButton3              = 0
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

---

### Post by DemonSpeedster on 2011-07-25
This also happen to me in 10.04 and 10.10 on Vaio E when I'm using the Microsoft Mobile Wireless 4000, but not with my Razer Orochi bluetooth mouse

The built in touchpad, as far as I can remember works normally

---

### Post by mschlager on 2012-02-03
Not sure if this will help.  Not even sure if this has worked for me before, but I tried it today and it helped work around the problem.

Just unplugged the USB mouse and plugged it into a different USB port.

Of course if the problem is with your touchpad, you will have to find a different strategy.

---

### Post by lhankins on 2012-08-07
I have the same problem on a fresh 12.04 Ubuntu install (64-bit).

Its definitely NOT a hardware problem (have tried multiple mice).

The symptoms :   I do something that causes the left mouse button to appear stuck down (its like a MOUSE_UP event never happened).   

When this happens, it doesn't happen in ALL apps, just certain apps.

Intellij IDEA (a Java development environment) is the one it kills me in (I end up having to reboot... which is painful).    I have occasionally seen it happen in Chromium too.

I have tried tons of things... from disconnecting the mouse and hooking it to a new USB port, to trying to use various commands to reset the state of the mouse (all to no avail).

When this happens... I end up having to reboot. 

One thing that seems to make it happen more often... (using Unity)... in a terminal, if I press ALT (and type in some menu command), that seems to cause it a lot.   

Also, I"m usually running one or two VirtualBox VMs... not sure if that contributes to it.

---

### Post by lhankins on 2012-08-08
One other piece of information (related to my post directly above).

This issue only happens in Unity.

After having to reboot 3 times yesterday to get around this issue, I installed Gnome Shell.      I've been working using Gnome classic all day today with zero occurrences of the problem.

---

### Post by lhankins on 2012-10-02
I figured out an easy way to resolve this when it happens.    Basically - I had my laptop's touchpad disabled in the BIOS (since I would often accidentally hit the touchpad while typing).     I re-enabled the touchpad, and now when things get into the state described above (left mouse button permanently stuck) pressing the left button on the touchpad "resets" things (puts things back into normal working conditions).

---


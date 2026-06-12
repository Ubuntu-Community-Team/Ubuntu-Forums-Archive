---
title: "Help configuring extra mouse buttons"
date: 2009-07-08
forum: General Help
---

### Post by stasheck on 2009-07-08
Hi everyone

I've just spent whole afternoon trying to setup my new Logitech Cordless Trackman Optical trackball so I could use extra mouse buttons, and I'm getting dizzy.

Already searched quite a few tutorials, all I got from them is that I should setup my **xorg.conf** in some way or another, and that I should use *imwheel* to get required result - but the amount of combinations I yielded is beyond my ability and time for tests. Furthermore, many of these tutorials were quite old, so I doubt they still work.

Anyway, here's the situation: I identyfied buttons using *xev* as follows:
- **left mouse button**: *button 1*
- **middle mouse button** (under scrollwheel): *b2*
- **right mouse button**: *b3*
- **wheel up**: *b4*
- **"up wheel button"**: *b11/b4* (xev outputs b11 and b4 almost simultanesly)
- **wheel down**: *b5*
- **"down wheel button"**: *b12/b5*
- **"down arrow" button**: *b8*
- **"up arrow" button**: *b9*
- **"lock" button**: *b10*

Now, what I want is to use:
- left, middle and right mb **as usual**
- "up/down" arrow **as page up/page down**
- "lock" the same **as middle** (second middle button)

That should be no rocket science, but I'm unable to do it. When trying to use *imwheel -c* I get:
- **left mouse button**: *"Wheel: Left (Button6)"*
- **middle mouse button** (under scrollwheel): *"Wheel: Left (Button6)"*
- **right mouse button**: *"Wheel: Left (Button6)"*
- **wheel up**: *"Wheel: Up (Button4)"*
- **"up wheel button"**: *"Wheel: Left (Button6)"*
- **wheel down**: *"Wheel: Down (Button5)"*
- **"down wheel button"**: *"Wheel: Left (Button6)"*
- **"down arrow" button**: *"Button: Thumb1 (Button8)"*
- **"up arrow" button**: *"Button: Thumb2 (Button9)"*
- **"lock" button**: *"Wheel: Left (Button6)"*

My **xorg.conf**:
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"    
EndSection                                   

Section "Files"
EndSection     

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1" 
    Load           "freetype"
    Load           "glx"     
EndSection                   

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection                       

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse" 
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 94.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M GS"
    Option         "Coolbits" "1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1920x1080 +0+0, DFP: nvidia-auto-select +0+1080"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by stasheck on 2009-07-09
Is that possible I'm the single one out there, who needs such a lousy thing as assigning useful functions to mousebuttons, and noone can share their experience?

---

### Post by stasheck on 2009-07-17
It's a shame noone bothered to answer me, but I was successful after all - and I bet my solution is the best there is.

Turns out we have an appropriate software in our repositories - it's called btnx. Google, can you hear me? EXTRA MOUSE BUTTONS, HANDLING, btnx :-)

Setup is piece of cake, software has a graphic tool for the job - really nice. As for Logitech mouse, I suggest installing locomo and issuing
sudo lomoco --no-sms
if you have extra buttons which send 2 events at single press.

Anyway, if anyone has problems setting up btnx - I'm willing to help, ask in this thread.

---

### Post by jinks on 2009-09-01
just wanted to say thank you for this info!  I haven't used ubuntu since Dapper Drake, and just got back on it yesterda.  I have the same trackball, and stumbled upon this thread.  btnx is great.  Can I ask you what your xorg.conf is for your mouse?  I couldn't get btnx to work until I copied and pasted from your xorg.conf in your first post.  Is it still the same?

---

### Post by stasheck on 2009-09-02
Glad I could help someone :-)

As for xorg.conf, right now it looks like this:
```
Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse" 
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "Buttons" "12"        
    Option         "ZAxisMapping" "4 5"  
    Option         "ButtonMapping" "1 10 3 8 9 2"
    Option         "EmulateWheelButton" "8"
EndSection
```

I'm pretty sure that "ButtonMapping" doesn't matter right now, when using btnx and it's just artifact from "before".

I'd also suggest installing "lomoco" and running "lomoco --no-sms", which disables extra mouse events for scroll buttons (not scrollwheel).

---


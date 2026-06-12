---
title: "Mouse Tilt Wheel"
date: 2009-07-28
forum: General Help
---

### Post by Lucky75 on 2009-07-28
Hi all,

I have a Logitech S510 wireless mouse/keyboard combo, and I was wondering if anyone knew how to get the axis tilt on the wheel to work (left+right)?
I'm not too sure what to configure here. Do I need to config my Xorg.conf file? Or can I get away with doing it somewhere else, maybe through the HAL?

I ran "xev" and this was the result:

_For Left button press:_

```

ButtonPress event, serial 35, synthetic NO, window 0x3a00001,
    root 0x1a7, subw 0x3a00002, time 1105953278, (33,51), root:(40,76),
    state 0x10, **button 1**, same_screen YES

```

_For Middle/Wheel button:_
```

ButtonPress event, serial 35, synthetic NO, window 0x3a00001,
    root 0x1a7, subw 0x3a00002, time 1105954782, (33,51), root:(40,76),
    state 0x10, **button 2**, same_screen YES

```

_For Right Button_
```

ButtonPress event, serial 35, synthetic NO, window 0x3a00001,
    root 0x1a7, subw 0x3a00002, time 1105953822, (33,51), root:(40,76),
    state 0x10, **button 3**, same_screen YES

```


Now, for tilt left and right, it's a bit different. It doesn't seem to be a button press anymore?

_Left Tilt:_
```

KeyPress event, serial 37, synthetic NO, window 0x3a00001,
    root 0x1a7, subw 0x3a00002, time 1106104734, (42,38), root:(49,63),
    state 0x10, **keycode 113 **(keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x3a00001,
    root 0x1a7, subw 0x3a00002, time 1106104742, (42,38), root:(49,63),
    state 0x10, **keycode 113** (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 37, synthetic NO, window 0x3a00001,
    root 0x1a7, subw 0x3a00002, time 1106105246, (43,38), root:(50,63),
    state 0x10,** keycode 78** (keysym 0xff14, Scroll_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x3a00001,
    root 0x1a7, subw 0x3a00002, time 1106105253, (43,38), root:(50,63),
    state 0x10, **keycode 78** (keysym 0xff14, Scroll_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


```
Where 113 is the tilting left, and 78 seems to be returning to centre?


_Right Tilt:_
```

KeyPress event, serial 37, synthetic NO, window 0x3a00001,
    root 0x1a7, subw 0x3a00002, time 1106107494, (47,39), root:(54,64),
    state 0x10, **keycode 114** (keysym 0xff53, Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x3a00001,
    root 0x1a7, subw 0x3a00002, time 1106107501, (47,39), root:(54,64),
    state 0x10,** keycode 114** (keysym 0xff53, Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyPress event, serial 37, synthetic NO, window 0x3a00001,
    root 0x1a7, subw 0x3a00002, time 1106108014, (48,39), root:(55,64),
    state 0x10, **keycode 78** (keysym 0xff14, Scroll_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x3a00001,
    root 0x1a7, subw 0x3a00002, time 1106105253, (43,38), root:(50,63),
    state 0x10, **keycode 78** (keysym 0xff14, Scroll_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


```

Where 114 is the tilting right, and 78 seems to be returning to centre?


Help would be much appreciated. Thanks!

---

### Post by Lucky75 on 2009-07-28
To add, here's my current Xorg.conf file:

```

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Option          "AddARGBGLXVisuals"     "True"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Extensions"
        Option          "Composite"     "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Screen  0
        BusID   "PCI:1:0:0"
EndSection

Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection

```

I guess I should mention that I'm using Ubuntu 9.04, Gnome.

---

### Post by Lucky75 on 2009-07-29
Bump. Any help would be much appreciated. THanks!

---

### Post by 3rdalbum on 2009-07-29
If you're using Intrepid or Jaunty, you should already have use of the left-right function on your scroll wheel. Are you using Hardy or an earlier version?

---

### Post by Lucky75 on 2009-07-29
Nope, jaunty. Maybe I just need to enable it then? How would I get it to go back/forward in firefox?

Edit: Hey, you're right! I have to hold the Alt key down though. Thanks!

It seems that no matter if I change the Mousewheel.Horizontal.Action =2 or not in about:config, nothing actually changes. Seems to be a bug in FF for ubuntu or something.

---

### Post by Lucky75 on 2009-07-29
This is what I pulled from a website, and it's what I've been doing, but it still doesn't work. It seems to be a problem with firefox and linux. 

> 
In Firefox 3 on Linux, the mouse button assignments for Back and Forward have changed, to follow X11 customs. Previous versions of Firefox used buttons 6 and 7 for Back and Forward, respectively. Firefox 3 uses buttons 8 and 9. You can configure Firefox to use 6 and 7 by editing some hidden preferences.

   1. In the Location bar, type about:config and press EnterReturn.
          * The about:config "This might void your warranty!" warning page may appear. Click I'll be careful, I promise!, to continue to the about:config page. 
   2. In the Filter: box, type mousewheel.horizscroll.withnokey.
   3. Double-click on mousewheel.horizscroll.withnokey.action, set the value to 2, and click OK.
   4. Double-click on mousewheel.horizscroll.withnokey.numlines, set the value to -1, and click OK.
   5. Double-click on mousewheel.horizscroll.withnokey.sysnumlines, which should set the value to false. 

You can now close the about:config page.


---


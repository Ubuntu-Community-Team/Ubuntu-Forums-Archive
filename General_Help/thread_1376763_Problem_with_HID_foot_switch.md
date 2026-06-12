---
title: "Problem with HID foot switch"
date: 2010-01-09
forum: General Help
---

### Post by MarcusAntonius on 2010-01-09
Hello,

I purchased a foot pedal ([http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&Item=220535948343&Category=162&_trkparms=algo%3DLVI%26its%3DI%26otn%3D1](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&Item=220535948343&Category=162&_trkparms=algo%3DLVI%26its%3DI%26otn%3D1)), which I want to use as a substitute for the ALT, CTRL and SHIFT key (Mainly in my texteditor, Emacs, where these modifiers are used a lot for commands).

So instead of pressing ALT+x I want to press the left pedal + x. However, instead of going into the command mode it just types x to the screen. If I keep the pedal pressed, and type another x, it switches into command mode, like it should have done right away.

The device seems to use HID, and lsusb gives
Bus 005 Device 004: ID 1130:660c Tenx Technology, Inc.

Is there a way, how I can change the behaviour of the device?

---

### Post by jpkotta on 2010-01-09
Control, alt, shift, and a few other keys are special: they're *modifiers*.  You could use xev to see what keycodes the pedal is sending, and then add them to the list of modifiers with xmodmap.  

```
xev # and then press e.g. alt
```
```
Outer window is 0x4200001, inner window is 0x4200002

PropertyNotify event, serial 8, synthetic NO, window 0x4200001,
    atom 0x27 (WM_NAME), time 1085946706, state PropertyNewValue

PropertyNotify event, serial 9, synthetic NO, window 0x4200001,
    atom 0x22 (WM_COMMAND), time 1085946706, state PropertyNewValue

PropertyNotify event, serial 10, synthetic NO, window 0x4200001,
    atom 0x28 (WM_NORMAL_HINTS), time 1085946706, state PropertyNewValue

CreateNotify event, serial 11, synthetic NO, window 0x4200001,
    parent 0x4200001, window 0x4200002, (10,10), width 50, height 50
border_width 4, override NO

PropertyNotify event, serial 14, synthetic NO, window 0x4200001,
    atom 0xea (WM_PROTOCOLS), time 1085946706, state PropertyNewValue

MapNotify event, serial 15, synthetic NO, window 0x4200001,
    event 0x4200001, window 0x4200002, override NO

ConfigureNotify event, serial 20, synthetic NO, window 0x4200001,
    event 0x4200001, window 0x4200001, (0,0), width 178, height 178,
    border_width 0, above 0xe0039b, override NO

ReparentNotify event, serial 20, synthetic NO, window 0x4200001,
    event 0x4200001, window 0x4200001, parent 0xe0609b,
    (0,0), override NO

ConfigureNotify event, serial 23, synthetic YES, window 0x4200001,
    event 0x4200001, window 0x4200001, (1284,27), width 178, height 178,
    border_width 0, above 0xe0609a, override NO

PropertyNotify event, serial 23, synthetic NO, window 0x4200001,
    atom 0x1a2 (_NET_WM_DESKTOP), time 1085946715, state PropertyNewValue

PropertyNotify event, serial 23, synthetic NO, window 0x4200001,
    atom 0x1df (_NET_WM_ALLOWED_ACTIONS), time 1085946715, state PropertyNewValue

PropertyNotify event, serial 24, synthetic NO, window 0x4200001,
    atom 0x12e (_KDE_NET_WM_FRAME_STRUT), time 1085946715, state PropertyNewValue

PropertyNotify event, serial 24, synthetic NO, window 0x4200001,
    atom 0x1a0 (_NET_FRAME_EXTENTS), time 1085946715, state PropertyNewValue

PropertyNotify event, serial 25, synthetic NO, window 0x4200001,
    atom 0x1e9 (_WIN_STATE), time 1085946715, state PropertyNewValue

PropertyNotify event, serial 25, synthetic NO, window 0x4200001,
    atom 0x1e8 (_WIN_LAYER), time 1085946715, state PropertyNewValue

PropertyNotify event, serial 25, synthetic NO, window 0x4200001,
    atom 0x1eb (_WIN_WORKSPACE), time 1085946715, state PropertyNewValue

PropertyNotify event, serial 25, synthetic NO, window 0x4200001,
    atom 0x1f1 (_WIN_AREA), time 1085946715, state PropertyNewValue

ConfigureNotify event, serial 25, synthetic YES, window 0x4200001,
    event 0x4200001, window 0x4200001, (1284,27), width 178, height 178,
    border_width 0, above 0xe0609a, override NO

MapNotify event, serial 26, synthetic NO, window 0x4200001,
    event 0x4200001, window 0x4200001, override NO

VisibilityNotify event, serial 26, synthetic NO, window 0x4200001,
    state VisibilityUnobscured

Expose event, serial 26, synthetic NO, window 0x4200001,
    (0,0), width 178, height 10, count 3

Expose event, serial 26, synthetic NO, window 0x4200001,
    (0,10), width 10, height 58, count 2

Expose event, serial 26, synthetic NO, window 0x4200001,
    (68,10), width 110, height 58, count 1

Expose event, serial 26, synthetic NO, window 0x4200001,
    (0,68), width 178, height 110, count 0

PropertyNotify event, serial 26, synthetic NO, window 0x4200001,
    atom 0xef (WM_STATE), time 1085946716, state PropertyNewValue

FocusIn event, serial 26, synthetic NO, window 0x4200001,
    mode NotifyNormal, detail NotifyNonlinear

KeymapNotify event, serial 26, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 32, synthetic NO, window 0x4200001,
    root 0x1a7, subw 0x0, time 1085946728, (271,769), root:(1555,796),
    state 0x10, keycode 36 (keysym 0xff0d, Return), same_screen YES,
"   XLookupString gives 1 bytes: (0d) "
    XFilterEvent returns: False

EnterNotify event, serial 32, synthetic NO, window 0x4200001,
    root 0x1a7, subw 0x0, time 1085946730, (271,769), root:(1555,796),
    mode NotifyGrab, detail NotifyNonlinear, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 33, synthetic NO, window 0x4200001,
    mode NotifyNormal, detail NotifyNonlinear

FocusIn event, serial 33, synthetic NO, window 0x4200001,
    mode NotifyNormal, detail NotifyNonlinear

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  4294967207 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

LeaveNotify event, serial 35, synthetic NO, window 0x4200001,
    root 0x1a7, subw 0x0, time 1085946735, (271,769), root:(1555,796),
    mode NotifyUngrab, detail NotifyNonlinear, same_screen YES,
    focus YES, state 16

[B]KeyPress event, serial 35, synthetic NO, window 0x4200001,
    root 0x1a7, subw 0x0, time 1085949320, (271,769), root:(1555,796),
    state 0x10, keycode 64 (keysym 0xffe9, [COLOR="#ff0000"]Alt_L[/COLOR]), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x4200001,
    root 0x1a7, subw 0x0, time 1085949400, (271,769), root:(1555,796),
    state 0x18, keycode 64 (keysym 0xffe9, [COLOR="Red"]Alt_L[/COLOR]), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
[/B]
EnterNotify event, serial 35, synthetic NO, window 0x4200001,
    root 0x1a7, subw 0x0, time 1085949765, (271,769), root:(1555,796),
    mode NotifyGrab, detail NotifyNonlinear, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 35, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 35, synthetic NO, window 0x4200001,
    mode NotifyNormal, detail NotifyNonlinear

FocusIn event, serial 35, synthetic NO, window 0x4200001,
    mode NotifyNormal, detail NotifyNonlinear

KeymapNotify event, serial 35, synthetic NO, window 0x0,
    keys:  4294967207 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

LeaveNotify event, serial 35, synthetic NO, window 0x4200001,
    root 0x1a7, subw 0x0, time 1085949770, (271,769), root:(1555,796),
    mode NotifyUngrab, detail NotifyNonlinear, same_screen YES,
    focus YES, state 16

FocusOut event, serial 35, synthetic NO, window 0x4200001,
    mode NotifyNormal, detail NotifyNonlinear
^C

```

Then something like
```
xmodmap -e "add mod1 = Alt_L"
```

mod1 is xmodmap's name for the alt/meta modifier.  Control and shift modifiers have the names you'd expect.

Obviously this is an X-only solution, it won't work in a terminal (unless it's an xterm, then it might work).

---

### Post by MarcusAntonius on 2010-01-10
Thank you very much jpkotta for your post. I was not aware, that the xev and xmodmap commands exist, they are very helpful.

However, I found that also other people experience the same problem (see [http://ubuntuforums.org/showthread.php?t=1231551](http://ubuntuforums.org/showthread.php?t=1231551)). My problem seems to be a bug in xinput. It can be solved by installing the xorg-xi2 package on [https://launchpad.net/~thjaeger/+archive/xorg-xi2](https://launchpad.net/~thjaeger/+archive/xorg-xi2)

---

### Post by rnerwein on 2010-01-10
hi
xev isn't available in all unix/linux distros. what i did (i have german and us keybords on my box) is i
use the command: xmodmap -pke > mymodmap.txt. the file mymodmap.txt is plain asci. you can edit it to your behavior. just to change the keycodes then use: xmodmap mymodmap.txt. this is then valid for the session.
ciao

---


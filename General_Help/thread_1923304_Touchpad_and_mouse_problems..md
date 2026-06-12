---
title: "Touchpad and mouse problems."
date: 2012-02-10
forum: General Help
---

### Post by Cig on 2012-02-10
Hi.
Recently, i tried to switch to Ubuntu. However, i'm having one problem which makes work on my laptop (Acer Extensa 5235) impossible. In Ubuntu, it seems that my touchpad isn't working as it should. I can move my coursor, but can't click anywhere. When i try to click, Ubuntu just ignores it. With mouse attached, system works (some time, but then problem occures again), but when i try to use touchpad then my mouse stops working immediately. Furthermore, i tried to install Kubuntu. Great, mouse has no problems at all. But after using my touchpad, it has the same problem as Ubuntu. However, after logging off, I again, can click with mouse\touchpad on the login fields without problems. I'm new to Linux and i'm trying to switch, but I work a lot outdoors and this problem makes it impossible to switch.

If it's important, I have no problems with my touchpad\mouse in windows, so harware is fine. Tried on 32 and x64 Ubuntu and x64 Kubuntu.

Solution for Kubuntu is preferred (if different), as I find KDE more suitable for myself.

I tried to google, but no fix was found. So if you can give me the link where it's solved, Ill accept my stupidity and be gone:)

Thank you for your help and pardon my English. Hope you understood what I'm talking about here.

---

### Post by abePdIta on 2012-09-19
Hi everybody! Sorry for my bad English too!
I have the same problem with an Acer Extensa 5230E.
USB mouses work fine.
Once you touch the touchpad, you can click anywhere with no result.
I tried to investigate and it seems that moving the cursor using the touchpad causes a mouse_left_down (the start of a click) being fired, but mouse_left_up never comes. The result is that further mouse clicks have no effect.

Is there a way to identify the hardware e.g. the touchpad model no./id?
Somebody knows what parameter to change to try make this works as expected?
Thank you very much!

PS: maybe this thread should go under "hardware & laptops"

---

### Post by f8l_0e on 2012-09-19
By cannot click, is that with the touchpad button of tap to click or both?

---

### Post by abePdIta on 2012-09-19
OK, I find some infos; dmesg says:
psmouse serio2: synaptics: Touchpad model: 1, fw: 6.3, id: 0x12a0b1, caps: 0xa04711/0xa04000/0x0
Looking for id in Google gives no good results.
I hope someone can help me.
Thank you!

---

### Post by abePdIta on 2012-09-19
> **f8l_0e said:**
> By cannot click, is that with the touchpad button of tap to click or both?

Both! Not even the USB mouse.

---

### Post by f8l_0e on 2012-09-19
Try running ```
xev -root
``` to see if the button clicks are being picked up.

---

### Post by abePdIta on 2012-09-20
Thanks for your interest!
I ran xev -root. Here are the results.
```

ClientMessage event, serial 13, synthetic YES, window 0xab,
    message_type 0x149 (WM_PROTOCOLS), format 32

ClientMessage event, serial 13, synthetic YES, window 0xab,
    message_type 0x149 (WM_PROTOCOLS), format 32

ClientMessage event, serial 13, synthetic YES, window 0xab,
    message_type 0x149 (WM_PROTOCOLS), format 32

ClientMessage event, serial 13, synthetic YES, window 0xab,
    message_type 0x149 (WM_PROTOCOLS), format 32

[…]
```
These are the events that occur when the left mouse click does not work.
Thank you again!

---

### Post by abePdIta on 2012-09-20
I tried to run "xev" immediately after login.
I never touched the touchpad before I started "xev".
As soon as I pass the finger on the touchpad (I make the movement to move the cursor, not a "tap" to get a click), left click start (I can see this because the cursor starts a drag operation).
```

[…]

ClientMessage event, serial 13, synthetic YES, window 0xab,
    message_type 0x149 (WM_PROTOCOLS), format 32

ClientMessage event, serial 14, synthetic YES, window 0xab,
    message_type 0x149 (WM_PROTOCOLS), format 32

ClientMessage event, serial 14, synthetic YES, window 0xab,
    message_type 0x149 (WM_PROTOCOLS), format 32

ConfigureNotify event, serial 14, synthetic NO, window 0xab,
    event 0xab, window 0xc00104, (0,0), width 1280, height 800,
    border_width 0, above 0x0, override YES

PropertyNotify event, serial 14, synthetic NO, window 0xab,
    atom 0x14c (_NET_ACTIVE_WINDOW), time 10713408, state PropertyNewValue

ClientMessage event, serial 14, synthetic YES, window 0x3600006,
    message_type 0x1f1 (_COMPIZ_DECOR_PENDING), format 32

ClientMessage event, serial 16, synthetic YES, window 0x3600006,
    message_type 0x1f2 (_COMPIZ_DECOR_REQUEST), format 32

ClientMessage event, serial 17, synthetic YES, window 0xab,
    message_type 0x21a (_COMPIZ_DECOR_DELETE_PIXMAP), format 32

ClientMessage event, serial 18, synthetic YES, window 0xab,
    message_type 0x149 (WM_PROTOCOLS), format 32

[…]

ClientMessage event, serial 18, synthetic YES, window 0xab,
    message_type 0x149 (WM_PROTOCOLS), format 32

FocusIn event, serial 18, synthetic NO, window 0xab,
    mode NotifyGrab, detail NotifyInferior

KeymapNotify event, serial 18, synthetic NO, window 0x0,
    keys:  73  0   0   0   0   0   0   0   1   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 18, synthetic NO, window 0xab,
    mode NotifyUngrab, detail NotifyInferior

CreateNotify event, serial 18, synthetic NO, window 0xab,
    parent 0xab, window 0x18009a6, (0,0), width 170, height 33
border_width 0, override YES

ConfigureNotify event, serial 18, synthetic NO, window 0xab,
    event 0xab, window 0x18009a6, (1281,801), width 170, height 33,
    border_width 0, above 0x18002ee, override YES

ClientMessage event, serial 18, synthetic YES, window 0x18009a6,
    message_type 0x157 (_NET_WM_STATE), format 32

MapNotify event, serial 18, synthetic NO, window 0xab,
    event 0xab, window 0x18009a6, override YES

UnmapNotify event, serial 19, synthetic NO, window 0xab,
    event 0xab, window 0x18009a6, from_configure NO

UnmapNotify event, serial 19, synthetic YES, window 0xab,
    event 0xab, window 0x18009a6, from_configure NO

UnmapNotify event, serial 19, synthetic YES, window 0xab,
    event 0xab, window 0x18009a6, from_configure NO

FocusIn event, serial 19, synthetic NO, window 0xab,
    mode NotifyGrab, detail NotifyInferior

KeymapNotify event, serial 19, synthetic NO, window 0x0,
    keys:  4294967206 0   4294967168 0   0   0   0   0   1   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 19, synthetic NO, window 0xab,
    mode NotifyGrab, detail NotifyInferior

ConfigureNotify event, serial 19, synthetic NO, window 0xab,
    event 0xab, window 0xc00107, (-1380,-900), width 1280, height 800,
    border_width 0, above 0xc003db, override YES

ConfigureNotify event, serial 19, synthetic NO, window 0xab,
    event 0xab, window 0xc0010a, (0,24), width 65, height 776,
    border_width 0, above 0xc00107, override YES

ConfigureNotify event, serial 19, synthetic NO, window 0xab,
    event 0xab, window 0xc00110, (0,0), width 1280, height 24,
    border_width 0, above 0xc0010a, override YES

ConfigureNotify event, serial 19, synthetic NO, window 0xab,
    event 0xab, window 0xc00113, (-420,-300), width 320, height 200,
    border_width 0, above 0xc00110, override YES

ConfigureNotify event, serial 19, synthetic NO, window 0xab,
    event 0xab, window 0xc00116, (-420,-300), width 320, height 200,
    border_width 0, above 0xc00113, override YES

ConfigureNotify event, serial 19, synthetic NO, window 0xab,
    event 0xab, window 0xc003db, (-1180,-700), width 1080, height 600,
    border_width 0, above 0xc00116, override YES

PropertyNotify event, serial 19, synthetic NO, window 0xab,
    atom 0x1c2 (_NET_CLIENT_LIST_STACKING), time 10724591, state PropertyNewValue

PropertyNotify event, serial 19, synthetic NO, window 0xab,
    atom 0x1c2 (_NET_CLIENT_LIST_STACKING), time 10724592, state PropertyNewValue

PropertyNotify event, serial 19, synthetic NO, window 0xab,
    atom 0x1c2 (_NET_CLIENT_LIST_STACKING), time 10724592, state PropertyNewValue

PropertyNotify event, serial 19, synthetic NO, window 0xab,
    atom 0x1c2 (_NET_CLIENT_LIST_STACKING), time 10724593, state PropertyNewValue

PropertyNotify event, serial 19, synthetic NO, window 0xab,
    atom 0x1c2 (_NET_CLIENT_LIST_STACKING), time 10724593, state PropertyNewValue

PropertyNotify event, serial 19, synthetic NO, window 0xab,
    atom 0x1c2 (_NET_CLIENT_LIST_STACKING), time 10724594, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0xab,
    atom 0x14c (_NET_ACTIVE_WINDOW), time 10724667, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0xab,
    atom 0x14c (_NET_ACTIVE_WINDOW), time 10726357, state PropertyNewValue

ClientMessage event, serial 20, synthetic YES, window 0x3600006,
    message_type 0x1f1 (_COMPIZ_DECOR_PENDING), format 32

ClientMessage event, serial 20, synthetic YES, window 0x3600006,
    message_type 0x1f2 (_COMPIZ_DECOR_REQUEST), format 32

ClientMessage event, serial 20, synthetic YES, window 0xab,
    message_type 0x21a (_COMPIZ_DECOR_DELETE_PIXMAP), format 32

ClientMessage event, serial 20, synthetic YES, window 0xab,
    message_type 0x149 (WM_PROTOCOLS), format 32

[…]

ClientMessage event, serial 20, synthetic YES, window 0xab,
    message_type 0x149 (WM_PROTOCOLS), format 32
```
After this, any further click has no effect (dragging never ends, unless I press "esc").
From this point onwards, "xev" remains (almost) silent (see my prev. post).
I have to run "sudo modprobe-r psmouse" so that the "long click" to end.
Thank you very much for your help.

---

### Post by sandyd on 2012-09-20
Try this:
```

 sudo nano /etc/X11/xorg.conf

```
paste
```


Section "InputClass"
Identifier "ETPS/2 Elantech Touchpad"
MatchProduct "ETPS/2 Elantech Touchpad"
MatchDevicePath "/dev/input/event*"
Driver "synaptics"
Option "TapButton1" "1"
Option "TapButton2" "3"
Option "TapButton3" "2"
Option "VertTwoFingerScroll" "1"
Option "HorizTwoFingerScroll" "1"
Option "CoastingSpeed" "10"
Option "EdgeMotionMinZ" "30"
Option "EdgeMotionMaxZ" "40"
Option "EdgeMotionMinSpeed" "100"
Option "EdgeMotionMaxSpeed" "400"
Option "FingerLow" "9"
Option "FingerHigh" "12"
Option "EmulateMidButtonTime" "0"
Option "ClickPad" "True"
Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
EndSection

```
Press control+x to save, and restart

---

### Post by abePdIta on 2012-09-20
> **sandyd said:**
> Try this:
```

 sudo nano /etc/X11/xorg.conf

```
[…]
Press control+x to save, and restart
Hi sandyd! Thank you for your reply.
I edited xorg.conf as you told me, but I did not get results.
The behavior of the mouse has remained the same.

---

### Post by f8l_0e on 2012-09-20
In that case, I would remove the section you just added to xorg.conf to keep clutter out.  If it were my machine, the next thing I would try is ```
sudo apt-get purge remove xserver-xorg-input-synaptics
``` and see if the stock mouse driver doesn't get stuck.  You will lose tap to click and drag to scroll, but it that solves the problem, you might be able to use another driver.

---

### Post by abePdIta on 2012-09-21
Thanks for the suggestion.
I suppose the correct command is ```
sudo apt-get purge xserver-xorg-input-synaptics
```
In any case, xserver-xorg-input-synaptics removed. I see increased speed in cursor movements, but the problem is still here.

---

### Post by dishe on 2012-11-07
Any progress on this (he asks, knowing full well that this thread is 2 months old and if there was progress it would have been reported)?

It sounds a bit like what I'm describing here:
[http://ubuntuforums.org/showthread.php?t=2081855&highlight=mouse+stuck](http://ubuntuforums.org/showthread.php?t=2081855&highlight=mouse+stuck)

Looks like in my case, the mouse clicks ARE working, but the GUI isn't interpreting them to be on the right layer. For example, within an application, if a context window pops up (OK / Cancel), I can't click on it. I try, but the clicks are actually being registered on the application window BEHIND it. Particular windows seem to assume control of the mouse, making it difficult / impossible to click elsewhere in the GUI. 
I can click around in an app, but no where outside of it (settings, other app windows, etc). But closing the app that has assumed control of the mouse (alt-f4) and suddenly I can. This appears to happen in almost any application, Firefox, X-chat, documents, however on occasion it will work fine.

Are you sure this isn't what you are noticing?

---

### Post by Bewise_Hive on 2013-08-26
I only want to mention that the Acer Extensa Notebooks do have different Touchpads. I for instance own an Acer Extensa 5230e that has no Synaptics-Touchpad in it, but an ALPS-Touchpad.

Maybe this might cause some of the problems?

I only know that to find out which touchpad-producer has contributed the touchpad in your specific device you can put the following in a Terminal:

grep -B 5 mouse /proc/bus/input/devices

If - after that - some text like the following appears, your device has a Synaptics-Touchpad:
I: Bus=0011 Vendor=0002 Product=0007 Version=0000
N: Name="SynPS/2 Synaptics TouchPad"

But if some text appears like as this, then your device has an Alps-Touchpad:
I: Bus=0011 Vendor=0002 Product=0008 Version=6337
N: Name="AlpsPS/2 ALPS GlidePoint"

Maybe there are other producers of touchpads as well, but in case of some of the acer extensa notebooks you can find different touchpad models in notebooks with the same model-numbers.

---


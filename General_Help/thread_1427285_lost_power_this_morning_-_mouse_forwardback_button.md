---
title: "lost power this morning - mouse forward/back buttons stopped working"
date: 2010-03-11
forum: General Help
---

### Post by sibble on 2010-03-11
I didn't have to do anything to get this working from the start, default Ubuntu 9.10 installation they worked from the get-go.

My back/forward thumb buttons on my mouse are no longer working for anything, they DID work for Nautilus, Firefox, Chrome (basically everything.)

I tried using 'xev' to see what the button codes are so I can use xbindkeys to map them, but xev isn't even seeing them either.

This makes me think that there is probably some kind of default configuration somewhere else...

Help please!!

---

### Post by sibble on 2010-03-11
I booted from LiveCD and the mouse buttons work properly.

How can I copy over a configuration to my installed OS?  I have no idea where it's configured.

---

### Post by flippo on 2010-03-11
Hmmm, sounds odd.  How is your xorg detecting them? (/var/log/xorg.0.log should have this information). How does this differ from the live cd?

I don't know how 9.10 deals with new hardware devices (older versions use HAL with fdi policies, but I believe they took that out in 9.10), but Xorg should at least tell you the difference in configurations.

---

### Post by sibble on 2010-03-11
thank you for replying :)

I'm attaching:
LiveCD Xorg.0.log - [http://sibble.com/Xorg.0.log](http://sibble.com/Xorg.0.log) - file was too big to attach.
Xorg.0.txt - copied /var/log/Xorg.0.log from my installed OS
Xorg.1.txt - copied /var/log/Xorg.1.log from my installed OS, not sure why I have this, but it's from 4 days ago.

Also I just had something weird happen.  Upon my last reboot, when I get to GDM, that extra accessibility menu bar appeared on the top of my screen, and it's always appeared at the bottom.

---

### Post by sibble on 2010-03-11
Correction - xev sees that I'm hitting the 2 buttons, but it doesn't register them as "button 8/9" which it should and does on LiveCD

```
LeaveNotify event, serial 36, synthetic NO, window 0x5400001,
    root 0x13f, subw 0x0, time 1055076, (169,5), root:(172,1016),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

EnterNotify event, serial 36, synthetic NO, window 0x5400001,
    root 0x13f, subw 0x0, time 1055077, (169,5), root:(172,1016),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  63  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

LeaveNotify event, serial 36, synthetic NO, window 0x5400001,
    root 0x13f, subw 0x0, time 1056652, (169,5), root:(172,1016),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

EnterNotify event, serial 36, synthetic NO, window 0x5400001,
    root 0x13f, subw 0x0, time 1056653, (169,5), root:(172,1016),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  63  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
```

-Is what I got when I hit button 8 and 9 on my mouse.

---

### Post by flippo on 2010-03-11
Well, your xorg, and second report from xdev report that the buttons are being detected in the same way from a liveCD and on your normal boot.  I'm afraid I don't know what happens in 9.10 after that point, so I can't help beyond that.  Sorry.

---

### Post by sibble on 2010-03-11
thanks for trying regardless, much appreciated

---


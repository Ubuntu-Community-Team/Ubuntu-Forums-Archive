---
title: "mouse button no longer working"
date: 2010-05-19
forum: General Help
---

### Post by eeperson on 2010-05-19
I have a 'Microsoft Comfort Optical Mouse 3000'.  In addition to the regular left/right click and scroll wheel it has an extra button on the side.  In previous versions of Ubuntu I was able to remap this button to act as double-click using 'xbindkeys'.  However, in Lucid this no longer seems to work.  X seems to know about all of the buttons on the mouse since 'xinput' lists the device as having 13 buttons and labels button 8 as 'Button Side'.  However, 'xev' does not show a button event when I press the button.  Instead it shows:

```

LeaveNotify event, serial 31, synthetic NO, window 0x5c00001,
    root 0x10f, subw 0x0, time 223243870, (49,81), root:(1787,927),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

EnterNotify event, serial 31, synthetic NO, window 0x5c00001,
    root 0x10f, subw 0x0, time 223244020, (49,81), root:(1787,927),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  15  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```

Does anybody know how I can get this button to act as double click again?

---

### Post by eeperson on 2010-05-19
I realized that that there was already an instance of 'xbindkeys' running that was messing with the 'xev' output.  So the button is now being detected properly.  However, the configuration I had for 'xbindkeys' no longer works.  The following no longer works:

```

"/usr/bin/xte 'mouseup 9' 'mouseclick 1' 'mouseclick 1' &"
b:9

```

but this kind of works

```

"/usr/bin/xte 'mouseclick 1' 'mouseclick 1' &"
b:9 + Release

``` 

The new version produces slightly different results because it double clicks on mouse up instead of on mouse down.  If anybody knows how to get the first working let me know.

---


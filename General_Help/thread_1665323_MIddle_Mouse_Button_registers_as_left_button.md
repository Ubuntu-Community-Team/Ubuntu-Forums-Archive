---
title: "MIddle Mouse Button registers as left button"
date: 2011-01-12
forum: General Help
---

### Post by SpaceTeddy on 2011-01-12
Hi Everyone, 

i've installed Maverick yesterday, and since then my middle mouse button is not detected anymore. I am refering to the physical button on my laptop (HP 8530p).

When using xev to show the events from the button, this happens when i press the left button:
[I]ButtonPress event, serial 36, synthetic NO, window 0xb200001,
    root 0x110, subw 0x0, time 5309778, (-1,82), root:(1135,132),
    state 0x10, **button 1**, same_screen YES[/I]

This happens when i press the right button:
[I]ButtonPress event, serial 36, synthetic NO, window 0xb200001,
    root 0x110, subw 0x0, time 5343161, (-2,104), root:(1134,154),
    state 0x10, **button 3**, same_screen YES
[/I]
and this happens when i press the middle button
[I]ButtonPress event, serial 36, synthetic NO, window 0xb200001,
    root 0x110, subw 0x0, time 5375153, (-2,60), root:(1134,110),
    state 0x10, **button 1**, same_screen YES[/I]

However, if i use the emulated middle button (i.e. left and right mouse button at the same time) this happens:
ButtonPress event, serial 36, synthetic NO, window 0xb200001,
    root 0x110, subw 0x0, time 5434970, (-1,128), root:(1135,178),
    state 0x10, **button 2**, same_screen YES

So, as i can see that, the button from the mouse is mapped wrong, as the emulated button gives me the correct behavior for the middle mouse button, while the middle mouse button is mapped to Button 1 - which is the left mouse button.

And here is the touchpad type from /proc/bus/input/devices
```
I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input8
U: Uniq=
H: Handlers=mouse0 event8 
B: EV=b
B: KEY=420 670000 0 0 0 0
B: ABS=11000003
```

Does anyone have any idea on how i can fix this issue ? How to load a different driver for the touchpad or remap the button so that it works again ?
I would really appreciate the help - this is driving me nuts (i need that button for firefox tabs, fast copy and paste, etc...)

Thanks a lot.

---

### Post by SpaceTeddy on 2011-01-12
More stuff i found out.

When i unload the psmouse module, and reload it with the proto=imps options (as suggested somewhere else) the middle mouse button starts to behave correctly. However, in this case the scrolling on the side of the mouse pad is disabled (it only generates a cursor movement in xev instead of a button event)

something is really weird here.

As a summary:
**with *psmouse* loaded**
no middle mouse button but scrolling works

**with *psmouse proto=imps* loaded**
middle mouse button works but the scrolling is disabled

Anybody got any idea what the cause is (and how i can fix this) ?

---

### Post by SpaceTeddy on 2011-01-15
Ok, i'Ve solved the problem. It seems to be a reverse bug for the touchpad i have installed in the computer. It does not recognize it correctly, loading a wrong button code for the middle mouse button.

the problem is described in this thread:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/612591]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/612591")

where post #11 fixes the problem (for me):
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/612591/comments/11]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/612591/comments/11")

i've followed the instuctions, and even tho the 2.6.35-24 kernel is the current one, the patch for the 2.6.35-22 still works. If i remember correctly, i did not change any versions - i just followed the commands.

Finally, the middle mouse button works...

---


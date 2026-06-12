---
title: "The calculator makes my mouse unusable in 10.10"
date: 2010-10-12
forum: General Help
---

### Post by Meandlinux on 2010-10-12
When I press the calculator key on my keyboard and the calculator comes up, I can't use my mouse anymore. I can move it but I can't click on anything. Is there a fix for this?

---

### Post by gaellafond on 2010-10-20
I have exactly the same problem. It also occur in other circumstances.

I will post more details if I manage to reproduce the bug without the Keyboard calc button, to be able to reproduce it without that type of keyboard.

---

### Post by gaellafond on 2010-10-20
The problem occur with all the media button from my external keyboard (play/pause, volume up/down, mute and calculator). When I use the buttons from my native Laptop Keyboard, everything is fine. When I use the one from my external Keyboard, the event occur as expected + it screw up the mouse.

Here is the output of xev for Volume +. I had to make a ScreenShot and retype everything because I could not copy it without a mouse. I hope there is no typo.

Laptop native keyboard (the one that works fine):
[FONT=Courier New]FocusIn event, serial 36, synthetic NO, window 0x1e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 36, synthetic NO, window 0x0,[/FONT] [FONT=Courier New]
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
[/FONT]
External keyboard (the one that screw up the mouse) (note: the FocusOut appear before the FocusIn):
[FONT=Courier New]FocusOut event, serial 37, synthetic NO, window 0x1e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 37, synthetic NO, window 0x1e00001,[/FONT] [FONT=Courier New]
    mode NotifyUngrab, detail NotifyNonlinear

[/FONT]Note: It seems that the mouse left button 'down' event is fired but not  the 'up' event. Same as if I click the left mouse button but never  release it. If the mouse is over the Desktop before I click a Keyboard  media button, than I move the mouse, it draw a rectangle to select my  Desktop icons. The ESC key only cancel the selection rectangle, not the 'down' event. The only solution I found to get the mouse back without rebooting is to restart GDM from a text terminal:
1. press Ctrl+Alt+F1
2. Log-in
3. type the command: 'sudo service gdm restart'

---

### Post by tnat on 2010-11-03
keyboard plugoff, plugin and mouse-left-click also gets it workin' again!

---

### Post by Meandlinux on 2010-12-06
I have not this problem in Linux Mint 10.

---


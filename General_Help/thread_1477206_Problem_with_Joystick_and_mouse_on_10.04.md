---
title: "Problem with Joystick and mouse on 10.04"
date: 2010-05-08
forum: General Help
---

### Post by janagn on 2010-05-08
Hello all,

not sure if this is the correct place to ask/raise this issue so forgive me if I am doing something wrong, besides it is my first post :) So right after I installed 10.04 there seems to be some short of mouse/joystick mess. What I mean is that 2 types of joysticks (Saitek x52 and CH Products Yoke) seems to control the mouse as well! So when I pitch/roll the joysticks the mouse cursor also moves. When I move the middle lever of the CH products yoke, the mouse also moves horizontally. Also it is almost impossible to work with the scroll bars of windows as joysticks interacts with  them via the cursor and issues botton clikcs scrolling the bars to the end!!

This looks to be a new issue on 10.04 as 9.10 had no such issue.

Kind Regards
Yiannis

---

### Post by janagn on 2010-05-13
I think I fixed the problem. Not sure if it is advisable but by removing package xseerver-xorg-input-joystick it fixed the problem. Now I have a Saitek X52Pro, the CH Yoke and the pedals all working great.

If anybody has any better idea or a justification for this, would be great to find out.

Regards
Yiannis

---

### Post by Newk_77 on 2010-07-04
thank you allot!

there are more suffering from that issue:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/418470](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/418470)

cheers!

---

### Post by Kryzzalid on 2011-08-18
Worked for me! Thanks:)

---


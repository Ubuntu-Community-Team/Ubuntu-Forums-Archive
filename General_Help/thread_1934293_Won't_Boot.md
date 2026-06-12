---
title: "Won't Boot"
date: 2012-03-01
forum: General Help
---

### Post by Foxheadz on 2012-03-01
Im running a dual boot with ubuntu and windows 7, windows 7 is on my primary hard drive along with grub and ubuntu is on the other. I just installed it. Now for some reason I can't boot into ubuntu, whenever I select it in grub the screen just goes purple and my caps lock and scroll lock lights start flickering... If I run it in verbose mode i just get a black flickering screen with my caps lock and scroll lock also just flashing... Anyone know what's wrong?

---

### Post by Los Frijoles on 2012-03-02
Caps lock and scroll flashing means a kernel panic. I have had it happen to me a few times; re-installing Ubuntu worked for me (of course, my setup was reverse: Ubuntu was the primary and windows was sitting around unused on the other partition).

Kernel panics can be caused by hardware failure or by some sort of software corruption. When I had it happen to me the computer hadn't been turned on in 2 years or so.

Does it even boot into recovery mode (a root shell)?

EDIT: Didn't notice the part about black flickering screen. I have that happen when my graphics crash. What are your system specs?

---

### Post by Foxheadz on 2012-03-02
Nope, not even in recovery mode. I'm guessing something just went wrong with the install so ill redo that and see if it fixes it. Thanks!

---


---
title: "Question on ATI Video."
date: 2012-05-09
forum: General Help
---

### Post by livewire94 on 2012-05-09
I installed the proprietary drivers after a clean install of Ubuntu x64 12.04.  I have an ATI Radeon HD 4670 video card.

How do I check the fan speed and clock speeds under Ubuntu?

---

### Post by 3Miro on 2012-05-09
Search the Unity menu for Catalyst. It is the AMD control center, which should give you all information about your video card.

---

### Post by livewire94 on 2012-05-09
I looked there.  It doesn't display the current clock speeds or fan speeds.

---

### Post by livewire94 on 2012-05-09
After searching google some more I found this  (Sudo DISPLAY=:0 aticonfig --pplib-cmd "get fanspeed 0")  and it displays this  (Fan speed query: 
Query Index: 0, Speed in percent
Result: Fan Speed: 3%


Guess a percentage is good enough.  I just wanted to see what it was at.  Still can't find current clock speeds.  I know in Windows they are automatic.

---

### Post by 3Miro on 2012-05-09
I have been using mostly Nvidia and there I can get both the clock and fan speed in the graphical utility. If you can get the fan speed in the terminal, there should be a command for the clock too.

In general, fan and clock speed are both automatic and you shouldn't mess with them (unless you know what you are doing).

---


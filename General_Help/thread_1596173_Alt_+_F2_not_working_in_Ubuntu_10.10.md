---
title: "Alt + F2 not working in Ubuntu 10.10"
date: 2010-10-14
forum: General Help
---

### Post by tareq.mhd on 2010-10-14
I am using Ubuntu 10.10 64-bit and have some problems. Alt + F2 does not working. Any idea about the problem ? I am thinking back to the Lucid now :(

---

### Post by wilee-nilee on 2010-10-14
Works on my version, you might check your keyboard setup.

---

### Post by VMC on 2010-10-14
> **tareq.mhd said:**
> I am using Ubuntu 10.10 64-bit and have some problems. Alt + F2 does not working. Any idea about the problem ? I am thinking back to the Lucid now :(

Open Keyboard (System > Preferences > Keyboard) and make sure it's enabled:

---

### Post by dabomb1022 on 2010-10-14
Same here! I'm on 32 not 64 though. I can't seem to update to 10.10 from the 10.10 RC!

---

### Post by tareq.mhd on 2010-10-14
Shortcut is enabled, but no change. I am gonna downgrade to Lucid 10.04.1 LTS 64-bit soon.

---

### Post by snowguy on 2010-10-16
Doesn't work for me either. In fact my system becomes unstable when I push that key combination. I am using a microsoft wireless keyboard connected by USB. Maybe that has something to do with it.  I am also using the 64 bit version of 10.10.

---

### Post by WorMzy on 2010-10-16
What window manager are you using? If you're using Compiz, make sure you have the gnome-compatibility plugin enabled.

To Ubuntu, a keyboard is a keyboard is a keyboard. It doesn't care if it's made by Microsoft, or if it's connected by USB. The keyboard is not the problem.

---

### Post by falcon_1 on 2010-10-18
Doesn't work here either, 64bit, assigning it to atl+f3 doesn't help.

---

### Post by snowguy on 2010-10-18
I"m using Gnome and I think this happened right after a fresh install  before I changed any settings. I think I will try to reinstall the whole thing 10.10 32 bit.

---

### Post by thekaleb on 2010-10-19
I am using the 10.10 netbook edition, and I am getting the same problem. alt+f1 also does not work. For me, I believe that it may have something to do with the new unity interface.

---

### Post by snowguy on 2010-10-20
SOLVED PROBLEM FOR ME. 

Switched to a standard keyboard.


Here's some more information.
* When I first posted on this problem I had ubuntu 10.10 64 bit. I had a microsoft wireless keyboard 5000 that came with a mouse.I had all updates installed. When I clicked Alt F2 the window would become selected and as I moved the mouse it would move the window around the screen. Hitting escape unselected that particular window. At that point the mouse would stop working all together. And I would need to use the keyboard to restart the computer. Upon restart it woudl work properly.
* I reinstalled 10.10 64 to see if there was perhaps something I installed that caused this problem. However I confirmed the exact same behavior with a fresh install.
* I installed 10.10 32 bit. Observed the same problem
* At that point I tried taking out the USB wireless keyboard and mouse and instead used a standard keyboard and mouse that both plug into the old type keyboard mouse connectors (not sure what they are called--the little cirlces--not USB).
At that point Alt-F2 worked just fine.

Hoping this information helps someone else.

---

### Post by helpdeskicra on 2010-10-22
After I had upgraded from 10.04 x64 to 10.10 x64 and Alt+F2 had stopped working.
Neither did the print screen button worked, did not check the other shortcuts. But as advised above, I enabled Gnome compatibility under Compiz and all is well now.
thanks for the tip!

---


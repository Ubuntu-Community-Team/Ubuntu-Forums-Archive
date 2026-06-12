---
title: "Weird temporary hangs.  Maybe caused by fglrx"
date: 2009-08-17
forum: General Help
---

### Post by lavinog on 2009-08-17
Lately I have been experiencing some weird behavior.
For the past month my computer will hang until I force an application to close.

I am running 9.04 64bit with fglrx 9-7 and flash 10.0 r22 (64bit alpha - Just realized there is a newer version)

I almost always have at least one terminal window open, and firefox with 3-5 tabs.

I can switch windows sometimes when the hang occurs, but after switching too many times, they will stop updating.
I have been running htop lately, and when the hang occurs, htop will show one core as nan% while the other shows about 5-30%
If I right click on a task on the taskbar and select close, then force quit, everything goes back to normal.

I suspect the problem is due to fglrx or flash, and the problem isn't due to ubuntu. I am thinking fglrx is the most likely cause due to the cpu error and other random black boxes that show up.

Edit: Just found out the new fglrx driver (9-8) was released today, going to give it a try

I was curious if anyone else has experienced this?

---

### Post by R.Bucky on 2009-10-06
Yes, I have noticed "nan%" on one of my processors using htop. it shows for only a second then shows 0% or whatever. No cpu spiking...

---


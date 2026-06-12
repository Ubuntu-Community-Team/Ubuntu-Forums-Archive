---
title: "Tv"
date: 2010-12-14
forum: General Help
---

### Post by Unbreakable1 on 2010-12-14
I have almost everything congigured on my new Ubuntu desktop, now i just need to get the TV working, works fine in Vista. 

I have a couple of programs installed, neither detect the TV Tuner, guessing i either need a driver or it just wont work at all.

After a bit of research i found this to be my TV Tuner - 
AVerMedia H789 PCI-E Hybrid DVB-T

Any ideas?

---

### Post by dandnsmith on 2010-12-14
Have you seen [this tv card guide](http://www.wikihow.com/Make-a-Tv-Tuner-Card-Work-on-Ubuntu-Hardy-Heron)?

It might have some tips of use to you.

---

### Post by fragos on 2010-12-14
Some TV viewers only work with particular drivers. TVtime works great with BTTV but not at all with IVTV. My WinTV card uses BTTV and drivers for it are automatically loaded -- I only needed to install TVtime which basically configures itself. On the command lione run "lsmod |grep tv" and you should see if any TV drivers were loaded. At least it does for me.

---

### Post by Unbreakable1 on 2010-12-15
I installed TV Time, and it just flashes on my screen and goes away, i checked that command line and one driver came up, so i am guessing there is one installed and working.

Not sure what to do from here, but i am going to keep trying.

---

### Post by fragos on 2010-12-15
What was the output of "lsmod |grep tv"? Perhaps TVtime isn't compatible with that driver. [http://tvtime.sourceforge.net/cards.html](http://tvtime.sourceforge.net/cards.html) offers help for each TV chipset.

---


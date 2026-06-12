---
title: "Need help installing nvidia drivers"
date: 2010-11-01
forum: General Help
---

### Post by extremejosh on 2010-11-01
Ok here is my problem and I have looked for quite some time for a solution im a new Linux user just installed ubuntu 10.10 and everything looks awesome, great. Ok so i go to install the the proprietary drivers for 3d and all but on reboot it goes to a terminal interface no GUI at all so i've tried different methods of install the drivers and still face the problem does anyone have a solution for me? the driver version is nvidia 260.19.12
im graphics card is a geforce 7 series i cant exactly remember the number

---

### Post by extremejosh on 2010-11-07
Just thought id post the solution for this problem i found a while ago so i can mark this thread as solved for me ( and this worked both on ubuntu 10.04 and 10.10) i enter the grub on startup and hit "e"  thin after quiet splash i typed vmalloc=192M thin hit ctrl+x to boot up i used 256M at first but seems to run smoother with 192M hope this helps anyone else with this problem

---

### Post by P4man on 2010-11-07
Thats interesting. Can you tell us a bit more about your system (im guessing you are pretty low on ram?) and how you discovered this? Could you also test replacing that setting with nomodeset and see if that also helps or not?

---

### Post by extremejosh on 2010-11-07
> **P4man said:**
> Thats interesting. Can you tell us a bit more about your system (im guessing you are pretty low on ram?) and how you discovered this? Could you also test replacing that setting with nomodeset and see if that also helps or not?

i tried using nomodeset instead and no that didn't help i have 2gigs of ddr2 ram and a geforce 7350 le graphics i think and i came up with this fix out of curiosity i was going on almost 2 weeks with still no fix to my driver problems when i came across i forum where someone was posting problems about there driver problems although the error they wore getting was totally different from what i was getting but i decided to try it anyways and it worked

EDIT: i do have a problem though is there a way to make this permanent so i don't have to keep going into the grub at every start up

also and i was going to make another thread for this problem but on all my 3d games i cant play them my monitor says input out of range change settings to 1366x768-60Hz i have been searching every where for a fix to this but nothing works

---

### Post by P4man on 2010-11-07
To make the setting permanent, check my signature, last section. it doesnt mention your kernel option (yet :) ) but you will get the idea.
For the resolution issue I suggest you do start a new thread.

---

### Post by extremejosh on 2010-11-07
> **P4man said:**
> To make the setting permanent, check my signature, last section. it doesnt mention your kernel option (yet :) ) but you will get the idea.
For the resolution issue I suggest you do start a new thread.

alright and thanks for the help

---


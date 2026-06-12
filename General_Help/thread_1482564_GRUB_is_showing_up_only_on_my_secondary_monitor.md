---
title: "GRUB is showing up only on my secondary monitor"
date: 2010-05-13
forum: General Help
---

### Post by hypercube on 2010-05-13
I have a laptop setup to dual boot with Ubuntu and Vista.  Usually I use an external monitor setup when I use vista but I have not gotten around to configuring this for Ubuntu.  

Here is the problem, I had the monitor attached to the laptop during startup. Usually what happens is GRUB will load simultaneously on both the primary monitor on the laptop and also on the external monitor.  I was away from the computer and the computer loaded Ubuntu.  I decided to restart and then an error occured during shutdown and it froze so I did a manual shutdown.

Now when the computer starts nothing at all will show up on the primary monitor except I know power is running to it.  If I plug in the external monitor GRUB will appear but neither ubuntu or vista will load properly (I can however load ubuntu in recovery mode).

Any suggestions on how to make my primary montor work again?

---

### Post by sir_nasty on 2010-05-13
you could go into the bios reset it to defaults then save and exit, see if that changes anything.

---

### Post by hypercube on 2010-05-13
Did not work

---

### Post by almufadado on 2010-05-13
If your laptop has a button to acess other functions, like a brightness you should have a little monitor or a label "crt" if yes
Use the fn + crt to choose the primary monitor.

---

### Post by hypercube on 2010-05-13
Thanks, but this also did not do anything.  

Here are some more specifics when booting Ubuntu.  When it gets to the following:

**[COLOR=Black]Setting Advaned Power Management level to 0xfe (254)[/COLOR] [OK]**

The external screen blinks 3 times and then stays here.

---

### Post by sir_nasty on 2010-05-13
lets try something oldschoolish.... unplug the laptop from power, remove the battery, hold the power button down for about 15 seconds and then re-assemble and try to boot... Also, I can you get into the safe graphics mode or whatever it's called?

---

### Post by hypercube on 2010-05-13
Thanks, but this also did not work...blast!

---

### Post by sir_nasty on 2010-05-13
I know there is some way to do a safe mode of some sort in ubuntu but I'm not sure.... if you get the grub menu to show it may have a fallback mode

---

### Post by hypercube on 2010-05-13
I can get into the recovery mode no problem, but I am not sure what you mean.

---

### Post by sir_nasty on 2010-05-13
If you get into recovery mode then you can reconfigure xorg.conf using the display tools possibly....

---

### Post by hypercube on 2010-05-13
I actually did try this before, it was unsuccessful.

---

### Post by sir_nasty on 2010-05-13
this one is semi risky in my opinion.... what if you set the bios to disable the external monitor and disconnect it? or have you tried that?

If you rename xorg.conf while in recovery mode and reboot will it re-create it and allow you to boot into normal mode?  What about disabling all the power management stuff? (I'm just throwing out ideas at this point.... grasping at straws but trying to help none the less.... I'll check in later, gotta head home from work for now)

---

### Post by hypercube on 2010-05-13
Hmm, the first option sounds interesting, where would this option be in the bios?

Thanks for the ideas and help

---

### Post by sir_nasty on 2010-05-14
I'm not certain without knowing bios versions etc... even then it'd be hard to tell without looking at it.  It should be something titled video or advanced/Video.  Have you tried renaming the xorg.conf file to see if it will boot a default?

---


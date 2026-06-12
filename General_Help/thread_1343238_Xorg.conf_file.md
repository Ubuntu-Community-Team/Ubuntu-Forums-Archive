---
title: "Xorg.conf file??"
date: 2009-12-01
forum: General Help
---

### Post by johnhdsi on 2009-12-01
I installed 9.10 as a dual boot on my machine and I have run into an error with the graphics. I have Nvidia 6150 LE integrated graphics on the machine and when I boot into Ubuntu my screen gets "out of range" so the screen shifts and I can't see most of the desktop. When I go to System>Preferences>Display I get the following 

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

Upon saying "yes" I get he Nvidia control panel (Nvidia X Server settings)

From here I am able to set my desktop to 1024x768 using the X server display configuration. But when I try to save the settings I get the following,

"Failed to Parse exsisting X config file '/etc/X11/Xorg.conf"

Then if I reboot I get the same problem. I am using the Nvidia Version 185 driver which is the recommended one from Ubuntu. I'm not sure why I can't save my configuration, I have tried numerous display settings and each time it is the same thing.I am able to get desktop effects set to "normal" and that stays put even after the reboot. Any ideas on what I am doing wrong here?  

John

---

### Post by fooman on 2009-12-01
to save the settings to the xorg file...you must be root.

open a terminal and type or copy/paste the following:

```
gksudo nvidia-settings
```

set the correct resolution,  *then* save to xorg.conf.

hope that helps.

---

### Post by johnhdsi on 2009-12-01
Ok I did that and here's what I got


VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".


I see in the nvidia settings where it says Model: I have NON 8221A (CRT-0 on GPU-0)

---

### Post by ranch hand on 2009-12-01
The /etc/X11/xorg.conf file does not exist, by default, in 9.10.

If you have installed your driver through System>Administration>Hardware Drivers, it should be generated for you.  If not then you will have to get a copy from someone with your driver.

I can't help there as I have an ATI card.

---

### Post by bodhi.zazen on 2009-12-01
> **johnhdsi said:**
> Ok I did that and here's what I got


VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".


I see in the nvidia settings where it says Model: I have NON 8221A (CRT-0 on GPU-0)

When saving your configuration, do not merge it with the existing file. By default I believe it attempts to merge and so un-select the merge option.

---

### Post by johnhdsi on 2009-12-01
Ok, weird but apparently it worked lol...instead of selecting "Yes" when prompted to use the graphics vendor tool I selected "No" and it brought up the basic Display settings not the Nvidia control panel, now when I change my display rez it stays where I set it at. Not sure if this is a Nvidia bug or just something with the driver tool. I looked for an option to merge the Xorg file but I didn't see any options for merge it just pops up the error dialogue when I hit save. Guess it's no longer a problem lol.  Thanks for all the help guys!! I really appreciate it!!

John

---


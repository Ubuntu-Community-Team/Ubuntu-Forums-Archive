---
title: "Newbie Help - Old Intel Graphics Driver"
date: 2010-10-11
forum: General Help
---

### Post by Quarkrad on 2010-10-11
I'm getting a little confused – installing 10.04 on an old Acer Travelmate 292 laptop (friends laptop).  The only way to install – and then run – is to run in low graphics mode.  Having installed I have amended grub so that the term i915.modeset=1 comes after quiet splash.  So far so good – laptop running.   Eventually my friend would like to try video (Skype) on this beast but I fear low graphics mode could be a problem.  Ubuntu documentation states things like **If you are running ubuntu v7.10 and possibly 7.04, use the "intel" driver instead. It is more up to date, has similar configuration settings, and, most importantly, you do not need the i915 tool anymore. This means your fancy monitor with a strange resolution will work out of the box** but I do not have a card – the graphics is on the motherboard.  I do not think I have a driver for my intel 82852/855 graphics controller because it will installs/runs with a blank screen unless low graphics mode is enabled.
I'm pursuing this because other docs speak about better graphics with the Intel driver but I'm lost how to get/install it.  Other pages tell me what to add to my xorg.conf file - e.g.

[B]Configuring xorg.conf's "Device" section
You first of all have to find the device section already related to your graphics card. It can have any identifier, or might even not exist if you are just installing your xserver. You can usually find it right after your mouse entry. 
It should look like this: 
Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection[/B]

but I do not have a xorg.conf file!  As a newbie I'm getting very confused as to what drivers are native in 10.04, how to get at them and what are not.   I think I have to get and install one of these drivers but I need help.

---

### Post by Rasa1111 on 2010-10-11
10.04 gave many people these issues. 

To be honest.. Since 10.10 is now out, 
and does not have these issues~

 I would suggest making an attempt to install 10.10 instead of 10.04. 

 You may find your issues vanish, and you may not have to mess with extra drivers at all. 

 10.04 gave me (and many others) many problems with graphics/card issues.

 But I have not seen one in 10.10.

---

### Post by Quarkrad on 2010-10-12
You were right - 10.10 rocks :) Many thanks.

---

### Post by Quarkrad on 2010-10-14
Almost there - after a few days I'm finding that now and again when I close down a window a small part (the size is random) remains on the desktop/screen.  Sometimes with the graphics of the previous window, sometimes it looks like an indent within the Desktop background.  What happens is that this small window remains on top of the screen despite opening further windows so part of your new window is masked.

---


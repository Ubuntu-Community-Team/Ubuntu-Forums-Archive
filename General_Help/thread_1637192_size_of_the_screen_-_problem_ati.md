---
title: "size of the screen - problem ati"
date: 2010-12-04
forum: General Help
---

### Post by zerogad94 on 2010-12-04
[CENTER][SIZE=4]The problem of length and width of the screen Ubuntu  --[/SIZE][SIZE=4][COLOR=#000000]I can not work for 1280 * 960 in size of the screen[/COLOR][/SIZE][SIZE=4]
I cannot terracing graphics card ati 4350


im ubuntu 10.10
[/SIZE][/CENTER]

---

### Post by Matt West on 2010-12-04
There are a number of things that could be causing this problem. Can you please give us a little more information.

What graphics card are you using?
How do you connect to your monitor? (VGA,DVI,HDMI)

---

### Post by zerogad94 on 2010-12-04
i used ati 4350 hd

VGA


sorry i not good English

---

### Post by dandnsmith on 2010-12-04
If it's anything like my ATI Radeon cards (9200 is one of them), then the VGA connection will only get about three quarters of the display.
To utilise the full display you would need to connect via HDMI or DVI.

---

### Post by zerogad94 on 2010-12-04
I do not understand why now I can not  change  resolution?? 1280*960 

It works with Windows  7 strain without any problems, nor the slightest problem



"soory im not speak english good"

---

### Post by dandnsmith on 2010-12-05
This could be a problem - I think we need more information to get further:

1. Is the display used to it's full width?
2. Is it used to it's full length?
3. What style of screen is it (4x3, 16x9 ...)?
4. what sort of cable/connectors are you using?
5. what video driver is in use? (the command *lsmod* in a terminal window will give a list which includes the module - it might be *vesa*, but you could post the output if in doubt.
6. have you attempted to hand-configure the display usage by creating a file like xorg.conf?

NB I believe there are help resources in other languages, which might be better for you.

---

### Post by zerogad94 on 2010-12-05
[CENTER][SIZE=4]1- Windows Server in the largest length and width is 1280 * 960 screen, which fit well 

Ubuntu did not find the 1280 * 960 

my screen supports 1280 * 960 does not support higher

Ati 4350 card did not I Tariff I do not know how tariff

And support for other languages I can not advise me not to take advantage of them see


[http://ubuntuforums.org/showthread.php?p=10195999#post10195999](http://ubuntuforums.org/showthread.php?p=10195999#post10195999)



[COLOR=#000000]I apologize for the bad language[/COLOR]
[COLOR=#000000][/COLOR]
[COLOR=#000000]im used translate.google[/COLOR][/SIZE]
[COLOR=#000000][/COLOR][/CENTER]

---

### Post by Mark Phelps on 2010-12-05
> **zerogad94 said:**
> It works with Windows  7 strain without any problems, nor the slightest problem

Sorry ... but the two OSs (Win7 and Linux) use TOTALLY different video drivers.  What works in one has absolutely nothing to do with what works in the other.

---

### Post by zerogad94 on 2010-12-05
I want to make my screen 1280 * 960


i need setup driver ati 4350

---

### Post by Matt West on 2010-12-06
You can try:
System > Preferences > Additional Drivers

There may be a proprietary driver for your ATI card here.

Activate the driver > Reboot

Let us know how you get on

---

### Post by dandnsmith on 2010-12-06
Latest advice I've come across says that the latest ati drivers don't work for the last couple of releases of Ubuntu and other distros on the same kernel, and that anyone having a proproblem with them should remove them and use the default driver modules (I think this might turn out to be vesa.

---

### Post by zerogad94 on 2010-12-06
[CENTER][SIZE=5]Terracing tried the normal way of no use

As Brstr It brings the screen black and yellow bulb[/SIZE][/CENTER]

---

### Post by NeT_DeMoN on 2010-12-06
I don't know about 10.10 but I know 10.04 you could use this terminal command to do it.
> xrandr --addmode default 1280x960_60.00

I hope this helps.

---

### Post by zerogad94 on 2010-12-06
[CENTER][SIZE=3]zerogad94@zerogad:~$ xrandr --addmode default 1280x960_60.00 
xrandr: Failed to get size of gamma for output default
xrandr: cannot find mode "1280x960_60.00"
:-(
[/SIZE][/CENTER]

---

### Post by NeT_DeMoN on 2010-12-06
Try observing this link. 
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

---

### Post by zerogad94 on 2010-12-06
> **NeT_DeMoN said:**
> Try observing this link. 
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)
wait

---

### Post by zerogad94 on 2010-12-06
[SIZE=4][COLOR=#000000]Did not change anything

[/COLOR][/SIZE]The *X Server does not* support the XRandR[SIZE=4]
[/SIZE]

---

### Post by zerogad94 on 2010-12-07
helllllp meeeeeeee :o

---

### Post by zerogad94 on 2010-12-08
up up up up help me

---


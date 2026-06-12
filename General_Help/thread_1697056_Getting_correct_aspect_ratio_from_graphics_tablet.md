---
title: "Getting correct aspect ratio from graphics tablet"
date: 2011-02-28
forum: General Help
---

### Post by halfbeing on 2011-02-28
Hello,

I've just got hold of a Trust 200 graphics tablet which has an aspect ratio of 4:3. My laptop screen is wider than this and when I have an external monitor plugged in my desktop is wider still.

Is there a way to get the tablet to work with the correct aspect ratio? For instance is it possible in x.org to restrict the coordinates it can work within to those of my external 4:3 monitor?

Many thanks

---

### Post by Favux on 2011-02-28
Hi halfbeing,

Sure.  It partly depends on what driver the tablet is using.  Do you know?  Usually it consists of setting your BottomX & Y or the equivalent.  You do lose some of the working surface of your tablet doing that though.

You can identify the tablet (and what driver it is likely using) by entering into a terminal:
```
xinput list
```
Identify the "device name" for your stylus/tablet and enter in a terminal:
```
xinput list-props "device name"
```
That should show the driver and what coordinate settings are available.

---

### Post by halfbeing on 2011-03-01
Thanks for the reply.

What I get is the following:

robert@ermintrude:~$ xinput list-props Aiptek
Device 'Aiptek':
        Device Enabled (155):   1                                                             
        Coordinate Transformation Matrix (157): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (275):     0
        Device Accel Constant Deceleration (276):       1.000000
        Device Accel Adaptive Deceleration (277):       1.000000
        Device Accel Velocity Scaling (278):    10.000000
        Evdev Reopen Attempts (273):    10
        Evdev Axis Inversion (279):     0, 0
        Evdev Axis Calibration (280):   <no items>
        Evdev Axes Swap (281):  0
        Axis Labels (282):      "Abs X" (683), "Abs Y" (684), "Abs Wheel" (685), "Abs Pressure" (686), "Abs Tilt X" (687), "Abs Tilt Y" (688), "None" (0)
        Button Labels (283):    "Button Left" (158), "Button Middle" (159), "Button Right" (160), "Button Wheel Up" (161), "Button Wheel Down" (162), "Button Horiz Wheel Left" (163), "Button Horiz Wheel Right" (164)
        Evdev Middle Button Emulation (284):    2
        Evdev Middle Button Timeout (285):      50
        Evdev Wheel Emulation (286):    0
        Evdev Wheel Emulation Axes (287):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (288):    10
        Evdev Wheel Emulation Timeout (289):    200
        Evdev Wheel Emulation Button (290):     4
        Evdev Drag Lock Buttons (291):  0


It's not obvious to me which if any of these will do the job.

---

### Post by Favux on 2011-03-01
I agree, but the first thing I noticed is that your Aiptek tablet is not using the Aiptek driver, it's being picked up by the evdev driver.  Evdev is the "fail-safe" driver that tries to pick up devices not claimed by any other driver.

So hopefully it's just as simple as you using the Software Center or Synaptic Package Manager to install the Aiptek driver package:  xserver-xorg-input-aiptek  And rebooting.

---

### Post by halfbeing on 2011-03-03
I've installed the aiptek driver, but xinput still gives me the same information. I'm pretty sure that means I have to create a configuration file somewhere in /etc . Unfortunately I can't remember how to do it :(

---

### Post by Favux on 2011-03-03
Hi halfbeing,

Correct, you need an aiptek.conf file.  But the location is different depending on whether you're in Lucid or Maverick.  Which release are you using?

Usually the package installs the .conf file for its driver.  I wonder if one is included in the package and it just doesn't install?

The basic aiptek.conf should look something like this:
```
Section "InputClass"
        Identifier "Aiptek class"
        MatchProduct "Aiptek|AIPTEK|aiptek"
        MatchDevicePath "/dev/input/event*"
        Driver "aiptek"
EndSection

```
We may need to add some more entries depending on how much the Aiptek driver auto-configures.

---

### Post by halfbeing on 2011-03-04
I really appreciate you taking this trouble, Favux.

I'm using Maverick.

I've looked through the installed files using Synaptic and aiptek.conf is not listed. Should I report this as a bug?

---

### Post by Favux on 2011-03-04
For Maverick the aiptek.conf should go in /usr/share/X11/xorg.conf.d.  Let's follow the wizardpen.conf and call it 70-aiptek.conf.  So you can use:
```
gksudo gedit /usr/share/X11/xorg.conf.d/70-aiptek.conf
```
to create the file and add the above content into it.  Reboot and see where you are.  It's possible, not likely, that that will break X.  In which case just remove or rename the new file from the command line in Recovery boot.

Yes I think that should be reported as a bug.  Any driver in Maverick should come packaged with a .conf file.

But it wouldn't be in a separate package.  So make sure it isn't in /usr/share/X11/xorg.conf.d or maybe /etc/X11/xorg.conf.d before doing any of the above.

---

### Post by halfbeing on 2011-03-07
It didn't work and it broke middle button scrolling unfortunately :(

---

### Post by Favux on 2011-03-08
Which middle button scrolling?

OK, add to the aiptek.conf the following lines:
```

Section "InputClass"
        Identifier "Aiptek class"
        MatchProduct "Aiptek|AIPTEK|aiptek"
        MatchDevicePath "/dev/input/event*"
        Driver "aiptek"
        Option "USB" "on"
        Option "Type" "stylus"
        Option "Mode" "absolute"
        Option "zMin" "0"
        Option "zMax" "511"
EndSection
```
Do you know how many pressure levels your tablet supports?  If it is 1024 change zMax to "1023".

By the way I'm getting this stuff from:
[http://ubuntuforums.org/showthread.php?t=1607134](http://ubuntuforums.org/showthread.php?t=1607134)
[https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet)

And we were able to place one on the WizardPen driver:
[http://ubuntuforums.org/showthread.php?t=1578595](http://ubuntuforums.org/showthread.php?t=1578595)

---


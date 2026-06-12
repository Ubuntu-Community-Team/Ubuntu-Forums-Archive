---
title: "Mouse click delay"
date: 2010-12-02
forum: General Help
---

### Post by zorocke on 2010-12-02
Hey, after upgrading to the latest ubuntu 10.04 I've been having trouble with my mouse. For some reason, I cannot easily single click on anything. I need to hold down the left mouse button to click on things. 

I've tried setting the double click time out and simulated double click under mouse settings, and still the same problem. 


There must be a setting somewhere? Thanks.

---

### Post by JordanH on 2010-12-22
I was having the exact same issue with my Lenovo x200s w/ Ubuntu 10.04.  It manifests as a pause after clicking; your first symptoms will be that you get frustrated when trying to highlight text or when you try to drag a window or change its size;  The delay causes you to miss the first few characters of selection if you move the mouse too soon and you'll often "miss" catching the window when you try to drag or resize it.

I tried many different methods to resolve this issue and found that it was something I did to cause the problem.

Symptom
There is a delay between clicking the left mouse button and when you can assume that click has taken place.

Problem
Middle button emulation is enabled with a timeout.

Resolution
Disable middle button emulation or reduce the timeout.

There are a number of different ways that this may be disabled depending on how you have your input device configured.

xorg.conf
(old style) If you have your device configured via xorg.conf, then you need to add Option "Emulate3Buttons" "false" in the Input Device section and then restart X.

xinput
If you use xinput to configure your device, then go through this process.
Use a terminal to...
1.  Discover your device name or ID.  You may use the full name in quotations or the ID number for the rest of the instructions.
Example$ xinput list
output:  TPPS/2 IBM TrackPoint  id=10

2.  Check the properties to verify emulation is enabled/disabled. Evdev Middle Button Emulation 0 is off, 1 is on.  Evdev Middle Button Timeout value tells you how long you will wait; I believe it is in milliseconds. 
xinput --list-props <device>
Example$ xinput --list-props 10
Example$ xinput --list-props "IBM TPPS/2 IBM TrackPoint"

3.  Disable middle button emulation or reduce the timeout
xinput --set-prop <device> "Evdev Middle Button Emulation" 0
Example$  xinput --set-prop "TPPS/2 IBM TrackPoint" "Evdev Middle Button Emulation" 0
Example$  xinput --set-prop 10 "Evdev Middle Button Timeout" 50

I found that this was all set automatically when I used the gpointing-device-settings utility to enable horizontal and vertical scrolling on my laptop.  It was my mistake that I chose to enable the middle button emulation with a longer timeout.  If you use any such utility, make sure you check it to disable emulation!

I hope this helps.
Jordan.

---

### Post by JordanH on 2011-04-26
I ran into this problem again while re-installing Ubuntu 10.04.2
For some reason, these changes are not being made permanent when I follow my own instructions this time.

This link ([http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)) suggests that we should place the options in the xorg.conf.d folder, however, this location changes between versions of Ubuntu.

Does anyone know where these settings are intended to be saved?  I've been going through the backup of my previous installation and can't find them saved anywhere.

---


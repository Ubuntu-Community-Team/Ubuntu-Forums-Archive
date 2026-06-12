---
title: "Changed monitor cable; Ubuntu now no longer recognizes it"
date: 2012-07-16
forum: General Help
---

### Post by JamesCameron on 2012-07-16
I upgraded my VGA-with-converters cable to a straight DVI-D cable yesterday, and now Ubuntu 12.04 can't find the monitor I upgraded the cable for. I've tried switching the cables around on the video card (a GeForce 8800) and changing the drivers from the recommended driver to the post-update driver via Advanced Drivers, but no dice.

Both screens are fine in Windows 7, so I know it's not a hardware problem with the monitors, cables, or video card. In fact, all of my POST information and boot screens appear on the monitor that Ubuntu won't recognize. The secondary monitor is still on a VGA-to-DVI-D conversion, but the main monitor -- which is native DVI-D plugging into a native DVI-D port on the video card -- just can't get found no matter what. 

Is there a start-from-scratch method for reinstalling the video drivers entirely, or another option that might force Ubuntu to recognize this screen?

---

### Post by dino99 on 2012-07-16
try:

sudo rm /etc/X11/xorg.conf
sudo apt-get purge nvidia-current

sudo update-pciids && sudo update-usbids
sudo apt-get update
sudo apt-get install nvidia-current

logout/in

and run nvidia-settings to set both monitors config

note: cable is often to blame in such case. Watch the logs to know about usefull eroor/warning (/var/log/ & .xsession-errors)

---

### Post by JamesCameron on 2012-07-16
Thanks -- at work now, but will try again when I get home this evening. 

Question: is the Ubuntu/cable issue sensitive enough that seeing the monitor work for POST/BIOS and in Windows isn't enough of an indication that it's okay? 

Not trying to snark, I genuinely don't know how these things work on the micro level, and if a cable can have some sort of superminor fault that will snarfle up Ubuntu while other OSs work fine.

---

### Post by JamesCameron on 2012-07-17
That did it, dino99 -- thanks!

---


---
title: "New User: Compiz Q"
date: 2012-03-04
forum: General Help
---

### Post by ArchaicReality on 2012-03-04
Hello Linux users. I am a brand new user of Linux distros especially Ubuntu. My problem lies in the are of compiz. I have watched tutorial after tutorial on how to use compiz but to no avail...it doesnt work. I have all for apps for compiz installed but when I choose lets say wobbly windows, nothing happens. I heard from an excellent source that compiz does not work with Ubuntu 11.10 Unity..is this true?

---

### Post by Rodney9 on 2012-03-04
[http://www.howtoforge.com/enabling-compiz-fusion-on-ubuntu-11.10-oneiric-ocelot](http://www.howtoforge.com/enabling-compiz-fusion-on-ubuntu-11.10-oneiric-ocelot)

Your system must have a 3D-capable graphics card.

Rodney

---

### Post by grahammechanical on 2012-03-04
Compiz is the window manager or compositing manager for Ubuntu and has been for some time. It is still used in 11.10 and in the soon to be released 12.04.

In the past you could not use Compiz for special or enhanced visual effects unless you had both a video card capable of giving 3D effects and a driver that use the 3D effects. But compiz was still used for the ordinary or standard desktop.

From 11.10 onwards Compiz is used for standard Ubuntu but as the driver necessary for 3D is a proprietary driver it has to be installed and activated after installation of the OS. There is a special utility called Additional Drivers to do it.

If your computer lacks the hardware to have 3D effects then Ubuntu is installed in fall-back mode. This is called Ubuntu 2D and it uses Metacity as the window manager or compositing manager and not Compiz.

It is most likely that you are logging into the Ubuntu 2D desktop.

First, make sure that you have the proprietary driver installed for your video card. Then re-boot and at the log in screen click on the cog icon (I think) and select Ubuntu. You should see a menu with Ubuntu and Ubuntu 2D on it.

Now Compiz Configuration Settings Manager (CCSM) will work but be careful not all of the settings will work correctly. Some will break the desktop and make it unusable. You are safe with Wobbly windows. I use that and it does not break things. Others I cannot speak about becasue I have not tried them.

If you have problems then you must re-boot into Ubuntu 2D mode and undo what you have done. Do not make too many adjustments all at once.

In 12.04 we now get a message warning us that 

> CCSM is an advanced tool -use with caution. This tool allows you to deeply configure Compiz's settings. Some options may be incompatible with each other unless used with care. It is possible to be left with an unusable desktop.

In 12.04 some Unity settings have been moved into the appearance utility and it is possible that this movement of settings will continue and one day CCSM may no longer be available for download.

Regards.

---

### Post by ArchaicReality on 2012-03-05
I have an AMD graphics card and I went and tried all the commands and stuff but to no avail. I guess I am screwed and wont be able to enjoy the quarks and effects like everyone else..oh well...I just need the internet anyways

---


---
title: "Slightly Urgent: Nvidia Driver install deleted resolutions"
date: 2009-07-15
forum: General Help
---

### Post by Bucky Ball on 2009-07-15
Hi all,

Am interstate visiting inlaws, partly to check out a few quirks with their Ubuntu machine which I built for them in February. 

Arrived a few hours ago after a long drive and just checking things out before I go to bed and notice in 'Hardware Drivers' the nvidia driver hasn't been loaded. So I load it. Now I have spent an hour of precious time trying to figure out something that wasn't a problem when I got here! Nice work!

I rebooted after installing nvidia driver and was offered low res mode, I hit continue and now everything's huge on the screen. I have uninstalled the driver but no different. I have almost lost my patience but thought I would post here and go to bed, hoping someone might have left a bit of good news in the morning (or at least a clue as to how to get back to what it was).

Here is the graphics:

```
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7050 PV / nForce 630a (rev a2)
```... and here is my xorg.conf:

```

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
EndSection
Section "Extensions"
EndSection
```TNX in advance.

* Sorry, this machine is also 8.04
** I spent ages setting up the graphics on this thing without nvidia and now six months later I forget and do this! Sheesh!!

---

### Post by davidryderuk on 2009-07-15
Hi,
Sorry if this is too obvious, but did you check to see if any automatic backups of xorg.conf were generated before the nvidia driver was installed? It might be worth checking the /etc/X11/ directory for any backups, and seeing if there are any noticeable changes between them and what you have now.

---

### Post by Bucky Ball on 2009-07-15
Thanks for that. It is obvious now but not this morning at 2am!

Okay, there are in fact lots of backups, some of which are still there from when I built and set up the machine. There is one there that is called 'xorg.conf.works' but when I change to that one, no different. I change, log out and back in and nothing. But just wondering if I need to restart the machine or stop X server to make the changes and then start again.

Any more help gratefully appreciated! :)

---

### Post by Bucky Ball on 2009-07-16
Sorry to bump but running out of time ... :)

---

### Post by davidryderuk on 2009-07-17
I don't really have any idea why your computer is still not working. Maybe it would help if you posted your backup up xorg.conf file here so someone could see if there are any notable differences? But if the backup doesn't work, it sounds like the problem isn't your xorg.conf file, but something else.

After a bit more googling I have found the following thread about uninstalling nvidia drivers on feisty. It might be worth following it to be sure the drivers have been completely uninstalled.

[http://ubuntuforums.org/showthread.php?t=481887](http://ubuntuforums.org/showthread.php?t=481887)

---

### Post by Bucky Ball on 2009-07-17
Thanks for that. Where I am up to with it is that the drivers are installed no problems and things are working, but when I try to use the Nvidia settings, I am told to edit my xorg.conf file. I did a manual graphics configuration at boot and set to 1360x768 widescreen but once on the desktop, the best resolution (and default) is 1024x780 (from memory).

I am in Melbourne for a couple of days then back at that computer for a couple before heading 750kms home, so I will tinker some more when I get there and post the xorg.conf which is interesting but a bit hard to explain. Describes the monitor res correctly but doesn't provide a modeline for it, so  basically, what I am after now is a modeline for 1360x768 and all will (probably, hopefully) be sweet.

Any ideas anyone?

---

### Post by merlinus on 2009-07-17
Don't know if this will be useful, as I am running 9.04, but here is a bit from my xorg.conf dealing with screen resolutions.  You might be able to use it, of course changing the 1280x1024_85 to what you are wanting.  I am using the 180 nvidia driver.

Good luck!

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024_85 +0+0; 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by davidryderuk on 2009-07-17
Well done in getting the drivers to work. I don't know anything about mode lines myself having not had quite that much trouble with my monitors resolution.The following post seems like it could help though.

[http://ubuntuforums.org/showthread.php?t=276650](http://ubuntuforums.org/showthread.php?t=276650)

> If you need to just alter the Monitor section of the xorg.conf then here is how I sorted mine.

Go to /var/log and look for the xorg.0.log file and open it with gedit.
scroll through the log (big file, search if you like, for lines that refer to the Monitor.
there you should find info relating to the Vertical and Horizontal ranges...something like this...

(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 25.2 MHz Image Size: 304 x 228 mm
(II) fglrx(0): h_active: 640 h_sync: 688 h_sync_end 784 h_blank_end 800 h_border: 0
(II) fglrx(0): v_active: 350 v_sync: 410 v_sync_end 412 v_blanking: 449 v_border: 0
(II) fglrx(0): Ranges: V min: 50 V max: 75 Hz, H min: 31 H max: 61 kHz, PixClock max 80 MHz
(II) fglrx(0): Monitor name: AL1511
(II) fglrx(0): ACER
(II) fglrx(0): End of Display1 EDID data --------------------

My monitor has a vertical range of 50-75 and horizontal 31-61.

You may find all sorts of other warning [WW] and eror messages [EE] which may also give clues as to how to put things right.

Use the Vertical and Horizontal values you find in YOUR log to insert as HorizSync
and VertRefresh statements in your xorg.conf file.
(use sudo gedit /etc/X11/xorg.conf) copy it to a backup file first, in case you make a mistake and need a working config again..

This is what the section should look like (with YOUR monitor values from your log file, of course, not mine)
Section "Monitor"
HorizSync 31-61
Identifier "Generic Monitor"
Option "DPMS"
VertRefresh 50-75
Modeline "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

You could also check your Modeline statement is correct by referring to the values for the clock,
h_active,h_sync, h_sync_end, h_blank_end, v_active, v_sync, v_sync_end, v_blanking

If you are going to use the Modeline statement you must declare the mode in the Screen section...

Something like this:

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82852/855GM Integrated Graphics Device"
Monitor "Generic Monitor"
SubSection "Display"
Depth 24
Modes "1280x800@60"
EndSubsection
EndSection


This eliminates all the other mode statements for individual depths that you have in your current config so delete them from the Display subsection.
I have tested this method on my monitor.
(My current entry, based on those 'actual'log entries at the beginning )

Section "Monitor"
Identifier "AL1511"
Option "DPMS"
Modeline "1024x768" 25.20 640 688 784 800 350 410 412 449
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
Monitor "AL1511"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection

EndSection

It works(even without the Vert and Horiz sync values) and my available resolutions and refresh rates are now to be found in the Screen>Preferences dialog. So find your log file and get looking for those values.

---

### Post by Bucky Ball on 2009-07-17
Thanks everyone for the extremely helpful leads. I will be back at that computer tomorrow afternoon so will let you know how I go with it all.

:)

ps: When I built this computer, I was so impressed with the Acer monitor I went and bought two more, one for me and one for my wife. Plugged them in and they automatically set the correct resolution immediately: 1360x768. Weird. This machine ... not so. Go figure.

---

### Post by Bucky Ball on 2009-07-19
Here is my current xorg.conf, BTW:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Boardname    "vesa"
    Busid        "PCI:0:18:0"
    Driver        "vesa"
    Screen    0
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1360x768"
    Horizsync    31.5-48.0
    Vertrefresh    56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor        "Configured Monitor"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Modes        "800x600@60"    "1024x768@60"    "800x600@56"    "640x480@60"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
    Load        "glx"
    Load        "GLcore"
    Load        "v4l"
EndSection
Section "ServerFlags"
EndSection
```Also, I find no line in the log that looks like this:

(II) fglrx(0): Supported additional Video Mode

... so still no idea of what the modeline should look like. Thanks for the suggestions. Any more? I leave tomorrow morning so running out of time! :(

When I try to open Nvidia X Server Settings from Synaptics told to edit Xorg.conf, but in Hardware Drivers, Nvidia driver in use. Xorg.conf seems to be using Vesa and GLX. Hmm. Any help appreciated.

---

### Post by Bucky Ball on 2009-07-20
This is what I am getting in /var/log/xorg.0.log (think that is it!):

                                       (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
   
  
So if the Nvidia driver was kicking in I might be having a little more success. Any ideas how I might fix this? I'll keep looking ...

So,

Hardware Drivers: Nvidia driver enabled
xorg.conf: vesa and glx instructions are in there
Log tells me GLX failed to initialise.

Just wondering if backing up xorg.conf and running:

```
sudo dpkg-reconfigure xserver-xorg
```might help. I might then be able to do a patchwork of the two files. :)

---


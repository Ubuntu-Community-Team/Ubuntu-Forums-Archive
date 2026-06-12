---
title: "Ubuntu 9.10 randomly freezes"
date: 2009-11-02
forum: General Help
---

### Post by AdamRG on 2009-11-02
I have recently done a clean install of 9.10.  After some time sitting idle, the system seems to lock up.  The mouse is active, however I can't click on anything and the keyboard no longer is active.  The only thing I can do is power down the machine and reboot.  I am not sure being a novice where to look in trouble shooting this.  

Any suggestions?

---

### Post by AdamRG on 2009-11-03
I found a similiar posting.  Looks like the issue is related to my graphics card.  A bug report has been filed.  Bug #466310.  ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/466310](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/466310))

Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)


[http://ubuntuforums.org/showthread.php?t=1307413&highlight=Intel+Corporation+Chipset+Integrated+Graphics+Device+%28rev+03%29](http://ubuntuforums.org/showthread.php?t=1307413&highlight=Intel+Corporation+Chipset+Integrated+Graphics+Device+%28rev+03%29)

---

### Post by P4man on 2009-11-03
This may or may not help:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

I would also try turning off desktop effects and see if it helps.

Lastly, rather than hitting the power switch, try a gracefull shutdown or reboot using [REISUB]("http://kember.net/articles/231/reisub-the-gentle-linux-restart"). Its hardly a real solution but it at least it will prevent damage to your filesystem due to improper shutdowns

---

### Post by AdamRG on 2009-11-03
Thanks for the tips.  I seem to have gotten around the freezing by using the vesa graphics driver.  It is not the best due to the poor resolution, but at least it doesn't freeze up any longer.

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection

---

### Post by kagashe on 2009-11-04
> **P4man said:**
> This may or may not help:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

I would also try turning off desktop effects and see if it helps.
This PCI ID is blacklisted on COMPIZ and Desktop Effects are already disabled.

kagashe

---

### Post by AdamRG on 2009-11-05
Does anyone have a sample xorg.conf file that will provide better resolution?  I have tried numerous things without success.

---

### Post by Giblet5 on 2009-11-05
Before you can successfully create an xorg.conf file, you'll need the horizontal and vertical sync frequency range of your monitor.

Most vendors publish this as Horizontal Sync and Vertical Refresh.

Once you have those values, you can generate a skeleton xorg.conf by flipping to the text console (CtrlAltF1), disabling gdm via ```
sudo /etc/init.d/gdm stop
``` and running ```
X -configure
```

Once you have a skeleton xorg.conf, re-enable gdm via ```
sudo /etc/init.d/gdm start
``` log in, bring up a terminal window and enter ```
sudo gedit /etc/X11/xorg.conf
```

Look for the "Monitor" section and add the HorizSync and VertRefresh options. [COLOR="DarkRed"]DON'T change any other values[/COLOR].

Example: ```
...

Section "Monitor"
    Identifier     "Default Monitor"
    HorizSync       30.0 - 94.0
    VertRefresh     48.0 - 85.0
EndSection

...
```

Save it and exit gedit.

From the terminal window, run ```
sudo /etc/init.d/gdm restart
```

That will restart X and pick up the new monitor timings. You should be able to select all of the best resolutions for your monitor now. No more, and no less.

---

### Post by AdamRG on 2009-11-05
I have tried to follow the instructions you gave regarding the creation of the custom xorg.conf file.  It is not working however.  Any ideas?

 Here are the log messages from the X.org log:

    Information    VESA(0): Total Memory: 13 64KB banks (832kB)
    Information    VESA(0): Monitor0: Using hsync range of 30.00-61.00 kHz
    Information    VESA(0): Monitor0: Using vrefresh range of 56.00-76.00 Hz
    Information    VESA(0): Monitor0: Using maximum pixel clock of 80.00 MHz
    Warning    VESA(0): Unable to estimate virtual size
    Probed    VESA(0): Virtual size is 640x480 (pitch 640)
    From config file    VESA(0): *Built-in mode "640x480"


I have a Dell E151FPb monitor.  According to the documentation.  Here is the doc from Dell on this monitor...

Horizontal Scan Range - 30 kHz to 61 kHz (automatic)
Vertical Scan Range - 56 Hz to 76 Hz (automatic)
Optimal Preset Resolution 1024 x 768 at 60 Hz
Highest Preset Resolution 1024 x 768 at 75 Hz

This is the relevant (I think) section of the xorg.conf

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync    30.0 - 61.0
    VertRefresh  56.0 - 76.0
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "vesa"
    VendorName  "Intel Corporation"
    BoardName   "82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by P4man on 2009-11-06
Try adding these red lines:
```

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync    30.0 - 61.0
    VertRefresh  56.0 - 76.0
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "vesa"
    VendorName  "Intel Corporation"
    BoardName   "82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
        [COLOR="Red"]Virtual 1024 768[/COLOR]
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
        [COLOR="Red"]Virtual 1024 768[/COLOR]
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
        [COLOR="Red"]Virtual 1024 768[/COLOR]
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
        [COLOR="Red"]Virtual 1024 768[/COLOR]
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
      [COLOR="Red"]  Virtual 1024 768[/COLOR]
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        [COLOR="Red"]Virtual 1024 768[/COLOR]

    EndSubSection
EndSection
```

only the last one (using 24 bit color) will really matter I guess.

I would also suggest not using vesa but the intel driver again, and use these tricks to try and stabilize it:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Narrow%20Subsystem%20it%20Occurs%20in](https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Narrow%20Subsystem%20it%20Occurs%20in)

---

### Post by AdamRG on 2009-11-07
All of the changes to xorg.conf haven't helped.  I found instructions regarding reverting back to the Intel 2.4 version of the driver and that has seemed to help.  Here is the  link:  

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by martez81 on 2009-11-07
I had similar problem with ubuntu 8.10 and found out it was related with my usb wireless adapter. I changed adapter for different brand and it solved the problem.

---

### Post by AdamRG on 2009-11-07
Thanks for the tip.  Reverting to the older intel driver has resolved the problem for me.  I haven't locked up again.

---

### Post by JohnGalt2010 on 2009-11-07
I had two freezes this last weekend while using Firefox, one freeze Thursday while using Gnucash, and one freeze today while using Firefox. The only way to escape, was a hard boot.

I have a fresh install of Karmic with an Intel 82845G/GL integrated video (according to the Xorg.0.log).

---

It may be worth noting that the Xorg.0.log showed an error trying to load the "i810" driver, which it couldn't find. Also, I noticed that Extreme Tux Racer is running somewhat "choppy". I assume this means that graphics acceleration is not active.

---
Update: Reverted to the xorg-video-intel-2.4 package per instructions.  All text was illegible.  Went back to the original xorg-video-intel package.

---
Update2: For some reason, 2.4 seems to work now.  Go figure?

---

### Post by michaelzap on 2009-11-07
You might try out the latest release candidate of the new kernel(2.6.32-rc6):
[http://ubuntuforums.org/showpost.php?p=8263419&postcount=135](http://ubuntuforums.org/showpost.php?p=8263419&postcount=135)

That seems to be doing the trick for me. I've gone three or four hours without a crash or freeze now, and that never happened before with Karmic.

---


---
title: "ATI Radeon 9000 v Ubuntu 9.10 slow performance"
date: 2009-12-04
forum: General Help
---

### Post by NX3 on 2009-12-04
I've installed Ubuntu 9.10 Karmic on a PC with a ATI Radeon 9000 but found the video performance extremely slow. Web was just about ok but video clips on the BBC news site or Youtube were running at about 10fps and terrible!

Much googling and I didn't find a proper solution but clues but I've eventually got something acceptable so here is my fix !

Ubuntu 9.10 doesn't have a xorg.conf file by default on a clean install. So the first thing you need to do is create one. In terminal enter :

sudo nano /etc/X11/xorg.conf

This will load a text editor. I found loads of settings online with no confirmation by anyone of what worked or didn't. So I took the following information only and pasted it into my xorg.conf file. I think saved the file and restarted Ubuntu. 

Section "Device"
        Identifier      "Radeon 9000"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option         "XAANoOffscreenPixmaps"
        Option         "EnableDepthMoves" "True"
        Option         "EnablePageFlip" "True"
        Option         "DMAForXv" "True"
        Option         "AccelDFS" "True"
        Option         "ColorTiling" "True"
        Option         "RenderAccel" "True"
        Option         "VGAAccess" "True"
        Option         "AccelMethod" "EXA"
        Option         "DRI" "True"
        Option         "MigrationHeuristics" "Greedy"
        Option         "TripleBuffer" "True"
        Option         "EXAOptimizeMigration" "True"
        Option         "EXANoComposite" "No"
        Option         "BackingStore" "True"
EndSection

Videos now play smoothly and performance is much better.

---

### Post by vladkras on 2009-12-10
i've followed your instruction and my PC could work only in low grafics mode, so i had to delete xorg.conf

anyway, i still got problems with my radeon 9000 and karmic koala

when trying to install the driver i downloaded from the official server i see this:

==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/9.10
Requested package is not supported.
Removing temporary directory: fglrx-install

i checked out the list of supported packages, here it is:

Ubuntu Packages:
    Ubuntu/warty
    Ubuntu/4.10
    Ubuntu/hoary
    Ubuntu/5.04
    Ubuntu/breezy
    Ubuntu/5.10
    Ubuntu/dapper
    Ubuntu/6.06
    Ubuntu/edgy
    Ubuntu/6.10

so how can i build Ubuntu/9.10 package for my Ubuntu 9.10?

---

### Post by apheren on 2010-01-20
Hi

Well I have a Radeon 9000 and my problem is that I can set my monitor to 1280x1024, which is the recommended resolution, otherwise It looks kind blurry.

I picked one xorg.conf and I try to configure it myself but it went wrong, when login in to Ubuntu appears a message on the screen "Out of Scale - xx Hz / xx KHz" - according to the manufacturer specifications all was well configured, I guess it was something related with Horizontal Sync or Refresh Rate -"DGP" or something like that.

I can't remember exactly the numbers, that's why I put "xx", anyway it was normal to appear that but then it used to log. I've tried also to install Envy and restart X Server, but again no video response.


EDIT: Well, it works! Feedback is positive, much smoother now.


Still I have this problem
[http://ubuntuforums.org/showthread.php?t=1381771](http://ubuntuforums.org/showthread.php?t=1381771)

no background or desktop icons when 1280x1024. I can have background and desktop icons in 1280x1024 but only with the animations off, If it were any way around it.

---

### Post by apheren on 2010-01-22
Sorry for double-posting, but I guess this maybe worthy for someone.



[B]CAUTION - beware of the monitor specifications, with this name it should work for anyone, It is just set for mine.
If you're using other kind of monitor like 16/9 you should leave the modes section blank with any resolution, or put them if you know what you're doing. For more info type man radeon

[/B]Anyway, I didn't change many stuff like the OP, but this is just a test and I will try some more stuff then. 

```


Section "Device"
    Identifier    "ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
    Driver        "ati"
    BusID        "PCI:1:0:0"
    Option "XAANoOffscreenPixmaps"
    Option "EnableDepthMoves" "True"
    Option "EnablePageFlip" "True"
    Option "DMAForXv" "True"
    Option "AccelDFS" "True"
    Option "ColorTiling" "True"
    Option "RenderAccel" "True"
    Option "VGAAccess" "True"
    Option "AccelMethod" "EXA"
    Option "DRI" "True"
    Option "MigrationHeuristics" "Greedy"
    Option "TripleBuffer" "True"
    Option "EXAOptimizeMigration" "True"
    Option "EXANoComposite" "No"
    Option "BackingStore" "True"
EndSection

Section "Monitor"
    Identifier    "L1919S"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
    Monitor        "L1919S"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```


EDIT:

---

### Post by geoffp on 2010-02-25
Thanks for this -- really seems to have helped my performance on my old Mac G4 tower!

---

### Post by Xendarq on 2010-04-10
Also wanted to convey sincere thanks for this - the change improved glxgears on my 9800 Pro from 500 frames in 5 seconds to 13000+ frames in 5 seconds.  It also allows video to display reasonably well considering the age of the box.

**We should really try to get this fix automated into the Ubuntu display configuration.**  Does anyone know how to go about doing that?

I'm not sure if this will be of additional help, but I changed  only the "Device" section.  I left everything else defaulted and, again, the improvement has been dramatic.  Here is my Xorg.conf, which I would imagine would be suitable regardless of monitor.

```

Section "Device"
        Identifier      "ATI Technologies Inc Radeon 9800 Pro"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "EnableDepthMoves"      "True"
        Option          "EnablePageFlip"        "True"
        Option          "DMAForXv"              "True"
        Option          "AccelDFS"              "True"
        Option          "ColorTiling"           "True"
        Option          "RenderAccel"           "True"
        Option          "VGAAccess"             "True"
        Option          "AccelMethod"           "EXA"
        Option          "DRI"                   "True"
        Option          "MigrationHeuristics"   "Greedy"
        Option          "TripleBuffer"          "True"
        Option          "EXAOptimizeMigration"  "True"
        Option          "EXANoComposite"        "No"
        Option          "BackingStore"          "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "dri"
        Load    "GLcore"
EndSection

```

---


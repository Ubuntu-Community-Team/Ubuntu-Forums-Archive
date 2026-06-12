---
title: "ATI Drivers -&gt; Monitor &quot;Signal frequency is out of range&quot;"
date: 2006-06-02
forum: General Help
---

### Post by MellonCollie on 2006-06-02
Hi folks!

I tried to install the ATI drivers as described in 'Method 1' on [this page.]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") 

```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

There were no errors or warnings in the terminal, everything seemed to go well. However, when I rebooted I got a "Signal frequency is out of range" error message from my monitor (Mitsubishi 930SB), just as the desktop was about to load, and because of this my Ubuntu installation is currently KO'd.

Before I rebooted I copied the contents of xorg.conf to a text file, for possible troubleshooting. Please have a look at the following and tell me if anything's amiss.... (Items in [COLOR="SeaGreen"]green[/COLOR] were manually added by me)

```

Section "Monitor"
Identifier   "NEC HR19"
Option      "DPMS"
[COLOR="SeaGreen"]HorizSync    30.0 - 110.0
VertRefresh  50.0 - 160.0[/COLOR]
EndSection


Section "Monitor"

Identifier   "aticonfig-Monitor[0]"
Option      "VendorName" "ATI Proprietary Driver"
Option      "ModelName" "Generic Autodetecting Monitor"
Option      "DPMS" "true"
EndSection

Section "Device"
Identifier  "ATI Technologies, Inc. R350 AH [Radeon 9800 SE]"
Driver      "vesa"
BusID       "PCI:3:0:0"
EndSection

Section "Device"
Identifier  "aticonfig-Device[0]"
Driver      "fglrx"
Option      "VideoOverlay" "on"
Option      "OpenGLOverlay" "off"
EndSection


Section "Screen"
Identifier "Default Screen"
Device     "ATI Technologies, Inc. R350 AH [Radeon 9800 SE]"
Monitor    "NEC HR19"
DefaultDepth     24

SubSection "Display"
Depth     1	Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection

SubSection "Display"
Depth     4	Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection

SubSection "Display"
Depth     8	Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection

SubSection "Display"
Depth     15	Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection

SubSection "Display"
Depth     16	Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection

SubSection "Display"
Depth     24	Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection



Section "Screen"

Identifier "aticonfig-Screen[0]"
Device     "aticonfig-Device[0]"
Monitor    "aticonfig-Monitor[0]"
DefaultDepth     24
SubSection "Display"
Viewport   0 0
```


Does anyone have any ideas as to how to go about rectifying this? :(

---

### Post by Dryer Lint on 2006-06-02
It seems X is running at a resolution/refresh rate combination your screen does not support.

Are you sure the values you entered are right?

I bet X tries to run at the highest resolution at a frequency that is unsupported. Try deleting the 1600x1200 and 1280x1024 resolutions from your xorg.conf and see if it works.
Or alternatively set your gfx card driver to "vesa", the screen will run at 60Hz then.

Then you have to find out at which frequency your screen is able to run at your desired resolution. For example, my Dell monitor supports up to 75Hz, but at the highest resolution only 60Hz works. I copied a fitting modeline from someone else, so I can't help you there...

---

### Post by MellonCollie on 2006-06-02
Thank for the reply! :)

[QUOTE=Dryer Lint]It seems X is running at a resolution/refresh rate combination your screen does not support.

Are you sure the values you entered are right?[/QUOTE]

I was under the impression (please correct me if I'm wrong) that you're supposed to put the full range of frequencies that your monitor supports in the HorizSync and VertRefresh parts? If that's true then the numbers I added are correct because I double-checked the monitor's user manual. 

 
[QUOTE=Dryer Lint]
I bet X tries to run at the highest resolution at a frequency that is unsupported. Try deleting the 1600x1200 and 1280x1024 resolutions from your xorg.conf and see if it works.[/QUOTE]

I just tried that and it's a no-go. When it hangs before the desktop loads and gives the "signal frequency is out of range" message, the on-screen display says that the monitor's frequencies are H: 112.6 and V:75.1

I tried changing the highest values in HorizSync and VertRefresh to 85, but it still gave the same message.

[QUOTE=Dryer Lint]
Or alternatively set your gfx card driver to "vesa", the screen will run at 60Hz then.[/QUOTE]

I'm trying to get away from the vesa driver because 60Hz is killing my eyes. :( 


[QUOTE=Dryer Lint]
Then you have to find out at which frequency your screen is able to run at your desired resolution. For example, my Dell monitor supports up to 75Hz, but at the highest resolution only 60Hz works. I copied a fitting modeline from someone else, so I can't help you there...[/QUOTE]

I know my monitor can support 1280x1024 @ 85 so I don't understand why it's complaining (I've used 1280x1024 @ 90 in Windows with no problems). My monitor's max refresh rates for some of the most common resolutions are as follows:

640x480 @ 160 Hz
800x600 @ 160 Hz
1024x768 @ 132 Hz
1280x1024 @ 101 Hz
1600x1200 @ 87 Hz


](*,)

---

### Post by MellonCollie on 2006-06-02
Awesome! :) I managed to get things sorted by adding 'Modes' in the botton section, like so....

```

Section "Screen"

Identifier "aticonfig-Screen[0]"
Device     "aticonfig-Device[0]"
Monitor    "aticonfig-Monitor[0]"
DefaultDepth     24
SubSection "Display"
Viewport   0 0
[COLOR="SeaGreen"]Modes    "1280x1024"[/COLOR]
```


:D

---

### Post by flyingbrass on 2006-06-02
aticonfig --initial gets one started, but I was stuck at 1600x1200.  I got other resolutions working by manually altering xorg.conf, but later found that resolutions can be changed with aticonfig.  Type aticonfig -h to see all the options.

Your HorizSync and VertRefresh settings would have worked (unless the driver ignores them now) if you had added them in the correct monitor section.  "NEC HR19" was from your orginal xorg setup.   "aticonfig-Monitor[0]" is the monitor added by aticonfig and the section actually being used.  Same for the added device and screen sections.

It is confusing at first.  You still would have had to specify a mode or several, as you finally did, to have the resolution(s) you want available.

Someone familiar with aticonfig use and options should write clearer instructions.  Current guides, at least the ones I've seen, leave the impression all one needs to do is type two lines and everything is good to go.

I'm curious which other settings actually work and should be enabled.  I turned on vsync.  What about FSAA and its options?  From what I gather it needs to be left off if using Xgl.

---


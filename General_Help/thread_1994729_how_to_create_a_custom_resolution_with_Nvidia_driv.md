---
title: "how to create a custom resolution with Nvidia driver like windows?"
date: 2012-06-03
forum: General Help
---

### Post by sdowney717 on 2012-06-03
I have a problem with a samsung LCD 216bw monitor that will not auto detect in any os on the DVI port.

In Vista, I finally figured out a custom resolution to make it perform perfectly at 1680 by 1050. 

Ubuntu when running Nvidia driver can only show 640 or 800.
Running without the Nvidia driver, I get a blank screen or colored lines.

How can I force a setting ?

The screen shot shows it running in Vista with the custom resolution and all the various settings. And is using this monitor.

---

### Post by LinGNUbie on 2012-06-03
Using the Nvidia drivers I have come to find that a custom xorg.conf will do the trick, as long as one never uses the Nvidia control panel to make a resolution adjustment after that, but uses the normal monitor applet in system settings instead.

My advice would be to find in the monitor documentation the Horizon and Vertical refresh rates, then use a modeline generator, such as [www.arachnoid.com/modelines/index.html]("www.arachnoid.com/modelines/index.html"), to create an xorg.conf file with the required resolutions and refresh rates. There are many sites with examples. Mainly you just need the portion for monitor and screen like in the example I have posted [here]("http://ubuntuforums.org/showthread.php?t=1923165").

---

### Post by sdowney717 on 2012-06-03
I copied that xorg and made some substitutions. geenrated a modeline using

cvt 1680 1050 60 
changed the hor and vert 
and still dont see anything new, just 640.
I have the latest nvidia driver running
So what do I do?
```
Section "Monitor"
    Identifier	"Configured Monitor"
    Vendorname	"Samsung"
    Modelname	"216bw"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync
    Modeline "640x480_72.00"   29.50  640 664 728 816  480 483 487 503 -hsync +vsync
    Modeline "640x480_75.00"   30.75  640 664 728 816  480 483 487 504 -hsync +vsync
    Modeline "720x400_70.00"   26.25  720 744 808 896  400 403 413 420 -hsync +vsync
    Modeline "800x600_56.00"   35.00  800 832 904 1008  600 603 607 623 -hsync +vsync
    Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
    Modeline "800x600_72.00"   47.00  800 840 920 1040  600 603 607 628 -hsync +vsync
    Modeline "800x600_75.00"   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync
    Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
    Modeline "1024x768_70.00"   75.25  1024 1080 1184 1344  768 771 775 802 -hsync +vsync
    Modeline "1024x768_75.00"   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync
    Modeline "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
    Modeline "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
    Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
    Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

EndSection

Section "Screen"
    Identifier	"Default Screen"
    Device	"Configured Video Device"
    Monitor	"Configured Monitor"
    Defaultdepth	24
    SubSection "Display"
    Depth	24
    Modes	"1680x1050@60"	"1360x768@60"	"1280x768@60"	"1280x720@60"	"1024x768@75"	"1024x768@70"	"1024x768@60"	"800x600@75"	"800x600@72"	"800x600@60"	"800x600@56"	"720x400@70"	"640x480@72"	"640x480@60"
    EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

---

### Post by sdowney717 on 2012-06-03
from xorg.0.log, YES I KNOW there is no EDID coming from this monitor like it should!

So how to force it take 1680x1050 like it can do in win7?
xorg.cong it sees the resolution says invalid due to no EDID data from monitor. 

```
[    24.458] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-0 is invalid:
[    24.458] (WW) NVIDIA(GPU-0):     unrecognized EDID Header.
[    24.458] (--) NVIDIA(GPU-0): 
[    24.458] (--) NVIDIA(GPU-0): Raw EDID bytes:
[    24.458] (--) NVIDIA(GPU-0): 
[    24.458] (--) NVIDIA(GPU-0):   00 00 00 00 7f ff ff 00  4c 2d 0d 03 32 32 45 4d
[    24.458] (--) NVIDIA(GPU-0):   13 11 01 03 80 2f 1e 78  2a d5 15 a4 55 49 9a 27
[    24.458] (--) NVIDIA(GPU-0):   14 50 54 bf ef 80 b3 00  81 80 81 40 71 4f 01 01
[    24.458] (--) NVIDIA(GPU-0):   01 01 01 01 01 01 7c 2e  90 a0 60 1a 1e 40 30 20
[    24.458] (--) NVIDIA(GPU-0):   36 00 da 28 11 00 00 1a  00 00 00 fd 00 38 4b 1e
[    24.458] (--) NVIDIA(GPU-0):   51 0e 00 0a 20 20 20 20  20 20 00 00 00 fc 00 53
[    24.458] (--) NVIDIA(GPU-0):   79 6e 63 4d 61 73 74 65  72 0a 20 20 00 00 00 ff
[    24.458] (--) NVIDIA(GPU-0):   00 48 56 43 50 35 30 36  33 38 33 0a 20 20 00 b2
[    24.458] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    24.458] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    24.458] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    24.458] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    24.458] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    24.458] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    24.458] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    24.458] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    24.458] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    24.458] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    24.458] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    24.458] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    24.458] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    24.458] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    24.458] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    24.458] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    24.458] (--) NVIDIA(GPU-0): 
[    24.459] (II) NVIDIA(0): NVIDIA GPU GeForce 8400 GS (G98) at PCI:1:0:0 (GPU-0)
[    24.459] (--) NVIDIA(0): Memory: 524288 kBytes
[    24.459] (--) NVIDIA(0): VideoBIOS: 62.98.29.00.51
[    24.459] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    24.459] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    24.460] (--) NVIDIA(0): Connected display device(s) on GeForce 8400 GS at PCI:1:0:0
[    24.460] (--) NVIDIA(0):     DFP-0
[    24.460] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    24.460] (--) NVIDIA(0): DFP-0: Internal Dual Link TMDS
[    24.534] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    24.534] (**) NVIDIA(0):     device DFP-0 (Using EDID frequencies has been enabled on
[    24.534] (**) NVIDIA(0):     all display devices.)
[    24.542] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    24.542] (WW) NVIDIA(0): No valid modes for "1680x1050@60"; removing.
[    24.542] (WW) NVIDIA(0): 
[    24.542] (WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
[    24.542] (WW) NVIDIA(0):     "nvidia-auto-select".
[    24.542] (WW) NVIDIA(0): 
[    24.542] (II) NVIDIA(0): Validated modes:
[    24.542] (II) NVIDIA(0):     "nvidia-auto-select"
[    24.542] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    24.564] (WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
```

---

### Post by LinGNUbie on 2012-06-03
I know of programs for finding and interpreting edid info such as read-edid, but from there i am at a a loss. I assumed the xorg overrode display settings. However I have seen the Horiz & Vert being incorrect prevent a display from running any higher than what you are getting.

---

### Post by LinGNUbie on 2012-06-03
As a side perhaps you should try with change:

```
Section "Screen"
    Identifier	"Default Screen"

```

to:

```
Section "Screen"
    Identifier	"DFP-0"

```

---

### Post by sdowney717 on 2012-06-04
[http://ubuntuforums.org/showthread.php?t=1121160&page=2](http://ubuntuforums.org/showthread.php?t=1121160&page=2)

here at the last entry, a poster found some edid data put it in a file and redirected xorg to read it.

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX2235wm"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTX"
    Option         "NoLogo" "True"
    Option         "UseDisplayDevice" "DFP-0"
    Option         "CustomEDID" "DFP-0:/etc/X11/edid.raw"
EndSection

```
from here, 
[http://www.tomshardware.com/forum/272181-33-samsung-216bw-1920-1080p](http://www.tomshardware.com/forum/272181-33-samsung-216bw-1920-1080p)

I found something maybe might work?
Does this look like a edid.raw file?
save this to a file and try it?
```
EDID ( Extendid Display Identification Data) Report 


Vendor/Product Identification: 

Monitor Name : SyncMaster 
Monitor Serial Number : H9LPC05274 
Manufacturer Name : Samsung 
Product Id : 30D 
Serial Number : 1296380466 
Week Of Manufacture : 49 
Year Of Manufacture : 2007 
EDIDVersion : V1.3 
Number Of Extension Flag : 0 

Display parameters: 

Video Input Definition : Digital Signal 
DFP1X Compatible Interface : False 
Max Horizontal Image Size : 470 mm 
Max Vertical Image Size : 300 mm 

Power Management and Features: 

Standby : Not Supported 
Suspend : Not Supported 
ActiveOff : Supported 
Video Input : 1 
sRGB Default ColorSpace : False 
Default GTF : Not Supported 
Prefered Timing Mode : True 

Gamma/Color and Etablished Timings: 

Display Gamma : 2.2 
Red : x = 0.644 - y = 0.333 
Green : x = 0.286 - y = 0.603 
Blue : x = 0.152 - y = 0.079 
White : x = 0.313 - y = 0.329 

Etablished Timings : 
800 x 600 @ 60Hz (VESA) 
800 x 600 @ 56Hz (VESA) 
640 x 480 @ 75Hz (VESA) 
640 x 480 @ 72Hz (VESA) 
640 x 480 @ 67Hz (Apple, Mac II) 
640 x 480 @ 60Hz (IBM, VGA) 
720 x 400 @ 70Hz (IBM, VGA) 
1280 x 1024 @ 75Hz (VESA) 
1024 x 768 @ 75Hz (VESA) 
1024 x 768 @ 70Hz (VESA) 
1024 x 768 @ 60Hz (VESA) 
832 x 624 @ 75Hz (Apple, Mac II) 
800 x 600 @ 75Hz (VESA) 
800 x 600 @ 72Hz (VESA) 
1152 x 870 @ 75Hz (Apple, Mac II) 

Display Type : RGB Color Display 

Standard Timing: 


Standard Timings n°	2 
X Resolution : 1280 
Y Resolution : 1024 
Vertical Frequency : 60 

Standard Timings n°	3 
X Resolution : 1280 
Y Resolution : 960 
Vertical Frequency : 60 

Standard Timings n°	4 
X Resolution : 1152 
Y Resolution : 864 
Vertical Frequency : 75 

Preferred Detailed Timing: 

Pixel Clock : 119 Mhz 

Horizontal Active : 1680 pixels 
Horizontal Blanking : 160 pixels 
Horizontal Sync Offset : 48 pixels 
Horizontal Sync Pulse Width : 32 pixels 
Horizontal Border : 0 pixels 
Horizontal Size : 474 mm 

Vertical Active : 1050 lines 
Vertical Blanking : 30 lines 
Vertical Sync Offset : 3 lines 
Vertical Sync Pulse Width : 6 lines 
Vertical Border : 0 lines 
Vertical Size : 40 mm 

Input Type : Digital Separate 
Interlaced : False 
VerticalPolarity : False 
HorizontalPolarity : True 

Monitor Range Limit: 

Maximum Vertical Frequency : 75 Hz 
Minimum Vertical Frequency : 56 Hz 
Maximum Horizontal Frequency : 81 KHz 
Minimum Horizontal Frequency : 30 KHz 
Maximum Pixel Clock : 140 MHz 

Stereo Display: 

Stereo Display : Normal display (no stereo) 

I downloaded a freeware program called EDID Viewer, and this is the report it produced from the system registry.

```

---

### Post by sdowney717 on 2012-06-04
[http://whereyouwantto.bplaced.net/wiki/index.php?title=Reactivate_LCD_monitors_dead_DVI_input](http://whereyouwantto.bplaced.net/wiki/index.php?title=Reactivate_LCD_monitors_dead_DVI_input)

more info on edid file reading and sounds posible to rewrite edid data for the dvi port.
Also makes it sound like a vga cable works when dvi does not and might be able to get edid data from a vga cable (which I dont have)

What I need is a edid raw file for a samsung 216bw monitor

---

### Post by nicolasforum89 on 2012-06-04
Tha nks for the link

---

### Post by sdowney717 on 2012-06-04
looks like that is not an edid raw format
> [    24.342] (WW) NVIDIA(GPU-0): Unable to use EDID file '/etc/X11/edid.raw': file format not
[    24.342] (WW) NVIDIA(GPU-0):     recognized

also I tried your idea of gfp-0 for identifier with that xorg.conf and it did not work.

---

### Post by sdowney717 on 2012-06-04
I got it working!!
from here this guy had the right stuff
[http://forum.xbmc.org/showthread.php?tid=54685](http://forum.xbmc.org/showthread.php?tid=54685)


this xorg.conf gives me 1680 by 1050!
I used the command "cvt 1680 1050 60" to generate the modeline

these options were critical
Option "ExactModeTimingsDVI" "TRUE"
Option "ModeValidation" "NoEdidModes"
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 295.53  (buildmeister@swio-display-x86-rhel47-03.nvidia.com)  Sat May 12 00:17:08 PDT 2012

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
    Option "ExactModeTimingsDVI" "TRUE"
    Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option "ModeValidation" "NoEdidModes"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes "1680x1050"
    EndSubSection
EndSection
```

oddly, when I loaded up nvidia config screen, It shows a large number of available resolutions
why is that showing up??

---

### Post by LinGNUbie on 2012-06-04
Good stuff! Research goes a long way!

> **sdowney717 said:**
> 
oddly, when I loaded up nvidia config screen, It shows a large number of available resolutions
why is that showing up??

Probably due to Nvidia using a "virtual" desktop via the driver, it is supposed to take the actual settings and then be able to resize it virtually to any configuration one would like.

I would add a few more resolution modelines just in case any future updates "decide" that your singular mode isn't correct. The xorg.conf and Nvidia will always attempt to use the highest preferred resolution though, or whichever was set last. I believe it is specified in an xml file in the user's home folder, but not for certain.

---

### Post by sdowney717 on 2012-06-04
Looks like this also can be a problem with hooking up HDTV
Needing to tell xorg to stop the X server from validating the modes against the EDID info received from the monitor or TV. In my case the EDID data is corrupted, in this other case not allowing the TV to show the right mode resolution. Wonder what's the real cause of his trouble.

[http://judsonsnotes.com/notes/index.php?option=com_content&view=article&id=182:modelines-for-sony-tv-and-nvidia-9400gt&catid=37:tech-notes&Itemid=59](http://judsonsnotes.com/notes/index.php?option=com_content&view=article&id=182:modelines-for-sony-tv-and-nvidia-9400gt&catid=37:tech-notes&Itemid=59)

I found a lot of hits on this with various fixes which worked for some and not others. If your monitor is sending out bogus EDID data, then this type approach should work. 

As a history, I got this monitor from my in law's. A 2007 model where the capacitors had died. I replaced the invertor power supply capacitors which had bulged-popped. I had also removed the VGA DVI connection board and even though had done nothing overtly to it, maybe caused it to loose its rom data. How, I just dont know.
Not very robust, IMO for this LCD monitor.

More on modding EDID
[http://analogbit.com/node/23](http://analogbit.com/node/23)
[http://blog.komeil.com/2008/06/fixing-edid-dvi-monitors-no-signal.html](http://blog.komeil.com/2008/06/fixing-edid-dvi-monitors-no-signal.html)

---

### Post by sdowney717 on 2012-06-05
I have totally solved this by writing a corrected edid header in the eeprom of the monitor
all edid header's are like 00 ff ff ff ff ff ff 00 

Use a registered version of powerstrip
[http://www.ddc-ci.com/](http://www.ddc-ci.com/)
I put the monitor in service mode so the eeprom is no longer write protected. Must be done or you wont be able to write new edid data.

> [http://www.sjkingston.com/blog/service-menu-on-samsung-lcd-monitors](http://www.sjkingston.com/blog/service-menu-on-samsung-lcd-monitors)
Service menu on Samsung LCD monitors

A little-known feature in all Samsung LCD monitors (that is, the PC monitors) is the service menu. It displays lots of good information about the panel, such as its uptime, firmware revision, etc.

Getting it up is quite easy, if not a little fiddly depending on your monitor&#8217;s buttons (the 2243BW has touch-sensitive pads instead of actual buttons).

Bring up the normal OSD menu and set your brightness and contrast to 0 (don&#8217;t forget to remember your previous settings).
Once you have finished setting the contrast (do it last), press menu once to back out of the contrast setting.
Hold down the source button for approximately 5 seconds until a new red OSD pops up. This is the service menu.
Once you have finished in the service menu, simply switch the monitor off and on again to get rid of it. You will have to reset your brightness and contrast settings (you did remember them, right?).


Some people on the entec forum say hold down menu button after setting contrast and brightness to zero, that did not work on my samsung 216bw.

Make sure your monitor is connected using the cable to the bad port that has corrupted edid data.
Each port has its own unique edid data.

Then running powerstrip in windows, you select the monitor info adjustment, whatever. You go to bottom left drop down box and select write edid to monitor.
Powerstrip will prompt you several times and one of the prompts says to correct bad edid header. That is the one I used.
Typically the edid header is what gets corrupted for some reason.

So now it is working and nvidia shows it as a Samsung
It is detected in both linux and windows again.
Why the edid dvi port so easily corrupted, some were saying Nvidia  gfx cards can do this, dont know. Some say dont hot plug the monitors.

I came across lots of frustrated folks with corrupted edid data in google searches.
A utility for this eeprom writing corrected headers would be nice feature for linux.

adding more on using a customized edid
[http://analogbit.com/node/23](http://analogbit.com/node/23)

---

### Post by dannyboy79 on 2012-12-03
> **sdowney717 said:**
> I got it working!!
from here this guy had the right stuff
[http://forum.xbmc.org/showthread.php?tid=54685](http://forum.xbmc.org/showthread.php?tid=54685)


this xorg.conf gives me 1680 by 1050!
I used the command "cvt 1680 1050 60" to generate the modeline

these options were critical
Option "ExactModeTimingsDVI" "TRUE"
Option "ModeValidation" "NoEdidModes"
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 295.53  (buildmeister@swio-display-x86-rhel47-03.nvidia.com)  Sat May 12 00:17:08 PDT 2012

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
    Option "ExactModeTimingsDVI" "TRUE"
    Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option "ModeValidation" "NoEdidModes"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes "1680x1050"
    EndSubSection
EndSection
```

oddly, when I loaded up nvidia config screen, It shows a large number of available resolutions
why is that showing up??
which nvidia driver are you using for your 8400 gs? I have a PCIe 2.0 @16x coming from Newegg soon. I am running 10.04.4 with kernel 2.6.35-22 and am curious what driver i need to use and whether I should use VGA or HDMI, that's all my Olevia 23" TV has for inputs.

---


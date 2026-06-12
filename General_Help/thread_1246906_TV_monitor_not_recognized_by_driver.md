---
title: "TV monitor not recognized by driver?"
date: 2009-08-22
forum: General Help
---

### Post by thomash72 on 2009-08-22
I've just installed Ubuntu 9.04 on my new Asrock ION 330, mainly for using XBMC. But Ubuntu/Nvidia does not seem to recognize my TV when connected with VGA. My Panasonic PV-70 only support 1:1 pixel mapping on VGA (HDMI results in serious overscan). In NVIDIA control panel the screen is set to 'CRT-0 (CRT 0 on GPU 0)', and the screen resolution is set to 640x480. I have no options to change these settings in the NVIDIA monitor tool. The NVIDIA driver version is 185.18.36. Any proposals ? Thank you!

---

### Post by scouser73 on 2009-08-22
You need to use the nVidia Settings as root, enter this command **gksudo nvidia-settings** once you're happy, click **Apply** then click **Save to X Configuration File**

---

### Post by thomash72 on 2009-08-22
Thanks. I Tried this now. This commeand opened the Nvidia X Server settings, but in the 'X server Display configuration', I can not select any other Display model than 'CRT-0' - there are no other entries available in the pick-list, and the only resolution options available is 640x480, 320x240 and auto.

---

### Post by scouser73 on 2009-08-22
Did you click **Detect Display** at all?

---

### Post by thomash72 on 2009-08-22
Yes - whenever I click 'Detect Display' nothing happens. I can see the button being pressed, but nothing after that :(

---

### Post by messinwu on 2009-08-22
I believe Nvidia driver version 185.18.36 is faulty.  I had four monitors running just fine with 180.60 and decided to update to the latest, released just yesterday.  After the update, only 3 monitors will function.  No matter what I did to my xorg.conf settings, the fourth monitor will not display.  Using the same xorg.conf, I downgraded back to 180.60 and all four worked again.  

So, they either changed something in the driver to where more things need to be called in xorg or the driver is bad.  

This might be the cause of your issues.  Downgrade the driver and try that.  When I pushed the Detect Displays button, nothing happend just as you're describing.

---

### Post by thomash72 on 2009-08-26
Update: I downgraded my driver, but still not able to get the "Detect Display" button to work. So I'm stuck with 640x480 resolution.
I found this post [http://ubuntuforums.org/archive/index.php/t-996442.html](http://ubuntuforums.org/archive/index.php/t-996442.html) claiming that there is a shortcoming/bug in Ubuntu with regards to detecting displays when connecting monitors with VGA (I'm my case I'm connecting to a Panasonic TV). When the display is not detected, Ubuntu does not provide the user with options to set the resolution manually, or provide other display information which will help set the correct resolution. Can anyone of the experts comment on if this is most likely the source of my problems and maybe not the NVIDIA driver (I have now tried three different drivers:-/) Proposals on how to resolve are highly welcome (I'm a Linux newbie, so be gentle:-)
Thanks!

---

### Post by Turbofly on 2011-01-11
Did you ever resolve this? I'm having the same issues also with a Panasonic tv.

---

### Post by BicyclerBoy on 2011-01-11
Be aware that almost no new TVs will allow VGA at the panel native resolution.
They will not do 50Hz video modes over VGA. (no big deal for US)

If you do not have serious over-scan using VGA it is because the internal scaler is working.

The hdmi input & PC input mode is most likely be required to get direct pixel mapping/just scan.

---

### Post by Turbofly on 2011-01-12
I’m using the pc input on a Panasonic lcd projection tv. I’m also using the same video card as the OP, it’s a 6600 GT. Ubuntu finds the correct monitor on 2 of my other TV’s a 26” sanyo and a 32” Samsung, both of which are flat panel lcds through the pc input, And allows me to change the resolution. For some reason it just won’t detect the projection TV.

---

### Post by BicyclerBoy on 2011-01-12
Old TVs do not have EDID over VGA.
My VGA CRT does not report EDID.

Your projection TV could be in this group.

It is easy enough to config in xorg.conf to disable EDID mode validation & setup a require video mode.

---

### Post by Turbofly on 2011-01-12
This is the procedure I tried, it didn't work. Should this have been effective?


To successfully ignore EDID’s reported values to our xorg.conf do the following steps (you have to make sure that your graphics card can display 1024x768 resolution):

goto command line: CTRL ALT F1

turn off display manager:
/etc/init.d/gdm stop { Gnome is default in Ubuntu; in KDE must be kdm }
you can prefix it with sudo just in case you are not logged as root. better to log as root to make sure =)

back-up xorg.conf: { just in case you end up having black screen on X }
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

edit xorg.conf:
pico /etc/X11/xorg.conf { I prefer pico =) }

refer to the ff and modify xorg like so:

Section “Device”
Identifier “your graphics card model”
Driver “your graphics card driver”
BusID “PCI:1:0:0&#8243;
Option “IgnoreEDID” “true” < < put this line if this is missing
EndSection

Section "Screen"
Identifier "Default Screen"
Device "your graphics card model"
Monitor "your monitor"
DefaultDepth 24
:
: {go to Subsection 24 to change resolution}
:
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" << put this line replace old one
EndSubSection
EndSection

Save xorg.conf.

Restart display manager:
/etc/init.d/gdm start { or kdm }

Please note that when you try to use the command xresprobe “driver” , it will report the value that EDID reported and not the custom values you modified in xorg.conf.

---

### Post by BicyclerBoy on 2011-01-12
You need to find the supported videro modes by your TV.
It will most likely be the std video modes 480i60,576p50,720p60,1080i60.

I seriously doubt the TV will allow native resolution video modes.

If you want to try to stop mode validating against the EDID then :
edit /etc/X11/xorg.conf

Code:

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "ModeValidation" "NoEdidModes"
    Option         "ModeValidation" "AllowInterlacedModes"
    Option         "UseEDID" "FALSE"
    Option         "UseDisplayDevice" "CRT-0"
    Option "TVStandard" "HD1080i"
    SubSection     "Display"
        Depth       24
        Modes      "HD1080i"
    EndSubSection
EndSection

This assumes your TV is 1080i capable..
"HD720p" "HD1080i" are valid built-in TV video modes.
The Modes entry may not be usable.

The"CRT-0" may not match the wired ports of your video card, may need "CRT-1".
You may need to try these commands as well:
Option "IgnoreEDID" "True" # not used anymore ?
Option "ConnectedMonitor" "CRT-0" # not recommended as overwrite scan

---

### Post by Turbofly on 2011-01-17
Still no dice. Your code did manage to disable the EDID because it will no longer detects my other devices. However there is still only two choices for resolution. 640x480 and 320x???. I have another video card I can try that has HDMI out. Maybe I'll have better luck with that one.

---

### Post by Turbofly on 2011-01-17
On page 23 of my TV manual it show all usable resolutions. What would be the code to hard set one of them?


[http://service.us.panasonic.com/OPERMANPDF/PT52LCX66.PDF](http://service.us.panasonic.com/OPERMANPDF/PT52LCX66.PDF)

---


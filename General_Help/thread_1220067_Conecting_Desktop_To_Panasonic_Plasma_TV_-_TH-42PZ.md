---
title: "Conecting Desktop To Panasonic Plasma TV - TH-42PZ70B"
date: 2009-07-22
forum: General Help
---

### Post by Healey on 2009-07-22
Hi

I have tried to search for help on this problem, but I just cannot fix the following problem

I am trying to connect my desktop to my Panasonic TH-42PZ70B (Plasma TV) The problem is that I cannot get 1360x768 I can only get 1024x768 or lower.

The following may be of help

I am using jaunty
The Monitor is a Panasonic TH-42PZ70B (Plasma TV)
Graphics card is a Nvidia GEForce4 MX440 
I Dual boot with Windoze XP and when I am in XP I get a perfect 1360x768
Works fine on my LCD Viewsonic Monitor at 1400x900 in Ubuntu and XP

Here is my Xorg.conf which gives me 1024x768, but what I would like is 1360x768 which I can get in Windoze !



Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen" 0 0
InputDevice "Keyboard0" "CoreKeyboard"
InputDevice "Mouse0" "CorePointer"
EndSection

Section "Module"
Load "glx"
EndSection

Section "InputDevice"

# generated from default
Identifier "Keyboard0"
Driver "keyboard"
EndSection

Section "InputDevice"

# generated from default
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/psaux"
Option "Emulate3Buttons" "no"
Option "ZAxisMapping" "4 5"
EndSection

Section "Monitor"

# Custom modes
Identifier "Configured Monitor"
HorizSync 31.0 - 69.0
VertRefresh 59.0 - 86.0
ModeLine "1920x1080" 148.5 1920 1980 2028 2200 1080 1084 1089 1125
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
EndSection

Section "Screen"

## Modes "1920x1080"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
DefaultDepth 24
Option "PreferredMode" "1360x768"
Option "AddARGBGLXVisuals" "True"
Option "NoLogo" "True"
SubSection "Display"
Depth 24
Modes "nvidia-auto-select"
EndSubSection
EndSection



I have tried using the nvidia X server settings gui which shows the 1360x768 that I want, but it looks wrong and it will not keep the settings on the next boot

Any one help please

Thanks

Healey

---

### Post by Healey on 2009-07-23
Hi
OK - No Replies - No Problem

In case anyone else has a similar problem here is a crude solution based heavily on this site

[http://www.mythtv.org/wiki/Modeline_Database#Panasonic](http://www.mythtv.org/wiki/Modeline_Database#Panasonic)

I have highlighted in red the changes from my last xorg

My xorg.conf  now looks like this :

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
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

Section "Monitor"

	# Custom modes
    Identifier     "Configured Monitor"
    HorizSync       31.0 - 69.0
    VertRefresh     59.0 - 86.0
##    ModeLine       "1920x1080" 148.5 1920 1980 2028 2200 1080 1084 1089 1125
    [COLOR="Red"]Modeline "1366x768" 85.500 1360 1440 1552 1792 768 771 777 795 +hsync +vsync[/COLOR]

EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    [COLOR="Red"]Option       "ModeValidation" "NoDFPNativeResolutionCheck"[/COLOR]

EndSection

Section "Screen"

##	Modes "1920x1080"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
##    Option         "PreferredMode" "1360x768"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
[COLOR="Red"]##        Modes      "nvidia-auto-select"[/COLOR]
	[COLOR="Red"]Modes      "1366x768"[/COLOR]
    EndSubSection
EndSection


I now have 1360x768 - I wont mark this as solved, as it still needs more work - but I am pleased anyway

Hope it helps someone

Healey

---


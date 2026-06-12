---
title: "Resolution/Graphics Driver Problem... Nothing that I'm trying is working (ARGH!!)"
date: 2010-02-08
forum: General Help
---

### Post by CloudArchitect on 2010-02-08
I've been loitering over my resolution and nvidia xserver settings for about 2 days now, fiddling with xorg.conf and breaking ubuntu in the process trying to get my resolution at it's native settings. I've searched through many forums and none of them have solved my problem. Its maximum resolution is 1360x768, which isn't enough. It should be 1440x900. I have tried adding custom modes to the xorg.conf file and it wouldn't work. I don't know what's going on. 

Also here is my xorg.conf since I saved the nvidia settings to it...

> 
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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
    Identifier     "Configured Monitor"
    VendorName     "Hanon"
    ModelName      "hanon H-341wdb"
    HorizSync       50.0 - 70.0
    VertRefresh     50.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1152x864 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSectionThankyou all in advance :)!!!

---

### Post by Johnny B on 2010-02-08
I think the most important part is the horizsync and vertrefresh
lookup the correct settings for your monitor.

heres part of mine:
> Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer AL1917W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
	# HorizSync source: edid, VertRefresh source: edid
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection

Section "Screen"



---

### Post by CloudArchitect on 2010-02-09
I saved the nvidia driver details to my xorg.conf (I did make a backup) ... It showed the horizSync and VRefreshes.. Is there anything in this which is making it impossible for my monitor to display natively. I'll edit the new one on the original post too

> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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
    Identifier     "Configured Monitor"
    VendorName     "Hanon"
    ModelName      "hanon H-341wdb"
    HorizSync       50.0 - 70.0
    VertRefresh     50.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1152x864 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by 23dornot23d on 2010-02-09
Is this the only monitor you use > [http://en.kioskea.net/guide/details/1174818-hanton-h-341wdb-black](http://en.kioskea.net/guide/details/1174818-hanton-h-341wdb-black)

Yours  (Hanon ? or Hanton)

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Hanon"
    ModelName      "hanon H-341wdb"
    HorizSync       50.0 - 70.0
    VertRefresh     50.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection



**The existing xorg.conf .... file looks wrong** ....... 

have removed my suggestion but this line looks to be wrong .... [COLOR=Blue]Option         "metamodes" "1152x864 +0+0" 

[/COLOR]If the required size is to be  .... 1440x900
[COLOR=Blue] 
[/COLOR]

---

### Post by stoneage on 2010-02-09
Check the manufacturer's specification for the Horizsync and Vertrefresh rates, it doesn't look right......(I could be wrong)

You could also (if you haven't already) try generating a modeline with xrandr, in conjunction with the manufacturer's specifications.

---

### Post by 23dornot23d on 2010-02-09
I just found this   [http://en.kioskea.net/guide/details/1174818-hanton-h-341wdb-black](http://en.kioskea.net/guide/details/1174818-hanton-h-341wdb-black)

NameHanton H-341WDB BlackDescriptionFlat-panel (TFT), 19 inch, 
max resolution 1440x900 pixels, 
built-in speakers: Yes, 5.3 kg
Monitor TypePC MonitorScreen typeFlat-panel 
(TFT)Screen size19.0 InchWidescreenYes
Touch ScreenNoDot pitch0.285 mmMaximum resolution1440x900 pixels pixels

Frequency at max. resolution Hz

Horizontal frequency30-80 kHz kHzVertical frequency56-75 Hz HzColor depth16.2 million

These are just taken from the above link ...... check they are right with your manufacturers booklet

---

### Post by CloudArchitect on 2010-02-09
23Dornot23d -- Nothing happened when I changed metamode I'm afraid, thankyou for your help though man :)
Edit: Woah I just saw the edit you did, I'll change the frequencies now :P!

And stoneage -- I'm just working out how to do that now. I'll tell you how that went when I'm done, thanks man :)

---

### Post by 23dornot23d on 2010-02-09
( I would personally not edit the frequencies .....  )

What version of Ubuntu do you run ..... > ?

What graphics card do you have ? ( is it the GeForce 6200 as stated in the xorg.conf file )

VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"

just checking here .....

you obviously managed to get it working .... but if it was my system ....

I would Go into .........

System >>> Administration >>> Nvidia Display Settings ...... 9.10
or
(System >>> Preferences >>> Nvidia Display Settings) ...... older systems

let me know if you can you get this ..... ?  ( its a good place to start )

and could you please do a screenshot ........ showing what you have ,,,,, on your screen ,,,,

[COLOR=Lime]*( sorry about all the editing just trying to find the simple way of doing this ...... as the original xorg.conf seems to be wrong )*[/COLOR]

if  ......... Nvidia Display Settings is not in the Menu Bar at the top  ..... go into a terminal and do

sudo apt-get update

sudo apt-get install nvidia-settings

sudo nvidia-settings

within this application ...... you can re-create a new xorg.conf file

[IMG]http://i45.tinypic.com/68yeyg.jpg[/IMG]


[COLOR=Blue]It should look something like the above ...... if you want 1440 x 900
so this line in the config is not going to give you the above sizes .....
Option         "metamodes" "1152x864 +0+0"
[/COLOR]  
Using save to X-configuration .... ( you can save a copy to your Desktop just to have a look at the file too - to ensure it looks right )
  ........ if you run it from sudo it merges the info with the current one ....... no manual editing necessary hopefully

I will look on my own dual display .... and see what the output is ...... later on .......
(but I set mine up on a 32" Orion Tv and a Phillips 17" Monitor) 
so its going to be slightly different .....

[IMG]http://i49.tinypic.com/2iiziiq.jpg[/IMG]


[http://i48.tinypic.com/23r0fah.jpg](http://i48.tinypic.com/23r0fah.jpg)

I find more info is better than none ..... and to keep trying ..... be careful with frequencies though ..... 
the newer monitor may be protected but ......
(from what I have read you can fry older monitors if you get it wrong ........)

[B]Hope this might be of some help .... 

Interesting Read .... [/B][http://www.x.org/wiki/Projects/XRandR](http://www.x.org/wiki/Projects/XRandR)[B]  ..... links to other articles too ....

For version of xrandr running on your system ..... Link to commands ... [/B][http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)
[B] $ xrandr -v

Query screens available ,,,
$ xrandr -q
[/B]

---

### Post by CloudArchitect on 2010-02-09
Hey 23Dornot23d, I really have no idea what happened, but when I logged back onto ubuntu after coming back from college (this is why i took so long to reply back, I'm sorry), I have about 10 + different resolutions including my native one!!??! :guitar::popcorn:

I'm going to find out why this happened if I can... I'll post xorg.conf since I changed it so that if anyone has this problem then if they find this thread on google or something then they'll be able to solve it easier than I did :D

Thankyou dornot for your help :)! And thanks to Johnnyb and Stoneage too :)!

Right, in the save to X configuration file, I copied the text... So here's my new xorg.conf now that it works! 

> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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
    Identifier     "Configured Monitor"
    VendorName     "Hanon"
    ModelName      "hanon H-341wdb"
    HorizSync       50.0 - 70.0
    VertRefresh     50.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 80.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
# Removed Option "metamodes" "1152x864 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1440x900 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


If any of you know what I've done to the computer from that I'd be very grateful to know as for future references and stuff :)

---

### Post by 23dornot23d on 2010-02-09
Its just commented out the bad line and replaced it ...
The hash sign means it ignores that line when running .....

# Removed Option "metamodes" "1152x864 +0+0"

and replaced with 

Option         "metamodes" "1440x900 +0+0"


as far as I can see ... it has not done anything else ...

The computer probably just needed to be re booted to read in the new file ....
I think (ctrl + alt + backspace) does the same thing ..... it reloads the X screen drivers

Good to see it worked ..... mark it as Solved if you would please

---


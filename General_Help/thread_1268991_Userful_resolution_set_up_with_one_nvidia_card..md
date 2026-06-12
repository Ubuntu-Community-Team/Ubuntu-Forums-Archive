---
title: "Userful resolution set up with one nvidia card."
date: 2009-09-17
forum: General Help
---

### Post by branislavski on 2009-09-17
Hi, 
i would like to set up multi-seat using userful but the resolution is just not working for me. i have the following configuration:
Make: HP pavilion dv9700 
OS: Ubuntu 9.04
Bios: PhoenixBIOS 4.0 release 6.1
Processor: AMD turion 64 X2 TL-64 (2 CPUs) 2.2Ghz
Memory: 3006 RAm
DirctX version: DirectX 10
Graphics Card: GeForce 7150M / nforce 630m

This is my usual resolution when using windows dualview:
Primary laptop screen:  1440x900
Secondary: Sony TV 1360x768 (Connected via RGB)

I would like to run two stations using multiplier, but keep the resolution using one (not two)  mentioned nvidia card.
Any ideas??

---

### Post by branislavski on 2009-09-18
Bump... Anyone?

---

### Post by gordintoronto on 2009-09-18
Your graphics card is not on the list of supported cards for Userful Multiplier.

Are you using the nVidia propietary driver?

It's not clear to me what you are getting versus what you want.

---

### Post by branislavski on 2009-09-18
Its not on the list but im using it effectively, the only issue is the resolution on both my screens is bad and i cant start any of the usual ways to edit it. Nvidia x server settings make my machine log out and the display setting says "randr extension not found".
I would like to know if there is some internal settings or way that i can set it manually while using multiplier. 
again when im not running multiplier resolution is perfect on both screens.
All i need is to setup multi-seat properly.

---

### Post by gordintoronto on 2009-09-19
Does the Multiplier site have forums?  [smile]

---

### Post by opentechgirl on 2009-09-20
try downloading the new beta version of Multiplier, 325, as it has increased support for Nvidia cards.  

Also, i noted that the resolution that you are currently running is higher than the supported resolutions listed by Userful

[INDENT]"The first time Userful Multiplier starts, a text mode configuration tool enables you to set screen resolutions. If you need to change the screen resolutions at a later time, delete the /etc/X11/userful.Mxorg.conf file and restart X. The text mode configuration tool will once again activate, enabling you to set a new screen resolution, and create a new userful.Mxorg.conf file. Userful Multiplier supports resolutions of 640x480, 800x600, 1024x768 and 1280x1024."

[/INDENT]You could try to modify the Mxorg.conf file manually.

If you plan to use only one video card, also note that Userful currently only supports VGA or DVI outputs (not HDMI or DVI-D though)

---

### Post by xiaolin99 on 2009-09-21
You have to manually edit multiplier's X config file (/etc/X11/userful.Mxorg.conf)
Go the the "Screen Section" and change resolution for each station to whatever you want.

Example (note the default Depth is 16, reboot after edit)
###################### 
# Screen Section 
###################### 
Section "Screen" 
    Identifier "Screen0" 
    Device "Videocard0" 
  Monitor "Monitor0 
  Option  "ExactModeTimingsDVI"   "TRUE" 
    DefaultDepth 16 
    SubSection "Display" 
        Depth 8 
        Modes "1440x900" 
    EndSubSection 
    SubSection "Display" 
        Depth 15 
        Modes "1440x900" 
    EndSubSection 
    SubSection "Display" 
        Depth 16 
        Modes "1440x900" 
    EndSubSection 
    SubSection "Display" 
        Depth 24 
        Modes "1440x900" 
    EndSubSection 
EndSection 

Section "Screen" 
    Identifier "Screen1" 
    Device "Videocard1" 
  Monitor "Monitor1 
  Option  "ExactModeTimingsDVI"   "TRUE" 
    DefaultDepth 16 
    SubSection "Display" 
        Depth 8 
        Modes "1440x900" 
    EndSubSection 
    SubSection "Display" 
        Depth 15 
        Modes "1440x900" 
    EndSubSection 
    SubSection "Display" 
        Depth 16 
        Modes "1440x900" 
    EndSubSection 
    SubSection "Display" 
        Depth 24 
        Modes "1440x900" 
    EndSubSection 
EndSection

---

### Post by branislavski on 2009-09-21
Doesnt that mean that im supposed to have two graohic cards?
It has videocard0 and videocard1 in the code?

---

### Post by ignisuti on 2010-03-13
I'm having a similar problem. I was able to set the resolution to 800x600 (not ideal, but at least I know my HDTV will display it. So, it's my starting point). 

My problem is that the VGA output to the TV continues to shift across the screen. Not sure if this is a vsync issue or what it'd be called. My guess is that the HorizSync and VertRefresh values in my userful.Mxorg.conf file need adjust, but to what?

---


---
title: "xorg.config File Help"
date: 2009-12-03
forum: General Help
---

### Post by black28 on 2009-12-03
hey guys, im still working on my screen resolution. i've searched lots and lots. and just wondering if anyone could run me through the xorg.config file. i'm completely lost! i found another thread that i wanted to try here

[http://ubuntuforums.org/showthread.php?t=806835&highlight=manual+TRident+Ubuntu+Install&page=2](http://ubuntuforums.org/showthread.php?t=806835&highlight=manual+TRident+Ubuntu+Install&page=2)

but i don't know how to edit or anything. can anyone help with this? thanks.

p.s. i have a Trident Microsystems Cyberblade i1

---

### Post by akakingess on 2009-12-03
> **black28 said:**
> hey guys, im still working on my screen resolution. i've searched lots and lots. and just wondering if anyone could run me through the xorg.config file. i'm completely lost! i found another thread that i wanted to try here

[http://ubuntuforums.org/showthread.php?t=806835&highlight=manual+TRident+Ubuntu+Install&page=2](http://ubuntuforums.org/showthread.php?t=806835&highlight=manual+TRident+Ubuntu+Install&page=2)

but i don't know how to edit or anything. can anyone help with this? thanks.

Before editing the current version, have you tried renaming the current one by copying it as xorg.config.backup or something of that nature and then trashing the original and seeing if it will "rebuild" itself anew and if the screen res problem goes away or at least you have a relatively "clean" version of the config to start testing with. And obviously, you can always just bring the old one back since it will be there, just with .backup added to the end. There's one place to start unless you have tried all of that already.

Apologies: You can disregard all I stated as I didn't even notice or read the other thread, so I was probably just rehashing old news, sorry about that..

---

### Post by plusnplus on 2009-12-03
I also looking for this one.
Anyone have simple example xorg.conf file?
Basicly i only want have some resolution option, beside the default one (800 x 600)

---

### Post by black28 on 2009-12-03
exactly! lol. i don't like how big 800x600 looks on my flat screen. it makes everything so big. really wanna tackle this but completely lost!

---

### Post by akakingess on 2009-12-03
Give me a sec and I will post my xorg.conf if it will help y'all any (yes, I am a Texan, can you tell by the y'all?), but I am searching for it right now and don't have beagle installed on this machine yet, so give me a sec.

Don't think mine is going to help (I'm in the middle of turning this machine into the server for the house, but here is what I've got so far:

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "extmod"
    Load  "dri"
    Load  "record"
    Load  "dbe"
    Load  "dri2"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    #DisplaySize      330   240    # mm
    Identifier   "Monitor0"
    VendorName   "GWY"
    ModelName    "Gateway EV700"
    HorizSync    30.0 - 70.0
    VertRefresh  50.0 - 120.0
    Option        "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
        #Option     "DefaultTVDACAdj"        # [<bool>]
        #Option     "Int10"                  # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "ATOMTVOut"              # [<bool>]
        #Option     "R4xxATOM"               # [<bool>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "DynamicPM"              # [<bool>]
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "Radeon X1650 Pro"
    BusID       "PCI:2:0:0"
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

```
Let me also keep searching, cuz I know I've got this somewhere, sorry about the confusion, but I'm only up attending to a sick child, so I am also a little distracted.

---

### Post by black28 on 2009-12-03
that would be great. my desktop has a Trident Microsystems Cyberblade a1 Video Card, and please explain what to do with that file and everything as good as u can please.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **plusnplus said:**
> 
Anyone have simple example xorg.conf file?


A xorg.conf file reflects the specific hardware of the computer. A different monitor or GPU creates a different xorg.conf file. It is unique to a single computer as defined by the hardware.

---

### Post by akakingess on 2009-12-03
> **black28 said:**
> that would be great. my desktop has a Trident Microsystems Cyberblade a1 Video Card, and please explain what to do with that file and everything as good as u can please.

Well, the only relevant section should be 
```
   Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
        #Option     "DefaultTVDACAdj"        # [<bool>]
        #Option     "Int10"                  # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "ATOMTVOut"              # [<bool>]
        #Option     "R4xxATOM"               # [<bool>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "DynamicPM"              # [<bool>]
        Identifier  "Card0"
        Driver      "radeon"
        VendorName  "ATI Technologies Inc"
        BoardName   "Radeon X1650 Pro"
        BusID       "PCI:2:0:0"
```However, the monitor is also what it can look at to determine resolution possibilities if I'm not mistaken (again, very tired and distracted at this point), and that would be these:
```
Section "Monitor"
    #DisplaySize      330   240    # mm
    Identifier   "Monitor0"
    VendorName   "GWY"
    ModelName    "Gateway EV700"
    HorizSync    30.0 - 70.0
    VertRefresh  50.0 - 120.0
    Option        "DPMS"
```But, I don't know if this will help with your particular situation. This would take some sleep and searching for me to get you a better answer, if I don't return soon, I will definitely return by tomorrow lunchtime, maybe see what you can do with what I've given you until then.

---

### Post by akakingess on 2009-12-03
Also, did you check out this [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) , just trying to get you all the info I can before I am no longer of any use to anyone ;)

The main gist I got from that link was installing the "resolution switcher" software, which is available under Applications>Ubuntu Software Center.  That would be my recommendation for both of you. An easy way to switch resolutions without messing with the xorg.conf if it works for you.

---

### Post by plusnplus on 2009-12-03
> **u.b.u.n.t.u said:**
> A xorg.conf file reflects the specific hardware of the computer. A different monitor or GPU creates a different xorg.conf file. It is unique to a single computer as defined by the hardware.

here is my xorg.conf file:
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

how i can change it to have multiple screen resolution option?
Thanks for any info

---

### Post by akakingess on 2009-12-03
See, there's the rub, like I stated in a previous post, if you are running 9.10 Karmic Koala, then I would just install Resolution Switcher from the Ubuntu Software Center which is in the Applications menu. That will put a little tray icon up there on your top bar and from there you can select different resolutions. Like I also stated earlier, I might have better solutions for you at some point tomorrow after my child stops "getting sick all over the place" and I have had some rest  (at least a couple of hours).

By the way, if you install that and somehow mess something up, all you have to do is delete the file ~/.config/monitors.xml

---

### Post by u.b.u.n.t.u on 2009-12-03
> **plusnplus said:**
> 
how i can change it to have multiple screen resolution option?
Thanks for any info

What is your GPU?

I do not use an xorg.conf file because it won't work. The terminal commands will not create one correctly and the ATI 9.11 drivers freeze Ubuntu 9.10 at boot. I am waiting for ATI to release the next drivers, 9.12, hopefully this month.

I therefore use the default VESA driver and it gives the correct screen resolution and color depth.

Have you booted without an xorg.conf file, and if so, what was the result?

I cannot determine your monitor resolutions.

If you look at my signature you will see two brainstorm ideas I have submitted. One calls for a GUI interface for creating a xorg.conf file. If you think that is a good idea, I welcome you to leave a comment to that effect.

---

### Post by black28 on 2009-12-03
thanks, but i don't even know what and how to do with the files you posted. where and how am i suppose to edit those on mine?

---

### Post by akakingess on 2009-12-03
> **black28 said:**
> thanks, but i don't even know what and how to do with the files you posted. where and how am i suppose to edit those on mine?
What version of Ubuntu are you using? If 9.10, then go to the Applications menu, and then choose Ubuntu Software Center, in there do a search for Resolution Switcher and install that. It will install a little tray icon in the upper right-hand corner (usually), click on that and there should be all of your available resolutions. If you are using an older version of Ubuntu, we'll try something different. If you are on 9.10, you shouldn't need your xorg.conf file, unless Ubuntu is not reading your hardware (graphics card and monitor) correctly.

By The Way: The tray icon looks like a little monitor with a little yellow scale(triangle) over part of it.

---

### Post by black28 on 2009-12-03
i actually have that already. when i was trying to fix it before i posted... that is the problem. it's not reading my Trident Microsystems Cyberblade Video Card. when i go to drivers it doesnt catch it. need to know how to install or put in vesa and the Trident Generic driver for it to read right to make the adjustments.

---

### Post by black28 on 2009-12-03
can anyone explain the whole process thoroughly please? i'd really like to get this fixed and also to learn it....

also, how can i install the flash plugin for youtube on firefox? thanks guys.

---

### Post by hobo14 on 2009-12-03
I'm looking for more info on fixing my xorg.conf file too, but here is some useful info I've learnt so far.

This post is for 9.10

To change resolutions (to ones other than the ones you can see in System > Preferences > Display), an example to change to 1440x800 in 4 steps:

1.
```
cvt 1440 800
```
This doesn't do anything, you just need the output which will be something like: *Modeline [COLOR="Green"]"1440x800_60.00"   94.00  1440 1520 1664 1888  800 803 813 831 -hsync +vsync[/COLOR]*

You will use that line of output, except the "Modeline" as part of the next command.

2.
```
xrandr --newmode [COLOR="Green"]"1440x800_60.00"   94.00  1440 1520 1664 1888  800 803 813 831 -hsync +vsync[/COLOR]
```
Note how the output from step 1 is used in step 2.

3.
```
xrandr --addmode VGA1 [COLOR="Green"]1440x800_60.00[/COLOR]
```

4.
```
xrandr --output VGA1 --mode [COLOR="Green"]1440x800_60.00[/COLOR] [COLOR="Blue"]--output LVDS1 --off[/COLOR]
```
Note for this last step, the second half of the command ("[COLOR="Blue"]--output LVDS1 --off[/COLOR]") is just to turn my laptop screen off (I use a monitor plugged into a laptop), if you aren't using a laptop, cut that half of the command out.

That will change the resolution to 1440x800, even though I can't change to that resolution through the GUI.

Substitute your desired resolution for 1440x800.

**NOTE: This does not change the resolution permanently!**  That is what I'm trying to find out how to do now.

If you set your screen to a resolution that's all messed up, just R-Alt+PrScreen+K back to login.

If xrandr says it can't find VGA1, it must be named something else. Type just "xrandr" and find the name on the line above the list of resolutions.
Eg. my monitor is VGA1:
[I]Screen 0: minimum 320 x 200, current 1152 x 864, maximum 4096 x 4096
**VGA1** connected 1152x864+0+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080      60.0 +
   1280x1024      75.0  
   1152x864       75.0* 
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1 [/I]

---

### Post by u.b.u.n.t.u on 2009-12-03
Trying to manually configure xorg would be like trying to disarm a bomb, with both hands tied behind ones back, and using only ones teeth.

If managed however, one passes the "test" to become a developer!

---

### Post by black28 on 2009-12-03
okay, so i tried it out and this is what i got... i was goin for 1024x768...

it fully has the user name and desktop and everything. i just didnt cut those out from the terminal...

> ~$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  18
  Current serial number in output stream:  18
:~$ xrandr --addmode default 1024x768_60.00
:~$ xrandr --output default --mode 1024x768_60.00
xrandr: screen cannot be larger than 800x600 (desired size 1024x768)mine didnt have VGA1 it said "defaut connected" so i subbed the VGA1 with default. any suggestions? hopefully someone can explain the whole xrog file configuration. would really like to get this gong!

---

### Post by hobo14 on 2009-12-03
> **black28 said:**
> okay, so i tried it out and this is what i got... i was goin for 1024x768...

it fully has the user name and desktop and everything. i just didnt cut those out from the terminal...

mine didnt have VGA1 it said "defaut connected" so i subbed the VGA1 with default. any suggestions? hopefully someone can explain the whole xrog file configuration. would really like to get this gong!

I think you have a different problem to mine. Maybe this thread or the links in it will help: [http://ubuntuforums.org/showthread.php?t=1318677]("http://ubuntuforums.org/showthread.php?t=1318677")

---

### Post by black28 on 2009-12-03
yah, that's kinda what i was looking for. reading through it  now. thanks! if its all applied through (Terminal) it'll be all good. its the whole Configuring of Xorg file that gets me. i don't have a clue on anything. can anyone assist with that?

---

### Post by black28 on 2009-12-03
does anyone know how to make this?  | <- i need it but can't copy paste in my situation

---

### Post by u.b.u.n.t.u on 2009-12-03
| that one?

It is above the "Enter" button.

It requires shift to be pressed.


||||||||||||||||||||||||||||||||

---

### Post by black28 on 2009-12-03
lol... | okay there we go. nah when i was tryna get it in shell mode it kinda looked like a stretched out : like what it looks like on the keyboard. thanks.

---


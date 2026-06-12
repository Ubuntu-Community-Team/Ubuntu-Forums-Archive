---
title: "Wrong resolution in Karmic, no xorg.conf file"
date: 2009-12-16
forum: General Help
---

### Post by jmpmjmpm on 2009-12-16
hi

my resolution is wrong in karmic, it cant detect my monitor so I cant get the option for 1440x900. I looked for the xorg.conf file, but there isn't one... can anyone help? I looked around the web but only found what seemed to be out of date info

graphics card is ati radeon x1550 (old card), no proprietary drivers are offered either...

---

### Post by Chesamo on 2009-12-16
You won't find xorg.conf anymore because it's been depricated. However, you can create one if you need to override any of the automatic settings. Try running xorgconfig.

---

### Post by Dark_Stang on 2009-12-16
If you go System > Preferences > Display. Can you fix it there?

---

### Post by jmpmjmpm on 2009-12-16
chesamo - i get command not found when trying to run xorgconfig

dark_stang - tried that but the correct resolution is not listed. 

this is strange because I'm sure it worked fine in 8.04

thanks for the replies guys, any other ideas?

---

### Post by ST3ALTHPSYCH0 on 2009-12-16
If you don't want to manually configure you could try the link in my sig.

---

### Post by jmpmjmpm on 2009-12-16
thanks, I will try that one now

---

### Post by jmpmjmpm on 2009-12-16
fixed it, got xorg to make a new xorg.conf file with 

sudo service gdm stop

sudo Xorg -configure

which created a xorg.conf.new file in my home folder. I moved this to /etc/X11/ and renamed it xorg.conf
then I edited it with sudo nano /etc/X11/xorg.conf

and added the line 

Modes    "1440x900"

as shown below

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
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes		"1440x900"

	EndSubSection

thanks for your help guys

---

### Post by khelben1979 on 2009-12-16
Try
```
sudo xorg -configure
```

---

### Post by kikazaru on 2009-12-16
I made an xorg.conf file and saved it in /etc/X11 but it seems to have no effect at all. It's attached below. I made it using Xorg -configure and added the Modes entries by hand.

I need to use a projector, and it seems that it's resolutions cannot be detected automatically. If I plug in a monitor, the options for its resolutions appear in the System->Preferences->Display window and I can set a reasonable resolution, and switch the VGA cable back to the projector. But I don't want to do this every time I turn on the computer...

When I boot up with the projector I just get the really low res modes. If I do "sudo service gdm stop" "sudo service gdm start" with the monitor plugged it, I get a really high resolution log in screen, then when I reach the gnome desktop the resolution switches again to an intermediate resolution.

It seems that the xorg.conf file is not having any effect. I want to override the automatic detection that seems to be occurring... 

Any suggestions !?



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
        Load  "dri2"
        Load  "glx"
        Load  "dbe"
        Load  "record"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                   # [<bool>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "ColorKey"                  # <i>
        #Option     "CacheLines"                # <i>
        #Option     "Dac6Bit"                   # [<bool>]
        #Option     "DRI"                       # [<bool>]
        #Option     "NoDDC"                     # [<bool>]
        #Option     "ShowCache"                 # [<bool>]
        #Option     "XvMCSurfaces"              # <i>
        #Option     "PageFlip"                  # [<bool>]
        Identifier  "Card0"
        Driver      "intel"
        VendorName  "Intel Corporation"
        BoardName   "82G33/G31 Express Integrated Graphics Controller"
        BusID       "PCI:0:2:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth  24
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
#               Modes "1440x1024"
#               Modes "1440x900"
#               Modes "1280x1024"
                Modes "1280x768"
                Modes "1280x720"
                Modes "1152x864"
                Modes "1024x768"
                Modes "800x600"
                Modes "720x480"
                Modes "640x480"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
#               Modes "1440x1024"
#               Modes "1440x900"
#               Modes "1280x1024"
                Modes "1280x768"
                Modes "1280x720"
                Modes "1152x864"
                Modes "1024x768"
                Modes "800x600"
                Modes "720x480"
                Modes "640x480"
        EndSubSection
EndSection

```

---

### Post by smilingfrog on 2009-12-17
> **kikazaru said:**
>  I get a really high resolution log in screen, then when I reach the gnome desktop the resolution switches again to an intermediate resolution.

It seems that the xorg.conf file is not having any effect. I want to override the automatic detection that seems to be occurring... 

Any suggestions !?


There is a file called ~/.config/montiors.xml that is sometimes created, and can wreak havoc with your resolution. It seems to override xorg.conf. If monitors.xml is there, delete it, and then ctrl-alt-backspace.

---

### Post by itang sanjana on 2009-12-17
> **kikazaru said:**
> I made an xorg.conf file and saved it in /etc/X11 but it seems to have no effect at all ..

```

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        [COLOR="Red"]Modeline "1440x1024_60.00"  122.25  1440 1528 1680 1920 1024 1027 1037 1063 -hsync +vsync[/COLOR]
EndSection

```

Beside smilingfrog suggestion, also put your desired modeline under the Section "Monitor". Use cvt to configure this modline and copy/paste only this modeline (colored red) e.g.

```
$ cvt 1440 1024
# 1440x1024 59.90 Hz (CVT) hsync: 63.67 kHz; pclk: 122.25 MHz
[COLOR="Red"]Modeline "1440x1024_60.00"  122.25  1440 1528 1680 1920 1024 1027 1037 1063 -hsync +vsync[/COLOR]
```

Go to System > Preferences > Display and it should be there i.e 1440x1024.

Note: The example above is under my hardware spec, so don't use it. Generate your own cvt instead :D

HTH

---

### Post by aboud on 2009-12-29
looks like there is no way I am going to solve this low res problem .

with no xorg.conf on karmic and after creating one with Xorg -configure and many tries to put Modes "1024x768" and Modeline generated with cvt non worked, when tested it just give black screen, .. without driver i had 800x600 .. but after successfully  installing it in may ways i can't have more than 640x480, if I tell the binary driver to auto config setting screen return 'input not supported' 

my karmic don't have any /.config/monitor.xml

---

### Post by john newbuntu on 2009-12-29
In Karmic, you use xranr to adjust display properties. Xorg.conf is not used by the display system.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by aboud on 2009-12-29
> **john newbuntu said:**
> In Karmic, you use xranr to adjust display properties. Xorg.conf is not used by the display system.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

I didn't spare this too ..,  xrandr can't add res bigger than the max it has , after adding new mode with cvt and xrandr --newmode , xrandr --addmode .. if you try to apply the new mode it will post a failure message.

---

### Post by jmpmjmpm on 2009-12-30
> **john newbuntu said:**
> In Karmic, you use xranr to adjust display properties. Xorg.conf is not used by the display system.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

strange, my xorg.conf is...

---


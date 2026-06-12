---
title: "Does Anyone Have this info?"
date: 2009-12-05
forum: General Help
---

### Post by black28 on 2009-12-05
hey guys, i'm trying to tweak my Xorg.conf file, I have a Trident Microsystems Cyberblade/i1 Video Card. and use the Samsung 906bw 19" Flat screen monitor. looking for the xorg.conf edits to make these compatible to go to higher resolutions. in my current file it looks like this...

[CODESection "ServerLayout"
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
    Load  "dbe"
    Load  "record"
    Load  "glx"
    Load  "dri"
    Load  "dri2"
    Load  "extmod"
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
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "AccelMethod"            # [<str>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "PciRetry"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "SetMClk"                # <freq>
        #Option     "MUXThreshold"           # <i>
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "NoMMIO"                 # [<bool>]
        #Option     "NoPciBurst"             # [<bool>]
        #Option     "MMIOonly"               # [<bool>]
        #Option     "CyberShadow"            # [<bool>]
        #Option     "CyberStretch"           # [<bool>]
        #Option     "XvHsync"                # <i>
        #Option     "XvVsync"                # <i>
        #Option     "XvBskew"                # <i>
        #Option     "XvRskew"                # <i>
        #Option     "FpDelay"                # <i>
        #Option     "Display1400"            # [<bool>]
        #Option     "Display"                # [<str>]
        #Option     "GammaBrightness"        # [<str>]
        #Option     "TVChipset"              # [<str>]
        #Option     "TVSignal"               # <i>
    Identifier  "Card0"
    Driver      "trident"
    VendorName  "Trident Microsystems"
    BoardName   "CyberBlade/i1"
    BusID       "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier "Monitor0"
    VendorName "Monitor Vendor"
    ModelName "Monitor Model"
    HorizSync 31.5 - 50
    VertRefresh 50-110
EndSection
Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Depth        1
        Viewport 0 0
        Modes      "800x600"
    EndSubSection
    SubSection "Display"
        Depth        4
        Viewport 0 0
        Modes      "800x600"
    EndSubSection
    SubSection "Display"
        Depth        8
        Viewport 0 0
        Modes      "800x600"
    EndSubSection
    SubSection "Display"
        Depth        16
        Viewport 0 0
        Modes      "800x600"
    EndSubSection
    SubSection "Display"
        Depth        24
        Viewport 0 0
        Modes      "800x600"
    EndSubSection
EndSection
][/code]

i've tried editing the 800x600 to 1440x900 but nothing happens. also don't know the"monitor", "screen", "device" and all that stuff for my hardware. don't really know what to look for. maybe someone could edit this and re-post it for me to try? all help is appreciated.

---

### Post by black28 on 2009-12-05
anyone know where i can get the info for my hardware?

---

### Post by black28 on 2009-12-05
no one knows what to do?

---

### Post by fluxbuntu on 2009-12-05
This thread may help you.

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by wojox on 2009-12-05
Hardware info:

```
sudo lshw -html > ~/hardware.html
```

Try this for configuring your card:

[http://ubuntuforums.org/showthread.php?t=763964&highlight=Trident+Microsystems](http://ubuntuforums.org/showthread.php?t=763964&highlight=Trident+Microsystems)

---

### Post by audiomick on 2009-12-05
I can't tell you what to edit it to, because the last time I had to do stuff in this direction was about 3 years ago.
If you haven't already, look at
```
man xorg.conf
```

it is a lot of stuff, but it helped me understand the file.

Your file has a lot less in it than is possible, and this is normal. For stuff that isn't specified, the x server uses default values.

You are on the right track trying to replace the 800x600 with the resolution you want. Bear in mind that this isn't the definition of the resolution itself, but rather a reference to a modeline. It might be worth a bit of a search to make sure that the modeline you need already exists by default. If not, you will have to write it into the xorg.conf file. I had to do that about 4 years ago when 1280x800 screens were still new on the market. I found a modeline in the net that someone had written for my laptop model using an internet search machine. Sometimes you get lucky..:D

---

### Post by black28 on 2009-12-05
i seen the first 2 threads searching. the manually one is good but i need the HArdware info. plus im still new to this and don't quite understand what needs to be added and stuff. the other one using the disc  "sudo displayconfig-gtk" doesnt work anymore am i right? i've tried and it says not found. what does "man xorg.conf" do? my Hardware Driver doesnt read any drivers on my desktop.

---

### Post by audiomick on 2009-12-05
The command "man" is a general command to open the manual pages for lots of things, like commands and config files.
If you do
```
man xorg.conf
```
it will show you the manual page for the file xorg.conf.

"man" is _absolutely safe_ to try out. If the manual page doesn't exist, if will just say
```
mick@ubuntu-desktop:~$ man goforabeer
No manual entry for goforabeer
mick@ubuntu-desktop:~$ 

```

If you are wondering about something that is supposed to be carried out in a terminal, or a config file, it is always worth a try to do
```
man whatever_you_are_looking_for
```

---

### Post by black28 on 2009-12-05
thanks. i found this [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) in a different thread. how can i tell what my monitor is capable of? i have this one [http://reviews.cnet.com/lcd-monitors/samsung-syncmaster-906bw/4507-3174_7-32327972.html](http://reviews.cnet.com/lcd-monitors/samsung-syncmaster-906bw/4507-3174_7-32327972.html) maybe i can generate a modeline for my screen and add it to my xorg.conf file? man this is pretty confusing. been trying to get this resolution going right for almost a week now....

---

### Post by audiomick on 2009-12-05
The best source for what the monitor is capable of is it's own users manual, or the web site of the manufacturer. There is a thing called EDID (Or something similar) which is supposed to automatically communicate the monitors capability to the video driver, but it seems, with my monitors, to be a bit erratic.

---

### Post by black28 on 2009-12-05
im starting to think maybe it's just my pc? it's a HP Pavilion 521c. with trident vid card. and 1 stick of 256mb ram. maybe it's just old? i have Full Screen on Xubuntu. the only thing is i wanted to make it look smaller. like side scroll bars thinner and stuff. it's just running at 800x600. i dont have the manual for my screen. i got it from a friend with the box but no papers. box doesnt say what i need.

---

### Post by Torrilin on 2009-12-05
Those specs would make it around a 10 year old machine. You may be able to find more information on it by using a search engine on the part names, but equipment that old did not always have a manufacturer web site. And even if it did, the manuals might not have been online, and the web page may no longer be online. It is very difficult to get a Linux install to do what you want if you do not understand your hardware's capabilities.

A distribution aimed at older machines might work better. A lot will depend on how popular the hardware you have was.

---


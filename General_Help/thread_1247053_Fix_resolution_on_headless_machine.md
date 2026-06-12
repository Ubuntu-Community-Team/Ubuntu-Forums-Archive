---
title: "Fix resolution on headless machine"
date: 2009-08-22
forum: General Help
---

### Post by Redsandro on 2009-08-22
Hi,

I used to use a machine with a monitor. I removed everything and I use it as a server, only reachable through the network. I usually prefer vnc.

But after a big problem I reformatted and installed Ubuntu 9.04. Now xorg.conf is empty of all those mode lines. But that seems to be normal.

The only problem is, now the maximum resolution is 800x600. But this used to be a lot higher (on the same hardware).

I have a user that logs on automatically and I share the desktop through vnc, but I'd like it to be 1280x1024. I cannot **xrandr** it because it only goes to 800x600.

Does anyone know how I can get the higher resolutions? I don't necesarily want to have all the modelines in xorg.conf. In fact, if there's a way to do it without that, that would be easier.

---

### Post by matthewbpt on 2009-08-22
Depends what graphics card you have and weather it's using proprietary or open source drivers. Can you give us some more info on the machine?

---

### Post by Redsandro on 2009-08-24
Sure. It's a Pentium 4 on an Asus P4C800 Deluxe motherboard, 1G of memory. The videocard is a nVidia geForce 5200FX.

I am using the open driver, because something [funny]("http://ubuntuforums.org/showthread.php?t=1069080") happened a while ago. The card went kind of broken. If I load the proprietary driver, the machine crashes. I've tried everything including reinstalling Ubuntu to see if it was a software issue, but it doesn't really matter since there's no problem running the open driver, and now that I use the machine headless there's no real use for the proprietary functions anyway. Except for tv-out but my tv also broke. Bad earth vibes or something. ;)

Anyway, all I did to fix this at the time was change *nvidia* to *nv* inside *xorg.conf*. I carefully built xorg.conf to support the displays and resolutions I wanted, nothing else.

Since the xorg.conf from a new install is kind of empty, no resolution data whatsoever, this must be getting decided somewhere else. Since I know my video card, also with the open driver, supports much greater resolutions, I was wondering where I can 'fix' this to default at 1280x1024 instead of 800x600 (which is currently the highest selectable resolution).

I am just guessing here but I think it takes 800x600 for savety reasons since it cannot detect a monitor. Because there is none.

---

### Post by P4man on 2009-08-24
You are right, and you already gave the solution: add the resolution you want to xorg.conf. A pretty empty xorg works these days, as the driver will fill the gaps I guess, but you can still force stuff, like a certain resolution in there, just like in the old days ;)

---

### Post by Redsandro on 2009-08-24
[SIZE="1"]-edit-
Sorry I just noticed my double post[/SIZE]

---

### Post by Redsandro on 2009-08-24
Ah, great. I also just discovered a backup from 2007 which was pretty much corrupted but the xorg.conf is still intact. I can use it (but use the open driver) since the hardware has not changed. (And I will post it below if for some reason someone wants to take a look or needs a template for the same hardware).

I'm just curious if I can change that default 800x600 somewhere.



```
# Edited by RED 24/09/2007 - 04/10/2007 for separate X session on TV
# www.REDnet.nl



#
# Monitors
#

Section "Monitor"
# TFT Flatpanel
    Identifier     "Monitor_TFT"
    VendorName     "Samsung"
    ModelName      "Samsung SyncMaster 172v"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
# Television
    Identifier     "Monitor_TV"
    VendorName     "Grundig"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection



#
# Video cards
#

# DVI only
Section "Device"
    Identifier     "Card_VGA"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:1:0:0"
    Option         "NoLogo"
    Option         "TwinView" "1"
    Screen 0
EndSection

# DVI and TV-OUT
Section "Device"
    Identifier     "Card_TV"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:1:0:0"
    Option         "NoLogo"
    Option         "TVOutFormat" "SVIDEO"  # Or "COMPOSITE"
    Option         "TVStandard" "PAL-B"
    Option         "ConnectedMonitor" "TV"
	# added RED
    Option         "TwinView" "1"
    Screen 0
EndSection



#
# Screens
#

# Monitor and TV - By RED
Section "Screen"
    Identifier     "Screen_TFT"
    Device         "Card_VGA"
    Monitor        "Monitor_TFT"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1280x1024 +0+0 , TV: 720x576 +0+0"
    Option         "TVOutFormat" "SVIDEO"  # Or "COMPOSITE"
    Option         "TVStandard" "PAL-B"
    Option         "RenderAccel" "On"
    Option         "HWcursor" "On"
    Option         "DamageEvents" "True"
    Option         "ConnectedMonitor" "CRT , TV"
    Option         "TwinViewOrientation" "TV Rightof CRT"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

# Monitor and TV - Exact clone at 1024 - by nVidia xServer Settings
Section "Screen"
    Identifier     "Screen_Clone"
    Device         "Card_VGA"
    Monitor        "Monitor_TFT"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1024x768 +0+0, TV: 1024x768 +0+0"
    Option         "TVOutFormat" "SVIDEO"  # Or "COMPOSITE"
    Option         "TVStandard" "PAL-B"
    Option         "RenderAccel" "On"
    Option         "HWcursor" "On"
    Option         "DamageEvents" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

# TV only
Section "Screen" 
    Identifier     "Screen_TV"
    Device         "Card_TV"
    Monitor        "Monitor_TV"
    DefaultDepth    24
    Option         "metamodes" "TV: 720x576 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "720x576" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection






#
# Define Server Layouts.
#

# Monitor only - default #SELFNOTE: Toch ook tv clone, mss niet optimaal. AANPASSEN!
Section "ServerLayout"
    Identifier     "monitor"
    Screen      0  "Screen_TFT" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

# Monitor with TV Clone (partial)
Section "ServerLayout"
    Identifier   "computer"
    Screen 0      "Screen_TFT" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice "Keyboard0" "CoreKeyboard"
EndSection

# TV clone of Monitor @ 1024
# startx -- :1 -layout "clonetv" (untested) - moet anders dynamically
Section "ServerLayout"
    Identifier     "clonetv"
    Screen      0  "Screen_Clone" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

# TV only; To switch, type:
# startx -- :1 -layout "tv"
Section "ServerLayout"
    Identifier     "tv"
    Screen      0  "Screen_TV" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection






#
# Input devices, can be used by all Server Layouts
#

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






#
# Now some global configuration
#

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
    Option         "TwinView" "1"
EndSection

```

---

### Post by P4man on 2009-08-24
wow. what a xorg.conf lol. Print it and hang it on your wall, but dont use it LOL. Take the almost empty existing one. In the section "screen" just add:

```

SubSection     "Display"
        Depth       24
        Modes      "1024x768" 
EndSubSection

```

(or whatever res you want).

---

### Post by Redsandro on 2009-08-24
I can do that. :) Thanks!

Somewhat off-topic, I just discovered FreeNX for remote desktopping, and it can have any resolution client-side. This way, it doesn't matter what xorg.conf sais.

But contrary to VNC, the way of remote desktopping I used before (and why I wanted the internal resolution to go up), the NX connection creates a new session, and I need to connect to my current session. Do you know if that is even possible with NX?

---

### Post by P4man on 2009-08-24
> **Redsandro said:**
> I can do that. :) Thanks!

Somewhat off-topic, I just discovered FreeNX for remote desktopping, and it can have any resolution client-side. This way, it doesn't matter what xorg.conf sais.

But contrary to VNC, the way of remote desktopping I used before (and why I wanted the internal resolution to go up), the NX connection creates a new session, and I need to connect to my current session. Do you know if that is even possible with NX?

its not possible afaik :(
I guess its the secret to its speed and flexibility.
There are some other alternative solutions comparable to NX, but they all start separate sessions. VNC (and xvnc and the like) are the only ones I know that will connect to an open session, and they are slow and will give you the same resolution as your host.

If you ever find something combining best of both worlds, pls let me know :)

---

### Post by Redsandro on 2009-08-24
Yes I will :)

I can disconnect from a session and continue it, so it FEELS like it could be possible one way or the other.
Also I can get a list of open sessions from my Xubuntu machine, but not from the Ubuntu one (discussed here).

If I find out I'll get back here. Please do the same if you beat me to the punch. :)

---

### Post by P4man on 2009-08-24
apparently there is  an option in nx called "shadow mode" which would enable just that, but i see quite a few threads with problems related to that. I can't test it here now, but thought I'd beat you to it nonetheless :p

---

### Post by Redsandro on 2009-08-24
Sounds promising. I will investigate when I have more time.
Thanks for the hint!

---

### Post by Redsandro on 2009-08-25
There's a 'shadow' option for Desktop in the NoMachine NX client. But it doesn't work on connect:
```
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Error: Connection with remote peer broken.
Error: Please check the state of your network and retry.
```

I read left and right on the web that the FreeNX server does not support shadowing mode.

The NoMachine server is ofcourse not an option. I like my source to be open and free.

I take that shadowing is also unavailable for **X -broadcast** and **ssh -CX**?

---

### Post by Redsandro on 2009-09-24
During a xorg edit I remembered setting the resolution alone is not enough to make the vnc server take this resolution. So for the sake of completeless let me also mention these need to be added in the monitor section:

HorizSync     31-101
VertRefresh   60-160

---

### Post by produnis on 2010-01-24
For me it works to use a xorg.conf as follws:

```

Section "Device"
Identifier "VNC Device"
Driver "vesa"
EndSection

Section "Screen"
Identifier "VNC Screen"
Device "VNC Device"
Monitor "VNC Monitor"
SubSection "Display"
Modes "1024x768"
EndSubSection
EndSection

Section "Monitor"
Identifier "VNC Monitor"
HorizSync 30-70
VertRefresh 50-75
EndSection

```

With that xorg.conf I have a VNC-Connection with resolution 1024x768
([thanks to Chris]("http://ubuntuforums.org/showpost.php?p=8144910&postcount=1"))

---

### Post by Redsandro on 2010-01-24
Thanks for the update!
I moved my server and use it with a KVM with my workstation so I don't use VNC a lot anymore. KVMs are sometimes ridiculously cheap on ebay but not too high quality.

---


---
title: "stumped trying to get 1080i out of nvidia card (dvi to hdmi)"
date: 2006-05-05
forum: General Help
---

### Post by Eduardo! on 2006-05-05
reposted from the Warty forum because i'm kinda dumb today, sheesh.

ok, i'm rebuilding my mythtv box, and i figured as long as i was going to do it i'd put in an nvidia 5500 card with a dvi out, use my dvi->hdmi cable and have bright shiny 1920x1080 widescreen (1080i) like my new samsung 30" slimfit hdtv supports...but no dice. and i've been fiddling with everything i can think of all day. at the moment, i get display on the tv, but X is stuck at 640x480.

this card only has a dvi out (well other than svideo but eww), i just don't know what else i can do. i plugged my tv into the dvi out on my desktop here, and 1920x1080 works fine. that was in windows, so i started up PowerStrip to get the modeline it used, so i know the modeline is good..anyway, here is my xorg.conf:

```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
#       Load    "ddc"
#       Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5500]"
        Driver          "nvidia"
        BusID           "PCI:0:19:0"
        Option          "NoLogo"        "1"
        Option          "NoDDC"
EndSection

Section "Monitor"
        Identifier      "SAMSUNG"
#       Option          "DPMS"
        Modeline        "1920x540" 74.250 1920 2008 2052 2200 540 542 547 562 interlace +hsync +vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5500]"
        Monitor         "SAMSUNG"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1920x540"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

so...any ideas why this may be spitting me into 640x480? i've scoured the net and it seems like i'm the only person that's tried to do this. =D

also, yes i tried reconfiguring x using that tool who's name escapes me right now and lets you choose resolutions..but anyway, it doesnt offer 16:9 resolutions, only 4:3 and 16:10, none of which i can use.

oh, here's part of my Xorg.0.log which is probably where the issue takes place i imagine:

```

(II) NVIDIA(0): Not using mode "1920x540" (no mode of this name)
(**) NVIDIA(0): Validated modes for display device DFP-0:
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480

```

but i have no idea why it might say that there's no mode available when it's really in there.

---

### Post by Jason_25 on 2006-05-05
I have a Philips 30pw9110d CRT with dvi to hdmi and I can't get 1080i either with the newest driver.  I could get a shaky 1080i with 81.78 though.  To help you, I'll need to know your nvidia driver version, because the syntax is different.  But honestly, you would be ALOT better off with 720p if your tv supported it.  You have a CRT hdtv right?  Most of the newer crts will take 720p input too.

---

### Post by Eduardo! on 2006-05-05
i actually don't know off the top of my head, whatever i got with apt-get install nvidia-glx yesterday, how would i go about checking that?

---

### Post by Jason_25 on 2006-05-05
```

glxinfo | grep version

```

---

### Post by Eduardo! on 2006-05-05
actually!

i just got it working in a 960x540p mode, which is great, no shake, just what i was lookin for, using another person's xorg.conf off the intarweb.

only problem is massive overscan, basically the bars at top and bottom of gnome are completely off the screen. is there a way to adjust that with nvidia's drivers? i know with the onboard sis chipset there was a utility to do it without having to fiddle with xorg.conf or restart x or anything.

---

### Post by Eduardo! on 2006-05-05
also, looks like 76.67 nvidia drivers

---

### Post by Eduardo! on 2006-05-05
oh, and my tv actually does not support 720p. it'll take it, but just converts it to 1080i (with a delay) in the tv. =(

---

### Post by Jason_25 on 2006-05-05
Yeah most CRT HDTVs don't have actual 720p resolution but many convert over.  Mine may convert but is still very clear at 720p.  I have a CRT monitor connected in twinview clone mode also so the overscan is no problem.  The movies you watch full screen are filmed with overscan in mind anyway.  Could you post the modeline you used for that resolution?

---

### Post by Eduardo! on 2006-05-05
[QUOTE=Jason_25]Could you post the modeline you used for that resolution?[/QUOTE]

Mode "960x540p"
     DotClock 37.26
     HTimings 960 976 1008 1104
     VTimings 540 542 548 563
     Flags "+HSync" "+VSync"
EndMode

---


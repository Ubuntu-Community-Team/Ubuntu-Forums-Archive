---
title: "&quot;Input signal out of range&quot; while booting up"
date: 2011-05-01
forum: General Help
---

### Post by megahost on 2011-05-01
While my Ubuntu computer was on the splash screen, my Ubuntu is in a bad resolution and I get the error on my monitor 
> "Input signal out of range, change settings to 1600 x 900 - 60Hz"
I tried editing the GRUB file to change

> #GRUB_GFXMODE=640x480
to
> GRUB_GFXMODE=640x480

Here's my xorg.conf file

```
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

```

Which is wierd because my xorg.conf.backup is
```

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
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Help is appreciated
Cheers :D

---

### Post by Hedgehog1 on 2011-05-01
Once you did this:

```
#GRUB_GFXMODE=640x480
```
to
```
GRUB_GFXMODE=640x480
```

Did you make the change 'real' by doing this:

```
sudo update-grub
```

Just checking...

***The Hedge***

:KS

---

### Post by megahost on 2011-05-01
> **Hedgehog1 said:**
> Once you did this:

```
#GRUB_GFXMODE=640x480
```
to
```
GRUB_GFXMODE=640x480
```

Did you make the change 'real' by doing this:

```
sudo update-grub
```

Just checking...

***The Hedge***

:KS

I did the update, and still got the error

---

### Post by megahost on 2011-05-01
Is there something wrong with the xorg.conf file or what's happening?

---

### Post by megahost on 2011-05-01
bump

---

### Post by megahost on 2011-05-01
I went into nvidia settings and set the resolution to 1600x900 - 60Hz. I still get on boot up "Input signal out of range..." This is getting irritating

---

### Post by megahost on 2011-05-01
Any suggestions. Sorry for being "wanty for help" but this problem is really bugging me.

---

### Post by stoneage on 2011-05-01
Did you upgrade instead of doing a clean install and then this occurred?

It could be you need to add back a modeline to the xorg.conf. You might get away with just adding back the HorizSync and VertRefresh values in the 'Monitor' section, or you may have to create a whole modeline.

Did you try reinstating the backed up xorg.conf?

More information here:-
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by megahost on 2011-05-02
It was when I upgraded. I looked at what you sent me and it was a bit confusing.

---

### Post by johnthei on 2011-05-12
I have the same problem. I did a new full clean install of 11.04 and the first thing I get now is the ''Input signal out of range  change settings to 1280x1024 60hz''

and nothing else happens. I dont know where to go at this point.

---


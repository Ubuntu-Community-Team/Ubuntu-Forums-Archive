---
title: "Monitor Resolution"
date: 2010-02-14
forum: General Help
---

### Post by stupidchunk on 2010-02-14
The right resolutions for my monitor are not being recognized. I already edited xorg.conf but to no avail. I also consulted with the ubuntu IRC channel and did what someone suggested - rename xorg.conf and run gksudo nvidia-setting/sudo nvidia-xconfig- but it still didnt work. Here's my current xorg. conf:

> 
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 60.0
    VertRefresh     56.0 - 75.0
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
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


I'm on Ubuntu Karmic. I'm using Samsung SyncMaster 151s, it's an LCD monitor but the model description in NVIDIA X Server Settings lists it as Samsung SyncMaster 151s (CRT-0). My driver is GEForce2 MX/MX 400. I usually use this monitor on a 1280x1024 resolution but the highest resolution nvidia-settings list is 1360x768. I really hope someone can help. I've been working on this for days. Thanks.

---

### Post by Satoru-san on 2010-02-14
Can you please paste your /var/log/Xorg.0.log?

If you are wondering how to do this:

put in a flash drive
```
[s]sudo mkdir /mnt/usb
sudo mount /dev/sdb1 /mnt/usb
sudo cp /var/log/Xorg.0.log /mnt/usb
sudo umount /mnt/usb[/s]
```This will tell us almost everything we need to know.


EDIT: I guess X is running so never mind. Just 

```
gksudo gedit /var/log/Xorg.0.log
```

---

### Post by byStanderone on 2010-02-14
...have done a specification check for samsung 151s, and it says that the maximum resolution of the model is 1024x768.

---

### Post by stupidchunk on 2010-02-14
> **Satoru-san said:**
> Can you please paste your /var/log/Xorg.0.log?

EDIT: I guess X is running so never mind. Just 

```
gksudo gedit /var/log/Xorg.0.log
```

The log is too long so I just pasted it here : [http://pastebin.com/f403955ea](http://pastebin.com/f403955ea)

---

### Post by stupidchunk on 2010-02-14
> **byStanderone said:**
> ...have done a specification check for samsung 151s, and it says that the maximum resolution of the model is 1024x768.

I was using this monitor on a Windows PC on a 1280x1024 resolution a few weeks ago though.

---

### Post by Satoru-san on 2010-02-14
> **byStanderone said:**
> ...have done a specification check for samsung 151s, and it says that the maximum resolution of the model is 1024x768.

That appears to be correct.

```

[LIST=1]
[*](WW) NVIDIA(0): No valid modes for "1600x1200"; removing.
[*](WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
[*](II) NVIDIA(0): Validated modes:
[*](II) NVIDIA(0):     "1024x768"
[*](II) NVIDIA(0):     "800x600"
[*](II) NVIDIA(0):     "640x480"
[*](II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[/LIST]

```
Don't know what to tell you, its either the graphics card or the moniter, more likely the latter than the former.

---

### Post by stupidchunk on 2010-02-14
Oh well, I guess I just have bad memory. Sorry, guys,

---


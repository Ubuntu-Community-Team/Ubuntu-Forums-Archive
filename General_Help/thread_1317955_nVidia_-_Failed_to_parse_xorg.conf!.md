---
title: "nVidia - Failed to parse xorg.conf!"
date: 2009-11-07
forum: General Help
---

### Post by RugeUKG on 2009-11-07
Hi folks,

I just did a fresh install of Karmic, looks good so far.

I have a GeForce 9400GT card with 2 inputs:

DVI (Using VGA adapter with an LG screen, 1280x960)
VGA (Using an IBM screen, 1280x960)

I've noticed that the monitor connected to the DVI port (Via VGA-to-DVI adapter) features default resolutions, and Karmic cannot detect my native resolutions.

My second issue is following installation of the nVidia 185 driver (latest, via Hardware Drivers), I cannot save my xorg.conf file. I have tried numerous solutions on the forums that I've found (such as renaming current xorg and letting nvidia-settings sort it out) but it still fails to parse the file!

My terminal displays this note also:

```
VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required.

Segmentation fault
RugeUKG@RugeUKG-desktop:~$ gksu nvidia-settings

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required.
```

Without a fix, I have to set my resolutions and dual monitor setup each time I boot!

Is there any way I could fix this? Thanks!

---

### Post by scouser73 on 2009-11-07
there is no xorg.conf file in Karmic,or an empty one.
Have a look in **/etc/X11/**

If there is one,delete it.Then make a new one:

**sudo nvidia-xconfig**

Restart X

then:

**gksudo nvidia-settings**

Make changes,apply,save to X configuration file

---

### Post by Paul D on 2009-11-07
I am  newbe, so pardon my stupidity.
Your line; [B]sudo nvidia-xconfig 
[/B]came back with;[B]
sudo: nvidia-xconfig: command not found

[/B]So what do I do?

I noticed there was no xorg.conf file in that directory in 9.10. How to create?

---

### Post by scouser73 on 2009-11-07
It's not **sudo:** it's just **sudo** perhaps that's why you're encountering a problem.

---

### Post by Paul D on 2009-11-07
I appreciate your patience with me. Please step through the process a little more for me.

How do I make an xorg.conf?
If I use a text editor to do that it will be an empty file... right/wrong?
If empty, from where would text come in it?

Is the following text exactly what to type in the command line, or am I supposed to know this is short-hand for something else? What does each of these steps do?

**sudo nvidia-xconfig**
(This runs a file, creates/installs/runs a script or what?)

Restart X
(This obviously restarts something)

then:

**gksudo nvidia-settings**
(I assume this allows editing of a file, or settings through a gui)

Do I need to download a specific nvidia driver at some point?

I am assuming that since I see no control mechanism in ubutu to set display settings, that one can be made available through this, or another method? My VGA compatible controller: nVidia Corporation NV15GL [Quadro2 Pro] in this ubuntu 9.10 studio install, appears to me as to not be performing to its best. When I attempt to play a DVD, the video stutters, updates the video image every 5 seconds or so. I am looking for a way to correct this. Am I barking up the wrong tree? Do you have another suggestion?
I am almost there with this install, I got the sound working, and the XP network working.
I think that just this video deal is all that isn't quite right.

---

### Post by scouser73 on 2009-11-07
Perhaps this will give you better guidance than me: [[COLOR="Red"]**Failed to parse xorg.conf!**[/COLOR]]("http://johnnydopefish.blogspot.com/2009/05/ubuntu-904-nvidia-failed-to-parse.html")

---

### Post by RugeUKG on 2009-11-07
Interesting, I woke up to find my main monitor can't be detected corectly by the driver (and that my resolutions are only 640x480 and cannot be changed).....

Thanks for the replies, will try these now!

---

### Post by RugeUKG on 2009-11-07
> **scouser73 said:**
> there is no xorg.conf file in Karmic,or an empty one.
Have a look in **/etc/X11/**

If there is one,delete it.Then make a new one:

**sudo nvidia-xconfig**

Restart X

then:

**gksudo nvidia-settings**

Make changes,apply,save to X configuration file

Hey mate, tried this and all is well! Unfortunately one of my screens (the one connected to DVI via a VGA port) has a resolution locked at 640x480 and I can't do a thing about it! :(

---

### Post by scouser73 on 2009-11-07
> **RugeUKG said:**
> Hey mate, tried this and all is well! Unfortunately one of my screens (the one connected to DVI via a VGA port) has a resolution locked at 640x480 and I can't do a thing about it! :(

I've had Karmic installed and had exactly the same trouble you've got. I don't know why dual monitor set up in 9.04 is so terrible.

Can I offer you some advice mate, perhaps you've even considered it yourself but I'd reinstall Jaunty again.

[[COLOR="Red"]**Download Jaunty Jackalope**[/COLOR]]("http://releases.ubuntu.com/jaunty/")

Please let me know how you get on, all the best

scouser73

---

### Post by RugeUKG on 2009-11-08
> **scouser73 said:**
> I've had Karmic installed and had exactly the same trouble you've got. I don't know why dual monitor set up in 9.04 is so terrible.

Hmm I had this issue with 9.04 as well as LinuxMint7. 

The common denominators were that I was running 2 VGA CRTs from 1 VGA and 1 DVI port... and I have an nVidia GFX card.

I will keep trying some other things but if I figure this out I'll let you know.

---

### Post by abandonedthe_mulletator on 2010-01-04
Hi I'm running Karmic on an ASUS laptop with a Nvidia gpu.  Every time I boot my resolution is reset and its a real pain in the ***.  I've tried these steps to fix it with no luck.
```
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
sudo nvidia-settings

```

What else can I do?

---

### Post by Linuxforall on 2010-01-04
gksudo nvidia-xconfig
gksudo nvidia-setting
set resolution and save to X.

---

### Post by abandonedthe_mulletator on 2010-01-04
> **Linuxforall said:**
> gksudo nvidia-xconfig
gksudo nvidia-setting
set resolution and save to X.

Did not work.  Any other ideas?

---

### Post by abandonedthe_mulletator on 2010-01-11
Am I the only person who has this problem?

---

### Post by Greenwidth on 2010-01-11
Post your xorg.conf.
It might be worth starting a new thread for it as well.

---

### Post by abandonedthe_mulletator on 2010-01-14
OK here it is.
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@americium)  Sat Nov 21 01:31:44 UTC 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Wed Dec  9 16:34:26 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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
    ModelName      "HSD160PHW1"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce G102M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1366x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Troya.one on 2010-02-06
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Fri Aug 14 18:33:37 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    ModelName      "LPL"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M GS"
EndSection

Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x800_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection





same problem! resolution changing to old after reboot

---

### Post by Troya.one on 2010-02-11
nobody...knows linux %)

---


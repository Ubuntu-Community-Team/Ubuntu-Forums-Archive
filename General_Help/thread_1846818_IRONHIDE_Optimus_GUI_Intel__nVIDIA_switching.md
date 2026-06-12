---
title: "IRONHIDE: Optimus GUI Intel / nVIDIA switching"
date: 2011-09-19
forum: General Help
---

### Post by frogotronic on 2011-09-19
Hello,

   I'd like to get some help working out Ironhide from this PPA: [https://launchpad.net/~mj-casalogic/+archive/ironhide/](https://launchpad.net/~mj-casalogic/+archive/ironhide/)

Any help would be appreciated.

Thanks,
CH

---

### Post by iMPR3SSiON on 2011-09-30
Me too, actually. I installed it and it seem not to be working at all... I can't even run 'glxgears'...

---

### Post by sanukcm on 2011-10-20
Having the same problem... anyone able to get it working?

---

### Post by frogotronic on 2011-10-21
it destroyed my install

I have no idea how to install it, how to activate it, and how to get it working and there are no instructions.

:confused:

---

### Post by Slave2Metal on 2011-10-24
I have an xps15 with optimus and wished to use the intel card only. This is what I did recently on ubuntu 11.04.  I used the default settings, instead of someone else's profile.

```
sudo apt-add-repository ppa:mj-casalogic/ironhide
```
```
 sudo apt-get update && sudo apt-get install ironhide
```

---

### Post by gooold on 2011-10-24
I have a Dell XPS 17 (L702X) running Ironhide and using Gnome3 with 3D effects.

What I did after new Install Ubuntu 11.10:

1. Do not install any Nvidia Drivers by default.
2.
sudo apt-add-repository ppa:mj-casalogic/ironhide3.
 sudo apt-get update && sudo apt-get install ironhide4. Complete the Installer, select the 2nd script (the guy with 19 ok's Ubuntu11.04)
5. select PROXY as container.
6. A Test will run for OpenGL .
7a  sudo ironhide-settings
7b. For my Dell I had to disable (1)Automatic Shutdown of Nvidia Card (NO) and 
                                                    (7) Always enable the Nvidia............ (NO)
8. reboot

Thats it 3D unity and Gnome 3 is on.
sudo ironhide-enablecard (works)
sudo ironhide-disablecard (works)
optirun "yourProgram" (works)

ps: If you activated any Nvidia Driver before installing Ironhide, I would not know how
to make it work. This work for me only on new install.

---

### Post by gooold on 2011-10-24
I have a Dell XPS 17 (L702X) running Ironhide and using Gnome3 with 3D effects.

What I did after new Install Ubuntu 11.10:

1. Do not install any Nvidia Drivers by default.

2.sudo apt-add-repository ppa:mj-casalogic/ironhide

3. sudo apt-get update && sudo apt-get install ironhide

4. Complete  the Installer, select the 2nd script (the guy with 19 ok's Ubuntu11.04)

5. select PROXY as container.

6. A Test will run for OpenGL .

7a  sudo ironhide-settings
7b. For my Dell I had to disable (1)Automatic Shutdown of Nvidia Card (NO) and 
                                                   (7) Always enable the Nvidia............ (NO)

8. reboot

Thats it 3D unity and Gnome 3 is on.
sudo ironhide-enablecard (works)
sudo ironhide-disablecard (works)
optirun "yourProgram" (works)

ps: If you activated any Nvidia Driver before installing Ironhide, I would not know how
to make it work. This work for me only on new install.

---

### Post by Slave2Metal on 2011-10-25
What kind of battery life are you getting?
> **gooold said:**
> I have a Dell XPS 17 (L702X) running Ironhide and using Gnome3 with 3D effects.

What I did after new Install Ubuntu 11.10:

1. Do not install any Nvidia Drivers by default.

2.sudo apt-add-repository ppa:mj-casalogic/ironhide

3. sudo apt-get update && sudo apt-get install ironhide

4. Complete  the Installer, select the 2nd script (the guy with 19 ok's Ubuntu11.04)

5. select PROXY as container.

6. A Test will run for OpenGL .

7a  sudo ironhide-settings
7b. For my Dell I had to disable (1)Automatic Shutdown of Nvidia Card (NO) and 
                                                   (7) Always enable the Nvidia............ (NO)

8. reboot

Thats it 3D unity and Gnome 3 is on.
sudo ironhide-enablecard (works)
sudo ironhide-disablecard (works)
optirun "yourProgram" (works)

ps: If you activated any Nvidia Driver before installing Ironhide, I would not know how
to make it work. This work for me only on new install.

---

### Post by frogotronic on 2011-10-25
So...

If you have a working install (not new) and have installed nvidia drivers, how does one get Ironhide to work?

Do you (I) have to install the intel drivers, before adding the ironhide PPA and installing the ironhide software?

Can you post your XORG.CONF file?

Thanks,
CH

---

### Post by gooold on 2011-10-25
I get about 4hr Battery (17"), jockey shows Nvidia installed but not in use.
The xorg.conf is not beeing used Ironhide installs xorg.conf.nvidia:

>>Xorg.conf
Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection


>>Xorg.conf.nvidia
Section "DRI"
    Mode 0666
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen         "Screen0"
    Option         "AutoAddDevices" "false"
EndSection

Section "Module"
    Load  "dbe"
    Load  "extmod"
    Load  "glx"
    Load  "record"
    Load  "freetype"
    Load  "type1"
EndSection

Section "Files"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BusID          "PCI:01:00:0"
    Option         "IgnoreEDID"
    Option         "ConnectedMonitor" "DFP-0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1920x1080" "1680x1050" "1600x1200" "1440x900" "1280x1024" "1366x768" "1360x768" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 73.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
    Modeline       "1920x1200"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
    Modeline       "1920x1080"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
    Modeline       "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
    Modeline       "1600x1200"  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync
    Modeline       "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
    Modeline       "1366x768"   85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsync
    Modeline       "1280x800"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
    Modeline       "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
EndSection

1st I had a update from 11.04 to 11.10 but was not able to get 3d effects, since the driver was loaded,
and I tried every command I could find to remove it. After a fresh install of 11.10 I was able to get
Ironhide functioning.

---

### Post by Slave2Metal on 2011-10-25
My goal was to keep a cool laptop and decent battery life in ubuntu with an optimus machine.  I learned last year about this time, not to install nvidia drivers to accomplish my goal. Installing the nvidia drivers just screwed everything up for me. 
> **cement_head said:**
> So...

If you have a working install (not new) and have installed nvidia drivers, how does one get Ironhide to work?

Do you (I) have to install the intel drivers, before adding the ironhide PPA and installing the ironhide software?

Can you post your XORG.CONF file?

Thanks,
CH

---


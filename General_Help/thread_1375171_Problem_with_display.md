---
title: "Problem with display"
date: 2010-01-07
forum: General Help
---

### Post by Remains on 2010-01-07
I have a samsung syncmaster 2033 hooked up to an onboard nvidia 6100 via analog. When I open the nvidia x server settings and go to display configuration it shows that my display has been detected as a CRT instead of an LCD. It also shows that the highest resolution available is 1360x768 but I would really prefer to change this to 1600x900.  I'm not sure what to do in this situation, any help would be appreciated.

---

### Post by blueshiftoverwatch on 2010-01-07
You can try running **gksudo gedit** and then from there opening up your xorg.conf settings file located in /etc/X11/. Your current resolution should be somewhere in there. Although I think Nvidia changes your Xorg.conf file around a bit.

Or you could possibly try [Xrandr]("http://www.perpetualpc.net/srtd_resolution.html").

---

### Post by Remains on 2010-01-07
> **blueshiftoverwatch said:**
> You can try running **gksudo gedit** and then from there opening up your xorg.conf settings file located in /etc/X11/. Your current resolution should be somewhere in there. Although I think Nvidia changes your Xorg.conf file around a bit.

Or you could possibly try [Xrandr]("http://www.perpetualpc.net/srtd_resolution.html").

This is all I got when I opened xorg.conf
```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```When I tried xrandr it told me that the maximum resolution I could run is 1024x768, but I know this to be untrue.

```
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   576x432        57.0  
   512x384        58.0  
   400x300        59.0     60.0     61.0  
   320x240        62.0  

```

---

### Post by Remains on 2010-01-08
Bump.

---

### Post by blueshiftoverwatch on 2010-01-09
If you tried setting the resolution from both nvidia-settings and Ubuntu 'Display' configuration app and neither one of those would let you get past 1360x768 I don't know.

The fact that nvidia-settings detects your display as a CRT instead of an LCD probably means there are bigger problems. Maybe check the [Nvidia forums]("http://forums.nvidia.com/") or [Cnet Samsung forums]("http://forums.cnet.com/samsung-forum/") if nobody here can provide any help.

See what happens if you uninstall nvidia-settings and your Nvidia GPU drivers. Uninstall them, restart your computer, and see if your Xorg.conf file looks any different.

---

### Post by warfacegod on 2010-01-09
Go to System> Admin.> Hardware Drivers and make sure you have the recommended driver activated.

---


---
title: "apperance preference"
date: 2010-01-30
forum: General Help
---

### Post by rflores2323 on 2010-01-30
I am trying to get compiz to work and when I try to set the visual effects to extra I keep getting this message "The Composite extension is not available".  I have searched and here are some things I have tried.  I have an acer revo 3610 with nvidia 185 drivers.  I have not updated the drivers as I am using the box as a xbmc theater box and hdmi is broke in the updated 190 and 195 drivers.


here is my xorg.confi file 

```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Extensions"
    Option         "Composite" "Disabled"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
    Option "FlatPanelProperties" "Scaling=Native"
EndSection
```I have tried to these recommendations and it does not work

**option 1**

adding this code ```
sudo nvidia-xconfig --add-argb-glx-visuals
```and I get the below output
```
xbmc@xbmc-desktop:~$ sudo nvidia-xconfig --add-argb-glx-visuals

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Option "AddARGBGLXVisuals" "True" added to Screen "Screen0".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```**option 2**

adding the below to my xorg.config file.

```
Section "Extensions"
Option "Composite" "1"
EndSection
```**Option 3**

enabled the below in xorg.config file

```
Section "Extensions"
    Option         "Composite" "Disabled"
EndSection
```nothing works as I keep getting this message and I cant get the functions of compiz to work.  any help please.

---

### Post by rflores2323 on 2010-01-30
anyone?

---


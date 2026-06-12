---
title: "I cant enable dasktop effects and play games"
date: 2010-10-08
forum: General Help
---

### Post by MdShion on 2010-10-08
I am using ubuntu 10.04. In my computer I cant enable dasktop effects and cant play other games. when I want to enable dasktop effects, there was a error massage "Desktop effects could not be enabled". my computer's RAM is "2GB", swap is "5.8GB" and video card is 
"01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)"
I download and install a software [from this site]("http://www.via.com.tw/en/support/drivers.jsp") but it doesn't work. now what can I do?

---

### Post by Quackers on 2010-10-08
Welcome to UbuntuForums
Have you tried going to System > Admin > Additional Drivers? Is a new driver available? Is there a driver activated there?

---

### Post by realzippy on 2010-10-08
*I download and install a software from this site but it doesn't work.*

What does this mean?
How did you install the software (run the *vinstall* script inside the .tar.gz )??
Did you use the xorg.conf ?

---

### Post by MdShion on 2010-10-08
> **Quackers said:**
> Welcome to UbuntuForums
Have you tried going to System > Admin > Additional Drivers? Is a new driver available? Is there a driver activated there?
are you talking about proprietary drivers? if yes then there is no driver to install. if no then saw this [picture ]("http://img257.imageshack.us/i/screenshot1hz.png/")

---

### Post by sikander3786 on 2010-10-08
> System > Admin > Additional Drivers

On Lucid it is System > Administration > Hardware Drivers and on Meerkat, System > Administration > Additional Drivers I believe.

---

### Post by MdShion on 2010-10-08
> **realzippy said:**
> *I download and install a software from this site but it doesn't work.*

What does this mean?
How did you install the software (run the *vinstall* script inside the .tar.gz )??
Did you use the xorg.conf ?
It mean I successfuly install this software, I use vinstall to install. I did not use xorg.conf.

---

### Post by Quackers on 2010-10-08
> **sikander3786 said:**
> On Lucid it is System > Administration > Hardware Drivers and on Meerkat, System > Administration > Additional Drivers I believe.

Oops!

---

### Post by realzippy on 2010-10-08
*I did not use xorg.conf*

...think you had to use the xorg.conf from the driver package.Please post current xorg.conf

```
 gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Hakunka-Matata on 2010-10-08
System > Administration > Software Sources:

the first four options should be checked, 

Canonical-supported ............... (main)
Community-maintained ...............(universe)
Proprietary drivers for devices ....(restricted)
Software restricted by copyright....(multiverse)

If you have those checked, you won't have to look for a site to download the proper driver for your video, Ubuntu will search and find it when you go to Hardware Drivers on the System > Administration menu.  You also must restart the computer after the driver has been installed.

---

### Post by realzippy on 2010-10-08
> **Hakunka-Matata said:**
> System > Administration > Software Sources:

the first four options should be checked, 

Canonical-supported ............... (main)
Community-maintained ...............(universe)
Proprietary drivers for devices ....(restricted)
Software restricted by copyright....(multiverse)

If you have those checked, you won't have to look for a site to download the proper driver for your video, Ubuntu will search and find it when you go to Hardware Drivers on the System > Administration menu.  You also must restart the computer after the driver has been installed.

ehm,OP has a VIA graphics chip.Never heard about via drivers
in jockey.

---

### Post by MdShion on 2010-10-08
> **realzippy said:**
> *I did not use xorg.conf*

...think you had to use the xorg.conf from the driver package.Please post current xorg.conf

```
 gksudo gedit /etc/X11/xorg.conf
```
Section "ServerLayout"
       Identifier    "Default Layout"
       Screen        "Default Screen"
       InputDevice    "Mouse"
       InputDevice    "Keyboard"
EndSection

Section "Files"
#     RgbPath      "/usr/local/share/X11/rgb"
       ModulePath   "/usr/lib/xorg/modules"
#     FontPath     "/usr/share/fonts/X11/misc/"
#     FontPath     "/usr/share/fonts/X11/TTF/"
#     FontPath     "/usr/share/fonts/X11/OTF"
#     FontPath     "/usr/share/fonts/X11/Type1/"
#     FontPath     "/usr/share/fonts/X11/100dpi/"
#     FontPath     "/usr/share/fonts/X11/75dpi/"
EndSection

Section "InputDevice"
       Identifier    "Keyboard"
       Driver        "kbd"
       Option        "XkbRules"    "xorg"
       Option        "XkbModel"    "pc105"
       Option        "XkbLayout"    "cn"
EndSection

Section "InputDevice"
       Identifier    "Mouse"
       Driver        "mouse"
       Option        "CorePointer"
EndSection

Section "Monitor"
       Identifier    "CRT"
       Option    "Enable"    "true"            
EndSection

Section "Monitor"
       Identifier    "LCD"
       Option     "Enable"    "false"         
EndSection    

Section "Monitor"
       Identifier    "DVI"
       Option     "Enable"    "false"
EndSection    

Section "Monitor"
       Identifier    "TV"
       Option  "Ignore"    "true"
EndSection    

Section "Monitor"
       Identifier    "HDMI"
       Option  "Ignore"    "true"
EndSection    

Section "Monitor"
       Identifier    "CRT-2"
       Option      "Ignore"    "true"
EndSection

Section "Monitor"
       Identifier    "LCD-2"
       Option      "Ignore"    "true"
EndSection

Section "Monitor"
       Identifier    "DVI-2"
       Option      "Ignore"    "true"
EndSection

Section "Monitor"
       Identifier    "TV-2"
       Option      "Ignore"    "true"
EndSection

Section "Device"
    #BusID "PCI:01:00:0"
    Driver     "via"
    VendorName      "VIA Tech"
    BoardName       "via"
    Identifier    "Configured Video Device"
    Option        "MigrationHeuristic" "greedy"
EndSection

Section "Screen"
       DefaultDepth 24
       SubSection "Display"
#             Virtual 2000 2000 
              Depth  24
       EndSubSection
       Identifier    "Default Screen"
       Device        "Configured Video Device"
EndSection

Section "Module"
      Load  "glx"
      Load  "dri"
      Load  "extmod"
EndSection

Section "DRI"
       Group 0
       Mode 0666
EndSection

Section "Extensions"
    Option    "Composite"            "Enable"
EndSection

---

### Post by Hakunka-Matata on 2010-10-08
> **realzippy said:**
> ehm,OP has a VIA graphics chip.Never heard about via drivers
in jockey.

Sorry about that, I did not know that.  Makes sense now ..

---

### Post by realzippy on 2010-10-08
If you have rebooted after the installation so xorg.conf (which looks fine) loaded,the driver should run.
What does:

```
glxinfo | grep direct
```

"say"?

---

### Post by MdShion on 2010-10-08
> **realzippy said:**
> If you have rebooted after the installation so xorg.conf (which looks fine) loaded,the driver should run.
What does:

```
glxinfo | grep direct
```

"say"?
I dont understand what are you talking about, because I dont know eanglish finely.

---

### Post by realzippy on 2010-10-08
Wanted to say:
If you have rebooted after the via driver installation,your driver should work.Can you open a terminal and type

```
glxinfo | grep direct
```

what is the output from that command?

---

### Post by Hakunka-Matata on 2010-10-08
Si ha reiniciado después de la instalación, por lo xorg.conf (que se ve bien) carga, el conductor debe ejecutar.

Este sitio web, traductor funciona bastante bien
[http://translate.google.com/?hl=es#]("http://translate.google.com/?hl=es#")

---

### Post by Hakunka-Matata on 2010-10-08
@realzippy:

I'll butt out now, thanks, you taught me a few things today.

---


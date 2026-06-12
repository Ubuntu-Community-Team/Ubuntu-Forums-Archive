---
title: "Problem with installation &amp; boot (nvidia)"
date: 2010-06-04
forum: General Help
---

### Post by yaslon on 2010-06-04
hi.
I'm trying to install Ubuntu 10.04 at my desctop PC.
When i start installation, display power off. 
Installation works only with special parameters (acpi=off noapic nolapic).
Install is ok, but don't starting without special parameters.
Computer hangs at boot on "Checking battery [OK]" and monitor was blinking.
4gb Memory / NVIDIA® GeForce® 9600 GS 768 Mb / Core 2 Quad Q9450 (2.6GHz) 

All Nvidia drivers installed correctly. I'm trying all what can find in google, but not work :(.
in /etc/X11/xorg.conf no section "Module".
When i replace "nvidia" on "nv"(in xorg.conf) computer boot ok without display, but sound is ok.
what happened? Please help me.

---

### Post by luceerose on 2010-06-04
Try running nvidia-xconfig that will rewrite your xorg file. Then you can start from there & make any other changes.
You can look at my xorg file & adapt from that if you can;
```
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
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "PHILIPS 107E4"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1024x768_85 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by yaslon on 2010-06-04
My xorg.conf

```

Section "ServerLayout" 
    Identifier     "Layout0" 
    Screen      0  "Screen0" 0 0 
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

---

### Post by yaslon on 2010-06-05
> **yaslon said:**
> 
Install is ok, but don't starting without special parameters.
Computer hangs at boot on "Checking battery [OK]" and monitor was 

I'm try ctrl + alt + f1, and ubuntu says :"unknown usb device".
In recovery mode system not understand keyboard too, but if i boot recovery mode with "acpi=off noapic nolapic" all ok.

I'm try to connect other keyboard and mouse without usb, but problem not gone...

What happened?
I can not understand in what direction to look.
don't let me die with windows :-D

---

### Post by realzippy on 2010-06-05
Do you have an onboard graphics chip also?
What is the output from 

```
lspci | grep VGA
```


Edit:
If system boots with *acpi=off noapic nolapic*,did you try to add this in /etc/default/grub?
Boot in recovery mode,drop to root shell,type:

```
nano /etc/default/grub
```

and add it: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off noapic nolapic"

save the file,run:

```
update-grub
```

```
exit
```

---

### Post by yaslon on 2010-06-05
If i added this lines to grub, computer may be works ok? :-)
What mean this lines?
I know tha acpi this power but cant find what mean noapic and nolapic.

---

### Post by wojox on 2010-06-05
What if you set *nomodeset* in the *GRUB_CMDLINE_LINUX_DEFAULT* ? That's what I had to do for my nvidia chip.

---

### Post by realzippy on 2010-06-05
> **yaslon said:**
> If i added this lines to grub, computer may be works ok? :-)
What mean this lines?
I know tha acpi this power but cant find what mean noapic and nolapic.


..here you find it:  (bottom of page)

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---


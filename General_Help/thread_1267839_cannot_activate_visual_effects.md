---
title: "cannot activate visual effects"
date: 2009-09-16
forum: General Help
---

### Post by hihihi100 on 2009-09-16
Hi there:

I have a N10M-GE1 NVIDIA graphics processor, 62.98.62.00.a1 vbios and 512 mb of memory, currently running the recommended version of drivers (180) downloaded from synaptic (I haven't downloaded anything from the NVIDIA official site, I havent installed anything via terminal, just what I found on synaptic).

Taken from hardware drivers, the installed and recommended 180 version of graphics drivers: "If you wish to enable desktop effects, this driver is required."

Well, when I click the icon to activate the effects (system - preferences - appearance), the clock appears, just to say after 5 seconds:

"Desktop effects could not be enabled"

Tips please?

---

### Post by gettinoriginal on 2009-09-16
You might try [here]("http://ubuntuforums.org/showthread.php?t=1139346") post #8
Also make sure that the restricted extras are enabled in synaptic
[ATTACH]128804[/ATTACH]

---

### Post by hihihi100 on 2009-09-17
Hiya again:

Due to my inexperience I downloaded EVERY restricted package I found. Yes, I shouldn't have done that, cause now the system is unstable again (I uninstalled every restricted package I installed, and even then, the system is unstable). When I log in, a window appears reading:

Taken from the X.org log:

    Error    Failed to load /usr/lib/xorg/modules/extensions//libglx.so
    Information    UnloadModule: "glx"
    Error    Failed to load module "glx" (loader failed, 7)

    Error    NVIDIA(0): Failed to initialize the GLX module; please check in your X
    Error    NVIDIA(0):     log file that the GLX module has been loaded in your X
    Error    NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
    Error    NVIDIA(0):     you continue to encounter problems, Please try
    Error    NVIDIA(0):     reinstalling the NVIDIA driver.
    Error    NVIDIA(0): Failed to load the NVIDIA kernel module!
    Error    NVIDIA(0):  *** Aborting ***
    Information    UnloadModule: "nvidia"
    Information    UnloadModule: "wfb"
    Information    UnloadModule: "fb"
    Error    Screen(s) found, but none have a usable configuration.


I have checked /etc/X11/xorg.conf and GLX is where it has to be, and the graphics card section is as it should be:

Section "Module"
    Load    "glx"
EndSection

and

Section "Device"
    Identifier     "Device0"
    VendorName     "NVIDIA Corporation"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Looks everything is fine, at least to me. Is there anything I should edit?

Do I have to uninstall absolutely EVERY nvidia driver and reinstall them all over again?

cheers

---

### Post by hihihi100 on 2009-09-17
an update that might help:

./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation Device 06ec (rev a1)
 Driver in use:         nvidia
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

What do I have to do?

---

### Post by shae on 2009-09-17
Try disabling nvidia through Restricted Driver Manager, rebooting, and re-enabling it.

---

### Post by hihihi100 on 2009-09-17
Restricted drivers? I went to system admin hardware drivers, and it shows the driver as not activated. When I click to activate it, it makes nothing. It looks like the driver (version 180) is installed, but cannot be activated...

Does this have to do with the rendering method?

---

### Post by shae on 2009-09-17
That sounds like it is the cause of the rendering method problem.

---

### Post by hihihi100 on 2009-09-18
So, do I have to uninstall EVERY Nvidia driver I can find? If so, it should be enough doing it via synaptic and uninstalling every nvidia 180 driver that I downloaded, am I right?

Unless any of you suggests a new approach...

---

### Post by shae on 2009-09-18
That sounds like a reasonable plan.

---

### Post by hihihi100 on 2009-09-19
k, so I have uninstalled via synaptic every nvidia 180 driver and every nvidia related file, plus I have opened a terminal and executed

[php]sudo aptitude purge nvidia-glx-180 nvidia-glx-173[/php]just to be sure.

I have rebooted the system, and now the x log is much shorter:

    Warning    Warning, couldn't open module glx
    Information    UnloadModule: "glx"
    Error    Failed to load module "glx" (module does not exist, 0)


and the other relevant part:

    Warning    Warning, couldn't open module nvidia
    Information    UnloadModule: "nvidia"
    Error    Failed to load module "nvidia" (module does not exist, 0)
    Error    No drivers available.

Fine, no drivers available, I can understand that, but what about the glx part?

And, once in the OS, I open synaptic again, reinstall the drivers (version 180), and the system goes back to the previous situation: low graphics, big size of icons and letters, cannot activate visual effects either, and the x log goes back to the large list of errors, the same list you can read on the third post of this thread...

Totally lost and confused

---

### Post by shae on 2009-09-19
What does your /etc/X11/xorg.conf file look like?

---

### Post by hihihi100 on 2009-09-20
copying the whole thing:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon Mar 23 15:33:27 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
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
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---


---
title: "External monitor"
date: 2012-01-13
forum: General Help
---

### Post by bjakke on 2012-01-13
{I am not english, so grammar-errors may occur.}

I have followed this awesome guide:
[http://wiki.xbmc.org/?title=XBMCbuntu]("http://wiki.xbmc.org/?title=XBMCbuntu")
to install XBMC on a bootable usb, for my sony vpccw1s1e laptop (Nvidia GeForce 230m).
I have successfully installed everything, including "restricted nvidia drivers" according to the guide.
My only problem now is that I can't get it to use my plasma as an external monitor through hdmi. I don't need to use the laptop monitor in my setup.
Xorg.log rightfully says that it identifies my plasma as DFP1, and selects DFP0 (sony lcd-panel) as default screen.

I used Ubuntu 10.04 "Lucid Lynx" Minimal CD x86 as OS.
I used NVIDIA-Linux-x86-290.10.run to install graphics driver.

Running xrandr returns "Can't open display".
Running nvidia-settings returns "ERROR: The control display is undefined; please run `nvidia-settings --help` for usage information.". GTK2 is installed.

I suspect I should add something in xorg.conf, but I don't know what.

---

### Post by bjakke on 2012-01-15
Here is a excerpt from my Xorg.0.log:
SONY AVAMP is a amplifier which redirects HDMI from the laptop to the TV. This is the device i would like to output the screen to.

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "DynamicTwinView" "False"
(**) Jan 15 12:47:48 NVIDIA(0): Enabling 2D acceleration
(II) Jan 15 12:47:50 NVIDIA(GPU-0): Display (Sony Nvidia Default Flat Panel (DFP-0)) does not
(II) Jan 15 12:47:50 NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
(II) Jan 15 12:47:50 NVIDIA(GPU-0): Display (SONY AVAMP (DFP-1)) does not support NVIDIA 3D Vision
(II) Jan 15 12:47:50 NVIDIA(GPU-0):     stereo.
(II) Jan 15 12:47:50 NVIDIA(0): NVIDIA GPU GeForce GT 230M (GT216) at PCI:1:0:0 (GPU-0)
(--) Jan 15 12:47:50 NVIDIA(0): Memory: 524288 kBytes
(--) Jan 15 12:47:50 NVIDIA(0): VideoBIOS: 70.16.27.00.09
(II) Jan 15 12:47:50 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Jan 15 12:47:50 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Jan 15 12:47:50 NVIDIA(0): Connected display device(s) on GeForce GT 230M at PCI:1:0:0
(--) Jan 15 12:47:50 NVIDIA(0):     Sony Nvidia Default Flat Panel (DFP-0)
(--) Jan 15 12:47:50 NVIDIA(0):     SONY AVAMP (DFP-1)
(--) Jan 15 12:47:50 NVIDIA(0): Sony Nvidia Default Flat Panel (DFP-0): 330.0 MHz maximum
(--) Jan 15 12:47:50 NVIDIA(0):     pixel clock
(--) Jan 15 12:47:50 NVIDIA(0): Sony Nvidia Default Flat Panel (DFP-0): Internal Dual Link
(--) Jan 15 12:47:50 NVIDIA(0):     LVDS
(--) Jan 15 12:47:50 NVIDIA(0): SONY AVAMP (DFP-1): 165.0 MHz maximum pixel clock
(--) Jan 15 12:47:50 NVIDIA(0): SONY AVAMP (DFP-1): Internal Single Link TMDS
(**) Jan 15 12:47:50 NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) Jan 15 12:47:50 NVIDIA(0):     enabled on all display devices.
(II) Jan 15 12:47:50 NVIDIA(0): Assigned Display Device: DFP-0
(==) Jan 15 12:47:50 NVIDIA(0): 
(==) Jan 15 12:47:50 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Jan 15 12:47:50 NVIDIA(0):     will be used as the requested mode.
(==) Jan 15 12:47:50 NVIDIA(0): 
(II) Jan 15 12:47:50 NVIDIA(0): Validated modes:
(II) Jan 15 12:47:50 NVIDIA(0):     "nvidia-auto-select"
(II) Jan 15 12:47:50 NVIDIA(0): Virtual screen size determined to be 1366 x 768
(--) Jan 15 12:47:51 NVIDIA(0): DPI set to (111, 114); computed from "UseEdidDpi" X config
(--) Jan 15 12:47:51 NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) Jan 15 12:47:51 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Jan 15 12:47:51 NVIDIA(0): ACPI: failed to connect to the ACPI event daemon; the daemon
(II) Jan 15 12:47:51 NVIDIA(0):     may not be running or the "AcpidSocketPath" X
(II) Jan 15 12:47:51 NVIDIA(0):     configuration option may not be set correctly.  When the
(II) Jan 15 12:47:51 NVIDIA(0):     ACPI event daemon is available, the NVIDIA X driver will
(II) Jan 15 12:47:51 NVIDIA(0):     try to use it to receive ACPI event notifications.  For
(II) Jan 15 12:47:51 NVIDIA(0):     details, please see the "ConnectToAcpid" and
(II) Jan 15 12:47:51 NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
(II) Jan 15 12:47:51 NVIDIA(0):     Config Options in the README.
(II) Jan 15 12:47:51 NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) Jan 15 12:47:51 NVIDIA(0):     enough to receive ACPI hotkey events.
(WW) Jan 15 12:47:51 NVIDIA(0): ACPI: Error: Unable to find the brightness file path under
(WW) Jan 15 12:47:51 NVIDIA(0):     /proc/acpi/video. The NVIDIA X driver will not be able to
(WW) Jan 15 12:47:51 NVIDIA(0):     respond to ACPI brightness change hotkey events.
(II) Jan 15 12:47:51 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(==) NVIDIA(0): Disabling shared memory pixmaps
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) Jan 15 12:47:51 NVIDIA(0): Option "TwinViewXineramaInfoOrder" requested "CRT", but no
(WW) Jan 15 12:47:51 NVIDIA(0):     such display device could be found, or all display devices
(WW) Jan 15 12:47:51 NVIDIA(0):     by that name are currently unavailable.
(WW) Jan 15 12:47:51 NVIDIA(0): Option "TwinViewXineramaInfoOrder" requested "TV", but no such
(WW) Jan 15 12:47:51 NVIDIA(0):     display device could be found, or all display devices by
(WW) Jan 15 12:47:51 NVIDIA(0):     that name are currently unavailable.
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX

```

and here is my xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 290.10  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Wed Nov 16 20:32:22 PST 2011

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
    Option         "NoLogo" "True"
    Option         "DynamicTwinView" "False"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection


```

Here is how you can help me:
Do you have a external monitor that you could connect to your ubuntu laptop?
[LIST=1]
[*]Look at your xorg.conf (/etc/X11/xorg.conf).
[*]Connect monitor.
[*]Run nvidia-settings, and configure to run on external monitor.
[*]If theres's any changes to xorg.conf, report what
[/LIST]

---

### Post by bjakke on 2012-01-15
I searched Google for something and found this thread:
[http://www.nvnews.net/vbulletin/showthread.php?t=101858]("http://www.nvnews.net/vbulletin/showthread.php?t=101858")
i copied some of the settings he uses in his xorg.conf to my xorg.conf so now it looks like this:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 290.10  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Wed Nov 16 20:32:22 PST 2011

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
    Option         "UseDisplayDevice" "DFP-1"
    Option         "UseEdidDpi" "DFP-1"
    Option         "RenderAccel" "True"
    Option         "UseEvents" "True"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "RenderAccel" "True"
    Option         "UseEvents" "True"
    BusID          "PCI:1:0:0"
    Screen         1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "DynamicTwinView" "False"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection


```

I haven't tested whether it's the addition of the second device section, or if it's the line     
Option         "UseDisplayDevice" "DFP-1"
that does the trick, but I don't care at this point.

---


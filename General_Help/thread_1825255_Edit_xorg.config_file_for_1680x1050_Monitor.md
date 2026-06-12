---
title: "Edit xorg.config file for 1680x1050 Monitor"
date: 2011-08-15
forum: General Help
---

### Post by dscarfogliero on 2011-08-15
How do I edit this file to include 1680x1050 resolution?


Section "Device"
Identifier	"Configured Video Device"
Driver	 "fbdev"
EndSection

Section "Monitor"
Identifier	"Configured Monitor"
EndSection

Section "Screen"
Identifier	"Default Screen"
Monitor	 "Configured Monitor"
Device	 "Configured Video Device"
EndSection


Thanks!

---

### Post by LowSky on 2011-08-15
Hi, you shouldn't need to edit the xorg by hand.


Can you gives us some information on what kind of computer you are trying to use Ubuntu on.

You may just need to install the correct graphics driver.

---

### Post by WyleECoyote on 2011-08-15
first make sure it is supported with this:
```
xrandr -s 1680x1050
```

if so:

try adding this:
Option	    "PreferredMode" "1680x1050"

after this:
Section "Monitor"
Identifier "Configured Monitor"

to look like this:
Section "Monitor"
Identifier "Configured Monitor"
Option	    "PreferredMode" "1680x1050"
EndSection

if not:

you may need to update or install proprietary drivers for your video card

---

### Post by fdrake on 2011-08-15
tells us furst what king of graphic card you have:

```
lspci | grep VGA
```

---

### Post by realzippy on 2011-08-15
> **WyleECoyote said:**
> first make sure it is supported with this:
```
xrandr -s 1680x1050
```


Even if that xrandr -s command did not work,it might be supported by adding a new mode.
More important is the ouput of "xrandr -q" which shows the maximum screen size possible.

@OP
run

```
xrandr -q 
```
and post ouput

Btw,
Driver "fbdev" might be a problem..

---

### Post by WyleECoyote on 2011-08-15
> **realzippy said:**
> 
```
xrandr -q 
```


nice, even better I will remember this one thanks

---

### Post by dscarfogliero on 2011-08-15
> **fdrake said:**
> tells us furst what king of graphic card you have:

```
lspci | grep VGA
```
Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)

---

### Post by dscarfogliero on 2011-08-15
> **LowSky said:**
> Hi, you shouldn't need to edit the xorg by hand.


Can you gives us some information on what kind of computer you are trying to use Ubuntu on.

You may just need to install the correct graphics driver.
I have an old IBM Lenovo ThinkCentre A55 (Type 8705).

---

### Post by realzippy on 2011-08-15
and
```
xrandr -q
```  ?

---

### Post by dscarfogliero on 2011-08-15
> **realzippy said:**
> and
```
xrandr -q
```  ?
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0*

---

### Post by realzippy on 2011-08-15
[I]Screen 0: minimum 1024 x 768, current 1024 x 768, [COLOR="Red"]maximum 1024 x 768[/COLOR]
default connected 1024x768+0+0 0mm x 0mm
[/I]
[COLOR="Red"]that[/COLOR] is bad.So adding new mode with xrandr will not work.

Try your file with intel as driver instead of vesa/fbdev

```
gksudo gedit /etc/X11/xorg.conf
```

paste in

```
Section    "Device"
Identifier "Configured Video Device"
Option     "ModeDebug"    "True"
Driver     "intel"
EndSection

Section    "Monitor"
Identifier "Configured Monitor"
HorizSync       30.0 - 81.0
VertRefresh     56.0 - 75.0
Option         "DPMS"
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
EndSection  #made by cvt

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
SubSection     "Display"
        Depth       24
        Modes        "1680x1050_60"
    EndSubSection
EndSection

```
reboot..
..if it should not boot,press shift when booting,recovery mode,failsafe X session.
there run
```
sudo rm /etc/X11/xorg.conf
```

---

### Post by dscarfogliero on 2011-08-15
It worked!!!! Thank you so much!

Just a quick question. Does it make a difference between 60 and 75 Refresh?

---

### Post by realzippy on 2011-08-15
No.
Maybe.
Old discussion.
It is no CRT monitor,where increasing Vrefresh
gives a better picture,
On LCD panels this is done by the backlight,which is more then 200 Hz..
Open a thread in the cafe,I am sure monitor nerds have an opinion...  :P

Set thread as solved and have fun!

---

### Post by dscarfogliero on 2011-08-15
Thanks again for all your help!

---

### Post by dscarfogliero on 2011-10-14
> **realzippy said:**
> [I]Screen 0: minimum 1024 x 768, current 1024 x 768, [COLOR="Red"]maximum 1024 x 768[/COLOR]
default connected 1024x768+0+0 0mm x 0mm
[/I]
[COLOR="Red"]that[/COLOR] is bad.So adding new mode with xrandr will not work.

Try your file with intel as driver instead of vesa/fbdev

```
gksudo gedit /etc/X11/xorg.conf
```

paste in

```
Section    "Device"
Identifier "Configured Video Device"
Option     "ModeDebug"    "True"
Driver     "intel"
EndSection

Section    "Monitor"
Identifier "Configured Monitor"
HorizSync       30.0 - 81.0
VertRefresh     56.0 - 75.0
Option         "DPMS"
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
EndSection  #made by cvt

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
SubSection     "Display"
        Depth       24
        Modes        "1680x1050_60"
    EndSubSection
EndSection

```
reboot..
..if it should not boot,press shift when booting,recovery mode,failsafe X session.
there run
```
sudo rm /etc/X11/xorg.conf
```

I was having some problems with Ubuntu so I switched to Fedora. Do you know how to get this to work with Fedora?

---

### Post by fdrake on 2011-10-15
red hat should use the same kind of file /etc/X11/xorg.conf. The new distributions do not need (and have) xorg.conf file by default anymore , but instead they use an app:
```
#system-config-display
```
it's a gui-app. also if you want to create the xorg.conf file just use "Xorg -configure" and copy the new file as /etc/X11/xorg.conf.

---

### Post by dscarfogliero on 2011-10-16
> **fdrake said:**
> red hat should use the same kind of file /etc/X11/xorg.conf. The new distributions do not need (and have) xorg.conf file by default anymore , but instead they use an app:
```
#system-config-display
```
it's a gui-app. also if you want to create the xorg.conf file just use "Xorg -configure" and copy the new file as /etc/X11/xorg.conf.

How do I access the #system-config-display app?

Also if that doesn't work I kept on getting errors when I tried to use Xorg -configure. It was saying that my monitor was already running.

---

### Post by fdrake on 2011-10-16
> 
How do I access the #system-config-display app?


in the terminal:
```
sudo su
<enter root pass>
system-config-display
```

---

### Post by dscarfogliero on 2011-10-16
> **fdrake said:**
> in the terminal:
```
sudo su
<enter root pass>
system-config-display
```

When I try that I get this error:

```
 bash: system-config-display: command not found...
```

---

### Post by dscarfogliero on 2011-10-16
I ran the following commands:

```
Xorg :1 -configure
```

and

```
cp /root/xorg.conf.new /etc/X11/xorg.conf
```

which created a template xorg.conf file (below).

```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "catalogue:/etc/X11/fontpath.d"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "record"
    Load  "dri"
    Load  "dbe"
    Load  "extmod"
    Load  "dri2"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "AccelMethod"            # [<str>]
        #Option     "DRI"                    # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "Shadow"                 # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "RelaxedFencing"         # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card1"
    Driver      "fbdev"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card2"
    Driver      "vesa"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

Can you please inform me on how to edit this for my 1680x1050 monitor? Thanks for the help!

---

### Post by fdrake on 2011-10-16
try first this
1.[http://rpmfind.net/linux/rpm2html/search.php?query=system-config-display](http://rpmfind.net/linux/rpm2html/search.php?query=system-config-display)
download the apropriate rpm for your machine on your desktop!

sudo rpm -i ~/Desktop/<package name>

sudo system-config-display

-----------------------------------------------
if not successful follow:

1. first copy and backup the prev conf file. 

2.find these lines and change the marked one
> 
Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
       **[COLOR="Red"] Modes     "1680x1050"[/COLOR]**
    EndSubSection
EndSection

if you encounter errors , use the live cd and restore the prev file. post here your  "tail -20 ~/.xsession-errors" or "less /var/log/Xorg.0.log" (you may need to check the name for this one! keep in minde of the log rotation at the boot time)


maybe also that your video chip is not supported or has the wrong driver installed. Google around and find out if ppl with your same vid card are successful with this setting.

---

### Post by dscarfogliero on 2011-10-16
> **fdrake said:**
> try first this
1.[http://rpmfind.net/linux/rpm2html/search.php?query=system-config-display](http://rpmfind.net/linux/rpm2html/search.php?query=system-config-display)
download the apropriate rpm for your machine on your desktop!

sudo rpm -i ~/<package name>

sudo system-config-display


When I try this, I get this error:

```

[dscarfogliero@DOMINICK-BETA ~]$ sudo su
[sudo] password for dscarfogliero: 
[root@DOMINICK-BETA dscarfogliero]# sudo rpm -i ~/system-config-display-2.2-1.fc12.i686.rpm
warning: /root/system-config-display-2.2-1.fc12.i686.rpm: Header V3 RSA/SHA256 Signature, key ID e8e40fde: NOKEY
error: Failed dependencies:
    libpython2.6.so.1.0 is needed by system-config-display-2.2-1.fc12.i686
    python(abi) = 2.6 is needed by system-config-display-2.2-1.fc12.i686
[root@DOMINICK-BETA dscarfogliero]# 

```

> 
-----------------------------------------------
if not successful follow:

1. first copy and backup the prev conf file. 

2.find these lines and change the marked one

if you encounter errors , use the live cd and restore the prev file. post here your  "tail -20 ~/.xsession-errors" or "less /var/log/Xorg.0.log" (you may need to check the name for this one! keep in minde of the log rotation at the boot time)


maybe also that your video chip is not supported or has the wrong driver installed. Google around and find out if ppl with your same vid card are successful with this setting.

When I try this Fedora will not even lode. Here is my log file:

```

[    30.056] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    30.056] X Protocol Version 11, Revision 0
[    30.056] Build Operating System: x86-16 2.6.32-131.2.1.el6.x86_64 
[    30.056] Current Operating System: Linux DOMINICK-BETA 2.6.40.6-0.fc15.i686 #1 SMP Tue Oct 4 00:51:19 UTC 2011 i686
[    30.056] Kernel command line: ro root=/dev/mapper/vg_dominickbeta-lv_root rd_LUKS_UUID=luks-b02b0f4a-f324-4c37-8e6c-fe6b2d86569a rd_LVM_LV=vg_dominickbeta/lv_root rd_LVM_LV=vg_dominickbeta/lv_swap rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us nomodeset rhgb quiet
[    30.056] Build Date: 07 September 2011  04:13:44PM
[    30.056] Build ID: xorg-x11-server 1.10.4-1.fc15 
[    30.056] Current version of pixman: 0.20.2
[    30.056]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    30.056] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    30.057] (==) Log file: "/var/log/Xorg.5.log", Time: Sun Oct 16 17:42:41 2011
[    30.057] (==) Using config file: "/etc/X11/xorg.conf"
[    30.057] (==) Using config directory: "/etc/X11/xorg.conf.d"
[    30.057] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    30.058] (==) ServerLayout "X.org Configured"
[    30.058] (**) |-->Screen "Screen0" (0)
[    30.058] (**) |   |-->Monitor "Monitor0"
[    30.058] (**) |   |-->Device "Card0"
[    30.058] (**) |-->Input Device "Mouse0"
[    30.058] (**) |-->Input Device "Keyboard0"
[    30.058] (==) Automatically adding devices
[    30.058] (==) Automatically enabling devices
[    30.058] (**) FontPath set to:
    catalogue:/etc/X11/fontpath.d,
    built-ins,
    catalogue:/etc/X11/fontpath.d,
    built-ins
[    30.058] (**) ModulePath set to "/usr/lib/xorg/modules"
[    30.058] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    30.058] (WW) Disabling Mouse0
[    30.059] (WW) Disabling Keyboard0
[    30.059] (II) Loader magic: 0x8229f20
[    30.059] (II) Module ABI versions:
[    30.059]     X.Org ANSI C Emulation: 0.4
[    30.059]     X.Org Video Driver: 10.0
[    30.059]     X.Org XInput driver : 12.2
[    30.059]     X.Org Server Extension : 5.0
[    30.060] (--) PCI:*(0:0:2:0) 8086:2972:17aa:1015 rev 2, Mem @ 0xd0000000/1048576, 0xc0000000/268435456, I/O @ 0x000018c0/8, BIOS @ 0x????????/131072
[    30.060] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    30.060] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    30.060] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    30.060] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[    30.060] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    30.060] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    30.060] (II) LoadModule: "record"
[    30.061] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    30.061] (II) Module record: vendor="X.Org Foundation"
[    30.061]     compiled for 1.10.4, module version = 1.13.0
[    30.061]     Module class: X.Org Server Extension
[    30.061]     ABI class: X.Org Server Extension, version 5.0
[    30.061] (II) Loading extension RECORD
[    30.061] (II) LoadModule: "dri"
[    30.062] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    30.062] (II) Module dri: vendor="X.Org Foundation"
[    30.062]     compiled for 1.10.4, module version = 1.0.0
[    30.062]     ABI class: X.Org Server Extension, version 5.0
[    30.062] (II) Loading extension XFree86-DRI
[    30.062] (II) LoadModule: "dbe"
[    30.063] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    30.063] (II) Module dbe: vendor="X.Org Foundation"
[    30.063]     compiled for 1.10.4, module version = 1.0.0
[    30.063]     Module class: X.Org Server Extension
[    30.063]     ABI class: X.Org Server Extension, version 5.0
[    30.063] (II) Loading extension DOUBLE-BUFFER
[    30.063] (II) LoadModule: "extmod"
[    30.064] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    30.064] (II) Module extmod: vendor="X.Org Foundation"
[    30.064]     compiled for 1.10.4, module version = 1.0.0
[    30.064]     Module class: X.Org Server Extension
[    30.064]     ABI class: X.Org Server Extension, version 5.0
[    30.064] (II) Loading extension SELinux
[    30.064] (II) Loading extension MIT-SCREEN-SAVER
[    30.064] (II) Loading extension XFree86-VidModeExtension
[    30.064] (II) Loading extension XFree86-DGA
[    30.064] (II) Loading extension DPMS
[    30.064] (II) Loading extension XVideo
[    30.064] (II) Loading extension XVideo-MotionCompensation
[    30.065] (II) Loading extension X-Resource
[    30.065] (II) LoadModule: "dri2"
[    30.065] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    30.065] (II) Module dri2: vendor="X.Org Foundation"
[    30.065]     compiled for 1.10.4, module version = 1.2.0
[    30.065]     ABI class: X.Org Server Extension, version 5.0
[    30.065] (II) Loading extension DRI2
[    30.065] (II) LoadModule: "glx"
[    30.066] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    30.066] (II) Module glx: vendor="X.Org Foundation"
[    30.066]     compiled for 1.10.4, module version = 1.0.0
[    30.066]     ABI class: X.Org Server Extension, version 5.0
[    30.066] (==) AIGLX enabled
[    30.066] (II) Loading extension GLX
[    30.066] (II) LoadModule: "intel"
[    30.067] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    30.067] (II) Module intel: vendor="X.Org Foundation"
[    30.067]     compiled for 1.10.2, module version = 2.15.0
[    30.067]     Module class: X.Org Video Driver
[    30.067]     ABI class: X.Org Video Driver, version 10.0
[    30.067] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    30.069] (--) using VT number 7

[    30.077] (EE) No devices detected.
[    30.077] 
Fatal server error:
[    30.077] no screens found
[    30.077] 
Please consult the Fedora Project support 
     at http://wiki.x.org
 for help. 
[    30.077] Please also check the log file at "/var/log/Xorg.5.log" for additional information.
[    30.077] 

```

---


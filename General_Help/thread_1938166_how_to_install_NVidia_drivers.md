---
title: "how to install NVidia drivers ?"
date: 2012-03-09
forum: General Help
---

### Post by overkill22 on 2012-03-09
i have lubuntu 11.10 on a netbook.
i tried to install nvidia driver:
1) removed nouveau driver, then install nvidia driver with .run packages from nvidia site. 
2) removed nouveau driver, then install nvidia driver with preferences --> additional drivers.

both methods gives me a lot of problem so i decided to reinstall lubuntu for the third times.

now i have

```
xrandr
```results
```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS-1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 256mm x 144mm
   1366x768       60.0*+
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
   720x400        59.6  
   640x400        60.0  
   640x350        59.8  
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
```and

```
lshw
```results
```

*-display
                description: VGA compatible controller
                product: ION VGA [GeForce 9400M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: b1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:21 memory:d2000000-d2ffffff memory:c0000000-cffff
```and

```
glxinfo|grep -i opengl
```results
```

OpenGL vendor string: nouveau
OpenGL renderer string: Gallium 0.4 on NVAC
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20
OpenGL extensions:
```whit nouveau it is not good, for example when the screensaver "fiberlamp" starts it is very very slow and *jerky *(from google translate)

so, what i have to do for install CLEANLY NVidia driver ? (i need the comand i must digit, not general guidelines)

thanx

---

### Post by Grenage on 2012-03-09
Hi there,

Is there a reason you can't install the driver using the "additional drivers" section?  It would certainly be easier.

---

### Post by overkill22 on 2012-03-09
> **Grenage said:**
> Hi there,

Is there a reason you can't install the driver using the "additional drivers" section?  It would certainly be easier.

i tried with additional drivers but then there was a problem, the size of the characters where too big...

with nouveau the resolution is good and the characters are good but there is no 3d acceleration...i think...

---

### Post by Grenage on 2012-03-09
Ok, well it sounds like the drivers installed ok, but the resolution was incorrect.  Have you tried setting the resolution using *xrandr*, when the proprietary drivers are active?

---

### Post by kc1di on 2012-03-09
> **overkill22 said:**
> i tried with additional drivers but then there was a problem, the size of the characters where too big...

with nouveau the resolution is good and the characters are good but there is no 3d acceleration...i think...

It would be helpful to know what video card your using.

Additional drivers should work. did you install the recommended driver?

---

### Post by pootan on 2012-03-09
I would recommend using additional drivers to install Nvidia and then report back here for help on how to adjust your resolution so your character size is more to your liking.

---

### Post by overkill22 on 2012-03-09
> **kc1di said:**
> It would be helpful to know what video card your using.

Additional drivers should work. did you install the recommended driver?

it is all write on the first post, however:

```
description: VGA compatible controller
                product: ION VGA [GeForce 9400M]
```

i've installed first time NVIDIA-Linux-x86-295.20.run.

then i cleaned all with a new lubuntu 11.10 installation
then i tried with recommended driver using preferences --> additional drivers.

nothing to do.

> **Grenage said:**
> Ok, well it sounds like the drivers installed  ok, but the resolution was incorrect.  Have you tried setting the  resolution using *xrandr*, when the proprietary drivers are active?

i don't know how to use xrandr for setting resolution, can you tell me ? 
but can you tell me also the correct way to install nvidia driver ?

---

### Post by Grenage on 2012-03-09
> **overkill22 said:**
> i don't know how to use xrandr for setting resolution, can you tell me ? 
but can you tell me also the correct way to install nvidia driver ?

Start with this, but obviously you'll want to replace the resolution with one of your choosing.

```
xrandr --output LVDS-1 --mode 1024x768
```

---

### Post by overkill22 on 2012-03-09
> **pootan said:**
> I would recommend using additional drivers to install Nvidia and then report back here for help on how to adjust your resolution so your character size is more to your liking.

before install nvidia driver i have to remove nouveau driver ?
if i use additional drivers to install nvidia driver, i see 2 possibility:

1) Nvidia driver (current version)  [reccomended]
2) nvidia driver (updates post-release) [version current-updates)

which one ?

---

### Post by Grenage on 2012-03-09
Don't worry about removing any drivers, just choose the (recommended) driver listed. :)

---

### Post by overkill22 on 2012-03-09
> **Grenage said:**
> Start with this, but obviously you'll want to replace the resolution with one of your choosing.

```
xrandr --output LVDS-1 --mode 1024x768
```


ok, i want to be shure and make without mistake.
now i will install reccomended driver. then i will post some screenshots. wait 10 minutes..

---

### Post by overkill22 on 2012-03-09
done.
see the attachments.

before NO driver-GOOD resolution
now WITH driver-BAD resolution

---

### Post by Grenage on 2012-03-09
Resolutions aren't normally a nightmare to resolve, so that's good news.  What happens when you try the xrandr command?  xrandr commands are not persistent, so if something goes wrong, it will only last until you reboot the PC (or reload x).

Make sure that you use the correct resolution with the xrandr command, the one I gave you was just an example.

---

### Post by overkill22 on 2012-03-09
now i have:

```
glxinfo|grep -i opengl
```

```
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: ION/PCI/SSE2
OpenGL version string: 3.3.0 NVIDIA 280.13
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL extensions:
```

```
xrandr 
```

```
xrandr: **[COLOR=Red]Failed to get size of gamma for output default[/COLOR]**
Screen 0: minimum 320 x 175, current 1366 x 768, maximum 1366 x 768
default connected 1366x768+0+0 0mm x 0mm
   1366x768       50.0* 
   1024x768       51.0     52.0  
   960x540        53.0  
   840x525        54.0  
   832x624        55.0  
   800x600        56.0     57.0     58.0     59.0     60.0  
   800x512        61.0  
   720x450        62.0  
   720x400        63.0  
   700x525        64.0  
   680x384        65.0     66.0  
   640x512        67.0     68.0  
   640x480        69.0     70.0     71.0     72.0     73.0  
   640x400        74.0  
   640x350        75.0  
   576x432        76.0     77.0     78.0     79.0     80.0     81.0  
   512x384        82.0     83.0     84.0     85.0     86.0  
   416x312        87.0  
   400x300        88.0     89.0     90.0     91.0     92.0  
   360x200        93.0  
   320x240        94.0     95.0     96.0     97.0  
   320x200        98.0  
   320x175        99.0  
```

now i must try with your command 
```
xrandr --output LVDS-1 --mode 1366x768
```

???

---

### Post by Grenage on 2012-03-09
Yup, try that.  You can not harm your system by trying resolutions.

---

### Post by overkill22 on 2012-03-09
done but:

```
xrandr: Failed to get size of gamma for output default
warning: output LVDS-1 not found; ignoring
```

---

### Post by Grenage on 2012-03-09
I'm guessing that the port name changes with the drivers, try:

```
randr --output LVDS --mode 1366x768
```

Failing that, post the output of:

```
xrandr -q
```

---

### Post by overkill22 on 2012-03-09
first, like you wrote:

```
utente@lubuntu:~$ [COLOR=Red]randr[/COLOR] --output LVDS --mode 1366x768
Comando "randr" non trovato. Forse si intendeva:
 Comando "grandr" dal pacchetto "grandr" (universe)
 Comando "rand" dal pacchetto "rand" (universe)
 Comando "xrandr" dal pacchetto "x11-xserver-utils" (main)
 Comando "arandr" dal pacchetto "arandr" (universe)
randr: comando non trovato
```

second like i supposed:

```
utente@lubuntu:~$ xrandr --output LVDS --mode 1366x768
xrandr: Failed to get size of gamma for output default
warning: output LVDS not found; ignoring
```

then xrandr comand

```
utente@lubuntu:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1366 x 768, maximum 1366 x 768
default connected 1366x768+0+0 0mm x 0mm
   1366x768       50.0* 
   1024x768       51.0     52.0  
   960x540        53.0  
   840x525        54.0  
   832x624        55.0  
   800x600        56.0     57.0     58.0     59.0     60.0  
   800x512        61.0  
   720x450        62.0  
   720x400        63.0  
   700x525        64.0  
   680x384        65.0     66.0  
   640x512        67.0     68.0  
   640x480        69.0     70.0     71.0     72.0     73.0  
   640x400        74.0  
   640x350        75.0  
   576x432        76.0     77.0     78.0     79.0     80.0     81.0  
   512x384        82.0     83.0     84.0     85.0     86.0  
   416x312        87.0  
   400x300        88.0     89.0     90.0     91.0     92.0  
   360x200        93.0  
   320x240        94.0     95.0     96.0     97.0  
   320x200        98.0  
   320x175        99.0  
```

---

### Post by Grenage on 2012-03-09
You supposed correctly. ^^

Forgive me but I forgot about the nvidia-settings utility, which is what we really want to try first (it's been a long morning).

```
sudo apt-get install nvidia-settings
```

It may already be installed.  Then use:

```
gksu nvidia-settings
```

If you change the resolution there, is it ok?

---

### Post by overkill22 on 2012-03-09
the resolution here is correct.
when i tryed first and second time i controlled all this stuff... :(

---

### Post by Grenage on 2012-03-09
I'm not quite following you.

Are you saying that in nvidia-settings, it lists the resolution you want, and you can click "Save to X configuration File", but it doesn't change the resolution?

---

### Post by overkill22 on 2012-03-09
> **Grenage said:**
> I'm not quite following you.

Are you saying that in nvidia-settings, it lists the resolution you want, and you can click "Save to X configuration File", but it doesn't change the resolution?

i mean if i go to the nvidia-settings i can see that the settings are ok, but i didn't made "Save"... now i saved and create the xorg file.
now pc is in rebooting....

---

### Post by overkill22 on 2012-03-09
no way...i will take some screenshot

---

### Post by overkill22 on 2012-03-09
look nvidia-settings

---

### Post by Grenage on 2012-03-09
It looks like it might be the right resolution now, but I find it hard to tell.  Is it?

---

### Post by overkill22 on 2012-03-09
> **Grenage said:**
> It looks like it might be the right resolution now, but I find it hard to tell.  Is it?

i don't understand what you mean...
the right resolution for me is the one you can see [HERE]("http://ubuntuforums.org/showpost.php?p=11751023&postcount=12"), screenshot named "no_driver.png" .... 
now this isn't right resolution...

---

### Post by overkill22 on 2012-03-09
it seems that xrandr has some problem after installing nvidia drivers... it doesn't found LVDS...

---

### Post by Grenage on 2012-03-09
It looks like the proprietary driver doesn't work with xrandr so well, although others may have input.

Can you post a copy of your /etc/X11/xorg.conf, and also the model/make of your netbook?

---

### Post by overkill22 on 2012-03-09
> **Grenage said:**
> It looks like the proprietary driver doesn't work with xrandr so well, although others may have input.

Can you post a copy of your /etc/X11/xorg.conf, and also the model/make of your netbook?

pc is compaq mini 311 model 311c-1025EL.

xorg.conf

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 280.13  (buildd@rothera)  Fri Aug  5 12:28:41 UTC 2011


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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
EndSection

Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select +0+0"
# Removed Option "metamodes" "1366x768 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

oter information in attachment

---

### Post by Grenage on 2012-03-09
Try replacing that.

```
gksu gedit /etc/X11/xorg.conf
```

Remove what's there, and paste in:

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1366x768"
    EndSubSection
EndSection
```

---

### Post by overkill22 on 2012-03-09
> **Grenage said:**
> Try replacing that.

```
gksu gedit /etc/X11/xorg.conf
```Remove what's there, and paste in:

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1366x768"
    EndSubSection
EndSection
```

done but nothing changed

---

### Post by Grenage on 2012-03-09
Try adding a modeline; so that your config looks like this, then restart.

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1366x768"
    EndSubSection
EndSection
```

---

### Post by overkill22 on 2012-03-09
what would this make ?

---

### Post by Grenage on 2012-03-09
It specifies a video mode; I've seen it solve ignored resolutions many a time.

---

### Post by overkill22 on 2012-03-09
ntohing to do. when i save xorg.conf i reboot the system. but nothing.

---

### Post by Grenage on 2012-03-09
I am at a total loss, if the current display is not 1368x768.

---

### Post by overkill22 on 2012-03-09
> **Grenage said:**
> I am at a total loss, if the current display is not 1368x768.

is the same problem i had on my notebook with ubuntu 10.04 , but a don't remember how i solve it, it was 2 years ago...
i think we had made a lot of attempts... now i will remove the nvidia driver hope that someone will help us to find the problem...
thank you for your time it was precious however !

---

### Post by Grenage on 2012-03-09
No problem, it's a shame we didn't get to the bottom of it.  If you do fix it, please let me know what you did. :)

---

### Post by overkill22 on 2012-03-10
i will ;)

---


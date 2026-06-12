---
title: "NVidia-settings crashes."
date: 2010-10-16
forum: General Help
---

### Post by Meneer Jansen on 2010-10-16
When I run 'nvidia-settings' for my NVidia 7600GS graphics card (driver ver. 173) then it crashes with the following error on the command line:

```

The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
 *(Details: serial 376 error_code 2 request_code 140 minor_code 19)
 *(Note to programmers: normally, X errors are reported asynchronously;
 * that is, you will receive the error a while after causing it.
 * To debug your program, run it with the --sync command line
 * option to change this behavior. You can then get a meaningful
 * backtrace from your debugger if you break on the gdk_x_error() function.)

```

This only happens when I try to adjust anything in the "GPU0" section (for example the TV out overscan). The other sections (xscreen 0 and 1) are fine.

How can I solve this?

---

### Post by P4man on 2010-10-16
Why are you using the 173 series drivers? Your card is still supported by the 260 series. Which version of ubuntu are you using?

---

### Post by Meneer Jansen on 2010-10-16
Thank you for your kind reply. I use Ubuntu 10.04 The Lucid Lynx. If I search in Synaptic then I can see some "nvidia-180-glx" stuff. But no 260 stuff. What is the latest Nvidia driver in Ubuntu? The 260 series? I'd like to install a driver that is as new as possible.

---

### Post by Meneer Jansen on 2010-10-16
Wait. I saw a "nvidia-current" package in Synaptic. That installed a 195.36.24-0ubuntu1~10.04 version of the driver. This also installed a 195.36 version of nvidia-settings which also crashes on anything listed under the "GPU0" section.

---

### Post by P4man on 2010-10-16
Are you sure it also updated nvidia-settings app? 

Try this
```

sudo apt-get remove --purge nvidia-settings
sudo apt-get install nvidia-settings
```

If that doesnt help, then I suspect you have some leftovers from the old drivers (that should never have been installed in the first place? Didnt jocky offer 195 drivers?). Anyway, try deleting or renaming your xorg.conf

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.back
```

last thing you could try:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Meneer Jansen on 2010-10-16
Thank you very much for your tips! I made the mistake to look in Synaptic for my driver version, when I should have consulted nvidia-settings for that.

After installing "nvidia-current" the used driver was still version 173. With trembling hands (wouhar!) I removed all version 173 things and rebooted.

Now nvidia-settings **works**!!! And the driver version is now 195. Wonder if I'll ever get version 260. :)

---

### Post by P4man on 2010-10-16
> **Meneer Jansen said:**
> Thank you very much for your tips! I made the mistake to look in Synaptic for my driver version, when I should have consulted nvidia-settings for that.

First mistake you made is installing it through synaptic. Ubuntu has such a nice utility to find and install drivers (system >adminstration>additional drivers), just use that :). Next stop is ubuntu software center

> Now nvidia-settings **works**!!! And the driver version is now 195. Wonder if I'll ever get version 260. :)

You already have. Its confusing and I dont understand it quite myself, but 185 or 195 seems to be the version of glx package, but it includes 260.19.6 drivers (according to software center). On nvidia site, the newest are barely any newer, 260.19.12.

---

### Post by Meneer Jansen on 2010-10-17
> **P4man said:**
> First mistake you made is installing it through synaptic. Ubuntu has such a nice utility to find and install drivers (system >adminstration>additional drivers), just use that :). Next stop is ubuntu software center

That's what I did in the first place and it installed 173...

> **P4man said:**
> 
You already have [driver 260]. Its confusing and I dont understand it quite myself, but 185 or 195 seems to be the version of glx package, but it includes 260.19.6 drivers (according to software center). On nvidia site, the newest are barely any newer, 260.19.12.
Thank you for the info. :)

---

### Post by TheSixthPandava on 2010-10-30
Sorry to bring this topic again, but I have exact problem, only mine isn't solved when I install nvidia-current [which installs 195] and remove all other versions. 

Should xserver-xorg-video-nouveau and xserver-xorg-video-nv be installed? I know I had them installed, but I removed them during this process, as I thought that they are somehow connected to my problem.

Anyhow, I installed nvidia-current as I said, but now, following nvidia-settings note that I should run

```
$ sudo nvidia-xconfig
```

and restart X as nvidia-settings tells me, virtually nothing happens, the screen just wents black. Installing xserver-xorg-video-nouveau and xserver-xorg-video-nv again isn't changing anything.

When I restart the system, it brings up that drivers failed. 

I installed nvidia-current from terminal, since when I go to System > Administration > Hardware Drivers nothing is shown.

---

### Post by P4man on 2010-10-30
First of all, what videocard do you have?

Secondly, try removing or renaming xorg.conf before running nvidia-xconfig

---

### Post by TheSixthPandava on 2010-10-30
> **P4man said:**
> First of all, what videocard do you have?

Secondly, try removing or renaming xorg.conf before running nvidia-xconfig

I'm using nVidia G-Force FX5200 128 mb.

I've tried that, nothing changes. I installed back 173 along with nvidia-current thinking that maybe 173 will serve as transitional, but still nothing changes.

---

### Post by TheSixthPandava on 2010-10-30
Alright. This is what happens. When I remove only xserver-xorg-video-nouveau, delete xorg.conf and restart the system, my resolution is back to normal. I then run sudo nvidia-config, again I restart and the following message comes up:

> The following error was encountered. You may need to update your configuration to solve this.
(EE) NVIDIA: Failed to load the NVIDIA kernel module.
Please check your
(EE) NVIDIA: system's kernel log for additional error messages.
(EE) Failed to load module &#8220;nvidia&#8221; (module-specific error, 0)
(EE) No drivers available.

EDIT: This time I tried only to run in low graphics mode, previosly restarting X from this point didn't help, and neither did reconfiguring graphical settings.

Nvidia-settings still won't open, it again says that I should run nvidia-config and restart X. 

I also checked in System > Administration > Hardware drivers, it says that nvidia-current is activated but not currently in use. But I can't get it in use, because of this problem.

---

### Post by P4man on 2010-10-30
Your videocard is no longer supported by nvidia-current, only by 173 legacy drivers. Jockey should have proposed that one but  I remember an issue with the 173 drivers not installing on top of nouveau, something I think was only fixed by nvidia recently, I dont know if that made its way to the ubuntu repo's yet, but probably why it wasnt proposed.

I would purge the drivers you have now and nvidia-settings. Then grab the latest from nvidia website here:
[http://www.nvidia.co.uk/object/linux-display-amd64-173.14.28-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-173.14.28-driver-uk.html)

(thats for **AMD64** for 32 bit browse to the appropriate download page). Make sure you right click the installer and select "save as". Make the file executable and run it in a terminal.

---

### Post by TheSixthPandava on 2010-10-30
Thank you very much for your replies.

I did all of this and it said to me that it is installed. However, it isn't shown in System > Administration > Hardware drivers [I presume because nvidia-common isn't installed] and their is no nvidia-settings. **Can I install nvidia-settings freely now from ubuntu repositories, and can I do that for nvidia-common also?** Nvidia setting are of course more important.

---

### Post by LeoMunky on 2012-06-26
Sorry to bring back an old thread, but I'm having the same exact problem as The SixthPandava. I'm using the nvidia drivers 173.14.31 with an nvidia geforce fx 5200 128mb. whenever changing any settings under the 'GPU 0' tab, I get;

```
The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 371 error_code 2 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```Tried everything I could find, nothing fixes it. I'm trying to fix my tv output overscan.

---

### Post by LeoMunky on 2012-06-26
Also, xorg.conf is as follows;

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Sun Jul 17 22:46:17 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
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
    ModelName      "LG EW224"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by Elfy on 2012-06-26
Closed - please start your own thread.

---


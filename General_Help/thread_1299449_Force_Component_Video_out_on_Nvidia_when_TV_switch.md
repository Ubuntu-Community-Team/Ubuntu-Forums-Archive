---
title: "Force Component Video out on Nvidia when TV switched off"
date: 2009-10-23
forum: General Help
---

### Post by mickyp on 2009-10-23
Hi all,
 
**I have solved my problem, please see my reply (#7) below for the solution.  **
 
**Link here (opens in a new window): [http://ubuntuforums.org/showpost.php?p=8234325&postcount=7](http://ubuntuforums.org/showpost.php?p=8234325&postcount=7)**
 
Apologies in advance if the answer is easy or could be found elsewhere. I have searched with no results.
 
I would like to force Ubuntu to send a signal over component regardless of whether the TV is switched on or off when the computer is started.
 
I am running Ubuntu 9.04 using the latest Nvidia beta drivers (190.42) for my GTS250. I run 720p over component video through an amplifier then to my TV as my HTPC.
 
The only remaining niggle I have is that the TV and amplifier must be switched on before the computer is turned on. If the TV and amplifier are not switched on, with the correct video channels selected, no video signal is sent over component. It seems like ubuntu detects that the display is not "attached" and chooses not to display anything on it. How can I force ubuntu to output to component even when the TV is switched off at boot?
 
The display sections of my xorg.conf:
 
```

Section "Monitor"
    Identifier     "Monitor0"
EndSection
 
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 250"
EndSection
 
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TVStandard" "HD720p"
    Option         "ConnectedMonitor" "Monitor0"
    Option         "TwinView" "0"
    Option         "metamodes" "1280x720 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
 
Thank you very much in advance,
 
Michael

---

### Post by odeatbe on 2009-10-23
i am not good at this, anyone here?

---

### Post by Giblet5 on 2009-10-23
It probably only matters that the amp is on when the PC is started. As the card does its self-test thing and probes the connections, it needs to see a live output or it will ignore that output connector. It does all that before it ever displays anything on the screen about the PC's self tests.

If the amp is on at powerup, and when the driver initializes and the GUI starts, the component output should remain alive.

Component video is very limited in functionality. There is likely nothing you can do about this behavior.

I got around this by connecting the PC directly to the TV's DVI jack and programming the R/C macro to power on the TV, then the PC, then switch the TV input to DVI. Much better video, and it just works.

---

### Post by brookie on 2009-10-23
Hope this helps. This is how I forced TV out on S-video: 

Section "Device"
    Identifier      "Radeon 9000"
    Driver          "ati"
    BusID           "PCI:1:0:0"
    Option          "monitor-LVDS"          "laptop"
    Option          "TVDACLoadDetect"       "TRUE"
    Option          "TVStandard"            "ntsc"
    Option          "monitor-S-video"       "SONY"
EndSection

Cheers, 
Brook

---

### Post by fergalm on 2009-10-27
This is more of a work around than a solution, but I use the following two commands to turn on the S-video output:


```
xrandr --output S-video --set load_detection 1
xrandr --output S-video --auto
```

---

### Post by brookie on 2009-10-31
> **fergalm said:**
> This is more of a work around than a solution, but I use the following two commands to turn on the S-video output:


```
xrandr --output S-video --set load_detection 1
xrandr --output S-video --auto
```

Thanks, that worked on this new karmic install. My last xorg.conf file above did not work in karmic any more. 

Any ideas how to add these commands to an xorg.conf file so that this can be permanent so that the TV/Monitor can be turned on/off in System/Preferences/Display.

---

### Post by mickyp on 2009-11-03
Hi all,
 
I recently had some time to go through the Nvidia readme, and have solved my problem. My Nvidia GTS 250 video card now forces component video out regardless of the state of the TV / Amplifier. I am using Nvidia Linux 32 bit drivers version 190.42 on Ubuntu 9.10.
 

My references from the Nvidia readme:
[LIST]
[*]Appendix C: [http://us.download.nvidia.com/XFree86/Linux-x86/190.42/README/appendix-c.html](http://us.download.nvidia.com/XFree86/Linux-x86/190.42/README/appendix-c.html)
[*]Configuring TwinView (although I am not using two screens, so this is disabled for me) [http://us.download.nvidia.com/XFree86/Linux-x86/190.42/README/chapter-13.html](http://us.download.nvidia.com/XFree86/Linux-x86/190.42/README/chapter-13.html)
[/LIST]Please note that this simply works for me, and I'm not sure whether it is entirely correct. It is also a Nvidia graphics card (I have no idea about ATI).
 
I had previously tried using the "ConnectedMonitor" option, but it had no effect. The reason (I believe) is because you have to use the name assigned to the device by the graphics card. See Appendix C for Nvidia Display Device Names. In my case this was TV-0.
 

I found the name of my device (TV-0) by[LIST=1]
[*]Starting the computer with the desired TV connected and switched on (this was the only monitor attached).
[*]I then opened /var/log/Xorg.0.log and scrolled through to find:
[/LIST]```

(--) Nov 04 08:23:35 NVIDIA(0): Connected display device(s) on GeForce GTS 250 at PCI:3:0:0:
(--) Nov 04 08:23:35 NVIDIA(0): NVIDIA TV Encoder (TV-0)

```
 

Then in /etc/X11/xorg.conf I changed[LIST=1]
[*]the "Identifier" in monitor to "TV-0"
[*]the "Monitor" in screen to "TV-0"
[*]the "ConnectedMonitor" option in screen to "TV-0"
[/LIST]My new xorg.conf:
 
```

Section "Monitor"
     Identifier "TV-0"
EndSection
 
Section "Device"
     Identifier "Device0"
     Driver "nvidia"
     VendorName "NVIDIA Corporation"
     BoardName "GeForce GTS 250"
EndSection
 
Section "Screen"
     Identifier "Screen0"
     Device "Device0"
     Monitor "TV-0"
     DefaultDepth 24
     Option "TVStandard" "HD720p"
     Option "ConnectedMonitor" "TV-0"
     Option "TwinView" "0"
     Option "metamodes" "1280x720 +0+0"
     SubSection "Display"
          Depth 24
     EndSubSection
EndSection

```
 
Hopefully this helps others! I am no expert, just a new linux user finding my way, but feel free to reply / ask questions.
 
Regards,
 
Michael

---


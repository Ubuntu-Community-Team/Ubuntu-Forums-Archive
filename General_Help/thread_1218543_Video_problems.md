---
title: "Video problems"
date: 2009-07-20
forum: General Help
---

### Post by Meuro on 2009-07-20
Hi guys.  I'm newish to Ubuntu.  I've experimented before but now I'm actually going to make the move for good.

I've been having lots of trouble with getting video and dvd to work properly.  I've finally managed to get DVDs to play on VLC but not any other media player.

However the problem is that, whether avi/video file or DVD or flash, if the window is too big or fullscreen, playback become very choppy and unwatchable.
I've followed the "[ Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683&page=7")" 

I've spent several hours already trawling through the forums so any help you could give me would be much appreciated.

System Setup:

Ubuntu 9.04 Desktop
inno3d 7600 graphics card
3GHz HT P4 processor
1GB ram

---

### Post by Meuro on 2009-07-21
I should also say that when the movement in teh video or dvd is quick, it gets jumpy aswell

---

### Post by Greenwidth on 2009-07-21
Just to make sure, do you have the nvidia driver enabled in:
System > Admin > Hardware Drivers ?

---

### Post by Meuro on 2009-07-21
Ah indeed I did not have the nvidia drivers activated.  Its made a huge difference.  Its still not quite perfect watching iplayer - its still a bit jittery and tearing still does occur but I suspect thats a flash issue.

Thanks very much for your help.  Now... to see if the projector will work with the linux...

---

### Post by Greenwidth on 2009-07-21
I can't remeber if "nvidia-settings" is enabled with the driver or not - its in the repo:
System > Admin > Nvidia X server Settings
theres 2 'Sync to V Blank' which should be checked.

Also from this page at Adobe:
[http://bugs.adobe.com/jira/browse/FP-1692](http://bugs.adobe.com/jira/browse/FP-1692)

This bit helps as well:
The solution below works with Nvidia 32 bit systems:

1. sudo mkdir /etc/adobe

2. sudo nano /etc/adobe/mms.cfg

3. Paste "OverrideGPUValidation=true" (without quotation marks)

4. Restart Firefox.

The above sadly does not work with the 64 bit Flash.

---

### Post by Meuro on 2009-07-21
Thanks for the tips.  They both do make a difference and I've managed to get the projector connected and working under the twinview.  Theres only a couple of bugs that seem to have appeared.  One is that when you click fullscreen on iplayer, it plays fullscreen on the monitor, not the projector.
The other is that I was watching a dvd and it stopped randomly at a point in the film and wouldn't play further.  If you tried to go past it, it would stop or crash.  This was true for GNOME mplayer, VLC, and the totem movie player.  I've not properly tested it with other dvds so I cant say for sure if its the disc or the drive or the system.

---

### Post by Meuro on 2009-07-21
Ok i dont think its the disc.  It plays fine on mpclassic on my windows laptop.

---

### Post by Greenwidth on 2009-07-21
Thats odd..
Is the DVD stopping at the same point each time and with each player?

---

### Post by Meuro on 2009-07-21
yup.  and in trying to skip past the part it stopped at, i crashed GNOME mplayer.  but no probs with wmc in windows.

---

### Post by Meuro on 2009-07-21
yup.  and in trying to skip past the part it stopped at, i crashed GNOME mplayer.  but no probs with wmc in windows.

---

### Post by 0pul3nce on 2009-07-21
Hello can anyone help me...i've got flash videos in firefox that start glitching. I can never have two or more windows open without the glitching, sometimes i get it with just one video. (noticable when varying from small to large)

I've got a powerful system, which can cope when in vista..with numerous videos playing. So i'm confident hardware is not the issue.

I've done an update on my graphic driver to Nvidia 180.44

I've not found help in the forums i've read so far, and i think it's because i'm running Linux-x86_64.

Please advise me how to fix this bug.

---

### Post by Greenwidth on 2009-07-21
Have you got the DVD playback packages installed (Section 4/5 of the link you posted)?
```
sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4
```

Try running totem from the console to see if you get any error messages.
```
totem /path/toDVD/
```

I forgot there is another 'Vsync to Blank' to enable in Compiz, you will need to get 'compizconfig-settings-manager' from the repo then:
System > Preferences > Compiz Settings
General Options > Display Settings > Sync is at the bottom.

---

### Post by Meuro on 2009-07-22
I redid the apt-get dvd stuff just in case.  It now does play past the point it did so perhaps its fixed.

One final last hurdle and I'll be at the point where my windows machine was.  
I thought everything was good until I restarted my computer and it loaded up all the display settings wrong.  It doesn't want to start with the dvi-d as the default/primary monitor.  So I have to take the analogue output which is normally plugged into the projector and plug it into the monitor.  Then once I can see what I'm doing much jiggery-pokery and frustration occurs until I get it the way I wanted it only for it to forget everything next time I restart the comp.  I've tried doing "Save to X Configuration File" but it gives the error "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'." and the config doesn't seem to take as everything falls apart next restart.

---

### Post by Greenwidth on 2009-07-22
"Save to X Configuration File" is the one in nvidia x server settings?

You need to be root to save to xorg.conf:
```
gksudo nvidia-settings
```
and your saved settings should stick.

---

### Post by Meuro on 2009-07-22
do you ever feel that sometimes linux just takes the piss, just to annoy you?  to answer every one of your solutions with a another problem?  You've single handedly managed to fix all my problems to date but with each one has come another.  The latest is that before iplayer played fine fullscreen, but now since changing the xorg.conf, it has become choppy fullscreen.  it seems fine played normally in the window but it changes going fullscreen.  avi videos and that play fine fullscreen as do dvds.  but i cant see how i've changed things for iplayer

---

### Post by Greenwidth on 2009-07-22
I can't think why that would have changed flash playback.
Can you post your xorg.conf, and the backup for comparison.
The files are in /etc/X11/

---

### Post by Greenwidth on 2009-07-23
If you: 
sudo nvidia-settings (check Vsync in OPenGL section is ticked)
close settings
Try iPlayer again fullscreen any difference?

---

### Post by Meuro on 2009-07-23
I've tried putting iplayer on either screen but there is no improvement.  (it should be noted that in twinview, the second screen has to be to the left of the first otherwise it will not fullscreen properly([http://ubuntuforums.org/showthread.php?p=7458326](http://ubuntuforums.org/showthread.php?p=7458326)).  So i tried the separate desktop thing and it switched round which was the primary monitor (ubuntu is forever trying to make the analogue output the primary and the dvi-d the secondary when i want it the other way round so i tried some poking about and editing of the conf which royally broked it) meaning I had to start again with a new xorg.conf and the problems remains.  I've put the xorg.conf as it is now below just in case there is somehting in there to provide enlightenment.


i tried changing the OpenGL settings and there is no difference.  

+++++++++++++++++

```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    ModelName      "OPTi Optoma EP720"
    HorizSync       30.0 - 100.0
    VertRefresh     48.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1280x1024 +1280+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Greenwidth on 2009-07-23
Theres nothing in there that I can see would be a problem, i've no experience with twinview though.

For the monitors swapping you could try adding to System > Preferences > Startup Applications (Add > paste into command)
```
nvidia-settings --load-config-only
```

For Flash add this to the end of your xorg.conf
```
Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```

Both will need a restart (X or PC)

These may or may not be useful but beyond that I'm out of ideas..

---


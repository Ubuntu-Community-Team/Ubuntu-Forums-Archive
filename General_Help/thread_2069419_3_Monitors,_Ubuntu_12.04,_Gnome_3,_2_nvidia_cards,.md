---
title: "3 Monitors, Ubuntu 12.04, Gnome 3, 2 nvidia cards, WITH xrandr or xinerama?"
date: 2012-10-10
forum: General Help
---

### Post by DJYoshaBYD on 2012-10-10
Ok. I have been banging my head against the wall for over a week now trying to get 3 monitors to work.

I have:

1 - Nvidia 8600 GT 512MB PCIEx16

1 - Nvidia GT 240 1GB PCIEx16

They are not running in SLI (obviously). I have tried to use everything from tutorials to a few templates, all the way up to nvidia-settings, etc etc etc.. From what I hear, Xinerama doesnt like gnome 3 because of the compositing, although I have read a lot about using Xrandr instead, and getting the compositing working, but alas, I cannot. It always either crashes X and I have to replace the xorg.conf with my backup, or it defaults to the gnome-classic desktop, and on top of that, when it does default, it keeps adding more and more panels.

Basically, I want to be able to use all 3 monitors (yes, just like in windows) to drag and drop from different windows.

I have xorg-edit, but I am still not too sure on how to set this up? Is there any way to:

A> Get compositing working with 3 monitors, 2 nvidia cards, xinerama, and gnome 3?

or

B>Use twinview with 3 monitors (I have heard it can be done by manually editing xorg.conf)

or

C>Set up Xrandr to draw all 3 monitors with compositing.

or

D>Use separate X for each monitor, and be able to use gnome with compositing, as well as drag between all 3

or

E>ANYTHING. lol. I just want this to work.

Any help you can provide would be greatly appreciated. BTW, I am running an ubuntu mini install with gnome. Everything works great but this. I can run it fine with 2 monitors and compositing, but not with 3.

Also, what is the best GUI tool for editing xorg.conf? Im not finding anything that is up to date at all, and also is understandable by humans. haha. Im actually an engineer by trade, and have been working with computers a LONG time, but this xorg.conf stuff is really confusing the crap out of me. lol

Thanks!

---

### Post by 3Miro on 2012-10-10
People use and recommend Nvidia drivers because they give good performance, however, they don't play nice with native tools. I cannot even set two monitors on one video card with anything other than Nvidia-settings.

Backup your xorg.conf (better safe then sorry). Then run:
```
gksudo nvidia-settings
```
now you can use the "save to Xorg configuration file" option in the Display menu. This is your only hope of getting anything Nvidia to work and your changes will persist after rebooting 

Some of the changes require you to reboot Xorg, but if you don't save the changes to xorg.conf then nothing will happen, and you can only save the changes if you have permission to write over xorg.conf, and only the super user can write to xorg.conf, hence you need "gksudo".

---

### Post by DJYoshaBYD on 2012-10-10
?????

Umm, yeah. Those are the basics I have been over that. nvidia-settings does not give an option that works with compiz/graphics, 3 monitors, and nvidia running on gnome 3. You have to basically edit the xorg.conf by hand, which I have done. I need a more advanced answer, as the solution is not a point-and-click one. That would be sweet if there were, though. :)

---

### Post by Favux on 2012-10-10
In retrospect you might have been better off posting in Multimedia & Video where maybe one of the video gurus would have been more likely to help.

What does your current xorg.conf look like?

Does the Nvidia settings gui show you both video cards and all three monitors?  If so I would think you should be able to set up two monitors on TwinView on one card and the third screen on the second card as a separate X monitor.  I think it is Xinerama that breaks compositing but not TwinView, but I'm ready to be corrected.

It sounds like you already have links to the Nvidia settings:
[http://manpages.ubuntu.com/manpages/oneiric/en/man1/nvidia-settings.1.html](http://manpages.ubuntu.com/manpages/oneiric/en/man1/nvidia-settings.1.html)
[http://manpages.ubuntu.com/manpages/precise/man1/alt-nvidia-current-xconfig.1.html](http://manpages.ubuntu.com/manpages/precise/man1/alt-nvidia-current-xconfig.1.html)

I was able to get dual monitors working with the Nouveau driver:
```
## HP TX2000 tablet PC xf86-video-nouveau driver dual monitor xorg.conf
## 00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce Go 6150] (rev a2)

Section "Device"
    Identifier     "GeForce_Go_6150"
    Driver         "nouveau"
    VendorName     "NVIDIA Corporation"
    BusID          "PCI:0:5:0"
    Option         "RandRRotation" "on"      # enable rotation
EndSection

Section "Monitor"
    Identifier     "LVDS-1"
    VendorName     "HP"
    ModelName      "Unknown"
    HorizSync       24.0 - 94.0
    VertRefresh     50.0 - 76.0
    Option         "PreferredMode" "1280x800"
EndSection

Section "Monitor"
    Identifier     "VGA-1"
    VendorName     "HP"
    ModelName      "HP_2310m"
    Option         "RightOf"       "LVDS-1"
#    Option         "LeftOf"        "LVDS-1"
#    Option         "Above"         "LVDS-1"
#    Option         "Below"         "LVDS-1"
    Option         "PreferredMode" "1920x1080"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "GeForce_Go_6150"
    Monitor        "LVDS-1"
    DefaultDepth    24
    SubSection     "Display"
        Depth           24
        Virtual         3200 1080
#        Virtual         4096 4096            # GeForce Go 6150 max.
    EndSubSection
EndSection
```
Don't know if that is a way to go for you.  You'd need a separate Device section for the other card.  And a Monitor section for the third monitor.  Then a Screen section specifying the second card and third monitor.  Don't know if at that point you'd need a "ServerLayout" section specifying the layout of the 3 monitors.  Maybe not, that seems to have become optional.

I had to disable the XrandR plugin for the gnome-settings-daemon because the default mirror setting interferes.  I guess the Nvidia gui had been hiding that little issue.  First install dconf-editor:
```
sudo apt-get install dconf-editor
```
then open it. Now navigate to org.gnome.settings-daemon.plugins.xrandr and uncheck the active box for the xrandr plug-in. Your xrandr static configuration should no longer be overwritten when you restart.

---

### Post by DJYoshaBYD on 2012-10-10
Yes. All cards and displays are recognized in nvidia-settings, and yes, I can do it with twin view for 2 monitors and a 3rd X, but then I dont have the same type of access to that screen. 

Here is my xorg.con. Its from a brand new install on this computer, not configured for anything at all except for 1 monitor. 

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 304.51  (buildmeister@swio-display-x86-rhel47-08.nvidia.com)  Tue Sep 18 18:26:36 PDT 2012

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
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Should I switch it to seperate x screens and show you the output then?

I can post the output of what I tried to do earlier, if you want. 

Again, my cards are recognized, and I can get 2 monitors working just fine with twinview, but I need 3 monitors, that can all share windows (yes, just like in windows), and that has hardware acceleration for effects running on all monitors. Im pretty sure that I would need to custom write a xorg.conf file, but it would be fantastic if there was some sort of GUI for it.

---

### Post by Favux on 2012-10-10
As far as I know TwinView only handles two monitors.

It looks like you might be able to get the setup you "want" if you enable TwinView for two monitors and the Xinerama for the third.  Looks a bit daunting.  See especially the last post:  [http://ubuntuforums.org/showthread.php?t=1703524](http://ubuntuforums.org/showthread.php?t=1703524)

If that doesn't seem viable you could try asking on Nvidia specific forums.  The Nvidia forums are apparently down due to a security breach.  But for linux they link to here:  [http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)  And the Phoronix one:  [http://www.phoronix.com/forums/forumdisplay.php?20-NVIDIA-Linux](http://www.phoronix.com/forums/forumdisplay.php?20-NVIDIA-Linux)

---

### Post by DJYoshaBYD on 2012-10-11
So yeah. Tried a bunch more stuff last night. I cannot get Gnome 3 to work with my 2 card/3 monitor setup WITH effects.

PLEASE, tell me there is a way to do this. I mean, I have literally been working on this for over a week now, and it seems that NO ONE has ANY CLUE how to do this? 

Can someone point me in the right direction, please? :)

---

### Post by DJYoshaBYD on 2012-10-11
Bumpy bumpy. Lol. There has to be at least ONE person here that has the following setup:

2 nvidia cards
3 monitors
gnome 3
effects and compositing enabled (Yes. in FULL gnome 3, not fallback)
hardware acceleration
able to fully use all 3 monitors, as well as drag windows between them.

There is no way that I am the only person that really want this fixed, as any info I have read online is SUPER outdated by at least a year or 2.

---

### Post by DJYoshaBYD on 2012-10-13
Well, I got this kind of working. All 3 monitors are up and working, but I still cannot get composting to work.

Here is my xorg.conf. Any suggestions?

> Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Files"
EndSection

Section "Module"
    Load "glx"
EndSection

Section "Extensions"
    Option "Composite" "Disable"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Acer"
    ModelName      "20 Inch"
    HorizSync       24.0 - 82.0
    VertRefresh     48.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "HP"
    ModelName      "MidPuta"
    HorizSync       24.0 - 82.0
    VertRefresh     48.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Samsung"
    ModelName      "10 Inch"
    HorizSync       24.0 - 82.0
    VertRefresh     48.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GT 240"
    BusID          "PCI:3:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GT 240"
    BusID          "PCI:3:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "8600 GT"
    BusID          "PCI:6:0:0"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
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
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by Favux on 2012-10-13
Loose the mouse and keyboard stuff.  Let Xorg/udev handle that:
```
Section "ServerLayout"
Identifier "Layout0"
Screen 0 "Screen0" 0 0
Screen 1 "Screen1" RightOf "Screen0"
Screen 2 "Screen2" RightOf "Screen1"
Option "Xinerama" "1"
EndSection

Section "Files"
EndSection

Section "Module"
Load "glx"
EndSection

Section "Extensions"
Option "Composite" "Disable"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Acer"
ModelName "20 Inch"
HorizSync 24.0 - 82.0
VertRefresh 48.0 - 76.0
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Monitor1"
VendorName "HP"
ModelName "MidPuta"
HorizSync 24.0 - 82.0
VertRefresh 48.0 - 76.0
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Monitor2"
VendorName "Samsung"
ModelName "10 Inch"
HorizSync 24.0 - 82.0
VertRefresh 48.0 - 76.0
Option "DPMS"
EndSection

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GT 240"
BusID "PCI:3:0:0"
Screen 0
EndSection

Section "Device"
Identifier "Device1"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GT 240"
BusID "PCI:3:0:0"
Screen 1
EndSection

Section "Device"
Identifier "Device2"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "8600 GT"
BusID "PCI:6:0:0"
Screen 0
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "DFP-1: nvidia-auto-select +0+0"
SubSection "Display"
Depth 24
EndSubSection
EndSection


Section "Screen"
Identifier "Screen1"
Device "Device1"
Monitor "Monitor1"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "CRT-1: nvidia-auto-select +0+0"
SubSection "Display"
Depth 24
EndSubSection
EndSection

Section "Screen"
Identifier "Screen2"
Device "Device2"
Monitor "Monitor2"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "DFP-0: nvidia-auto-select +0+0"
SubSection "Display"
Depth 24
EndSubSection
EndSection 
```
Is it Xinerama that requires this section?
```
Section "Extensions"
Option "Composite" "Disable"
EndSection
```
Does commenting it out break things?

---

### Post by DJYoshaBYD on 2012-10-13
I did that config and its the same as before. I need compositing for gnome 3 and compiz. with this config, it defaults to gnome classic, instead of gnome 3 with effects.

---

### Post by Favux on 2012-10-13
I assume you mean you removed the keyboard and mouse and commented out the Extensions section.  And that didn't change anything.  Compiz still won't function.

What happens when you comment out the glx or Module section?

---

### Post by DJYoshaBYD on 2012-10-13
yes. I removed the keyb and mouse stuff. I added the config you posted. But I do need compiz to function. Any ideas on how to do this?

---

### Post by DJYoshaBYD on 2012-10-13
dont I need the glx stuff in the module section for compositing to work and compiz/gnome3 to play nice?

---

### Post by Favux on 2012-10-13
Don't know for sure.  That's why I'm asking you to comment it and Extensions out rather than remove them.  Trying to find out what the baseline is for the 3 monitors working, although without compositing.  That way we'll know what changes are needed for compositing if you figure it out.

The Nvidia dev.s still configure a lot of deprecated stuff because Xorg still supports it.  The mouse and keyboard are examples.  I understand why, they don't want to clutter the code with conditionals checking which X Server they're in.  Makes the code easier to maintain, less likely to break, and makes backward compatability easier.

But remember the guy I linked you too before:  [http://ubuntuforums.org/showpost.php?p=11134887&postcount=11](http://ubuntuforums.org/showpost.php?p=11134887&postcount=11)   has:
```
Section "Module"
	Load           "dbe"
	Load           "extmod"
	Load           "type1"
	Load           "freetype"
	Load	"glx"
EndSection

Section "Extensions"
	Option         "Composite" "Enable"
EndSection
```
Notice the "Composite" "Enable".  Plus extra entries in "ServerLayout":
```
	Option         "AIGLX" "true"
	Option         "RenderAccel" "true"
	Option         "AllowGLXWithComposite" "true"
	Option         "XGL" "true"
```
While he doesn't explicitly state it he seems to have compositing.

---

### Post by DJYoshaBYD on 2012-10-13
I tried to comment the module section and the extensions section, and it made the screens (left, center) hooked to the GT 240 have blank screens, and the 3rd screen on the 8600 (right screen) has the gnome 3 running with compiz, but the mouse will not click on the images. I have to use the mouse on the far left screen to make it click on the 3rd screen. Basically, my mouse still thinks monitor0 (left) is the right one, but monitor2 (right) shows the output. 

This is what I had:

> Section "ServerLayout"
Identifier "Layout0"
Screen 0 "Screen0" 0 0
Screen 1 "Screen1" RightOf "Screen0"
Screen 2 "Screen2" RightOf "Screen1"
Option "Xinerama" "1"
EndSection

Section "Files"
EndSection

#Section "Module"
#Load "glx"
#EndSection

#Section "Extensions"
#Option "Composite" "Disable"
#EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Acer"
ModelName "20 Inch"
HorizSync 24.0 - 82.0
VertRefresh 48.0 - 76.0
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Monitor1"
VendorName "HP"
ModelName "MidPuta"
HorizSync 24.0 - 82.0
VertRefresh 48.0 - 76.0
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Monitor2"
VendorName "Samsung"
ModelName "10 Inch"
HorizSync 24.0 - 82.0
VertRefresh 48.0 - 76.0
Option "DPMS"
EndSection

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GT 240"
BusID "PCI:3:0:0"
Screen 0
EndSection

Section "Device"
Identifier "Device1"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GT 240"
BusID "PCI:3:0:0"
Screen 1
EndSection

Section "Device"
Identifier "Device2"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "8600 GT"
BusID "PCI:6:0:0"
Screen 0
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "DFP-1: nvidia-auto-select +0+0"
SubSection "Display"
Depth 24
EndSubSection
EndSection


Section "Screen"
Identifier "Screen1"
Device "Device1"
Monitor "Monitor1"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "CRT-1: nvidia-auto-select +0+0"
SubSection "Display"
Depth 24
EndSubSection
EndSection

Section "Screen"
Identifier "Screen2"
Device "Device2"
Monitor "Monitor2"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "DFP-0: nvidia-auto-select +0+0"
SubSection "Display"
Depth 24
EndSubSection
EndSection

---

### Post by Favux on 2012-10-13
OK try the other way:
```
Section "Module"
Load "glx"
EndSection

Section "Extensions"
Option "Composite" "Enabled"
EndSection

```
If that seems to work, but still without compositing try adding to "ServerLayout"
```
	Option         "AllowGLXWithComposite" "true"
```

---

### Post by DJYoshaBYD on 2012-10-14
Ok. Im trying it right now. Here is my log file for xorg.conf. Maybe this will help?

```


[  1869.983] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[  1869.983] X Protocol Version 11, Revision 0
[  1869.984] Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
[  1869.984] Current Operating System: Linux TIFA 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64
[  1869.984] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-32-generic root=UUID=cffe6d68-aaae-462f-9d3a-10f563f553d9 ro quiet splash vt.handoff=7
[  1869.984] Build Date: 29 August 2012  12:12:33AM
[  1869.984] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[  1869.984] Current version of pixman: 0.24.4
[  1869.984] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  1869.984] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1869.984] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 14 12:29:04 2012
[  1869.984] (==) Using config file: "/etc/X11/xorg.conf"
[  1869.984] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1869.984] (==) ServerLayout "Layout0"
[  1869.984] (**) |-->Screen "Screen0" (0)
[  1869.984] (**) |   |-->Monitor "Monitor0"
[  1869.984] (**) |   |-->Device "Device0"
[  1869.984] (**) |-->Screen "Screen1" (1)
[  1869.984] (**) |   |-->Monitor "Monitor1"
[  1869.984] (**) |   |-->Device "Device1"
[  1869.984] (**) |-->Screen "Screen2" (2)
[  1869.984] (**) |   |-->Monitor "Monitor2"
[  1869.984] (**) |   |-->Device "Device2"
[  1869.984] (**) Option "Xinerama" "1"
[  1869.984] (**) Option "AIGLX" "true"
[  1869.984] (==) Automatically adding devices
[  1869.984] (==) Automatically enabling devices
[  1869.984] (**) Xinerama: enabled
[  1869.984] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1869.984] 	Entry deleted from font path.
[  1869.984] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1869.985] 	Entry deleted from font path.
[  1869.985] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1869.985] 	Entry deleted from font path.
[  1869.985] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1869.985] 	Entry deleted from font path.
[  1869.985] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1869.985] 	Entry deleted from font path.
[  1869.985] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[  1869.985] 	Entry deleted from font path.
[  1869.985] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[  1869.985] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1869.985] (**) Extension "Composite" is disabled
[  1869.985] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1869.985] (II) Loader magic: 0x7fa6ad5e4b00
[  1869.985] (II) Module ABI versions:
[  1869.985] 	X.Org ANSI C Emulation: 0.4
[  1869.985] 	X.Org Video Driver: 11.0
[  1869.985] 	X.Org XInput driver : 16.0
[  1869.985] 	X.Org Server Extension : 6.0
[  1869.986] (--) PCI:*(0:3:0:0) 10de:0ca3:196e:0789 rev 162, Mem @ 0xec000000/16777216, 0xb0000000/268435456, 0xce000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[  1869.986] (--) PCI: (0:6:0:0) 10de:0402:196e:043a rev 161, Mem @ 0xea000000/16777216, 0x80000000/536870912, 0xe8000000/33554432, I/O @ 0x0000ac00/128, BIOS @ 0x????????/131072
[  1869.986] (II) Open ACPI successful (/var/run/acpid.socket)
[  1869.986] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[  1869.986] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[  1869.986] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[  1869.986] (II) "record" will be loaded by default.
[  1869.986] (II) "dri" will be loaded by default.
[  1869.986] (II) "dri2" will be loaded by default.
[  1869.986] (II) LoadModule: "dbe"
[  1869.986] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  1869.986] (II) Module dbe: vendor="X.Org Foundation"
[  1869.986] 	compiled for 1.11.3, module version = 1.0.0
[  1869.986] 	Module class: X.Org Server Extension
[  1869.986] 	ABI class: X.Org Server Extension, version 6.0
[  1869.986] (II) Loading extension DOUBLE-BUFFER
[  1869.986] (II) LoadModule: "extmod"
[  1869.986] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  1869.986] (II) Module extmod: vendor="X.Org Foundation"
[  1869.986] 	compiled for 1.11.3, module version = 1.0.0
[  1869.986] 	Module class: X.Org Server Extension
[  1869.986] 	ABI class: X.Org Server Extension, version 6.0
[  1869.986] (II) Loading extension MIT-SCREEN-SAVER
[  1869.986] (II) Loading extension XFree86-VidModeExtension
[  1869.986] (II) Loading extension XFree86-DGA
[  1869.986] (II) Loading extension DPMS
[  1869.986] (II) Loading extension XVideo
[  1869.986] (II) Loading extension XVideo-MotionCompensation
[  1869.986] (II) Loading extension X-Resource
[  1869.986] (II) LoadModule: "glx"
[  1869.987] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[  1870.000] (II) Module glx: vendor="NVIDIA Corporation"
[  1870.000] 	compiled for 4.0.2, module version = 1.0.0
[  1870.000] 	Module class: X.Org Server Extension
[  1870.000] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[  1870.000] (II) Loading extension GLX
[  1870.000] (II) LoadModule: "record"
[  1870.000] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  1870.000] (II) Module record: vendor="X.Org Foundation"
[  1870.000] 	compiled for 1.11.3, module version = 1.13.0
[  1870.000] 	Module class: X.Org Server Extension
[  1870.000] 	ABI class: X.Org Server Extension, version 6.0
[  1870.000] (II) Loading extension RECORD
[  1870.000] (II) LoadModule: "dri"
[  1870.000] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  1870.001] (II) Module dri: vendor="X.Org Foundation"
[  1870.001] 	compiled for 1.11.3, module version = 1.0.0
[  1870.001] 	ABI class: X.Org Server Extension, version 6.0
[  1870.001] (II) Loading extension XFree86-DRI
[  1870.001] (II) LoadModule: "dri2"
[  1870.001] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1870.001] (II) Module dri2: vendor="X.Org Foundation"
[  1870.001] 	compiled for 1.11.3, module version = 1.2.0
[  1870.001] 	ABI class: X.Org Server Extension, version 6.0
[  1870.001] (II) Loading extension DRI2
[  1870.001] (II) LoadModule: "nvidia"
[  1870.001] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  1870.001] (II) Module nvidia: vendor="NVIDIA Corporation"
[  1870.001] 	compiled for 4.0.2, module version = 1.0.0
[  1870.001] 	Module class: X.Org Video Driver
[  1870.001] (II) NVIDIA dlloader X Driver  295.40  Thu Apr  5 21:38:35 PDT 2012
[  1870.001] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  1870.001] (++) using VT number 7

[  1870.001] (II) Loading sub module "fb"
[  1870.001] (II) LoadModule: "fb"
[  1870.002] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1870.002] (II) Module fb: vendor="X.Org Foundation"
[  1870.002] 	compiled for 1.11.3, module version = 1.0.0
[  1870.002] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1870.002] (II) Loading sub module "wfb"
[  1870.002] (II) LoadModule: "wfb"
[  1870.002] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  1870.002] (II) Module wfb: vendor="X.Org Foundation"
[  1870.002] 	compiled for 1.11.3, module version = 1.0.0
[  1870.002] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1870.002] (II) Loading sub module "ramdac"
[  1870.002] (II) LoadModule: "ramdac"
[  1870.002] (II) Module "ramdac" already built-in
[  1870.002] (WW) NVIDIA: Xinerama is enabled, so RandR has likely been disabled by the
[  1870.002] (WW) NVIDIA:     X server.
[  1870.002] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  1870.002] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  1870.002] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1870.002] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  1870.002] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  1870.002] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1870.002] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  1870.002] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  1870.002] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1870.002] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[  1870.002] (==) NVIDIA(0): RGB weight 888
[  1870.002] (==) NVIDIA(0): Default visual is TrueColor
[  1870.002] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  1870.002] (**) NVIDIA(0): Option "TwinView" "0"
[  1870.002] (**) NVIDIA(0): Option "MetaModes" "DFP-1: nvidia-auto-select +0+0"
[  1870.002] (**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
[  1870.002] (**) NVIDIA(0): Enabling 2D acceleration
[  1870.022] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
[  1870.039] (II) NVIDIA(GPU-0): Display (Acer X193W+ (DFP-1)) does not support NVIDIA 3D
[  1870.039] (II) NVIDIA(GPU-0):     Vision stereo.
[  1870.041] (II) NVIDIA(0): NVIDIA GPU GeForce GT 240 (GT215) at PCI:3:0:0 (GPU-0)
[  1870.041] (--) NVIDIA(0): Memory: 1048576 kBytes
[  1870.041] (--) NVIDIA(0): VideoBIOS: 70.15.20.00.51
[  1870.041] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  1870.041] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  1870.043] (--) NVIDIA(0): Connected display device(s) on GeForce GT 240 at PCI:3:0:0
[  1870.043] (--) NVIDIA(0):     CRT-1
[  1870.043] (--) NVIDIA(0):     Acer X193W+ (DFP-1)
[  1870.043] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[  1870.043] (--) NVIDIA(0): Acer X193W+ (DFP-1): 165.0 MHz maximum pixel clock
[  1870.043] (--) NVIDIA(0): Acer X193W+ (DFP-1): Internal Single Link TMDS
[  1870.043] (II) NVIDIA(0): Display Device found referenced in MetaMode: DFP-1
[  1870.043] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  1870.043] (**) NVIDIA(0):     device Acer X193W+ (DFP-1) (Using EDID frequencies has
[  1870.043] (**) NVIDIA(0):     been enabled on all display devices.)
[  1870.111] (II) NVIDIA(0): Assigned Display Device: DFP-1
[  1870.111] (II) NVIDIA(0): Validated modes:
[  1870.111] (II) NVIDIA(0):     "DFP-1:nvidia-auto-select+0+0"
[  1870.111] (II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
[  1870.138] (--) NVIDIA(0): DPI set to (104, 102); computed from "UseEdidDpi" X config
[  1870.138] (--) NVIDIA(0):     option
[  1870.138] (WW) NVIDIA(0): 32-bit ARGB GLX visuals require the Composite extension.
[  1870.138] (WW) NVIDIA(0): 32-bit ARGB GLX visuals are not currently supported with the
[  1870.138] (WW) NVIDIA(0):     Xinerama extension.
[  1870.138] (WW) NVIDIA(0): Disabling 32-bit ARGB GLX visuals.
[  1870.138] (**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
[  1870.138] (==) NVIDIA(1): RGB weight 888
[  1870.138] (==) NVIDIA(1): Default visual is TrueColor
[  1870.138] (==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
[  1870.138] (**) NVIDIA(1): Option "TwinView" "0"
[  1870.138] (**) NVIDIA(1): Option "MetaModes" "CRT-1: nvidia-auto-select +0+0"
[  1870.138] (**) NVIDIA(1): Option "AddARGBGLXVisuals" "True"
[  1870.138] (II) NVIDIA(1): NVIDIA GPU GeForce GT 240 (GT215) at PCI:3:0:0 (GPU-0)
[  1870.138] (--) NVIDIA(1): Memory: 1048576 kBytes
[  1870.138] (--) NVIDIA(1): VideoBIOS: 70.15.20.00.51
[  1870.138] (II) NVIDIA(1): Detected PCI Express Link width: 16X
[  1870.138] (--) NVIDIA(1): Interlaced video modes are supported on this GPU
[  1870.140] (--) NVIDIA(1): Connected display device(s) on GeForce GT 240 at PCI:3:0:0
[  1870.140] (--) NVIDIA(1):     CRT-1
[  1870.140] (--) NVIDIA(1):     Acer X193W+ (DFP-1)
[  1870.140] (--) NVIDIA(1): CRT-1: 400.0 MHz maximum pixel clock
[  1870.140] (--) NVIDIA(1): Acer X193W+ (DFP-1): 165.0 MHz maximum pixel clock
[  1870.140] (--) NVIDIA(1): Acer X193W+ (DFP-1): Internal Single Link TMDS
[  1870.140] (II) NVIDIA(1): Display Device found referenced in MetaMode: CRT-1
[  1870.140] (**) NVIDIA(1): Using HorizSync/VertRefresh ranges from the EDID for display
[  1870.140] (**) NVIDIA(1):     device CRT-1 (Using EDID frequencies has been enabled on
[  1870.140] (**) NVIDIA(1):     all display devices.)
[  1870.155] (II) NVIDIA(1): Assigned Display Device: CRT-1
[  1870.155] (II) NVIDIA(1): Validated modes:
[  1870.155] (II) NVIDIA(1):     "CRT-1:nvidia-auto-select+0+0"
[  1870.155] (II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
[  1870.158] (WW) NVIDIA(1): Unable to get display device CRT-1's EDID; cannot compute DPI
[  1870.158] (WW) NVIDIA(1):     from CRT-1's EDID.
[  1870.158] (==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
[  1870.158] (WW) NVIDIA(1): 32-bit ARGB GLX visuals require the Composite extension.
[  1870.158] (WW) NVIDIA(1): 32-bit ARGB GLX visuals are not currently supported with the
[  1870.158] (WW) NVIDIA(1):     Xinerama extension.
[  1870.158] (WW) NVIDIA(1): Disabling 32-bit ARGB GLX visuals.
[  1870.158] (**) NVIDIA(2): Depth 24, (--) framebuffer bpp 32
[  1870.158] (==) NVIDIA(2): RGB weight 888
[  1870.158] (==) NVIDIA(2): Default visual is TrueColor
[  1870.158] (==) NVIDIA(2): Using gamma correction (1.0, 1.0, 1.0)
[  1870.158] (**) NVIDIA(2): Option "TwinView" "0"
[  1870.158] (**) NVIDIA(2): Option "MetaModes" "DFP-0: nvidia-auto-select +0+0"
[  1870.158] (**) NVIDIA(2): Option "AddARGBGLXVisuals" "True"
[  1870.158] (**) NVIDIA(2): Enabling 2D acceleration
[  1870.303] (II) NVIDIA(GPU-1): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[  1870.303] (II) NVIDIA(GPU-1):     3D Vision stereo.
[  1870.307] (II) NVIDIA(2): NVIDIA GPU GeForce 8600 GT (G84) at PCI:6:0:0 (GPU-1)
[  1870.307] (--) NVIDIA(2): Memory: 524288 kBytes
[  1870.307] (--) NVIDIA(2): VideoBIOS: 60.84.34.00.51
[  1870.307] (II) NVIDIA(2): Detected PCI Express Link width: 16X
[  1870.307] (--) NVIDIA(2): Interlaced video modes are supported on this GPU
[  1870.311] (--) NVIDIA(2): Connected display device(s) on GeForce 8600 GT at PCI:6:0:0
[  1870.311] (--) NVIDIA(2):     Samsung SyncMaster (DFP-0)
[  1870.311] (--) NVIDIA(2): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
[  1870.311] (--) NVIDIA(2): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
[  1870.311] (II) NVIDIA(2): Display Device found referenced in MetaMode: DFP-0
[  1870.311] (**) NVIDIA(2): Using HorizSync/VertRefresh ranges from the EDID for display
[  1870.311] (**) NVIDIA(2):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[  1870.311] (**) NVIDIA(2):     has been enabled on all display devices.)
[  1870.370] (II) NVIDIA(2): Assigned Display Device: DFP-0
[  1870.370] (II) NVIDIA(2): Validated modes:
[  1870.370] (II) NVIDIA(2):     "DFP-0:nvidia-auto-select+0+0"
[  1870.370] (II) NVIDIA(2): Virtual screen size determined to be 1440 x 900
[  1870.378] (--) NVIDIA(2): DPI set to (89, 87); computed from "UseEdidDpi" X config
[  1870.378] (--) NVIDIA(2):     option
[  1870.378] (WW) NVIDIA(2): 32-bit ARGB GLX visuals require the Composite extension.
[  1870.378] (WW) NVIDIA(2): 32-bit ARGB GLX visuals are not currently supported with the
[  1870.378] (WW) NVIDIA(2):     Xinerama extension.
[  1870.378] (WW) NVIDIA(2): Disabling 32-bit ARGB GLX visuals.
[  1870.378] (--) Depth 24 pixmap format is 32 bpp
[  1870.378] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[  1870.385] (II) NVIDIA(0): Setting mode "DFP-1:nvidia-auto-select+0+0"
[  1870.420] (II) Loading extension NV-GLX
[  1870.455] (==) NVIDIA(0): Disabling shared memory pixmaps
[  1870.455] (==) NVIDIA(0): Backing store disabled
[  1870.455] (==) NVIDIA(0): Silken mouse enabled
[  1870.455] (**) NVIDIA(0): DPMS enabled
[  1870.455] (II) Loading extension NV-CONTROL
[  1870.455] (II) Loading sub module "dri2"
[  1870.455] (II) LoadModule: "dri2"
[  1870.455] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1870.455] (II) Module dri2: vendor="X.Org Foundation"
[  1870.455] 	compiled for 1.11.3, module version = 1.2.0
[  1870.455] 	ABI class: X.Org Server Extension, version 6.0
[  1870.455] (II) NVIDIA(0): [DRI2] Setup complete
[  1870.455] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[  1870.455] (==) RandR enabled
[  1870.460] (II) NVIDIA(1): Setting mode "CRT-1:nvidia-auto-select+0+0"
[  1870.666] (==) NVIDIA(1): Disabling shared memory pixmaps
[  1870.666] (==) NVIDIA(1): Backing store disabled
[  1870.666] (==) NVIDIA(1): Silken mouse enabled
[  1870.666] (**) NVIDIA(1): DPMS enabled
[  1870.667] (II) Loading sub module "dri2"
[  1870.667] (II) LoadModule: "dri2"
[  1870.667] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1870.667] (II) Module dri2: vendor="X.Org Foundation"
[  1870.667] 	compiled for 1.11.3, module version = 1.2.0
[  1870.667] 	ABI class: X.Org Server Extension, version 6.0
[  1870.667] (II) NVIDIA(1): [DRI2] Setup complete
[  1870.667] (II) NVIDIA(1): [DRI2]   VDPAU driver: nvidia
[  1870.667] (==) RandR enabled
[  1870.678] (II) NVIDIA(2): Setting mode "DFP-0:nvidia-auto-select+0+0"
[  1870.763] (==) NVIDIA(2): Disabling shared memory pixmaps
[  1870.763] (==) NVIDIA(2): Backing store disabled
[  1870.763] (==) NVIDIA(2): Silken mouse enabled
[  1870.763] (**) NVIDIA(2): DPMS enabled
[  1870.763] (II) Loading sub module "dri2"
[  1870.763] (II) LoadModule: "dri2"
[  1870.763] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1870.763] (II) Module dri2: vendor="X.Org Foundation"
[  1870.763] 	compiled for 1.11.3, module version = 1.2.0
[  1870.763] 	ABI class: X.Org Server Extension, version 6.0
[  1870.764] (II) NVIDIA(2): [DRI2] Setup complete
[  1870.764] (II) NVIDIA(2): [DRI2]   VDPAU driver: nvidia
[  1870.764] (==) RandR enabled
[  1870.764] (II) Initializing built-in extension Generic Event Extension
[  1870.764] (II) Initializing built-in extension SHAPE
[  1870.764] (II) Initializing built-in extension MIT-SHM
[  1870.764] (II) Initializing built-in extension XInputExtension
[  1870.764] (II) Initializing built-in extension XTEST
[  1870.764] (II) Initializing built-in extension BIG-REQUESTS
[  1870.764] (II) Initializing built-in extension SYNC
[  1870.764] (II) Initializing built-in extension XKEYBOARD
[  1870.764] (II) Initializing built-in extension XC-MISC
[  1870.764] (II) Initializing built-in extension SECURITY
[  1870.764] (II) Initializing built-in extension XINERAMA
[  1870.764] (II) Initializing built-in extension XFIXES
[  1870.764] (II) Initializing built-in extension RENDER
[  1870.764] (II) Initializing built-in extension RANDR
[  1870.764] (II) Initializing built-in extension COMPOSITE
[  1870.764] (II) Initializing built-in extension DAMAGE
[  1870.765] (II) Initializing extension GLX
[  1870.869] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1870.871] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  1870.871] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1870.871] (II) LoadModule: "evdev"
[  1870.871] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1870.871] (II) Module evdev: vendor="X.Org Foundation"
[  1870.871] 	compiled for 1.11.3, module version = 2.7.0
[  1870.871] 	Module class: X.Org XInput Driver
[  1870.871] 	ABI class: X.Org XInput driver, version 16.0
[  1870.871] (II) Using input driver 'evdev' for 'Power Button'
[  1870.871] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1870.871] (**) Power Button: always reports core events
[  1870.871] (**) evdev: Power Button: Device: "/dev/input/event1"
[  1870.871] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1870.871] (--) evdev: Power Button: Found keys
[  1870.871] (II) evdev: Power Button: Configuring as keyboard
[  1870.871] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[  1870.871] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  1870.871] (**) Option "xkb_rules" "evdev"
[  1870.871] (**) Option "xkb_model" "pc105"
[  1870.871] (**) Option "xkb_layout" "us"
[  1870.872] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  1870.872] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1870.872] (II) Using input driver 'evdev' for 'Power Button'
[  1870.872] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1870.872] (**) Power Button: always reports core events
[  1870.872] (**) evdev: Power Button: Device: "/dev/input/event0"
[  1870.872] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1870.872] (--) evdev: Power Button: Found keys
[  1870.872] (II) evdev: Power Button: Configuring as keyboard
[  1870.872] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[  1870.872] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[  1870.872] (**) Option "xkb_rules" "evdev"
[  1870.872] (**) Option "xkb_model" "pc105"
[  1870.872] (**) Option "xkb_layout" "us"
[  1870.872] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event4)
[  1870.872] (II) No input driver specified, ignoring this device.
[  1870.872] (II) This device may have been added with another device file.
[  1870.873] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event5)
[  1870.873] (II) No input driver specified, ignoring this device.
[  1870.873] (II) This device may have been added with another device file.
[  1870.873] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event6)
[  1870.873] (II) No input driver specified, ignoring this device.
[  1870.873] (II) This device may have been added with another device file.
[  1870.873] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event7)
[  1870.873] (II) No input driver specified, ignoring this device.
[  1870.873] (II) This device may have been added with another device file.
[  1870.873] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/event3)
[  1870.873] (**) Logitech USB Trackball: Applying InputClass "evdev pointer catchall"
[  1870.873] (II) Using input driver 'evdev' for 'Logitech USB Trackball'
[  1870.873] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1870.873] (**) Logitech USB Trackball: always reports core events
[  1870.873] (**) evdev: Logitech USB Trackball: Device: "/dev/input/event3"
[  1870.873] (--) evdev: Logitech USB Trackball: Vendor 0x46d Product 0xc408
[  1870.873] (--) evdev: Logitech USB Trackball: Found 9 mouse buttons
[  1870.873] (--) evdev: Logitech USB Trackball: Found relative axes
[  1870.873] (--) evdev: Logitech USB Trackball: Found x and y relative axes
[  1870.873] (II) evdev: Logitech USB Trackball: Configuring as mouse
[  1870.873] (**) evdev: Logitech USB Trackball: YAxisMapping: buttons 4 and 5
[  1870.873] (**) evdev: Logitech USB Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1870.873] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-9/2-9:1.0/input/input3/event3"
[  1870.873] (II) XINPUT: Adding extended input device "Logitech USB Trackball" (type: MOUSE, id 8)
[  1870.873] (II) evdev: Logitech USB Trackball: initialized for relative axes.
[  1870.874] (**) Logitech USB Trackball: (accel) keeping acceleration scheme 1
[  1870.874] (**) Logitech USB Trackball: (accel) acceleration profile 0
[  1870.874] (**) Logitech USB Trackball: (accel) acceleration factor: 2.000
[  1870.874] (**) Logitech USB Trackball: (accel) acceleration threshold: 4
[  1870.874] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/mouse0)
[  1870.874] (II) No input driver specified, ignoring this device.
[  1870.874] (II) This device may have been added with another device file.
[  1870.874] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[  1870.874] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  1870.874] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  1870.874] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1870.874] (**) AT Translated Set 2 keyboard: always reports core events
[  1870.874] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[  1870.874] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[  1870.874] (--) evdev: AT Translated Set 2 keyboard: Found keys
[  1870.874] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[  1870.874] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[  1870.874] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[  1870.874] (**) Option "xkb_rules" "evdev"
[  1870.874] (**) Option "xkb_model" "pc105"
[  1870.874] (**) Option "xkb_layout" "us"
[  1876.570] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[  2042.013] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[  4006.094] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[  5086.007] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[  5532.018] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm


```

---

### Post by DJYoshaBYD on 2012-10-14
ok. So, with composite enabled, It will show an image on the right screen, but the center and left screen are black, even though I can move my house to the center and black one and see the mouse cursor. 

So, here is what its like:

      
  GT240-DFP-1                   
#Left Monitor###  -  
    Blank                             
Mouse pointer                 
   visible                            
Clicking on                    
this screen                     
causes clicks                               
on the right                    
screen




GT240-CRT-1  
###Center Monitor###-
Blank 
Mouse Pointer 
visible
clicking here
does nothing 




8600GT-DFP-0
#Right Monitor###
Full composite
right 1/3 of screen
is cut off
clicking here does
nothing, but keyboard
shortcuts work. 


I believe we are getting on the right track. Compositing now will work, but the 2 screens on the GT240 do not show anything except for a mouse pointer, although, the mouse goes screen to screen in order.

I think that the screen that is all of the way to the right needs to be pushed to the left screen, and it should work. 

Here is my current xorg.conf that I use for this:

```


Section "ServerLayout"
Identifier "Layout0"
Screen 0 "Screen0" 0 0
Screen 1 "Screen1" RightOf "Screen0"
Screen 2 "Screen2" RightOf "Screen1"
Option "Xinerama" "1"
#	Option         "AIGLX" "true"
#	Option         "RenderAccel" "true"
	Option         "AllowGLXWithComposite" "true"
#	Option         "XGL" "true"
EndSection

Section "Module"
#	Load           "dbe"
#	Load           "extmod"
#	Load           "type1"
#	Load           "freetype"
	Load	       "glx"
	Load           "dri"
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
	Option         "Composite" "enabled"
EndSection

############################################################################
############################# Monitors
##############################################################################

Section "Monitor"
Identifier "Monitor0"
VendorName "Acer"
ModelName "20 Inch"
HorizSync 24.0 - 82.0
VertRefresh 48.0 - 76.0
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Monitor1"
VendorName "HP"
ModelName "MidPuta"
HorizSync 24.0 - 82.0
VertRefresh 48.0 - 76.0
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Monitor2"
VendorName "Samsung"
ModelName "10 Inch"
HorizSync 24.0 - 82.0
VertRefresh 48.0 - 76.0
Option "DPMS"
EndSection

##########################################################################################
################################ Devices
############################################################################################3

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GT 240"
BusID "PCI:3:0:0"
Screen 0
EndSection

Section "Device"
Identifier "Device1"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GT 240"
BusID "PCI:3:0:0"
Screen 1
EndSection

Section "Device"
Identifier "Device2"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "8600 GT"
BusID "PCI:6:0:0"
Screen 0
EndSection

#############################################################################
######################### Screens
############################################################################

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "DFP-1: nvidia-auto-select +0+0"
Option         "AddARGBGLXVisuals" "True"
SubSection "Display"
Depth 24
EndSubSection
EndSection


Section "Screen"
Identifier "Screen1"
Device "Device1"
Monitor "Monitor1"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "CRT-1: nvidia-auto-select +0+0"
Option         "AddARGBGLXVisuals" "True"
SubSection "Display"
Depth 24
EndSubSection
EndSection

Section "Screen"
Identifier "Screen2"
Device "Device2"
Monitor "Monitor2"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "DFP-0: nvidia-auto-select +0+0"
Option         "AddARGBGLXVisuals" "True"
SubSection "Display"
Depth 24
EndSubSection
EndSection

```

And here is my current xorg.0.log

```


[    23.126] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    23.126] X Protocol Version 11, Revision 0
[    23.126] Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
[    23.126] Current Operating System: Linux TIFA 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64
[    23.126] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-32-generic root=UUID=cffe6d68-aaae-462f-9d3a-10f563f553d9 ro quiet splash vt.handoff=7
[    23.126] Build Date: 29 August 2012  12:12:33AM
[    23.126] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[    23.126] Current version of pixman: 0.24.4
[    23.126] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    23.126] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.126] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 14 14:18:59 2012
[    23.126] (==) Using config file: "/etc/X11/xorg.conf"
[    23.126] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.126] (==) ServerLayout "Layout0"
[    23.126] (**) |-->Screen "Screen0" (0)
[    23.126] (**) |   |-->Monitor "Monitor0"
[    23.126] (**) |   |-->Device "Device0"
[    23.126] (**) |-->Screen "Screen1" (1)
[    23.126] (**) |   |-->Monitor "Monitor1"
[    23.127] (**) |   |-->Device "Device1"
[    23.127] (**) |-->Screen "Screen2" (2)
[    23.127] (**) |   |-->Monitor "Monitor2"
[    23.127] (**) |   |-->Device "Device2"
[    23.127] (**) Option "Xinerama" "1"
[    23.127] (==) Automatically adding devices
[    23.127] (==) Automatically enabling devices
[    23.127] (**) Xinerama: enabled
[    23.127] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.127] 	Entry deleted from font path.
[    23.127] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    23.127] 	Entry deleted from font path.
[    23.127] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    23.127] 	Entry deleted from font path.
[    23.127] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    23.127] 	Entry deleted from font path.
[    23.127] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    23.127] 	Entry deleted from font path.
[    23.127] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    23.127] 	Entry deleted from font path.
[    23.127] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    23.127] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    23.127] (**) Extension "Composite" is enabled
[    23.127] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    23.127] (II) Loader magic: 0x7ff5e8062b00
[    23.127] (II) Module ABI versions:
[    23.127] 	X.Org ANSI C Emulation: 0.4
[    23.127] 	X.Org Video Driver: 11.0
[    23.127] 	X.Org XInput driver : 16.0
[    23.127] 	X.Org Server Extension : 6.0
[    23.128] (--) PCI:*(0:3:0:0) 10de:0ca3:196e:0789 rev 162, Mem @ 0xec000000/16777216, 0xb0000000/268435456, 0xce000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[    23.128] (--) PCI: (0:6:0:0) 10de:0402:196e:043a rev 161, Mem @ 0xea000000/16777216, 0x80000000/536870912, 0xe8000000/33554432, I/O @ 0x0000ac00/128, BIOS @ 0x????????/131072
[    23.128] (II) Open ACPI successful (/var/run/acpid.socket)
[    23.128] (II) "extmod" will be loaded by default.
[    23.128] (II) "dbe" will be loaded by default.
[    23.128] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    23.128] (II) "record" will be loaded by default.
[    23.128] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    23.128] (II) "dri2" will be loaded by default.
[    23.128] (II) LoadModule: "glx"
[    23.128] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    23.139] (II) Module glx: vendor="NVIDIA Corporation"
[    23.139] 	compiled for 4.0.2, module version = 1.0.0
[    23.139] 	Module class: X.Org Server Extension
[    23.139] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[    23.139] (II) Loading extension GLX
[    23.139] (II) LoadModule: "dri"
[    23.140] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    23.140] (II) Module dri: vendor="X.Org Foundation"
[    23.140] 	compiled for 1.11.3, module version = 1.0.0
[    23.140] 	ABI class: X.Org Server Extension, version 6.0
[    23.140] (II) Loading extension XFree86-DRI
[    23.140] (II) LoadModule: "extmod"
[    23.140] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    23.140] (II) Module extmod: vendor="X.Org Foundation"
[    23.140] 	compiled for 1.11.3, module version = 1.0.0
[    23.140] 	Module class: X.Org Server Extension
[    23.140] 	ABI class: X.Org Server Extension, version 6.0
[    23.140] (II) Loading extension MIT-SCREEN-SAVER
[    23.140] (II) Loading extension XFree86-VidModeExtension
[    23.140] (II) Loading extension XFree86-DGA
[    23.140] (II) Loading extension DPMS
[    23.140] (II) Loading extension XVideo
[    23.140] (II) Loading extension XVideo-MotionCompensation
[    23.140] (II) Loading extension X-Resource
[    23.140] (II) LoadModule: "dbe"
[    23.140] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    23.140] (II) Module dbe: vendor="X.Org Foundation"
[    23.140] 	compiled for 1.11.3, module version = 1.0.0
[    23.140] 	Module class: X.Org Server Extension
[    23.140] 	ABI class: X.Org Server Extension, version 6.0
[    23.140] (II) Loading extension DOUBLE-BUFFER
[    23.140] (II) LoadModule: "record"
[    23.140] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    23.140] (II) Module record: vendor="X.Org Foundation"
[    23.140] 	compiled for 1.11.3, module version = 1.13.0
[    23.140] 	Module class: X.Org Server Extension
[    23.140] 	ABI class: X.Org Server Extension, version 6.0
[    23.140] (II) Loading extension RECORD
[    23.141] (II) LoadModule: "dri2"
[    23.141] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    23.141] (II) Module dri2: vendor="X.Org Foundation"
[    23.141] 	compiled for 1.11.3, module version = 1.2.0
[    23.141] 	ABI class: X.Org Server Extension, version 6.0
[    23.141] (II) Loading extension DRI2
[    23.141] (II) LoadModule: "nvidia"
[    23.141] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    23.141] (II) Module nvidia: vendor="NVIDIA Corporation"
[    23.141] 	compiled for 4.0.2, module version = 1.0.0
[    23.141] 	Module class: X.Org Video Driver
[    23.141] (II) NVIDIA dlloader X Driver  295.40  Thu Apr  5 21:38:35 PDT 2012
[    23.141] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    23.141] (++) using VT number 7

[    23.141] (II) Loading sub module "fb"
[    23.141] (II) LoadModule: "fb"
[    23.142] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.142] (II) Module fb: vendor="X.Org Foundation"
[    23.142] 	compiled for 1.11.3, module version = 1.0.0
[    23.142] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.142] (II) Loading sub module "wfb"
[    23.142] (II) LoadModule: "wfb"
[    23.170] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    23.170] (II) Module wfb: vendor="X.Org Foundation"
[    23.170] 	compiled for 1.11.3, module version = 1.0.0
[    23.170] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.170] (II) Loading sub module "ramdac"
[    23.170] (II) LoadModule: "ramdac"
[    23.170] (II) Module "ramdac" already built-in
[    23.170] (WW) NVIDIA: The Composite and Xinerama extensions are both enabled, which
[    23.170] (WW) NVIDIA:     is an unsupported configuration.  The driver will continue
[    23.170] (WW) NVIDIA:     to load, but may behave strangely.
[    23.170] (WW) NVIDIA: Xinerama is enabled, so RandR has likely been disabled by the
[    23.170] (WW) NVIDIA:     X server.
[    23.170] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    23.170] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    23.170] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.170] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    23.170] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    23.170] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.170] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    23.170] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    23.170] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.170] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    23.170] (==) NVIDIA(0): RGB weight 888
[    23.170] (==) NVIDIA(0): Default visual is TrueColor
[    23.170] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    23.170] (**) NVIDIA(0): Option "TwinView" "0"
[    23.170] (**) NVIDIA(0): Option "MetaModes" "DFP-1: nvidia-auto-select +0+0"
[    23.170] (**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
[    23.170] (**) NVIDIA(0): Enabling 2D acceleration
[    24.691] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
[    24.708] (II) NVIDIA(GPU-0): Display (Acer X193W+ (DFP-1)) does not support NVIDIA 3D
[    24.708] (II) NVIDIA(GPU-0):     Vision stereo.
[    24.709] (II) NVIDIA(0): NVIDIA GPU GeForce GT 240 (GT215) at PCI:3:0:0 (GPU-0)
[    24.709] (--) NVIDIA(0): Memory: 1048576 kBytes
[    24.709] (--) NVIDIA(0): VideoBIOS: 70.15.20.00.51
[    24.709] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    24.709] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    24.711] (--) NVIDIA(0): Connected display device(s) on GeForce GT 240 at PCI:3:0:0
[    24.711] (--) NVIDIA(0):     CRT-1
[    24.711] (--) NVIDIA(0):     Acer X193W+ (DFP-1)
[    24.711] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    24.711] (--) NVIDIA(0): Acer X193W+ (DFP-1): 165.0 MHz maximum pixel clock
[    24.711] (--) NVIDIA(0): Acer X193W+ (DFP-1): Internal Single Link TMDS
[    24.711] (II) NVIDIA(0): Display Device found referenced in MetaMode: DFP-1
[    24.711] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    24.711] (**) NVIDIA(0):     device Acer X193W+ (DFP-1) (Using EDID frequencies has
[    24.711] (**) NVIDIA(0):     been enabled on all display devices.)
[    24.768] (II) NVIDIA(0): Assigned Display Device: DFP-1
[    24.768] (II) NVIDIA(0): Validated modes:
[    24.768] (II) NVIDIA(0):     "DFP-1:nvidia-auto-select+0+0"
[    24.768] (II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
[    24.790] (--) NVIDIA(0): DPI set to (104, 102); computed from "UseEdidDpi" X config
[    24.790] (--) NVIDIA(0):     option
[    24.790] (WW) NVIDIA(0): 32-bit ARGB GLX visuals are not currently supported with the
[    24.790] (WW) NVIDIA(0):     Xinerama extension.
[    24.790] (WW) NVIDIA(0): Disabling 32-bit ARGB GLX visuals.
[    24.790] (**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
[    24.790] (==) NVIDIA(1): RGB weight 888
[    24.790] (==) NVIDIA(1): Default visual is TrueColor
[    24.790] (==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
[    24.790] (**) NVIDIA(1): Option "TwinView" "0"
[    24.790] (**) NVIDIA(1): Option "MetaModes" "CRT-1: nvidia-auto-select +0+0"
[    24.790] (**) NVIDIA(1): Option "AddARGBGLXVisuals" "True"
[    24.791] (II) NVIDIA(1): NVIDIA GPU GeForce GT 240 (GT215) at PCI:3:0:0 (GPU-0)
[    24.791] (--) NVIDIA(1): Memory: 1048576 kBytes
[    24.791] (--) NVIDIA(1): VideoBIOS: 70.15.20.00.51
[    24.791] (II) NVIDIA(1): Detected PCI Express Link width: 16X
[    24.791] (--) NVIDIA(1): Interlaced video modes are supported on this GPU
[    24.792] (--) NVIDIA(1): Connected display device(s) on GeForce GT 240 at PCI:3:0:0
[    24.792] (--) NVIDIA(1):     CRT-1
[    24.792] (--) NVIDIA(1):     Acer X193W+ (DFP-1)
[    24.792] (--) NVIDIA(1): CRT-1: 400.0 MHz maximum pixel clock
[    24.792] (--) NVIDIA(1): Acer X193W+ (DFP-1): 165.0 MHz maximum pixel clock
[    24.792] (--) NVIDIA(1): Acer X193W+ (DFP-1): Internal Single Link TMDS
[    24.792] (II) NVIDIA(1): Display Device found referenced in MetaMode: CRT-1
[    24.792] (**) NVIDIA(1): Using HorizSync/VertRefresh ranges from the EDID for display
[    24.792] (**) NVIDIA(1):     device CRT-1 (Using EDID frequencies has been enabled on
[    24.792] (**) NVIDIA(1):     all display devices.)
[    24.803] (II) NVIDIA(1): Assigned Display Device: CRT-1
[    24.803] (II) NVIDIA(1): Validated modes:
[    24.803] (II) NVIDIA(1):     "CRT-1:nvidia-auto-select+0+0"
[    24.803] (II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
[    24.806] (WW) NVIDIA(1): Unable to get display device CRT-1's EDID; cannot compute DPI
[    24.806] (WW) NVIDIA(1):     from CRT-1's EDID.
[    24.806] (==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
[    24.806] (WW) NVIDIA(1): 32-bit ARGB GLX visuals are not currently supported with the
[    24.806] (WW) NVIDIA(1):     Xinerama extension.
[    24.806] (WW) NVIDIA(1): Disabling 32-bit ARGB GLX visuals.
[    24.806] (**) NVIDIA(2): Depth 24, (--) framebuffer bpp 32
[    24.806] (==) NVIDIA(2): RGB weight 888
[    24.806] (==) NVIDIA(2): Default visual is TrueColor
[    24.806] (==) NVIDIA(2): Using gamma correction (1.0, 1.0, 1.0)
[    24.806] (**) NVIDIA(2): Option "TwinView" "0"
[    24.806] (**) NVIDIA(2): Option "MetaModes" "DFP-0: nvidia-auto-select +0+0"
[    24.806] (**) NVIDIA(2): Option "AddARGBGLXVisuals" "True"
[    24.806] (**) NVIDIA(2): Enabling 2D acceleration
[    25.896] (II) NVIDIA(GPU-1): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[    25.896] (II) NVIDIA(GPU-1):     3D Vision stereo.
[    25.901] (II) NVIDIA(2): NVIDIA GPU GeForce 8600 GT (G84) at PCI:6:0:0 (GPU-1)
[    25.901] (--) NVIDIA(2): Memory: 524288 kBytes
[    25.901] (--) NVIDIA(2): VideoBIOS: 60.84.34.00.51
[    25.901] (II) NVIDIA(2): Detected PCI Express Link width: 16X
[    25.901] (--) NVIDIA(2): Interlaced video modes are supported on this GPU
[    25.905] (--) NVIDIA(2): Connected display device(s) on GeForce 8600 GT at PCI:6:0:0
[    25.905] (--) NVIDIA(2):     Samsung SyncMaster (DFP-0)
[    25.905] (--) NVIDIA(2): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
[    25.905] (--) NVIDIA(2): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
[    25.905] (II) NVIDIA(2): Display Device found referenced in MetaMode: DFP-0
[    25.905] (**) NVIDIA(2): Using HorizSync/VertRefresh ranges from the EDID for display
[    25.905] (**) NVIDIA(2):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[    25.905] (**) NVIDIA(2):     has been enabled on all display devices.)
[    25.963] (II) NVIDIA(2): Assigned Display Device: DFP-0
[    25.963] (II) NVIDIA(2): Validated modes:
[    25.963] (II) NVIDIA(2):     "DFP-0:nvidia-auto-select+0+0"
[    25.963] (II) NVIDIA(2): Virtual screen size determined to be 1440 x 900
[    25.971] (--) NVIDIA(2): DPI set to (89, 87); computed from "UseEdidDpi" X config
[    25.971] (--) NVIDIA(2):     option
[    25.971] (WW) NVIDIA(2): 32-bit ARGB GLX visuals are not currently supported with the
[    25.971] (WW) NVIDIA(2):     Xinerama extension.
[    25.971] (WW) NVIDIA(2): Disabling 32-bit ARGB GLX visuals.
[    25.971] (--) Depth 24 pixmap format is 32 bpp
[    25.971] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    25.977] (II) NVIDIA(0): Setting mode "DFP-1:nvidia-auto-select+0+0"
[    26.012] (II) Loading extension NV-GLX
[    26.061] (==) NVIDIA(0): Disabling shared memory pixmaps
[    26.061] (==) NVIDIA(0): Backing store disabled
[    26.061] (==) NVIDIA(0): Silken mouse enabled
[    26.062] (**) NVIDIA(0): DPMS enabled
[    26.062] (II) Loading extension NV-CONTROL
[    26.062] (II) Loading sub module "dri2"
[    26.062] (II) LoadModule: "dri2"
[    26.062] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.062] (II) Module dri2: vendor="X.Org Foundation"
[    26.062] 	compiled for 1.11.3, module version = 1.2.0
[    26.062] 	ABI class: X.Org Server Extension, version 6.0
[    26.062] (II) NVIDIA(0): [DRI2] Setup complete
[    26.062] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    26.062] (==) RandR enabled
[    26.066] (II) NVIDIA(1): Setting mode "CRT-1:nvidia-auto-select+0+0"
[    26.242] (==) NVIDIA(1): Disabling shared memory pixmaps
[    26.242] (==) NVIDIA(1): Backing store disabled
[    26.242] (==) NVIDIA(1): Silken mouse enabled
[    26.242] (**) NVIDIA(1): DPMS enabled
[    26.243] (II) Loading sub module "dri2"
[    26.243] (II) LoadModule: "dri2"
[    26.243] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.243] (II) Module dri2: vendor="X.Org Foundation"
[    26.243] 	compiled for 1.11.3, module version = 1.2.0
[    26.243] 	ABI class: X.Org Server Extension, version 6.0
[    26.243] (II) NVIDIA(1): [DRI2] Setup complete
[    26.243] (II) NVIDIA(1): [DRI2]   VDPAU driver: nvidia
[    26.243] (==) RandR enabled
[    26.252] (II) NVIDIA(2): Setting mode "DFP-0:nvidia-auto-select+0+0"
[    26.354] (==) NVIDIA(2): Disabling shared memory pixmaps
[    26.354] (==) NVIDIA(2): Backing store disabled
[    26.354] (==) NVIDIA(2): Silken mouse enabled
[    26.354] (**) NVIDIA(2): DPMS enabled
[    26.355] (II) Loading sub module "dri2"
[    26.355] (II) LoadModule: "dri2"
[    26.355] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.355] (II) Module dri2: vendor="X.Org Foundation"
[    26.355] 	compiled for 1.11.3, module version = 1.2.0
[    26.355] 	ABI class: X.Org Server Extension, version 6.0
[    26.355] (II) NVIDIA(2): [DRI2] Setup complete
[    26.355] (II) NVIDIA(2): [DRI2]   VDPAU driver: nvidia
[    26.355] (==) RandR enabled
[    26.355] (II) Initializing built-in extension Generic Event Extension
[    26.355] (II) Initializing built-in extension SHAPE
[    26.355] (II) Initializing built-in extension MIT-SHM
[    26.355] (II) Initializing built-in extension XInputExtension
[    26.355] (II) Initializing built-in extension XTEST
[    26.355] (II) Initializing built-in extension BIG-REQUESTS
[    26.355] (II) Initializing built-in extension SYNC
[    26.355] (II) Initializing built-in extension XKEYBOARD
[    26.355] (II) Initializing built-in extension XC-MISC
[    26.355] (II) Initializing built-in extension SECURITY
[    26.355] (II) Initializing built-in extension XINERAMA
[    26.355] (II) Initializing built-in extension XFIXES
[    26.355] (II) Initializing built-in extension RENDER
[    26.355] (II) Initializing built-in extension RANDR
[    26.355] (II) Initializing built-in extension COMPOSITE
[    26.355] (II) Initializing built-in extension DAMAGE
[    26.355] (II) Initializing extension GLX
[    26.456] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.458] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    26.458] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.458] (II) LoadModule: "evdev"
[    26.458] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.459] (II) Module evdev: vendor="X.Org Foundation"
[    26.459] 	compiled for 1.11.3, module version = 2.7.0
[    26.459] 	Module class: X.Org XInput Driver
[    26.459] 	ABI class: X.Org XInput driver, version 16.0
[    26.459] (II) Using input driver 'evdev' for 'Power Button'
[    26.459] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.459] (**) Power Button: always reports core events
[    26.459] (**) evdev: Power Button: Device: "/dev/input/event1"
[    26.459] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.459] (--) evdev: Power Button: Found keys
[    26.459] (II) evdev: Power Button: Configuring as keyboard
[    26.459] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    26.459] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    26.459] (**) Option "xkb_rules" "evdev"
[    26.459] (**) Option "xkb_model" "pc105"
[    26.459] (**) Option "xkb_layout" "us"
[    26.459] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    26.459] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.459] (II) Using input driver 'evdev' for 'Power Button'
[    26.459] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.459] (**) Power Button: always reports core events
[    26.459] (**) evdev: Power Button: Device: "/dev/input/event0"
[    26.459] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.459] (--) evdev: Power Button: Found keys
[    26.459] (II) evdev: Power Button: Configuring as keyboard
[    26.459] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    26.459] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    26.459] (**) Option "xkb_rules" "evdev"
[    26.459] (**) Option "xkb_model" "pc105"
[    26.459] (**) Option "xkb_layout" "us"
[    26.460] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event4)
[    26.460] (II) No input driver specified, ignoring this device.
[    26.460] (II) This device may have been added with another device file.
[    26.460] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event5)
[    26.460] (II) No input driver specified, ignoring this device.
[    26.460] (II) This device may have been added with another device file.
[    26.460] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event6)
[    26.460] (II) No input driver specified, ignoring this device.
[    26.460] (II) This device may have been added with another device file.
[    26.460] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event7)
[    26.460] (II) No input driver specified, ignoring this device.
[    26.460] (II) This device may have been added with another device file.
[    26.461] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/event3)
[    26.461] (**) Logitech USB Trackball: Applying InputClass "evdev pointer catchall"
[    26.461] (II) Using input driver 'evdev' for 'Logitech USB Trackball'
[    26.461] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.461] (**) Logitech USB Trackball: always reports core events
[    26.461] (**) evdev: Logitech USB Trackball: Device: "/dev/input/event3"
[    26.461] (--) evdev: Logitech USB Trackball: Vendor 0x46d Product 0xc408
[    26.461] (--) evdev: Logitech USB Trackball: Found 9 mouse buttons
[    26.461] (--) evdev: Logitech USB Trackball: Found relative axes
[    26.461] (--) evdev: Logitech USB Trackball: Found x and y relative axes
[    26.461] (II) evdev: Logitech USB Trackball: Configuring as mouse
[    26.461] (**) evdev: Logitech USB Trackball: YAxisMapping: buttons 4 and 5
[    26.461] (**) evdev: Logitech USB Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.461] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-9/2-9:1.0/input/input3/event3"
[    26.461] (II) XINPUT: Adding extended input device "Logitech USB Trackball" (type: MOUSE, id 8)
[    26.461] (II) evdev: Logitech USB Trackball: initialized for relative axes.
[    26.461] (**) Logitech USB Trackball: (accel) keeping acceleration scheme 1
[    26.461] (**) Logitech USB Trackball: (accel) acceleration profile 0
[    26.461] (**) Logitech USB Trackball: (accel) acceleration factor: 2.000
[    26.461] (**) Logitech USB Trackball: (accel) acceleration threshold: 4
[    26.461] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/mouse0)
[    26.461] (II) No input driver specified, ignoring this device.
[    26.461] (II) This device may have been added with another device file.
[    26.461] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    26.461] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    26.461] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    26.461] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.461] (**) AT Translated Set 2 keyboard: always reports core events
[    26.461] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    26.461] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    26.461] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    26.461] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    26.461] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    26.461] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    26.461] (**) Option "xkb_rules" "evdev"
[    26.461] (**) Option "xkb_model" "pc105"
[    26.461] (**) Option "xkb_layout" "us"
[    39.795] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm

```

---

### Post by DJYoshaBYD on 2012-10-14
Maybe there is a way to change the layout of the screens in server layout? or is this something that would be better handled my metamodes?

---

### Post by DJYoshaBYD on 2012-10-14
Now, I disabled xinerama and enabled composite, which should enable RandR and get all 3 screens working with compositing. Alas, it did not work. It defaulted back to classic, added a couple of panels, and now the left screen works, without compositing, and the center and right screen are white with panels, but when I right click them, they work like separate X screens.

Here is the xorg.conf for this setup:

```


Section "ServerLayout"
Identifier "Layout0"
Screen 0 "Screen0" 0 0
Screen 1 "Screen1" RightOf "Screen0"
Screen 2 "Screen2" RightOf "Screen1"
Option "Xinerama" "0"
#	Option         "AIGLX" "true"
#	Option         "RenderAccel" "true"
	Option         "AllowGLXWithComposite" "true"
#	Option         "XGL" "true"
EndSection

Section "Module"
#	Load           "dbe"
#	Load           "extmod"
#	Load           "type1"
#	Load           "freetype"
	Load	       "glx"
	Load           "dri"
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
	Option         "Composite" "enabled"
EndSection

############################################################################
############################# Monitors
##############################################################################

Section "Monitor"
Identifier "Monitor0"
VendorName "Acer"
ModelName "20 Inch"
HorizSync 24.0 - 82.0
VertRefresh 48.0 - 76.0
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Monitor1"
VendorName "HP"
ModelName "MidPuta"
HorizSync 24.0 - 82.0
VertRefresh 48.0 - 76.0
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Monitor2"
VendorName "Samsung"
ModelName "10 Inch"
HorizSync 24.0 - 82.0
VertRefresh 48.0 - 76.0
Option "DPMS"
EndSection

##########################################################################################
################################ Devices
############################################################################################3

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GT 240"
BusID "PCI:3:0:0"
Screen 0
EndSection

Section "Device"
Identifier "Device1"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GT 240"
BusID "PCI:3:0:0"
Screen 1
EndSection

Section "Device"
Identifier "Device2"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "8600 GT"
BusID "PCI:6:0:0"
Screen 0
EndSection

#############################################################################
######################### Screens
############################################################################

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "DFP-1: nvidia-auto-select +0+0"
Option         "AddARGBGLXVisuals" "True"
SubSection "Display"
Depth 24
EndSubSection
EndSection


Section "Screen"
Identifier "Screen1"
Device "Device1"
Monitor "Monitor1"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "CRT-1: nvidia-auto-select +0+0"
Option         "AddARGBGLXVisuals" "True"
SubSection "Display"
Depth 24
EndSubSection
EndSection

Section "Screen"
Identifier "Screen2"
Device "Device2"
Monitor "Monitor2"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "DFP-0: nvidia-auto-select +0+0"
Option         "AddARGBGLXVisuals" "True"
SubSection "Display"
Depth 24
EndSubSection
EndSection


```


and here is the log for this setup:

```


[    24.023] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    24.023] X Protocol Version 11, Revision 0
[    24.023] Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
[    24.023] Current Operating System: Linux TIFA 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64
[    24.023] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-32-generic root=UUID=cffe6d68-aaae-462f-9d3a-10f563f553d9 ro quiet splash vt.handoff=7
[    24.023] Build Date: 29 August 2012  12:12:33AM
[    24.023] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[    24.023] Current version of pixman: 0.24.4
[    24.023] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    24.023] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.023] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 14 14:52:51 2012
[    24.023] (==) Using config file: "/etc/X11/xorg.conf"
[    24.023] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.024] (==) ServerLayout "Layout0"
[    24.024] (**) |-->Screen "Screen0" (0)
[    24.024] (**) |   |-->Monitor "Monitor0"
[    24.024] (**) |   |-->Device "Device0"
[    24.024] (**) |-->Screen "Screen1" (1)
[    24.024] (**) |   |-->Monitor "Monitor1"
[    24.024] (**) |   |-->Device "Device1"
[    24.024] (**) |-->Screen "Screen2" (2)
[    24.024] (**) |   |-->Monitor "Monitor2"
[    24.024] (**) |   |-->Device "Device2"
[    24.024] (**) Option "Xinerama" "0"
[    24.024] (==) Automatically adding devices
[    24.024] (==) Automatically enabling devices
[    24.024] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.024] 	Entry deleted from font path.
[    24.024] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.024] 	Entry deleted from font path.
[    24.024] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.024] 	Entry deleted from font path.
[    24.024] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.024] 	Entry deleted from font path.
[    24.024] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.024] 	Entry deleted from font path.
[    24.024] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    24.024] 	Entry deleted from font path.
[    24.024] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    24.024] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.024] (**) Extension "Composite" is enabled
[    24.024] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.024] (II) Loader magic: 0x7f91b9eefb00
[    24.024] (II) Module ABI versions:
[    24.024] 	X.Org ANSI C Emulation: 0.4
[    24.024] 	X.Org Video Driver: 11.0
[    24.024] 	X.Org XInput driver : 16.0
[    24.024] 	X.Org Server Extension : 6.0
[    24.025] (--) PCI:*(0:3:0:0) 10de:0ca3:196e:0789 rev 162, Mem @ 0xec000000/16777216, 0xb0000000/268435456, 0xce000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[    24.025] (--) PCI: (0:6:0:0) 10de:0402:196e:043a rev 161, Mem @ 0xea000000/16777216, 0x80000000/536870912, 0xe8000000/33554432, I/O @ 0x0000ac00/128, BIOS @ 0x????????/131072
[    24.025] (II) Open ACPI successful (/var/run/acpid.socket)
[    24.025] (II) "extmod" will be loaded by default.
[    24.025] (II) "dbe" will be loaded by default.
[    24.025] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    24.025] (II) "record" will be loaded by default.
[    24.025] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    24.025] (II) "dri2" will be loaded by default.
[    24.025] (II) LoadModule: "glx"
[    24.026] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    24.037] (II) Module glx: vendor="NVIDIA Corporation"
[    24.037] 	compiled for 4.0.2, module version = 1.0.0
[    24.037] 	Module class: X.Org Server Extension
[    24.037] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[    24.037] (II) Loading extension GLX
[    24.037] (II) LoadModule: "dri"
[    24.037] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    24.037] (II) Module dri: vendor="X.Org Foundation"
[    24.037] 	compiled for 1.11.3, module version = 1.0.0
[    24.037] 	ABI class: X.Org Server Extension, version 6.0
[    24.037] (II) Loading extension XFree86-DRI
[    24.037] (II) LoadModule: "extmod"
[    24.037] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    24.038] (II) Module extmod: vendor="X.Org Foundation"
[    24.038] 	compiled for 1.11.3, module version = 1.0.0
[    24.038] 	Module class: X.Org Server Extension
[    24.038] 	ABI class: X.Org Server Extension, version 6.0
[    24.038] (II) Loading extension MIT-SCREEN-SAVER
[    24.038] (II) Loading extension XFree86-VidModeExtension
[    24.038] (II) Loading extension XFree86-DGA
[    24.038] (II) Loading extension DPMS
[    24.038] (II) Loading extension XVideo
[    24.038] (II) Loading extension XVideo-MotionCompensation
[    24.038] (II) Loading extension X-Resource
[    24.038] (II) LoadModule: "dbe"
[    24.038] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    24.038] (II) Module dbe: vendor="X.Org Foundation"
[    24.038] 	compiled for 1.11.3, module version = 1.0.0
[    24.038] 	Module class: X.Org Server Extension
[    24.038] 	ABI class: X.Org Server Extension, version 6.0
[    24.038] (II) Loading extension DOUBLE-BUFFER
[    24.038] (II) LoadModule: "record"
[    24.038] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    24.038] (II) Module record: vendor="X.Org Foundation"
[    24.038] 	compiled for 1.11.3, module version = 1.13.0
[    24.038] 	Module class: X.Org Server Extension
[    24.038] 	ABI class: X.Org Server Extension, version 6.0
[    24.038] (II) Loading extension RECORD
[    24.038] (II) LoadModule: "dri2"
[    24.038] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.038] (II) Module dri2: vendor="X.Org Foundation"
[    24.038] 	compiled for 1.11.3, module version = 1.2.0
[    24.038] 	ABI class: X.Org Server Extension, version 6.0
[    24.038] (II) Loading extension DRI2
[    24.038] (II) LoadModule: "nvidia"
[    24.038] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    24.039] (II) Module nvidia: vendor="NVIDIA Corporation"
[    24.039] 	compiled for 4.0.2, module version = 1.0.0
[    24.039] 	Module class: X.Org Video Driver
[    24.039] (II) NVIDIA dlloader X Driver  295.40  Thu Apr  5 21:38:35 PDT 2012
[    24.039] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    24.039] (++) using VT number 7

[    24.039] (II) Loading sub module "fb"
[    24.039] (II) LoadModule: "fb"
[    24.039] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.039] (II) Module fb: vendor="X.Org Foundation"
[    24.039] 	compiled for 1.11.3, module version = 1.0.0
[    24.039] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    24.039] (II) Loading sub module "wfb"
[    24.039] (II) LoadModule: "wfb"
[    24.073] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    24.073] (II) Module wfb: vendor="X.Org Foundation"
[    24.073] 	compiled for 1.11.3, module version = 1.0.0
[    24.073] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    24.073] (II) Loading sub module "ramdac"
[    24.073] (II) LoadModule: "ramdac"
[    24.073] (II) Module "ramdac" already built-in
[    24.073] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    24.073] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    24.073] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.073] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    24.073] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    24.073] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.073] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    24.073] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    24.073] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.073] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    24.073] (==) NVIDIA(0): RGB weight 888
[    24.073] (==) NVIDIA(0): Default visual is TrueColor
[    24.073] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    24.073] (**) NVIDIA(0): Option "TwinView" "0"
[    24.073] (**) NVIDIA(0): Option "MetaModes" "DFP-1: nvidia-auto-select +0+0"
[    24.073] (**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
[    24.073] (**) NVIDIA(0): Enabling 2D acceleration
[    25.591] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
[    25.608] (II) NVIDIA(GPU-0): Display (Acer X193W+ (DFP-1)) does not support NVIDIA 3D
[    25.608] (II) NVIDIA(GPU-0):     Vision stereo.
[    25.609] (II) NVIDIA(0): NVIDIA GPU GeForce GT 240 (GT215) at PCI:3:0:0 (GPU-0)
[    25.609] (--) NVIDIA(0): Memory: 1048576 kBytes
[    25.609] (--) NVIDIA(0): VideoBIOS: 70.15.20.00.51
[    25.609] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    25.609] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    25.611] (--) NVIDIA(0): Connected display device(s) on GeForce GT 240 at PCI:3:0:0
[    25.611] (--) NVIDIA(0):     CRT-1
[    25.612] (--) NVIDIA(0):     Acer X193W+ (DFP-1)
[    25.612] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    25.612] (--) NVIDIA(0): Acer X193W+ (DFP-1): 165.0 MHz maximum pixel clock
[    25.612] (--) NVIDIA(0): Acer X193W+ (DFP-1): Internal Single Link TMDS
[    25.612] (II) NVIDIA(0): Display Device found referenced in MetaMode: DFP-1
[    25.612] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    25.612] (**) NVIDIA(0):     device Acer X193W+ (DFP-1) (Using EDID frequencies has
[    25.612] (**) NVIDIA(0):     been enabled on all display devices.)
[    25.668] (II) NVIDIA(0): Assigned Display Device: DFP-1
[    25.668] (II) NVIDIA(0): Validated modes:
[    25.668] (II) NVIDIA(0):     "DFP-1:nvidia-auto-select+0+0"
[    25.668] (II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
[    25.691] (--) NVIDIA(0): DPI set to (104, 102); computed from "UseEdidDpi" X config
[    25.691] (--) NVIDIA(0):     option
[    25.691] (**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    25.691] (**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
[    25.691] (==) NVIDIA(1): RGB weight 888
[    25.691] (==) NVIDIA(1): Default visual is TrueColor
[    25.691] (==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
[    25.691] (**) NVIDIA(1): Option "TwinView" "0"
[    25.691] (**) NVIDIA(1): Option "MetaModes" "CRT-1: nvidia-auto-select +0+0"
[    25.691] (**) NVIDIA(1): Option "AddARGBGLXVisuals" "True"
[    25.691] (II) NVIDIA(1): NVIDIA GPU GeForce GT 240 (GT215) at PCI:3:0:0 (GPU-0)
[    25.691] (--) NVIDIA(1): Memory: 1048576 kBytes
[    25.691] (--) NVIDIA(1): VideoBIOS: 70.15.20.00.51
[    25.691] (II) NVIDIA(1): Detected PCI Express Link width: 16X
[    25.691] (--) NVIDIA(1): Interlaced video modes are supported on this GPU
[    25.693] (--) NVIDIA(1): Connected display device(s) on GeForce GT 240 at PCI:3:0:0
[    25.693] (--) NVIDIA(1):     CRT-1
[    25.693] (--) NVIDIA(1):     Acer X193W+ (DFP-1)
[    25.693] (--) NVIDIA(1): CRT-1: 400.0 MHz maximum pixel clock
[    25.693] (--) NVIDIA(1): Acer X193W+ (DFP-1): 165.0 MHz maximum pixel clock
[    25.693] (--) NVIDIA(1): Acer X193W+ (DFP-1): Internal Single Link TMDS
[    25.693] (II) NVIDIA(1): Display Device found referenced in MetaMode: CRT-1
[    25.693] (**) NVIDIA(1): Using HorizSync/VertRefresh ranges from the EDID for display
[    25.693] (**) NVIDIA(1):     device CRT-1 (Using EDID frequencies has been enabled on
[    25.693] (**) NVIDIA(1):     all display devices.)
[    25.704] (II) NVIDIA(1): Assigned Display Device: CRT-1
[    25.704] (II) NVIDIA(1): Validated modes:
[    25.704] (II) NVIDIA(1):     "CRT-1:nvidia-auto-select+0+0"
[    25.704] (II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
[    25.706] (WW) NVIDIA(1): Unable to get display device CRT-1's EDID; cannot compute DPI
[    25.706] (WW) NVIDIA(1):     from CRT-1's EDID.
[    25.706] (==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
[    25.706] (**) NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
[    25.706] (**) NVIDIA(2): Depth 24, (--) framebuffer bpp 32
[    25.706] (==) NVIDIA(2): RGB weight 888
[    25.706] (==) NVIDIA(2): Default visual is TrueColor
[    25.706] (==) NVIDIA(2): Using gamma correction (1.0, 1.0, 1.0)
[    25.706] (**) NVIDIA(2): Option "TwinView" "0"
[    25.706] (**) NVIDIA(2): Option "MetaModes" "DFP-0: nvidia-auto-select +0+0"
[    25.706] (**) NVIDIA(2): Option "AddARGBGLXVisuals" "True"
[    25.707] (**) NVIDIA(2): Enabling 2D acceleration
[    26.795] (II) NVIDIA(GPU-1): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[    26.795] (II) NVIDIA(GPU-1):     3D Vision stereo.
[    26.800] (II) NVIDIA(2): NVIDIA GPU GeForce 8600 GT (G84) at PCI:6:0:0 (GPU-1)
[    26.800] (--) NVIDIA(2): Memory: 524288 kBytes
[    26.800] (--) NVIDIA(2): VideoBIOS: 60.84.34.00.51
[    26.800] (II) NVIDIA(2): Detected PCI Express Link width: 16X
[    26.800] (--) NVIDIA(2): Interlaced video modes are supported on this GPU
[    26.804] (--) NVIDIA(2): Connected display device(s) on GeForce 8600 GT at PCI:6:0:0
[    26.804] (--) NVIDIA(2):     Samsung SyncMaster (DFP-0)
[    26.804] (--) NVIDIA(2): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
[    26.804] (--) NVIDIA(2): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
[    26.804] (II) NVIDIA(2): Display Device found referenced in MetaMode: DFP-0
[    26.804] (**) NVIDIA(2): Using HorizSync/VertRefresh ranges from the EDID for display
[    26.804] (**) NVIDIA(2):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[    26.804] (**) NVIDIA(2):     has been enabled on all display devices.)
[    26.862] (II) NVIDIA(2): Assigned Display Device: DFP-0
[    26.862] (II) NVIDIA(2): Validated modes:
[    26.862] (II) NVIDIA(2):     "DFP-0:nvidia-auto-select+0+0"
[    26.862] (II) NVIDIA(2): Virtual screen size determined to be 1440 x 900
[    26.870] (--) NVIDIA(2): DPI set to (89, 87); computed from "UseEdidDpi" X config
[    26.870] (--) NVIDIA(2):     option
[    26.870] (**) NVIDIA(2): Enabling 32-bit ARGB GLX visuals.
[    26.870] (--) Depth 24 pixmap format is 32 bpp
[    26.870] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    26.876] (II) NVIDIA(0): Setting mode "DFP-1:nvidia-auto-select+0+0"
[    26.911] (II) Loading extension NV-GLX
[    26.945] (==) NVIDIA(0): Disabling shared memory pixmaps
[    26.945] (==) NVIDIA(0): Backing store disabled
[    26.945] (==) NVIDIA(0): Silken mouse enabled
[    26.946] (**) NVIDIA(0): DPMS enabled
[    26.946] (II) Loading extension NV-CONTROL
[    26.946] (II) Loading extension XINERAMA
[    26.946] (II) Loading sub module "dri2"
[    26.946] (II) LoadModule: "dri2"
[    26.946] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.946] (II) Module dri2: vendor="X.Org Foundation"
[    26.946] 	compiled for 1.11.3, module version = 1.2.0
[    26.946] 	ABI class: X.Org Server Extension, version 6.0
[    26.946] (II) NVIDIA(0): [DRI2] Setup complete
[    26.946] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    26.946] (==) RandR enabled
[    26.950] (II) NVIDIA(1): Setting mode "CRT-1:nvidia-auto-select+0+0"
[    27.141] (==) NVIDIA(1): Disabling shared memory pixmaps
[    27.141] (==) NVIDIA(1): Backing store disabled
[    27.141] (==) NVIDIA(1): Silken mouse enabled
[    27.141] (**) NVIDIA(1): DPMS enabled
[    27.142] (II) Loading sub module "dri2"
[    27.142] (II) LoadModule: "dri2"
[    27.142] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    27.142] (II) Module dri2: vendor="X.Org Foundation"
[    27.142] 	compiled for 1.11.3, module version = 1.2.0
[    27.142] 	ABI class: X.Org Server Extension, version 6.0
[    27.142] (II) NVIDIA(1): [DRI2] Setup complete
[    27.142] (II) NVIDIA(1): [DRI2]   VDPAU driver: nvidia
[    27.142] (==) RandR enabled
[    27.151] (II) NVIDIA(2): Setting mode "DFP-0:nvidia-auto-select+0+0"
[    27.253] (==) NVIDIA(2): Disabling shared memory pixmaps
[    27.253] (==) NVIDIA(2): Backing store disabled
[    27.253] (==) NVIDIA(2): Silken mouse enabled
[    27.253] (**) NVIDIA(2): DPMS enabled
[    27.253] (II) Loading sub module "dri2"
[    27.253] (II) LoadModule: "dri2"
[    27.253] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    27.253] (II) Module dri2: vendor="X.Org Foundation"
[    27.253] 	compiled for 1.11.3, module version = 1.2.0
[    27.253] 	ABI class: X.Org Server Extension, version 6.0
[    27.253] (II) NVIDIA(2): [DRI2] Setup complete
[    27.253] (II) NVIDIA(2): [DRI2]   VDPAU driver: nvidia
[    27.253] (==) RandR enabled
[    27.253] (II) Initializing built-in extension Generic Event Extension
[    27.253] (II) Initializing built-in extension SHAPE
[    27.253] (II) Initializing built-in extension MIT-SHM
[    27.253] (II) Initializing built-in extension XInputExtension
[    27.253] (II) Initializing built-in extension XTEST
[    27.253] (II) Initializing built-in extension BIG-REQUESTS
[    27.253] (II) Initializing built-in extension SYNC
[    27.253] (II) Initializing built-in extension XKEYBOARD
[    27.253] (II) Initializing built-in extension XC-MISC
[    27.253] (II) Initializing built-in extension SECURITY
[    27.253] (II) Initializing built-in extension XINERAMA
[    27.253] (II) Initializing built-in extension XFIXES
[    27.253] (II) Initializing built-in extension RENDER
[    27.253] (II) Initializing built-in extension RANDR
[    27.253] (II) Initializing built-in extension COMPOSITE
[    27.253] (II) Initializing built-in extension DAMAGE
[    27.254] (II) Initializing extension GLX
[    27.273] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.275] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    27.275] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.275] (II) LoadModule: "evdev"
[    27.276] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.276] (II) Module evdev: vendor="X.Org Foundation"
[    27.276] 	compiled for 1.11.3, module version = 2.7.0
[    27.276] 	Module class: X.Org XInput Driver
[    27.276] 	ABI class: X.Org XInput driver, version 16.0
[    27.276] (II) Using input driver 'evdev' for 'Power Button'
[    27.276] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.276] (**) Power Button: always reports core events
[    27.276] (**) evdev: Power Button: Device: "/dev/input/event1"
[    27.276] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.276] (--) evdev: Power Button: Found keys
[    27.276] (II) evdev: Power Button: Configuring as keyboard
[    27.276] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    27.276] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    27.276] (**) Option "xkb_rules" "evdev"
[    27.276] (**) Option "xkb_model" "pc105"
[    27.276] (**) Option "xkb_layout" "us"
[    27.276] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    27.276] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.276] (II) Using input driver 'evdev' for 'Power Button'
[    27.276] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.276] (**) Power Button: always reports core events
[    27.276] (**) evdev: Power Button: Device: "/dev/input/event0"
[    27.276] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.276] (--) evdev: Power Button: Found keys
[    27.276] (II) evdev: Power Button: Configuring as keyboard
[    27.276] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    27.276] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    27.276] (**) Option "xkb_rules" "evdev"
[    27.276] (**) Option "xkb_model" "pc105"
[    27.277] (**) Option "xkb_layout" "us"
[    27.277] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event4)
[    27.277] (II) No input driver specified, ignoring this device.
[    27.277] (II) This device may have been added with another device file.
[    27.277] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event5)
[    27.277] (II) No input driver specified, ignoring this device.
[    27.277] (II) This device may have been added with another device file.
[    27.277] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event6)
[    27.277] (II) No input driver specified, ignoring this device.
[    27.277] (II) This device may have been added with another device file.
[    27.277] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event7)
[    27.278] (II) No input driver specified, ignoring this device.
[    27.278] (II) This device may have been added with another device file.
[    27.278] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/event3)
[    27.278] (**) Logitech USB Trackball: Applying InputClass "evdev pointer catchall"
[    27.278] (II) Using input driver 'evdev' for 'Logitech USB Trackball'
[    27.278] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.278] (**) Logitech USB Trackball: always reports core events
[    27.278] (**) evdev: Logitech USB Trackball: Device: "/dev/input/event3"
[    27.278] (--) evdev: Logitech USB Trackball: Vendor 0x46d Product 0xc408
[    27.278] (--) evdev: Logitech USB Trackball: Found 9 mouse buttons
[    27.278] (--) evdev: Logitech USB Trackball: Found relative axes
[    27.278] (--) evdev: Logitech USB Trackball: Found x and y relative axes
[    27.278] (II) evdev: Logitech USB Trackball: Configuring as mouse
[    27.278] (**) evdev: Logitech USB Trackball: YAxisMapping: buttons 4 and 5
[    27.278] (**) evdev: Logitech USB Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    27.278] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-9/2-9:1.0/input/input3/event3"
[    27.278] (II) XINPUT: Adding extended input device "Logitech USB Trackball" (type: MOUSE, id 8)
[    27.278] (II) evdev: Logitech USB Trackball: initialized for relative axes.
[    27.278] (**) Logitech USB Trackball: (accel) keeping acceleration scheme 1
[    27.278] (**) Logitech USB Trackball: (accel) acceleration profile 0
[    27.278] (**) Logitech USB Trackball: (accel) acceleration factor: 2.000
[    27.278] (**) Logitech USB Trackball: (accel) acceleration threshold: 4
[    27.278] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/mouse0)
[    27.278] (II) No input driver specified, ignoring this device.
[    27.278] (II) This device may have been added with another device file.
[    27.279] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    27.279] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    27.279] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    27.279] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.279] (**) AT Translated Set 2 keyboard: always reports core events
[    27.279] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    27.279] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    27.279] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    27.279] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    27.279] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    27.279] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    27.279] (**) Option "xkb_rules" "evdev"
[    27.279] (**) Option "xkb_model" "pc105"
[    27.279] (**) Option "xkb_layout" "us"
[    28.580] (II) NVIDIA(0): Setting mode "1680x1050_60_0"
[    36.444] (II) NVIDIA(1): Setting mode "CRT-1:nvidia-auto-select+0+0"
[    36.524] (II) NVIDIA(0): Setting mode "1024x768"
[    36.954] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm


```


Any ideas? lol :D

---

### Post by DJYoshaBYD on 2012-10-15
Bump, please. :D

---

### Post by Favux on 2012-10-15
Well looking at your post #19:  [http://ubuntuforums.org/showpost.php?p=12295699&postcount=19](http://ubuntuforums.org/showpost.php?p=12295699&postcount=19)  the one with the two blank screens I noticed something.  By the way I like how you've now got the xorg.conf so organized.  Anyway if you look at the link to the guy who claims to have 3 monitors working notice in one of his screen sections he has TwinView turned off:
```
	Option         "TwinView" "1"
```
Whereas you have them all with TwinView turned on:
```
	Option         "TwinView" "0"
```

The mental picture I have of what we're trying to emulate is two monitors in TwinView.  Then we treat the two monitors in Twinview as "one" monitor and put that "monitor" in Xinerama with the third monitor.

---

### Post by DJYoshaBYD on 2012-10-15
ok. Do you think you could make the changes to the xorg.conf file I posted so that I can try it later?

And yeah. lol. I hate the way it looks bone stock, so Im going to create a template. Im actually thinking about writing a GUI for doing advanced configuration with the xorg.conf file. That will be a work in progress, though. haha. :)

Thanks a lot for all of your help. I really want to get this running, as right now Im running gnome classic on 3 monitors, and its working great, this is the final piece of the puzzle for my workstation.

---

### Post by DJYoshaBYD on 2012-10-15
Also, doesnt having Xinerama on AT ALL disable compositing? Thats the issue Im trying to get around. With xinerama on at all, it will NOT run compositing, which sucks. From what I understand, I should be able to use XRandR to arrange my screens, and still use compositing. I know my drivers are XRandR compatible, but I cannot figure how to even use XRandR. 

Do you know how to use xrandr? I think that may be the only way to do this. :(

---

### Post by Favux on 2012-10-15
> Also, doesnt having Xinerama on AT ALL disable compositing? Thats the issue Im trying to get around.
That's my understanding.  Do you think the guy's claims are bogus?  Or that maybe I'm misunderstanding him?

My recollection is vague but it seems to me I read somewhere that Xinerama development was discontinued by Xorg 2-3 years ago.  But at that time they were working on implementing compositing, maybe.  Would need to find where the Xinerama code is and see if there are any commits related to that.

The problem you are having with quickly running through his suggestions is your Device0 is his Device2.  So his Screens and ServerLayout are in a different order than yours.

As far as XrandR goes I've done it with compositing on dual monitors:  [http://forums.linuxmint.com/viewtopic.php?f=42&t=111779&sid=4693cbe38463a884e770ff39e524388b](http://forums.linuxmint.com/viewtopic.php?f=42&t=111779&sid=4693cbe38463a884e770ff39e524388b)  As you can see I did the Monitor mapping or layout for the Screen section's Virtual screen in the second Monitor section rather than ServerLayout.  Haven't ever played with 3 monitors.

---

### Post by DJYoshaBYD on 2012-10-15
Yeah. I know that xinerama disables xrandr right off the bat, and xinerama wont use compositing, but xrandr will. xrandr does everything that Im looking for with all of the modules I need, but the discussions about it are usually vague, years old, probably outdated, and the manual reads like sign language to a blind person. haha. Im checking out that link.

Thanks so much for your help. I have been trying to get this working for 2 weeks straight. lol

---

### Post by DJYoshaBYD on 2012-10-17
Ok. So, Here is what I have so far:

```


Section "Device"
        Identifier      "Device0"
        BusID           "PCI:3:0:0"
        Option          "Monitor-DFP-1" "Left"
        Option          "Monitor-CRT-1" "Center"
        Option          "DPMS
        Option          "MultiGPU" "auto"
EndSection

Section "Device"
	Identifier      "Device1"
        BusID           "PCI:6:0:0"
        Option          "Monitor-CRT-1" "Right"
        Option          "DPMS"
        Option          "MultiGPU" "auto "
EndSection

Section "Monitor"
        Identifier      "Left"
    Option         "PreferredMode" "1680x1050"
EndSection

Section "Monitor"
        Identifier      "Center"
    Option         "PreferredMode" "1024x768"
EndSection

Section "Monitor"
        Identifier      "Right"
    Option         "PreferredMode" "1440x900"
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Device0"
        DefaultDepth    24
        SubSection "Display"
            Depth           24
            Virtual         4144 1050
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Device0"
        DefaultDepth    24
        SubSection "Display"
            Depth           24
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen2"
        Device          "Device1"
        DefaultDepth    24
        SubSection "Display"
            Depth           24
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Screen0"
        Screen          "Screen1"
	Screen          "Screen2"
EndSection


```

I can rotate the left and middle monitor using xrandr, and I get full compositing. I updated to the newest experimental drivers (to try and get xrandr 1.4 support, as it can handle multiple cards, I think), and it started to kind-of work. when I type xrandr, I get this:

```


joo@TIFA:~$ xrandr -q
Screen 0: minimum 8 x 8, current 2704 x 1050, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected 1024x768+1680+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   1360x768       60.0     59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384       119.9    119.6  
   640x480        59.9  
   512x384       120.0  
   400x300       144.4  
   320x240       120.1  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1680x1050      60.0*+
   1440x900       75.0     59.9  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x720       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
joo@TIFA:~$ 


```

I cannot get xrandr to see that my 8600GT has a monitor hooked up via CRT. Is there a way to make it aware of the other cards plugs?

---

### Post by Favux on 2012-10-17
[EDID]("http://en.wikipedia.org/wiki/Extended_display_identification_data") problem with one of the monitors?  You could try swapping them and the connectors around.

Let's see if [read-edid]("http://manpages.ubuntu.com/manpages/lucid/man1/get-edid.1.html") tells you anything.
```
sudo apt-get install read-edid
```
Then read edid with both cards and all 3 monitors attached.
```
sudo get-edid | parse-edid
```

---

### Post by DJYoshaBYD on 2012-10-18
I tried that, and it failed.

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
parse-edid: IO error reading EDID

Also, I cannot log in as my username anymore. After I type in my password and hit enter at the ubuntu login, it starts to log in, then just goes right back to the login screen. Weaaak. I feel like Im right there now, and Im not quitting until I figure this out. lol

---

### Post by DJYoshaBYD on 2012-10-18
Ok. I figured out how to stop the login issue I was having. Apparently its a permissions issue. HOW? I dont know. here was the fix.

```


sudo chown -R user:user /home/user


```

Replace "user" with your username. I just thought this might help someone in the future. :)

---

### Post by DJYoshaBYD on 2012-10-23
That is sad that this thread, and SO many others have died out, when this is such a huge issue for anyone running more than 2 monitors. 

Well, after about a month, and HOURS UPON HOURS per day reading, researching, breaking X, trying hacks, etc etc etc., I finally figured it out (kind of) using XRandR. Full compositing, full 3D graphics, the works. Its beautiful. 

Im going to do a write up on it once I get all of the little nuances straightened out, as its not hard, but the documentation is TERRIBLE! Its all old, nothing is updated, and most conversations about this subject are dead and ever older. 

I hope this thread and my future write up will help the BUNCHES of people out there who are dead in the water with multi monitor/multi-head setups. 

As soon as I have something solid, Ill post it. :guitar::guitar::guitar::guitar::guitar::guitar:

---

### Post by DJI274 on 2012-10-23
DJYoshaBYD,
Thanks for all your hardwork on this, I've been looking for a solution for some time. Look forward to reading your write up and implementing myself

---

### Post by WJohnG on 2012-10-31
DJYoshaBYD, please post the info - even if it is in cryptic form. 

I have also been trying to get three monitors going and have had only marginal success (3rd monitor as a separate X screen is not that useful).

thanks!
john

---

### Post by jpalko on 2012-11-05
Please, post what you needed to install or add/tweak/etc to your system and your xorg.conf.

I'm fighting with 3 1920x1080 monitors which I can get to work with xinerama on nvidia binary drivers (2 * 9800 GT cards) but have really annoying stuff with my setup like chrome flash doing weird stuff and not having composite of course. Would like really much to switch to something supporting composite.

I have also weird stuff like the center screen scrolling the left and possibly also the right hand virtual screen area for some reason.

---

### Post by schievelbein on 2012-11-12
I do not know if this will help anybody, but here is my xorg.conf.
I have three monitors running on 2 cards.  My main screen is in the center and run off my GTX460.  My two rotated side monitors are off from my GTX275.  ```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 295.33  (buildd@allspice)  Fri Mar 30 15:25:24 UTC 2012


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" RightOf "Screen1"
    Screen      1  "Screen1" 0 0
    Screen      2  "Screen2" RightOf "Screen0"
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
    ModelName      "DELL U3011"
    HorizSync       29.0 - 113.0
    VertRefresh     49.0 - 86.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer G205HV"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Acer G205HV"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 460"
    BusID          "PCI:3:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 275"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 275"
    BusID          "PCI:4:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "Rotate" "left"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0  { Rotation=left }"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "Rotate" "right"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0  { Rotation=right }"
#   Option         "metamodes" "DFP-0: nvidia-auto-select +0+400, DFP-1: nvidia-auto-select +1920+0 { Rotation=left }"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by jpalko on 2012-11-12
Does that setup work with Gnome 3 and Composite?

I think I tried that sort of separate screen setup using nvidia binary driver and Gnome 3 didn't like it much last time I tried.

I'd really like to get the nouveau driver working with composite using ZaphodHeads or any other solution that works with it. :)

DJYoshaBYD, please share your solution soonish. And I hope you've also tried it with 12.10 and not just with 12.04. :)

---

### Post by DJYoshaBYD on 2012-11-14
> **jpalko said:**
> Does that setup work with Gnome 3 and Composite?

I think I tried that sort of separate screen setup using nvidia binary driver and Gnome 3 didn't like it much last time I tried.

I'd really like to get the nouveau driver working with composite using ZaphodHeads or any other solution that works with it. :)

DJYoshaBYD, please share your solution soonish. And I hope you've also tried it with 12.10 and not just with 12.04. :)

Zaphod wont work, as they are separate x screens, and you cannot drag windows across, etc etc etc. Composite is cool, but you lose connectivity to the rest of the desktop. 

I doubt he got that working with composite, as xrandr does not span multiple cards at all; that function is just not there (although is planned for the next xrandr build (1.4 i think?)

---

### Post by DJYoshaBYD on 2012-11-14
> **schievelbein said:**
> I do not know if this will help anybody, but here is my xorg.conf.
I have three monitors running on 2 cards.  My main screen is in the center and run off my GTX460.  My two rotated side monitors are off from my GTX275.  ```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 295.33  (buildd@allspice)  Fri Mar 30 15:25:24 UTC 2012


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" RightOf "Screen1"
    Screen      1  "Screen1" 0 0
    Screen      2  "Screen2" RightOf "Screen0"
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
    ModelName      "DELL U3011"
    HorizSync       29.0 - 113.0
    VertRefresh     49.0 - 86.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer G205HV"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Acer G205HV"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 460"
    BusID          "PCI:3:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 275"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 275"
    BusID          "PCI:4:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "Rotate" "left"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0  { Rotation=left }"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "Rotate" "right"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0  { Rotation=right }"
#   Option         "metamodes" "DFP-0: nvidia-auto-select +0+400, DFP-1: nvidia-auto-select +1920+0 { Rotation=left }"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Yeah. My config looked like that, as well. Actually, a bunch of them did. hahaha. But I doubt that compositing is working up to par. Even though xinerama is off, I still couldnt get it to work, simply because of this:

    Option         "TwinView" "1"


That uses nvidia's implementation of xinerama to do this, and if you check your xorg.0.log, it will show that xinerama is getting activated, and composite ext is turned off, as they cannot, and will not be on at the same time. One disables the other.

**DISCLAIMER**
We all know that technology moves STUPID fast. My last post was about a week before I gave up this silly thing, and decided to wait until nvidia and x11 get it straightened out, as its their issue, and im not a programmer (although pretty competent). Something may have changed since then. I know there have been a couple driver updates, like this AM, nvidia released a new driver with a new nvidia-settings that adds support for randr rotation, reflection, viewport, and all sorts of stuff. Although, I cannot find any release notes to see what the changelog states. I believe its nvidia driver 310.19.

So yeah. You might actually have it working, but if you had it set up before I quit trying, I doubt it, as I wasted about a month, non-stop, every single day researching, writing, thinking, smoking way too much ganj, and came to the conclusion that, in short, if I dont work for nvidia and cannot get their source, and I dont know how to program very well, its just not going to happen, and if it does, like I did, it only works for a short time before crashing, and its super glitchy. not anywhere near a good solution. Im a patient man.. Ill wait and save myself the agony. hahahaha

---

### Post by DJYoshaBYD on 2012-11-14
Ok, this is a message I was going to send to someone who emailed me aboot this (thats right. I said it. haha), but I figured I would just post it here, considering there were some responses. 

"[QUOTE=WJohnG]hi DJYoshaBYD,

I would love to see how you got three monitors going (Re: 3 Monitors, Ubuntu 12.04, Gnome 3, 2 nvidia cards, WITH xrandr or xinerama?).

Could you please post your xorg.conf or whatever is easiest for you to get the rest of us going?

thanks!
john[/QUOTE]


Well, my computer/internet connection has been down for a while now (LONG story. haha. thats for another blog), and Im going to update my post today.

The fact of the matter is, yes. I did get it working, but SUPER unstable. It will NOT work, until xinerama is FULLY dropped from X11 (which is coming along better, now that nvidia is starting to give more attention to RandR, which in turn, of course, makes them put out drivers and hardware that support it. Xinerama, no matter what, will never be able to do this... ever. Not with hardware rendering. there was a program/api called xglx or something like that from about 7 years ago that used a software buffer to carry over to the hardware, but its outdated, not maintained.... useless.

In short, this will not be possible (2 cards, 3+ monitors, full HW rendering across all screens, all screens working together) until nvidia and x11 issues are squared away, the issue being xinerama.

As for the xorg.conf, its useless. well, not really, but for all intents and purposes, it caused nothing but problems, and when I had it working, my xorg.conf only had my video cards listed, and thats all. No monitor section, nothing. just a section for each card, the name of each port (VGA, DFP, etc) and the busid. The reason being, well, you just really dont need xorg.conf anymore, as the input is all taken care of by hal, and the rest, from my understanding, is handled by xRandR, which is what we want. The issue is, that with nvidia cards, they will use their own version of Xinerama (implementation, rather), which shuts off x11's native one. Under normal circumstances (ie 1 video card), thats just fine. BUT, if the xinerama extension is activated at ALL, it will NOT let the composite extension run, which means no pretty desktop (no matter how many monitors. 1 monitor with xinerama, no HW accel), but even worse, no hardware acceleration at all. 

My hack (yeah. pretty much), was to force xinerama to NEVER turn on. I did this by fuc**ng up the source code and changing the names to something that wouldnt be found; in this case, adding a "1" to the very end of anything that even remotely said xinerama, so that when I compiled and ran it, it would never run it, as its looking for a name that doesnt exist. This would let xRandr work for about 10 minutes at the most (every once in a while it would last longer), but it was shaky, and the monitor on the 2nd card would flicker here and there. Not stable, not a good fix, not necessarily a waste of time, though. hahaha. I learned a lot, and it was fun to get balls deep into linux and really see whats going on. 

Anyway, short of a hardware fix (buy 1 card that supports 3 monitors, or buy that ati multimonitor box thingy. cant remember the name), you will not get composite and 3 monitors running at the same time and have it be worth a damn until xinerama is completely deprecated. 

If Im wrong on anything, Im sorry. Lol. I gave up on that a couple of weeks ago, but read so much, that its hard to remember exactly everything. Im an engineer by trade, and know, well, i cant say... too much for my own good. 20+ years sleeping with a computer like a farmer sleeps with pigs. hahahaha. I understand what it is, and what needs to be done, but only from a guru's point of view. This is something that would need to be handled by the devs at Nvidia and x11, as for all of my experience, programming is a language that I dont speak yet (although I fully understand what is needed, how its done, etc etc etc.. Just cant speak/write it. hahaha), although, that is going to change in the next couple of months, as Im going to devote a WHOLE LOT of time to the Wine project, as I feel that is the most important project for linux/OSX right now. 

Feel free to pick my brain, and Ill answer anything that I can from what I have learned recently and what I can remember anyway. haha"

---

### Post by jpalko on 2012-11-14
Okay, thanks for the reply. I thought there would have been some nice simple solution that I hadn't just found out yet. Have to wait then for xrandr 1.4 or wayland to happen or something other. I did something a bit similar than what your solution attempt was with debian potato ages ago when I had to get dual head matrox working in 2000. :)

I'll continue using my 3 head xinerama desktop with xfce at work then. It actually is nice for working as it doesn't have anything excessively distracting from work. ;)

---

### Post by DJYoshaBYD on 2012-11-14
Well, Wayland is already implemented in the newer versions. Check your repo. Its installed. But until they COMPLETELY drop Xinerama from the trunk, we are SOL, even if everything goes to xrandr 1.4 and beyond. Xinerama will not, ever, let compositing run while its on. At least not from what I have read, and not from what I have seen. I probably have logged over 200 hours on this project. It aint happening. Im sure there are people on here a million times smarter than me, and I didnt get it, and they didnt get it, so now its up to the manufacturers. 

Although, almost all of the new nvidia drivers that I have seen come out in the last 2 months, have all had xrandr updates in the changelog. Xinerama is on its last leg, and now we just have to wait for nvidia and X to break that leg and throw xinerama in the orchards with the squirrels. hahaha

---

### Post by DJYoshaBYD on 2012-11-14
The bottom line, this is what we need:

Xinerama ELIMINATED, GONE, D-E-D... DED.
Xrandr FULLY implemented
Xrandr support for multicard/multihead support with composite

We get that, we are good to go.

---

### Post by jpalko on 2012-11-17
Since we're talking of cards as well. What's the most reasonably priced 3 head nvidia card that has triple HDMI or DVI output?

I don't want to go the amd/ati way with this one. Especially now that nvidia has just started really to improve drivers with Valve's co-operation and amd/ati has not been that active on that front, yet at least...

Or of course if I can get triplehead radeon (with open source driver) output with a much more reasonable price range, do tell of a such card and if something is necessary otherwise too. :) I have 3 monitors that have HDMI, DVI and D-SUB connectors. I was checking that some of those earlier models needed an Active DP->DVI adapter to get 3 monitors connected when the other 2 are in DVI and HDMI connectors. I couldn't find anything on those newest cards that have 2 DVI, 1 HDMI and 1 DP connector whether they need that still...

---

### Post by DJYoshaBYD on 2012-11-18
Honestly, I dont see the point of using open-source drivers any time soon, simply because they lack so many features. Im ALL about open source, but the native, proprietary drivers are fantastic. I have actually found Nvidia drivers to be great across the board for windows and linux. Never had an issue. The problem that is addressed here is directly related to the GFX manufacturers timeline of development conflicting with X, and thats just how it was. Times have changed, and its not only because of Steam; its because computers are faster now than they have ever been, and its time to step up to the plate and get more issues fixed that have been tossed to the wayside for more important projects. 

as for the video cards, Nvidia makes some FLY dual GPU cards that you could run 4+ monitors off of. Anytime I buy a new card, I never spend over 250, but I never drop under 150, either. Hit up newegg or tigerdirect and see whats on sale. Find something that you like and that fits your specs, then do some research, and make sure it will do what you want with the flavour of OS you are going to use. IMO, Nvidia is the best way to go, but its all about what you want, and what you like. Hope this helps out a bit.

---

### Post by linas on 2012-11-20
FYI, I just got 3 monitors, two nvidia graphics cards working, using the nouveau driver.  I found the magic instructions for doing this at: 

[http://nouveau.freedesktop.org/wiki/MultiMonitorDesktop](http://nouveau.freedesktop.org/wiki/MultiMonitorDesktop)

The secret was to use ZaphodHeads as described there.

Disclaimers:  
-- I'm only interested in 2D not 3D, so this is good enough for me. 
-- I'm running gnome classic, not unity
-- I can't figure out how to rotate the displays to vertical: xinerama disables randr and the X11 defaults to wide horizontal displays.  I wanted three tall vertical displays.  I'm getting worried that I can't do this ...

---

### Post by Favux on 2012-11-20
Hi linas,

Have you added to your **Section "Device"** sections?
```
    Option         "RandRRotation" "on"      # enable rotation
```

---

### Post by linas on 2012-11-20
> **Favux said:**
> 

Have you added to your **Section "Device"** sections?
```
    Option         "RandRRotation" "on"      # enable rotation
```

No, since RandR does not work with Xinerama!  (This is "well-known", discussed in many threads and blog posts) However, I found something that does work: Add this:

```
    Option         "Rotate" "Left" 
```

to **Section "Monitor"** (yes, you read that right -- Monitor, not Device!) Apparently, the nouveau driver knows about this option in this section, and will do the rotation, without the help of RandR.

(I rotated all three monitors, haven't yet tried rotating just one or two of them -- I suspect it'll work, although it might be weird with the mouse. Hmmm...)

---

### Post by Favux on 2012-11-20
Nice find.  Sure enough that is an Option in **man xorg.conf**'s "MONITOR SECTION".  And **man noveau** does tell you to see **man xorg.conf**.

---

### Post by DJYoshaBYD on 2012-11-21
Yeah. I knew that you could do that. But you still cant have composite and one huge desktop with xrandr until they fix it. For now Im just using an old laptop with a bad monitor or loose cable. I cant figure it out, but Im using synergy to at least be able to control that one. Its kind of nice. Has some cool benefits.

---

### Post by kinu on 2013-04-11
Hi,

Is this necrobumping? Sorry.

Anyway, I supose you have fixed your setup, but if not, this: [https://wiki.archlinux.org/index.php/NVIDIA#Mosaic_Mode](https://wiki.archlinux.org/index.php/NVIDIA#Mosaic_Mode) seems to work.

Regards

---

### Post by DJYoshaBYD on 2013-04-28
Not all cards support Mosaic mode. Mine do not. You cannot run composite over multiple cards like this. It sucks, but its still the same. haha. I just gave up on it. Got tired of wasting my time.

---


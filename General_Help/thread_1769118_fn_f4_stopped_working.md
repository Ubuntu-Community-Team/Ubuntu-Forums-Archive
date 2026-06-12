---
title: "fn f4 stopped working"
date: 2011-05-27
forum: General Help
---

### Post by Epiccabbage on 2011-05-27
Hello guys

Like everyday i'm watching movies on my laptop with my  monitor, normally i use fn+f4 to connect to the monitor. But yesterday i had an update with xubuntu and i couldn't use fn+f4 anymore. Is there any way to solve this problem? 

Thanks

---

### Post by Toz on 2011-05-27
What got updated? It would be listed in /var/log/apt/history.log. 

Also post back the contents of your ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml file.

And model/make of computer?

---

### Post by Epiccabbage on 2011-05-28
ok, first of all thanks for the reply

I'm not good at all with linux but i managed to open the history file and there was nothing on it. and i don't know how to open that config file :/
a question that i can answer is the name of my computer, fujitsu siemens amilo m3438G.

thanks

---

### Post by Toz on 2011-05-28
Ok. Try this. Start up the file manager (Thunar). 

For the first file, click on "File System" in the left pane, then double-click in the right pane, "var" then "apt" then "history.log". There must be some data in there.

For the second file, click back on your username in the left pane. Under the "View" menu, select "Show Hidden Files". Then back to the left pane, double-click ".config", then "xfce4" then "xfconf" then "xfce-prechannel-xml" then "xfce4-keyboard-shortcuts.xml"

What version of xubuntu are you using?

---

### Post by Epiccabbage on 2011-05-28
ok so my version of xubuntu is 2.6.38-8-generic

on history there is :Start-Date: 2011-05-28  09:17:30
Upgrade: firefox-globalmenu:i386 (4.0.1+build1+nobinonly-0ubuntu0.11.04.2, 4.0.1+build1+nobinonly-0ubuntu0.11.04.3), software-center:i386 (4.0.1, 4.0.2), firefox:i386 (4.0.1+build1+nobinonly-0ubuntu0.11.04.2, 4.0.1+build1+nobinonly-0ubuntu0.11.04.3), firefox-gnome-support:i386 (4.0.1+build1+nobinonly-0ubuntu0.11.04.2, 4.0.1+build1+nobinonly-0ubuntu0.11.04.3), firefox-branding:i386 (4.0.1+build1+nobinonly-0ubuntu0.11.04.2, 4.0.1+build1+nobinonly-0ubuntu0.11.04.3)
End-Date: 2011-05-28  09:18:49

and the keyboard shortcuts are <channel name="xfce4-keyboard-shortcuts" version="1.0"><property name="commands" type="empty"><property name="default" type="empty"><property name="<Alt>F2" type="empty"/><property name="<Control><Alt>Delete" type="empty"/><property name="XF86Display" type="empty"/><property name="Print" type="empty"/><property name="<Alt>Print" type="empty"/><property name="<Control>Escape" type="empty"/></property><property name="custom" type="empty"><property name="<Alt>F2" type="string" value="xfrun4"/><property name="<Control><Alt>Delete" type="string" value="xflock4"/><property name="Print" type="string" value="xfce4-screenshooter -f"/><property name="XF86Display" type="string" value="xrandr --auto"/><property name="<Alt>Print" type="string" value="xfce4-screenshooter -w"/><property name="<Control>Escape" type="string" value="xfce4-popup-menu"/><property name="override" type="bool" value="true"/></property></property><property name="xfwm4" type="empty"><property name="default" type="empty"><property name="<Alt>Insert" type="empty"/><property name="Escape" type="empty"/><property name="Left" type="empty"/><property name="Right" type="empty"/><property name="Up" type="empty"/><property name="Down" type="empty"/><property name="<Alt>Tab" type="empty"/><property name="<Alt><Shift>Tab" type="empty"/><property name="<Alt>Delete" type="empty"/><property name="<Control><Alt>Down" type="empty"/><property name="<Control><Alt>Left" type="empty"/><property name="<Shift><Alt>Page_Down" type="empty"/><property name="<Alt>F4" type="empty"/><property name="<Alt>F6" type="empty"/><property name="<Alt>F7" type="empty"/><property name="<Alt>F8" type="empty"/><property name="<Alt>F9" type="empty"/><property name="<Alt>F10" type="empty"/><property name="<Alt>F11" type="empty"/><property name="<Alt>F12" type="empty"/><property name="<Control><Shift><Alt>Left" type="empty"/><property name="<Alt><Control>End" type="empty"/><property name="<Alt><Control>Home" type="empty"/><property name="<Control><Shift><Alt>Right" type="empty"/><property name="<Control><Shift><Alt>Up" type="empty"/><property name="<Alt><Control>KP_1" type="empty"/><property name="<Alt><Control>KP_2" type="empty"/><property name="<Alt><Control>KP_3" type="empty"/><property name="<Alt><Control>KP_4" type="empty"/><property name="<Alt><Control>KP_5" type="empty"/><property name="<Alt><Control>KP_6" type="empty"/><property name="<Alt><Control>KP_7" type="empty"/><property name="<Alt><Control>KP_8" type="empty"/><property name="<Alt><Control>KP_9" type="empty"/><property name="<Alt>space" type="empty"/><property name="<Shift><Alt>Page_Up" type="empty"/><property name="<Control><Alt>Right" type="empty"/><property name="<Control><Alt>d" type="empty"/><property name="<Control><Alt>Up" type="empty"/><property name="<Control>F1" type="empty"/><property name="<Control>F2" type="empty"/><property name="<Control>F3" type="empty"/><property name="<Control>F4" type="empty"/><property name="<Control>F5" type="empty"/><property name="<Control>F6" type="empty"/><property name="<Control>F7" type="empty"/><property name="<Control>F8" type="empty"/><property name="<Control>F9" type="empty"/><property name="<Control>F10" type="empty"/><property name="<Control>F11" type="empty"/><property name="<Control>F12" type="empty"/></property><property name="custom" type="empty"><property name="<Control>F8" type="string" value="workspace_8_key"/><property name="<Control>F10" type="string" value="workspace_10_key"/><property name="<Control>F11" type="string" value="workspace_11_key"/><property name="<Control>F12" type="string" value="workspace_12_key"/><property name="<Control>F9" type="string" value="workspace_9_key"/><property name="<Alt>F10" type="string" value="maximize_window_key"/><property name="<Alt>F11" type="string" value="fullscreen_key"/><property name="<Alt>F12" type="string" value="above_key"/><property name="<Control><Alt>Up" type="string" value="up_workspace_key"/><property name="Escape" type="string" value="cancel_key"/><property name="<Alt><Shift>Tab" type="string" value="cycle_reverse_windows_key"/><property name="<Alt>space" type="string" value="popup_menu_key"/><property name="<Alt>Delete" type="string" value="del_workspace_key"/><property name="<Alt>F4" type="string" value="close_window_key"/><property name="<Shift><Alt>Page_Down" type="string" value="lower_window_key"/><property name="<Alt>F6" type="string" value="stick_window_key"/><property name="<Alt>F8" type="string" value="resize_window_key"/><property name="<Alt>F9" type="string" value="hide_window_key"/><property name="<Alt>F7" type="string" value="move_window_key"/><property name="<Control><Shift><Alt>Up" type="string" value="move_window_up_key"/><property name="<Control>F5" type="string" value="workspace_5_key"/><property name="<Control><Alt>Left" type="string" value="left_workspace_key"/><property name="<Control><Alt>Down" type="string" value="down_workspace_key"/><property name="<Alt><Control>KP_1" type="string" value="move_window_workspace_1_key"/><property name="<Control><Shift><Alt>Left" type="string" value="move_window_left_key"/><property name="<Alt><Control>KP_3" type="string" value="move_window_workspace_3_key"/><property name="<Alt><Control>KP_4" type="string" value="move_window_workspace_4_key"/><property name="<Alt><Control>KP_5" type="string" value="move_window_workspace_5_key"/><property name="<Alt><Control>KP_6" type="string" value="move_window_workspace_6_key"/><property name="<Alt><Control>KP_7" type="string" value="move_window_workspace_7_key"/><property name="<Alt><Control>KP_2" type="string" value="move_window_workspace_2_key"/><property name="Left" type="string" value="left_key"/><property name="<Alt><Control>KP_9" type="string" value="move_window_workspace_9_key"/><property name="<Alt><Control>KP_8" type="string" value="move_window_workspace_8_key"/><property name="Down" type="string" value="down_key"/><property name="<Alt><Control>Home" type="string" value="move_window_prev_workspace_key"/><property name="<Alt><Control>End" type="string" value="move_window_next_workspace_key"/><property name="<Control><Alt>Right" type="string" value="right_workspace_key"/><property name="<Control><Shift><Alt>Right" type="string" value="move_window_right_key"/><property name="Right" type="string" value="right_key"/><property name="<Alt>Tab" type="string" value="cycle_windows_key"/><property name="<Control>F1" type="string" value="workspace_1_key"/><property name="<Shift><Alt>Page_Up" type="string" value="raise_window_key"/><property name="<Control>F2" type="string" value="workspace_2_key"/><property name="<Control>F3" type="string" value="workspace_3_key"/><property name="Up" type="string" value="up_key"/><property name="<Control><Alt>d" type="string" value="show_desktop_key"/><property name="<Control>F7" type="string" value="workspace_7_key"/><property name="<Alt>Insert" type="string" value="add_workspace_key"/><property name="<Control>F6" type="string" value="workspace_6_key"/><property name="<Control>F4" type="string" value="workspace_4_key"/><property name="override" type="bool" value="true"/></property></property><property name="providers" type="array"><value type="string" value="xfwm4"/><value type="string" value="commands"/></property></channel>

thanks

---

### Post by Toz on 2011-05-28
Wow. As a note for next time, when you are posting code or file contents, click on the "Go Advanced" button and enclose them if the Code (#) blocks. It'll make it easier to read.

Two things to try:
1. Open a terminal window and type in (with the external monitor connected)```
xrandr --auto
```Does it work? If that doesn't work, type in ```
xrandr
``` and post back what it returns.

2. Is your numlock on? If it is, try turning it off and then pressing fn+f4 again.

---

### Post by Epiccabbage on 2011-05-28
hello, i can't seem to find the go advanced button so i'll do it like last time again

when i do xrandr --auto i get : 
vdbx@vdbx-Laptop1:~$ xrandr --auto
xrandr: Failed to get size of gamma for output default 

and when i do xrandr i get :

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0* 
   1360x768       51.0     52.0  
   1152x864       53.0  
   1024x768       54.0  
   960x600        55.0  
   960x540        56.0  
   840x525        57.0     58.0  
   800x600        59.0     60.0  
   800x512        61.0  
   720x450        62.0  
   680x384        63.0     64.0  
   640x512        65.0  
   640x480        66.0     67.0   
   576x432        68.0  
   512x384        69.0  
   400x300        70.0  
   320x240        71.0  


sorry that i'm not doing it in a code

---

### Post by Toz on 2011-05-28
Okay some more. With the monitor plugged in:

1. ```
xrandr -q
```

2. Contents of /etc/X11/xorg.conf

3. Contents of /var/log/Xorg.0.log

---

### Post by Epiccabbage on 2011-05-28
1) ```
vdbx@vdbx-Laptop1:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0* 
   1360x768       51.0     52.0  
   1152x864       53.0  
   1024x768       54.0  
   960x600        55.0  
   960x540        56.0  
   840x525        57.0     58.0  
   800x600        59.0     60.0  
   800x512        61.0  
   720x450        62.0  
   680x384        63.0     64.0  
   640x512        65.0  
   640x480        66.0     67.0  
   576x432        68.0  
   512x384        69.0  
   400x300        70.0  
   320x240        71.0  

```2) ```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection


```3) ```
[    32.845] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    32.845] X Protocol Version 11, Revision 0
[    32.845] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    32.845] Current Operating System: Linux vdbx-Laptop1 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    32.845] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=90d8c6e9-4581-4230-94c6-c774ac1931a7 ro quiet splash vt.handoff=7
[    32.845] Build Date: 19 April 2011  03:33:17PM
[    32.846] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    32.846] Current version of pixman: 0.20.2
[    32.846]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    32.846] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    32.846] (==) Log file: "/var/log/Xorg.0.log", Time: Sat May 28 17:48:55 2011
[    32.846] (==) Using config file: "/etc/X11/xorg.conf"
[    32.846] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    32.847] (==) No Layout section.  Using the first Screen section.
[    32.847] (**) |-->Screen "Default Screen" (0)
[    32.847] (**) |   |-->Monitor "<default monitor>"
[    32.848] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    32.848] (**) |   |-->Device "Default Device"
[    32.848] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    32.848] (==) Automatically adding devices
[    32.848] (==) Automatically enabling devices
[    32.848] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    32.848]     Entry deleted from font path.
[    32.848] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
```

---

### Post by Toz on 2011-05-28
Thanks, but I'll need to see the whole Xorg.0.log file. I believe what you sent is just the first bit. Have you made any recent changes to your video card driver?

---

### Post by Epiccabbage on 2011-05-28
```
[    32.845] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    32.845] X Protocol Version 11, Revision 0
[    32.845] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    32.845] Current Operating System: Linux vdbx-Laptop1 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    32.845] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=90d8c6e9-4581-4230-94c6-c774ac1931a7 ro quiet splash vt.handoff=7
[    32.845] Build Date: 19 April 2011  03:33:17PM
[    32.846] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    32.846] Current version of pixman: 0.20.2
[    32.846]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    32.846] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    32.846] (==) Log file: "/var/log/Xorg.0.log", Time: Sat May 28 17:48:55 2011
[    32.846] (==) Using config file: "/etc/X11/xorg.conf"
[    32.846] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    32.847] (==) No Layout section.  Using the first Screen section.
[    32.847] (**) |-->Screen "Default Screen" (0)
[    32.847] (**) |   |-->Monitor "<default monitor>"
[    32.848] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    32.848] (**) |   |-->Device "Default Device"
[    32.848] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    32.848] (==) Automatically adding devices
[    32.848] (==) Automatically enabling devices
[    32.848] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    32.848]     Entry deleted from font path.
[    32.848] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    32.848] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    32.848] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    32.848] (II) Loader magic: 0x81ffde0
[    32.848] (II) Module ABI versions:
[    32.848]     X.Org ANSI C Emulation: 0.4
[    32.848]     X.Org Video Driver: 10.0
[    32.848]     X.Org XInput driver : 12.3
[    32.848]     X.Org Server Extension : 5.0
[    32.850] (--) PCI:*(0:3:0:0) 10de:00c8:1734:107c rev 162, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
[    32.850] (II) Open ACPI successful (/var/run/acpid.socket)
[    32.850] (II) "extmod" will be loaded by default.
[    32.850] (II) "dbe" will be loaded by default.
[    32.850] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    32.850] (II) "record" will be loaded by default.
[    32.850] (II) "dri" will be loaded by default.
[    32.850] (II) "dri2" will be loaded by default.
[    32.850] (II) LoadModule: "glx"
[    32.851] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    32.914] (II) Module glx: vendor="NVIDIA Corporation"
[    32.914]     compiled for 4.0.2, module version = 1.0.0
[    32.914]     Module class: X.Org Server Extension
[    32.914] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    32.914] (II) Loading extension GLX
[    32.914] (II) LoadModule: "extmod"
[    32.926] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    32.927] (II) Module extmod: vendor="X.Org Foundation"
[    32.927]     compiled for 1.10.1, module version = 1.0.0
[    32.927]     Module class: X.Org Server Extension
[    32.927]     ABI class: X.Org Server Extension, version 5.0
[    32.927] (II) Loading extension MIT-SCREEN-SAVER
[    32.927] (II) Loading extension XFree86-VidModeExtension
[    32.927] (II) Loading extension XFree86-DGA
[    32.927] (II) Loading extension DPMS
[    32.927] (II) Loading extension XVideo
[    32.927] (II) Loading extension XVideo-MotionCompensation
[    32.927] (II) Loading extension X-Resource
[    32.927] (II) LoadModule: "dbe"
[    32.927] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    32.928] (II) Module dbe: vendor="X.Org Foundation"
[    32.928]     compiled for 1.10.1, module version = 1.0.0
[    32.928]     Module class: X.Org Server Extension
[    32.928]     ABI class: X.Org Server Extension, version 5.0
[    32.928] (II) Loading extension DOUBLE-BUFFER
[    32.928] (II) LoadModule: "record"
[    32.928] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    32.929] (II) Module record: vendor="X.Org Foundation"
[    32.929]     compiled for 1.10.1, module version = 1.13.0
[    32.929]     Module class: X.Org Server Extension
[    32.929]     ABI class: X.Org Server Extension, version 5.0
[    32.929] (II) Loading extension RECORD
[    32.929] (II) LoadModule: "dri"
[    32.929] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    32.930] (II) Module dri: vendor="X.Org Foundation"
[    32.930]     compiled for 1.10.1, module version = 1.0.0
[    32.930]     ABI class: X.Org Server Extension, version 5.0
[    32.930] (II) Loading extension XFree86-DRI
[    32.930] (II) LoadModule: "dri2"
[    32.930] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    32.931] (II) Module dri2: vendor="X.Org Foundation"
[    32.931]     compiled for 1.10.1, module version = 1.2.0
[    32.931]     ABI class: X.Org Server Extension, version 5.0
[    32.931] (II) Loading extension DRI2
[    32.931] (II) LoadModule: "nvidia"
[    32.931] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    32.932] (II) Module nvidia: vendor="NVIDIA Corporation"
[    32.932]     compiled for 4.0.2, module version = 1.0.0
[    32.932]     Module class: X.Org Video Driver
[    32.932] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[    32.932] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    32.932] (++) using VT number 7

[    32.933] (II) Loading sub module "fb"
[    32.933] (II) LoadModule: "fb"
[    32.946] (II) Loading /usr/lib/xorg/modules/libfb.so
[    32.946] (II) Module fb: vendor="X.Org Foundation"
[    32.946]     compiled for 1.10.1, module version = 1.0.0
[    32.946]     ABI class: X.Org ANSI C Emulation, version 0.4
[    32.946] (II) Loading sub module "wfb"
[    32.946] (II) LoadModule: "wfb"
[    32.946] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    32.947] (II) Module wfb: vendor="X.Org Foundation"
[    32.947]     compiled for 1.10.1, module version = 1.0.0
[    32.947]     ABI class: X.Org ANSI C Emulation, version 0.4
[    32.947] (II) Loading sub module "ramdac"
[    32.947] (II) LoadModule: "ramdac"
[    32.947] (II) Module "ramdac" already built-in
[    32.947] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    32.947] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    32.947] (II) Loading /usr/lib/xorg/modules/libfb.so
[    32.947] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    32.947] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    32.947] (==) NVIDIA(0): RGB weight 888
[    32.948] (==) NVIDIA(0): Default visual is TrueColor
[    32.948] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    32.948] (**) NVIDIA(0): Option "NoLogo" "True"
[    34.565] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    34.565] (II) NVIDIA(GPU-0): Display (QDS (DFP-0)) does not support NVIDIA 3D Vision
[    34.565] (II) NVIDIA(GPU-0):     stereo.
[    34.677] (II) NVIDIA(GPU-0): Display (hp L1702 (DFP-1)) does not support NVIDIA 3D Vision
[    34.677] (II) NVIDIA(GPU-0):     stereo.
[    34.680] (II) NVIDIA(0): NVIDIA GPU GeForce Go 6800 (NV41) at PCI:3:0:0 (GPU-0)
[    34.680] (--) NVIDIA(0): Memory: 262144 kBytes
[    34.680] (--) NVIDIA(0): VideoBIOS: 05.41.02.39.49
[    34.680] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    34.680] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    34.680] (--) NVIDIA(0): Connected display device(s) on GeForce Go 6800 at PCI:3:0:0
[    34.680] (--) NVIDIA(0):     CRT-0
[    34.680] (--) NVIDIA(0):     QDS (DFP-0)
[    34.680] (--) NVIDIA(0):     hp L1702 (DFP-1)
[    34.680] (--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
[    34.680] (--) NVIDIA(0): QDS (DFP-0): 310.0 MHz maximum pixel clock
[    34.680] (--) NVIDIA(0): QDS (DFP-0): Internal Dual Link LVDS
[    34.680] (--) NVIDIA(0): hp L1702 (DFP-1): 155.0 MHz maximum pixel clock
[    34.680] (--) NVIDIA(0): hp L1702 (DFP-1): Internal Single Link TMDS
[    34.681] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    34.681] (==) NVIDIA(0): 
[    34.681] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    34.681] (==) NVIDIA(0):     will be used as the requested mode.
[    34.681] (==) NVIDIA(0): 
[    34.681] (II) NVIDIA(0): Validated modes:
[    34.681] (II) NVIDIA(0):     "nvidia-auto-select"
[    34.682] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[    34.683] (--) NVIDIA(0): DPI set to (98, 99); computed from "UseEdidDpi" X config
[    34.683] (--) NVIDIA(0):     option
[    34.683] (--) Depth 24 pixmap format is 32 bpp
[    34.705] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    36.099] (II) Loading extension NV-GLX
[    36.156] (==) NVIDIA(0): Disabling shared memory pixmaps
[    36.156] (==) NVIDIA(0): Backing store disabled
[    36.156] (==) NVIDIA(0): Silken mouse enabled
[    36.157] (==) NVIDIA(0): DPMS enabled
[    36.157] (II) Loading extension NV-CONTROL
[    36.158] (II) Loading extension XINERAMA
[    36.158] (II) Loading sub module "dri2"
[    36.158] (II) LoadModule: "dri2"
[    36.158] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    36.159] (II) Module dri2: vendor="X.Org Foundation"
[    36.159]     compiled for 1.10.1, module version = 1.2.0
[    36.159]     ABI class: X.Org Server Extension, version 5.0
[    36.159] (II) NVIDIA(0): [DRI2] Setup complete
[    36.159] (==) RandR enabled
[    36.159] (II) Initializing built-in extension Generic Event Extension
[    36.159] (II) Initializing built-in extension SHAPE
[    36.159] (II) Initializing built-in extension MIT-SHM
[    36.159] (II) Initializing built-in extension XInputExtension
[    36.159] (II) Initializing built-in extension XTEST
[    36.159] (II) Initializing built-in extension BIG-REQUESTS
[    36.159] (II) Initializing built-in extension SYNC
[    36.159] (II) Initializing built-in extension XKEYBOARD
[    36.159] (II) Initializing built-in extension XC-MISC
[    36.159] (II) Initializing built-in extension SECURITY
[    36.159] (II) Initializing built-in extension XINERAMA
[    36.159] (II) Initializing built-in extension XFIXES
[    36.159] (II) Initializing built-in extension RENDER
[    36.159] (II) Initializing built-in extension RANDR
[    36.159] (II) Initializing built-in extension COMPOSITE
[    36.159] (II) Initializing built-in extension DAMAGE
[    36.159] (II) Initializing built-in extension GESTURE
[    36.159] (II) Initializing extension GLX
[    36.278] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    36.307] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    36.307] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    36.307] (II) LoadModule: "evdev"
[    36.308] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.309] (II) Module evdev: vendor="X.Org Foundation"
[    36.309]     compiled for 1.10.0.902, module version = 2.6.0
[    36.309]     Module class: X.Org XInput Driver
[    36.309]     ABI class: X.Org XInput driver, version 12.3
[    36.309] (II) Using input driver 'evdev' for 'Power Button'
[    36.309] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.309] (**) Power Button: always reports core events
[    36.309] (**) Power Button: Device: "/dev/input/event3"
[    36.309] (--) Power Button: Found keys
[    36.309] (II) Power Button: Configuring as keyboard
[    36.309] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    36.309] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    36.309] (**) Option "xkb_rules" "evdev"
[    36.309] (**) Option "xkb_model" "pc105"
[    36.309] (**) Option "xkb_layout" "be"
[    36.319] (II) XKB: reuse xkmfile /var/lib/xkb/server-BCDBD3DBC93B3E588F97965C4D87FE91FAEC6B41.xkm
[    36.338] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    36.338] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    36.338] (II) Using input driver 'evdev' for 'Video Bus'
[    36.338] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.338] (**) Video Bus: always reports core events
[    36.338] (**) Video Bus: Device: "/dev/input/event8"
[    36.338] (--) Video Bus: Found keys
[    36.338] (II) Video Bus: Configuring as keyboard
[    36.338] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19/LNXVIDEO:00/input/input8/event8"
[    36.338] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    36.338] (**) Option "xkb_rules" "evdev"
[    36.338] (**) Option "xkb_model" "pc105"
[    36.339] (**) Option "xkb_layout" "be"
[    36.340] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    36.340] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    36.340] (II) Using input driver 'evdev' for 'Power Button'
[    36.340] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.341] (**) Power Button: always reports core events
[    36.341] (**) Power Button: Device: "/dev/input/event2"
[    36.341] (--) Power Button: Found keys
[    36.341] (II) Power Button: Configuring as keyboard
[    36.341] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2"
[    36.341] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    36.341] (**) Option "xkb_rules" "evdev"
[    36.341] (**) Option "xkb_model" "pc105"
[    36.341] (**) Option "xkb_layout" "be"
[    36.342] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    36.342] (II) No input driver/identifier specified (ignoring)
[    36.343] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    36.343] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    36.343] (II) Using input driver 'evdev' for 'Sleep Button'
[    36.343] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.343] (**) Sleep Button: always reports core events
[    36.343] (**) Sleep Button: Device: "/dev/input/event1"
[    36.344] (--) Sleep Button: Found keys
[    36.344] (II) Sleep Button: Configuring as keyboard
[    36.344] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    36.344] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    36.344] (**) Option "xkb_rules" "evdev"
[    36.344] (**) Option "xkb_model" "pc105"
[    36.344] (**) Option "xkb_layout" "be"
[    36.351] (II) config/udev: Adding input device CHICONY HP Basic USB Keyboard (/dev/input/event5)
[    36.351] (**) CHICONY HP Basic USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    36.352] (II) Using input driver 'evdev' for 'CHICONY HP Basic USB Keyboard'
[    36.352] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.352] (**) CHICONY HP Basic USB Keyboard: always reports core events
[    36.352] (**) CHICONY HP Basic USB Keyboard: Device: "/dev/input/event5"
[    36.352] (--) CHICONY HP Basic USB Keyboard: Found keys
[    36.352] (II) CHICONY HP Basic USB Keyboard: Configuring as keyboard
[    36.352] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5/event5"
[    36.352] (II) XINPUT: Adding extended input device "CHICONY HP Basic USB Keyboard" (type: KEYBOARD)
[    36.352] (**) Option "xkb_rules" "evdev"
[    36.352] (**) Option "xkb_model" "pc105"
[    36.352] (**) Option "xkb_layout" "be"
[    36.355] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
[    36.355] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    36.355] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    36.355] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.355] (**) Logitech USB Receiver: always reports core events
[    36.356] (**) Logitech USB Receiver: Device: "/dev/input/event6"
[    36.356] (--) Logitech USB Receiver: Found 20 mouse buttons
[    36.356] (--) Logitech USB Receiver: Found scroll wheel(s)
[    36.356] (--) Logitech USB Receiver: Found relative axes
[    36.356] (--) Logitech USB Receiver: Found x and y relative axes
[    36.356] (II) Logitech USB Receiver: Configuring as mouse
[    36.356] (II) Logitech USB Receiver: Adding scrollwheel support
[    36.356] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    36.356] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    36.356] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input6/event6"
[    36.356] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
[    36.356] (II) Logitech USB Receiver: initialized for relative axes.
[    36.356] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    36.356] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    36.357] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    36.357] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    36.357] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    36.357] (II) No input driver/identifier specified (ignoring)
[    36.359] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event7)
[    36.359] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    36.359] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    36.359] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.359] (**) Logitech USB Receiver: always reports core events
[    36.359] (**) Logitech USB Receiver: Device: "/dev/input/event7"
[    36.359] (--) Logitech USB Receiver: Found 1 mouse buttons
[    36.359] (--) Logitech USB Receiver: Found scroll wheel(s)
[    36.359] (--) Logitech USB Receiver: Found relative axes
[    36.359] (--) Logitech USB Receiver: Found absolute axes
[    36.359] (II) evdev-grail: failed to open grail, no gesture support
[    36.359] (--) Logitech USB Receiver: Found keys
[    36.359] (II) Logitech USB Receiver: Configuring as mouse
[    36.359] (II) Logitech USB Receiver: Configuring as keyboard
[    36.359] (II) Logitech USB Receiver: Adding scrollwheel support
[    36.359] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    36.360] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    36.360] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/input/input7/event7"
[    36.360] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    36.360] (**) Option "xkb_rules" "evdev"
[    36.360] (**) Option "xkb_model" "pc105"
[    36.360] (**) Option "xkb_layout" "be"
[    36.360] (EE) Logitech USB Receiver: failed to initialize for relative axes.
[    36.361] (II) Logitech USB Receiver: initialized for absolute axes.
[    36.361] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    36.361] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    36.361] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    36.361] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    36.375] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    36.375] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    36.375] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    36.375] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.375] (**) AT Translated Set 2 keyboard: always reports core events
[    36.375] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    36.376] (--) AT Translated Set 2 keyboard: Found keys
[    36.376] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    36.376] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    36.376] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    36.376] (**) Option "xkb_rules" "evdev"
[    36.376] (**) Option "xkb_model" "pc105"
[    36.376] (**) Option "xkb_layout" "be"
[    36.377] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[    36.378] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    36.378] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    36.378] (II) LoadModule: "synaptics"
[    36.378] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    36.378] (II) Module synaptics: vendor="X.Org Foundation"
[    36.379]     compiled for 1.10.0.902, module version = 1.3.99
[    36.379]     Module class: X.Org XInput Driver
[    36.379]     ABI class: X.Org XInput driver, version 12.3
[    36.379] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    36.379] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    36.379] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    36.379] (**) Option "Device" "/dev/input/event9"
[    36.379] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    36.379] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    36.379] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    36.379] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    36.379] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    36.379] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    36.379] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    36.379] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input9/event9"
[    36.379] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    36.379] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    36.379] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    36.379] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    36.380] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    36.380] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    36.380] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    36.380] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    36.380] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    36.380] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    36.381] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    36.381] (II) No input driver/identifier specified (ignoring)

```

and no i didn't change anything

---

### Post by Toz on 2011-05-29
Well that's interesting. Xorg is picking up the external monitor but xrandr isn't. According to your keyboard shortcuts file, FN+F4 is mapped to run xrandr to make the change. So if this worked before and isn't working now, something has changed. According to your apt history file, only firefox was updated and that wouldn't make a difference. Something else must have been updated prior to that to have made the difference. You could look further back in the file, though I don't know what you'd be able to do about it realistically.

I also researched the issue and found many posts that stated that xrandr doesn't work well with nvidia cards (which is interesting that it worked fine for you). I came across this post: [http://maketecheasier.com/change-linux-displays-on-the-fly-with-disper/2010/12/22/](http://maketecheasier.com/change-linux-displays-on-the-fly-with-disper/2010/12/22/) which talks about using a package called disper to assist with changing displays on nvidia cards. Perhaps you can have a look and see if it helps. If you do choose to try, go to disper's homepage ([http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)) and use the PPA listed there - it will be easier than compiling from source as instructed in the installation section of the instructions.

Unfortunately, I don't have an nvidia card and don't think I can help you any further. Perhaps someone else with experience with display changing on nvidia cards can offer some advice. Good luck.

---

### Post by Epiccabbage on 2011-05-29
ok i got disper installed and i found a way to connect with my monitor using disper -S
ok, it's working on my monitor but the resolution didn't change, you know what i mean? i only see 50% of what i saw on my laptop

---

### Post by Toz on 2011-05-29
Try:```
disper -S -r <resolution>
```where <resolution> is the resolution you want. Something like:```
disper -S -r 1280x720
```

---

### Post by Epiccabbage on 2011-05-29
mate, you're my hero :D

anyways i did disper -S -r 960x600 but now, can i make a keybind to this like when i press a button like fn f4 it does the command?

---

### Post by Toz on 2011-05-29
Absolutely. Just go to the keyboard shortcuts progam (SettingsManager->Keyboard->Application Shortcuts tab), remove the existing fn+f4 shortcut then click Add and follow the prompts to create the new shortcut. Post back to let us know if it works.

---

### Post by Epiccabbage on 2011-05-29
ok i've tried to add a command to a keybind so i did as command :disper -S -r 1152x864
and as keybind PgUp. now when i press it nothing happens, but when i do the command in the terminal it works, i'm probably doing something wrong with the command?

---

### Post by Toz on 2011-05-29
Can you post back a screenshot of the mapping? Why not just map it back to fn+f4? Or try with the numlock off (or on) and see if that makes a difference.

---

### Post by Epiccabbage on 2011-05-30
oh, now pageup works probably needed to reboot. it's working now

thanks for your help man :)

---

### Post by Toz on 2011-05-30
Great - glad to hear. If you don't mind, can you flag this thread as solved via the Thread Tools menu at the top of the page?
Thanks

---


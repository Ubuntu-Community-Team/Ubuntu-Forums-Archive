---
title: "Compiz System Freeze"
date: 2009-09-30
forum: General Help
---

### Post by jewishj on 2009-09-30
Recently I started having some real issues with compiz.  Whenever I have compiz running, everything is stable until I either:

[LIST=1]
[*]Switch to emerald as the window decorator and Maximize a window, then move the mouse over the minimize/restore/close buttons
[*]Open a Windows XP (32 bit) guest in Virtual Box 3 - the bug will occur when at the flicker which occurs between the login screen and the Windows loading splash
[/LIST]

Those are the only ways I've been able to get the bug to occur.  When it does occur, the system will slow down and the mouse will go in and out of responsiveness.  The screen will pixelate in certain areas around the VM window or emerald-decorated window and wherever I move the mouse afterwards, and eventually the system will freeze.  Sometimes the monitors will black out, and sometimes not, but in any case the computer is completely unresponsive (including Alt+F2 or Alt+F12) and hitting the reboot button on the case is the only solution - however, the computer is not rebooting automatically or anything.

Here is relevant information about my setup.  I am using a GeForce 8400 GS connected to the Matrox TripleHead2Go Digital which is powering a triple monitor setup (not using Xinerama, the computer essentially sees one huge 5040x1050 monitor).  I'm running Jaunty 64-bit and using the Nvidia 1.80 drivers (through the built-in driver manager).

The weird thing is that this all worked perfectly before with the same exact setup (save the hard drive).  I previously had a hard drive failure which killed a RAID array which is why I had to re-install, but everything else runs fine so that shouldn't be a cause of the problem.

Following are my compiz settings and xorg.conf, please let me know if there is any other information I can provide to help diagnose. Thank you for any insight into this issue.

Compiz Settings
-------------------------------
General Options I changed from default
[LIST]
[*]General
[LIST]
[*]Audible Bell: true
[*]Ignore Hints When Maximized: true
[*]Hide Skip Taskbar Windows: true
[*]Edge Trigger Delay: 0
[*]Ping Delay: 5000
[*]Unredirect Fullscreen Windows: true
[*]Default icon: icon
[*]Force independent output painting: false
[*]Texture Compression: true
[/LIST]
[*]Display Settings
[LIST]
[*]Texture Filter: good
[*]Lighting: true
[*]Detect Refresh Rate: true
[*]Refresh Rate: 50
[*]Detect Outputs: true (also tried on false didn't change anything)
[*]Outputs: 
1680x1050+0+0
1680x1050+1680+0
1680x1050+3360+0
[*]Sync To VBlank: true
[/LIST]
[/LIST]

Enabled Plugins
[LIST]
[*]General
[LIST]
[*]Gnome Compatibility
[/LIST]
[*]Accessibility
[LIST]
[*]ADD Helper
[*]Opacify
[/LIST]
[*]Desktop
[LIST]
[*]Desktop Cube
[*]Expo
[*]Fade to Destop
[*]Rotate Cube
[*]Viewport Switcher
[/LIST]
[*]Effects
[LIST]
[*]3D Windows
[*]Animations
[*]Bicubic filter
[*]Blur Windows
[*]Cube Reflection and Deformation
[*]Fading Windows
[*]Motion Blur
[*]Window Decoration
[*]Wobbly Windows
[/LIST]
[*]Extras
[LIST]
[*]Window Previews
[/LIST]
[*]Image Loading
[LIST]
[*]JPEG
[*]Png
[*]Svg
[*]Text
[/LIST]
[*]Utility
[LIST]
[*]Crash handler
[*]Dbus
[*]Mouse position polling
[*]Regex Matching
[*]Resize Info
[*]Scale Addons
[*]Session Management
[*]Video Playback
[*]Workarounds (Firefox Menu Fix, OpenOffice.org Menu Fix, Java Window Fix, AIGLX Fragment Parameter Fix)
[/LIST]
[*]Window Management
[LIST]
[*]Application Switcher
[*]Extra WM Actions
[*]Move Window
[*]Resize Window
[*]Ring Switcher
[*]Scale
[/LIST]
[/LIST]


Xorg.conf
---------------------
```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen 0       "Screen0" 0 0
EndSection

Section "ServerFlags"
    Option         "RandR"        "True"
EndSection

Section "Extensions"
    Option         "RENDER"       "True"
    Option         "DAMAGE"       "True"
    Option         "Composite"    "True"
EndSection

Section "Module"
    Load           "dbe"
    Load           "glx"
    SubSection     "extmod"
        Option     "omit xfree86-dga"
    EndSubSection
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    Vendorname	   "Unknown"
    Modelname	   "Acer AL2216W"
    ModeLine	   "3840x1024" 254.31 3840 3856 3872 3976 1024 1025 1032 1066 +HSync +VSync
    ModeLine       "4080x768"  200.38 4080 4104 4136 4200  768  771  779  795 +HSync +VSync
    ModeLine       "4320x900"  320.10 4320 4400 4688 5712  900  903  915  934 +HSync +VSync
    ModeLine	   "5040x1050" 326.66 5040 5104 5168 5376 1050 1053 1057 1066 +HSync +VSync
    HorizSync      31-84
    VertRefresh    56-77
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseEDID" "False"
    Option         "ExactModeTimingsDVI"      "True"
    Option         "PixmapCacheSize"          "5760000"
    Option         "Coolbits"                 "1"
    Option         "NoLogo"                   "True"
    Option         "CursorShadow"             "True"
    Option         "RenderAccel"              "True"
    Option         "AddARGBGLXVisuals"        "True"
    Option         "ConnectToAcpid"           "False"
    Option         "TwinviewXineramaInfo"     "True"
    Option         "TwinViewXineramaInfoOverride" "1680x1050+1680+0, 1680x1050+0+0, 1680x1050+3360+0"
    SubSection     "Display"
        Viewport    0 0
        Depth       24
        Modes      "5040x1050"
    EndSubSection
EndSection

```

---

### Post by jewishj on 2009-10-01
I noticed something in my syslog file after a crash:

```

Oct  1 03:10:49 main kernel: [  600.787161] NVRM: Xid (0001:00): 13, 0001 00000000 0000502d 000002ac 00000003 00000100
Oct  1 03:10:49 main kernel: [  600.811321] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00000f04 3f7ae148 00000040
Oct  1 03:10:50 main gdm[4158]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Oct  1 03:10:51 main acpid: client 4166[0:0] has disconnected 
Oct  1 03:10:51 main acpid: client connected from 5350[0:0] 
Oct  1 03:10:53 main gdmgreeter[5416]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed 
Oct  1 03:10:53 main gdmgreeter[5416]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed 
Oct  1 03:10:53 main gdmgreeter[5416]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 

```

Kernel is 2.6.28-15-generic
Nvidia is 180.44 drivers

---


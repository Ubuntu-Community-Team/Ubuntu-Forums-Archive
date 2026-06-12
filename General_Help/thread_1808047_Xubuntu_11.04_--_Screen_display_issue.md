---
title: "Xubuntu 11.04 -- Screen display issue"
date: 2011-07-19
forum: General Help
---

### Post by hau5 on 2011-07-19
Hi,

I have recently installed Xubuntu 11.04 on an old pc and am using a flatscreen monitor.

The install went fine, but when I turn it on, the entire display is wrong.  It seems to be higher resolution than the monitor thinks it is.  

Vertically, the monitor screen is too small. I don't see the dock until I am at the very bottom of the screen and it only shows the upper half of the dock.  My mouse will stop at the monitor's edge so it is weird that the dock seems to be "below" the screen.  

Horizontally, the screen wraps around with a *small* sliver (about 5 mm) on the right.  The blue Xubuntu icon with the mouse on it has the right 3/4 at the left egde of the screen and the left 1/4 of the icon is on the right side of the monitor on the "wrap-around" section.  

When I go to Settings Manager/Display, the only resolutions available are 1024x768, 800x600, 848x480, and 640x480.  1024x768 is the current resolution and I believe this is what the native monitor resolution is because the screen is so close to the graphical display, but I cannot set a higher resolution. 

I have all the updates installed and the only additional driver was an Nvidia 3D Accelerator, but it didn't do anything to fix the problem.

I have tried to edit the xorg.conf file to manually set the resolution; however, it is not in /etc/X11/ and from what I've read it is because the file has been deprecated in Ubuntu 11.04.  I tried making a new xorg.conf file but that just crashed the computer and I had to reformat the hard drive and reinstall.

The output of lspci | grep "VGA":
02:00.0 VGA compatible controller:  nVidia Corporation NV18 [ GeForce4 MX - nForce GPU] (rev a3)

Based on this, I did sudo apt-get nvidia-settings but sudo nvidia-settings gives me a message saying "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file, and restart the X server." But again, the xorg.conf file got split up so I'm lost at this point...

Help?

---

### Post by Toz on 2011-07-20
Have a look at this page: [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution").

What does:
```
xrandr
```return?

---

### Post by hau5 on 2011-07-20
xrandr:

Screen 0:  minimum 320x200, current 1024x768, maximum 4096x4096
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm

1024x768    60.0*
800x600    60.3    56.2
848x480    60.0
640x480    59.9

I tried to make a new resolution 1280x960 (with cvt then using xrandr to set the mode) and it will go to the higher resolution, but it still has the same problems with display.

It seems as if the screen needs to be shifted over vertically a few (<50) pixels and the screen needs to be shortened by about 200 pixels. (those measurements are approximate...)

When making a new mode with cvt and adding it to xrandr, it seems as if I can change the height/width which would fix the problem but when I mess with those values, I get

X Error of failed requiest:  BadName (named color or font does not exist)
    Major opcode of failed request:  150 (RANDR)
    Minor opcode of failed request:  16 (RRCreateMode)
    Serial number of failed request:  23
    Current serial number in output stream:  23

I tried to google those error codes and how manually change height and width while sending the cvt profile to xrandr but couldn't find anything....

Thanks for your help!

---

### Post by Toz on 2011-07-20
How about the settings on the monitor itself. Can they be adjusted through the controls directly on the monitor to resize/re-position the image?

If not, what does **/var/log/Xorg.0.log** say?

---

### Post by hau5 on 2011-07-20
I can adjust the settings on the monitor itself but it just moves the entire image of the desktop.

If I move the screen up vertically, I get a black bar at the bottom and still only half of the dock shows up.

When I adjust the Clock value on the monitor, the screen image gets wider which would seem to fix part of the problem as the strip of the desktop from the left side moves off the right side of the screen, but the left side of the monitor still starts about 20 or so pixels over (the xubuntu mouse icon only shows the right 3/4, the rest 1/4 of the icon is on the strip on the right side of the image)

/var/log/Xorg.0.log

[    14.266] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    14.266] X Protocol Version 11, Revision 0
[    14.266] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    14.266] Current Operating System: Linux artemis 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686
[    14.266] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=ddd4a2c3-a1f9-413d-9a9a-270676344fce ro quiet splash vt.handoff=7
[    14.266] Build Date: 21 May 2011  11:38:35AM
[    14.266] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    14.266] Current version of pixman: 0.20.2
[    14.266]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    14.266] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.266] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 20 20:33:17 2011
[    14.277] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.277] (==) No Layout section.  Using the first Screen section.
[    14.277] (==) No screen section available. Using defaults.
[    14.277] (**) |-->Screen "Default Screen Section" (0)
[    14.277] (**) |   |-->Monitor "<default monitor>"
[    14.278] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    14.278] (==) Automatically adding devices
[    14.278] (==) Automatically enabling devices
[    14.278] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.278]     Entry deleted from font path.
[    14.278] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.278]     Entry deleted from font path.
[    14.278] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.278]     Entry deleted from font path.
[    14.278] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.278]     Entry deleted from font path.
[    14.278] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.278]     Entry deleted from font path.
[    14.278] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    14.278] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.278] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.278] (II) Loader magic: 0x81ffde0
[    14.278] (II) Module ABI versions:
[    14.278]     X.Org ANSI C Emulation: 0.4
[    14.278]     X.Org Video Driver: 10.0
[    14.278]     X.Org XInput driver : 12.3
[    14.278]     X.Org Server Extension : 5.0
[    14.279] (--) PCI:*(0:2:0:0) 10de:01f0:1509:904d rev 163, Mem @ 0xea000000/16777216, 0xe0000000/67108864, 0xe4000000/524288, BIOS @ 0x????????/131072
[    14.279] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    14.279] (II) LoadModule: "extmod"
[    14.291] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.291] (II) Module extmod: vendor="X.Org Foundation"
[    14.291]     compiled for 1.10.1, module version = 1.0.0
[    14.291]     Module class: X.Org Server Extension
[    14.291]     ABI class: X.Org Server Extension, version 5.0
[    14.291] (II) Loading extension MIT-SCREEN-SAVER
[    14.291] (II) Loading extension XFree86-VidModeExtension
[    14.291] (II) Loading extension XFree86-DGA
[    14.291] (II) Loading extension DPMS
[    14.291] (II) Loading extension XVideo
[    14.291] (II) Loading extension XVideo-MotionCompensation
[    14.291] (II) Loading extension X-Resource
[    14.291] (II) LoadModule: "dbe"
[    14.292] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.292] (II) Module dbe: vendor="X.Org Foundation"
[    14.292]     compiled for 1.10.1, module version = 1.0.0
[    14.292]     Module class: X.Org Server Extension
[    14.292]     ABI class: X.Org Server Extension, version 5.0
[    14.292] (II) Loading extension DOUBLE-BUFFER
[    14.292] (II) LoadModule: "glx"
[    14.292] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.292] (II) Module glx: vendor="X.Org Foundation"
[    14.292]     compiled for 1.10.1, module version = 1.0.0
[    14.292]     ABI class: X.Org Server Extension, version 5.0
[    14.292] (==) AIGLX enabled
[    14.292] (II) Loading extension GLX
[    14.292] (II) LoadModule: "record"
[    14.292] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.293] (II) Module record: vendor="X.Org Foundation"
[    14.293]     compiled for 1.10.1, module version = 1.13.0
[    14.293]     Module class: X.Org Server Extension
[    14.293]     ABI class: X.Org Server Extension, version 5.0
[    14.293] (II) Loading extension RECORD
[    14.293] (II) LoadModule: "dri"
[    14.293] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.293] (II) Module dri: vendor="X.Org Foundation"
[    14.293]     compiled for 1.10.1, module version = 1.0.0
[    14.293]     ABI class: X.Org Server Extension, version 5.0
[    14.293] (II) Loading extension XFree86-DRI
[    14.293] (II) LoadModule: "dri2"
[    14.293] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.293] (II) Module dri2: vendor="X.Org Foundation"
[    14.293]     compiled for 1.10.1, module version = 1.2.0
[    14.293]     ABI class: X.Org Server Extension, version 5.0
[    14.293] (II) Loading extension DRI2
[    14.293] (==) Matched nvidia as autoconfigured driver 0
[    14.293] (==) Matched nouveau as autoconfigured driver 1
[    14.293] (==) Matched nv as autoconfigured driver 2
[    14.293] (==) Matched vesa as autoconfigured driver 3
[    14.293] (==) Matched fbdev as autoconfigured driver 4
[    14.293] (==) Assigned the driver to the xf86ConfigLayout
[    14.293] (II) LoadModule: "nvidia"
[    14.302] (WW) Warning, couldn't open module nvidia
[    14.302] (II) UnloadModule: "nvidia"
[    14.302] (II) Unloading nvidia
[    14.302] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    14.302] (II) LoadModule: "nouveau"
[    14.302] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    14.303] (II) Module nouveau: vendor="X.Org Foundation"
[    14.303]     compiled for 1.10.0, module version = 0.0.16
[    14.303]     Module class: X.Org Video Driver
[    14.303]     ABI class: X.Org Video Driver, version 10.0
[    14.303] (II) LoadModule: "nv"
[    14.303] (WW) Warning, couldn't open module nv
[    14.303] (II) UnloadModule: "nv"
[    14.303] (II) Unloading nv
[    14.303] (EE) Failed to load module "nv" (module does not exist, 0)
[    14.303] (II) LoadModule: "vesa"
[    14.304] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.304] (II) Module vesa: vendor="X.Org Foundation"
[    14.304]     compiled for 1.10.0, module version = 2.3.0
[    14.304]     Module class: X.Org Video Driver
[    14.304]     ABI class: X.Org Video Driver, version 10.0
[    14.304] (II) LoadModule: "fbdev"
[    14.304] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.304] (II) Module fbdev: vendor="X.Org Foundation"
[    14.304]     compiled for 1.10.0, module version = 0.4.2
[    14.304]     ABI class: X.Org Video Driver, version 10.0
[    14.304] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[    14.304] (II) NOUVEAU driver for NVIDIA chipset families :
[    14.304]     RIVA TNT    (NV04)
[    14.304]     RIVA TNT2   (NV05)
[    14.304]     GeForce 256 (NV10)
[    14.304]     GeForce 2   (NV11, NV15)
[    14.305]     GeForce 4MX (NV17, NV18)
[    14.305]     GeForce 3   (NV20)
[    14.305]     GeForce 4Ti (NV25, NV28)
[    14.305]     GeForce FX  (NV3x)
[    14.305]     GeForce 6   (NV4x)
[    14.305]     GeForce 7   (G7x)
[    14.305]     GeForce 8   (G8x)
[    14.305] (II) VESA: driver for VESA chipsets: vesa
[    14.305] (II) FBDEV: driver for framebuffer: fbdev
[    14.305] (++) using VT number 7

[    14.305] drmOpenDevice: node name is /dev/dri/card0
[    14.305] drmOpenDevice: open result is 7, (OK)
[    14.305] drmOpenByBusid: Searching for BusID pci:0000:02:00.0
[    14.305] drmOpenDevice: node name is /dev/dri/card0
[    14.305] drmOpenDevice: open result is 7, (OK)
[    14.305] drmOpenByBusid: drmOpenMinor returns 7
[    14.305] drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
[    14.305] (II) [drm] nouveau interface version: 0.0.16
[    14.305] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    14.305] (WW) Falling back to old probe method for vesa
[    14.305] (WW) Falling back to old probe method for fbdev
[    14.306] (II) Loading sub module "fbdevhw"
[    14.306] (II) LoadModule: "fbdevhw"
[    14.306] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.306] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.306]     compiled for 1.10.1, module version = 0.0.2
[    14.306]     ABI class: X.Org Video Driver, version 10.0
[    14.306] (II) Loading sub module "dri"
[    14.306] (II) LoadModule: "dri"
[    14.306] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.306] (II) Module dri: vendor="X.Org Foundation"
[    14.306]     compiled for 1.10.1, module version = 1.0.0
[    14.306]     ABI class: X.Org Server Extension, version 5.0
[    14.306] (II) NOUVEAU(0): Loaded DRI module
[    14.306] drmOpenDevice: node name is /dev/dri/card0
[    14.306] drmOpenDevice: open result is 8, (OK)
[    14.306] drmOpenDevice: node name is /dev/dri/card0
[    14.306] drmOpenDevice: open result is 8, (OK)
[    14.307] drmOpenByBusid: Searching for BusID pci:0000:02:00.0
[    14.307] drmOpenDevice: node name is /dev/dri/card0
[    14.307] drmOpenDevice: open result is 8, (OK)
[    14.307] drmOpenByBusid: drmOpenMinor returns 8
[    14.307] drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
[    14.307] (II) [drm] DRM interface version 1.4
[    14.307] (II) [drm] DRM open master succeeded.
[    14.307] (--) NOUVEAU(0): Chipset: "NVIDIA NV1f"
[    14.307] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    14.307] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[    14.307] (==) NOUVEAU(0): RGB weight 888
[    14.307] (==) NOUVEAU(0): Default visual is TrueColor
[    14.307] (==) NOUVEAU(0): Using HW cursor
[    14.307] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[    14.344] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[    14.376] (II) NOUVEAU(0): EDID for output VGA-1
[    14.376] (II) NOUVEAU(0): Printing probed modes for output VGA-1
[    14.376] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.376] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.376] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    14.376] (II) NOUVEAU(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    14.376] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    14.376] (II) NOUVEAU(0): Output VGA-1 connected
[    14.376] (II) NOUVEAU(0): Using fuzzy aspect match for initial modes
[    14.376] (II) NOUVEAU(0): Output VGA-1 using initial mode 1024x768
[    14.376] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    14.376] (--) NOUVEAU(0): Virtual size is 1024x768 (pitch 0)
[    14.376] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[    14.376] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.376] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[    14.376] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.376] (**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[    14.376] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    14.376] (**) NOUVEAU(0):  Driver mode "848x480": 33.8 MHz (scaled from 0.0 MHz), 31.0 kHz, 60.0 Hz
[    14.376] (II) NOUVEAU(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    14.376] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
[    14.376] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    14.376] (==) NOUVEAU(0): DPI set to (96, 96)
[    14.376] (II) Loading sub module "fb"
[    14.376] (II) LoadModule: "fb"
[    14.377] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.377] (II) Module fb: vendor="X.Org Foundation"
[    14.377]     compiled for 1.10.1, module version = 1.0.0
[    14.377]     ABI class: X.Org ANSI C Emulation, version 0.4
[    14.377] (II) Loading sub module "exa"
[    14.377] (II) LoadModule: "exa"
[    14.378] (II) Loading /usr/lib/xorg/modules/libexa.so
[    14.378] (II) Module exa: vendor="X.Org Foundation"
[    14.378]     compiled for 1.10.1, module version = 2.5.0
[    14.378]     ABI class: X.Org Video Driver, version 10.0
[    14.378] (II) Loading sub module "shadowfb"
[    14.378] (II) LoadModule: "shadowfb"
[    14.378] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    14.378] (II) Module shadowfb: vendor="X.Org Foundation"
[    14.378]     compiled for 1.10.1, module version = 1.0.0
[    14.378]     ABI class: X.Org ANSI C Emulation, version 0.4
[    14.378] (II) UnloadModule: "vesa"
[    14.378] (II) Unloading vesa
[    14.378] (II) UnloadModule: "fbdev"
[    14.378] (II) Unloading fbdev
[    14.378] (II) UnloadModule: "fbdevhw"
[    14.378] (II) Unloading fbdevhw
[    14.378] (--) Depth 24 pixmap format is 32 bpp
[    14.382] (II) NOUVEAU(0): Opened GPU channel 1
[    14.382] (II) NOUVEAU(0): [DRI2] Setup complete
[    14.382] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau_vieux
[    14.382] (II) NOUVEAU(0): GART: 32MiB available
[    14.407] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[    14.407] (II) EXA(0): Driver allocated offscreen pixmaps
[    14.407] (II) EXA(0): Driver registered support for the following operations:
[    14.407] (II)         Solid
[    14.407] (II)         Copy
[    14.407] (II)         Composite (RENDER acceleration)
[    14.407] (II)         UploadToScreen
[    14.407] (II)         DownloadFromScreen
[    14.407] (==) NOUVEAU(0): Backing store disabled
[    14.407] (==) NOUVEAU(0): Silken mouse enabled
[    14.407] (==) NOUVEAU(0): DPMS enabled
[    14.407] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    14.408] (--) RandR disabled
[    14.408] (II) Initializing built-in extension Generic Event Extension
[    14.408] (II) Initializing built-in extension SHAPE
[    14.408] (II) Initializing built-in extension MIT-SHM
[    14.408] (II) Initializing built-in extension XInputExtension
[    14.408] (II) Initializing built-in extension XTEST
[    14.408] (II) Initializing built-in extension BIG-REQUESTS
[    14.408] (II) Initializing built-in extension SYNC
[    14.408] (II) Initializing built-in extension XKEYBOARD
[    14.408] (II) Initializing built-in extension XC-MISC
[    14.408] (II) Initializing built-in extension SECURITY
[    14.408] (II) Initializing built-in extension XINERAMA
[    14.408] (II) Initializing built-in extension XFIXES
[    14.408] (II) Initializing built-in extension RENDER
[    14.408] (II) Initializing built-in extension RANDR
[    14.408] (II) Initializing built-in extension COMPOSITE
[    14.408] (II) Initializing built-in extension DAMAGE
[    14.408] (II) Initializing built-in extension GESTURE
[    14.430] (II) AIGLX: Trying DRI driver /usr/lib/dri/nouveau_vieux_dri.so
[    14.442] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    14.442] (II) AIGLX: enabled GLX_INTEL_swap_event
[    14.442] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    14.442] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    14.442] (II) AIGLX: Loaded and initialized nouveau_vieux
[    14.442] (II) GLX: Initialized DRI2 GL provider for screen 0
[    14.455] (II) NOUVEAU(0): NVEnterVT is called.
[    15.188] (II) NOUVEAU(0): Setting screen physical size to 270 x 203
[    15.188] resize called 1024 768
[    15.216] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.242] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    15.242] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.242] (II) LoadModule: "evdev"
[    15.242] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.243] (II) Module evdev: vendor="X.Org Foundation"
[    15.243]     compiled for 1.10.0.902, module version = 2.6.0
[    15.243]     Module class: X.Org XInput Driver
[    15.243]     ABI class: X.Org XInput driver, version 12.3
[    15.243] (II) Using input driver 'evdev' for 'Power Button'
[    15.243] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.243] (**) Power Button: always reports core events
[    15.243] (**) Power Button: Device: "/dev/input/event1"
[    15.243] (--) Power Button: Found keys
[    15.243] (II) Power Button: Configuring as keyboard
[    15.243] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    15.243] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.243] (**) Option "xkb_rules" "evdev"
[    15.243] (**) Option "xkb_model" "pc105"
[    15.243] (**) Option "xkb_layout" "us"
[    15.243] (**) Option "xkb_variant" "mac"
[    15.251] (II) XKB: reuse xkmfile /var/lib/xkb/server-2981573DC6A9CB6BAB3002C414DE75F47749BC4F.xkm
[    15.266] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    15.266] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.266] (II) Using input driver 'evdev' for 'Power Button'
[    15.266] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.266] (**) Power Button: always reports core events
[    15.266] (**) Power Button: Device: "/dev/input/event0"
[    15.266] (--) Power Button: Found keys
[    15.266] (II) Power Button: Configuring as keyboard
[    15.267] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    15.267] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.267] (**) Option "xkb_rules" "evdev"
[    15.267] (**) Option "xkb_model" "pc105"
[    15.267] (**) Option "xkb_layout" "us"
[    15.267] (**) Option "xkb_variant" "mac"
[    15.271] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/event2)
[    15.272] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
[    15.272] (II) Using input driver 'evdev' for 'Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)'
[    15.272] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.272] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
[    15.272] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event2"
[    15.272] (--) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
[    15.272] (--) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
[    15.272] (--) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found relative axes
[    15.272] (--) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
[    15.272] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
[    15.272] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Adding scrollwheel support
[    15.272] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
[    15.272] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.272] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input2/event2"
[    15.272] (II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
[    15.272] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.
[    15.272] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
[    15.272] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration profile 0
[    15.272] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration factor: 2.000
[    15.272] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration threshold: 4
[    15.273] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/mouse0)
[    15.273] (II) No input driver/identifier specified (ignoring)
[    15.274] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event3)
[    15.274] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    15.274] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[    15.274] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.274] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[    15.274] (**) Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event3"
[    15.274] (--) Mitsumi Electric Apple Extended USB Keyboard: Found keys
[    15.274] (II) Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[    15.274] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2.3/2-2.3:1.0/input/input3/event3"
[    15.274] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD)
[    15.274] (**) Option "xkb_rules" "evdev"
[    15.274] (**) Option "xkb_model" "pc105"
[    15.274] (**) Option "xkb_layout" "us"
[    15.274] (**) Option "xkb_variant" "mac"
[    15.275] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event4)
[    15.275] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    15.275] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[    15.275] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.275] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[    15.275] (**) Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event4"
[    15.275] (--) Mitsumi Electric Apple Extended USB Keyboard: Found keys
[    15.275] (II) Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[    15.275] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2.3/2-2.3:1.1/input/input4/event4"
[    15.281] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD)
[    15.281] (**) Option "xkb_rules" "evdev"
[    15.281] (**) Option "xkb_model" "pc105"
[    15.281] (**) Option "xkb_layout" "us"
[    15.281] (**) Option "xkb_variant" "mac"

---

### Post by hau5 on 2011-07-20
maybe the problem is that it can't load the nvidia module? Do you know where I can get this?

---

### Post by wildmanne39 on 2011-07-21
Hi, you should install your nvidia driver, you can do it by clicking on additional drivers then install your driver, you will need an internet connection first.

Also you will want to uninstall the nouveau driver if it does not get replaced by the nvidia driver automatically, I think it will but open synaptic and make sure. Then restart your system.

---

### Post by hau5 on 2011-07-21
That did it!

Thanks, I was not aware I needed to manually install the drivers thru synaptic in order to activate it thru Additional Drivers.  Once I installed the package, it showed up in additional drivers and then I activated it and rebooted.  

Everything looks great now.

Thanks for your help!

*For anyone reading this as a potential solution to their own problem, I first uninstalled Nouveau as shown here:  [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by wildmanne39 on 2011-07-21
Hi, your welcome! would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---


---
title: "Oneiric nvidia consistent psuedo-locks"
date: 2011-11-24
forum: General Help
---

### Post by z84976 on 2011-11-24
Hi there.  Odd issue with stock install of Oneiric.  I upgraded a 11.04 machine not too long ago (amd cpu, nvidia cheap vid card) and started getting random screen locks.  As in, mouse moves, computer is fully functional (via ssh remotely) but no windows move.  It irritated me, and I wanted to build a new PC anyway (all I really use that one for was apache dev server anyway) so I built a new little amd system with built-in nvidia controller (nvidia c61 [geforce 7025]) onboard controller.  Fresh install of Oneiric.

Same issue.  I thought maybe it was a firefox issue, but it happens if I just bring up the control panel, or anything really.  Mouse works.  SOMETIMES whatever app you're using (t-bird, etc) still works inside its window.  Sometimes the menu in the upper taskbar still pops up when you move the mouse up there.  Sometimes not.  Sometimes everything works for a few minutes, other times (usually) it all happens within seconds of login.

So same problem, two different bits of hardware, sort of rules out a hardware issue since no components are shared, and one was an upgrade but other was a fresh install.

Tried Unity2d, tried reverting to old style desktop, same behavior.  Updated everything, eventually installed nvidia driver to test that.  Still the same.

Any ideas?  Putting 10.04 on the "new" machine (via live cd so far only) works with no issues.  Getting crazy, I deleted my .iso's of 11.04 so I think I may end up putting 10.04 on there just to make it work.  I want that to be my dev machine... but screen semi-freezes don't help me.  Also, sometimes it STARTS WORKING again after a while, but then freezes again.

I dug around on the forums and via Google, and can't find anything specifically about this issue anywhere.

---

### Post by z84976 on 2011-11-24
Interesting note, also, if I log in to the machine and DO NOTHING, it eventually goes to screen save.  I can put in my pw hours later and get back in fine.  But once I launch an app (firefox usually, or anything really) and it spawns a window, BOOM the gui lockup condition occurs.  As I said, machine is still stable and running in the background, but no love on the gui forefront.

After launching firefox, I get the FF window, and if (when using Unity) I hover the mouse over the upper task bar, the file-edit-etc stuff DOES appear, and the menus will pop down, but you can't move the primary FF window or launch other stuff.  Sometimes you CAN click something like "restore session" or a link in the FF window and it'll do it, then the window will instantly "shift" about 2" (on my screen) to the right and won't move again.  But links in any restored window in FF WILL work and it'll load pages.  No other links/icons/taskbars/etc on the screen will do anything.

I found a 11.04 64 desktop iso.  About to try it and see if it works.  Will post again.  Luckily no data on here that I can't recreate (go go IMAP!).

---

### Post by efflandt on 2011-11-25
Actually there are multiple posts about screen freeze in 11.10 with nvidia.  In my case it happens infrequently, but it just happened a few minutes ago (GT 430 w/nvidia-current 64-bit) and even though the mouse cursor would still move, there was no response to mouse clicks, scroll wheel, or keyboard, and I cannot ssh to it while frozen (which worked earlier today while not frozen).  But not sure if anyone figured it out yet since it happens with various nvidia driver versions.

---

### Post by z84976 on 2011-11-25
Before nuking the whole shebang and installing 11.04 Desktop 64, I tried 'sudo apt-get dist-upgrade' to force installation of new kernel stuff that was held back.  Not really very effective.

I've also tried a lot of the "fixes" for video related issues found on this forum, but as they didn't really apply to me (but couldn't hurt), they did nothing for me.

---

### Post by z84976 on 2011-11-25
efflandt, thanks for the response.  The weird thing to me is that generally (at least for FF and Tbird) the window open when it freezes kinda sorta sometimes works.  And ssh'ing into the machine always works;  it's not the machine that's dead, it's the gui system somehow.

---

### Post by z84976 on 2011-11-25
Have no idea where to go now.  Installed (fresh nuke-it-all install) 11.04 on this machine, substituted this:
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev  a1)
for the onboard nvidia video, did the whole x-swat thing:
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade

I uploaded a video of what it does, which is same as always:
[http://youtu.be/RTSar3nXBy8]("http://youtu.be/RTSar3nXBy8")

Also here's Xorg.0.log.  Fishy stuff is at the end.
```
[    11.131]
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    11.131] X Protocol Version 11, Revision 0
[    11.131] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    11.131] Current Operating System: Linux slick 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[    11.131] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=c0db84eb-49d5-439c-bcee-70c473af2f47 ro qui$
[    11.131] Build Date: 13 October 2011  05:43:01PM
[    11.131] xorg-server 2:1.10.1-1ubuntu1.3 (For technical support please see http://www.ubuntu.com/support)
[    11.131] Current version of pixman: 0.20.2
[    11.131]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    11.131] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.131] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov 25 11:32:46 2011
[    11.131] (==) Using config file: "/etc/X11/xorg.conf"
[    11.131] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.131] (==) No Layout section.  Using the first Screen section.
[    11.131] (==) No screen section available. Using defaults.
[    11.131] (**) |-->Screen "Default Screen Section" (0)
[    11.131] (**) |   |-->Monitor "<default monitor>"
[    11.131] (==) No device specified for screen "Default Screen Section".
        Using the first device section listed.
[    11.131] (**) |   |-->Device "Default Device"
[    11.131] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    11.131] (==) Automatically adding devices
[    11.131] (==) Automatically enabling devices
[    11.131] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.131]    Entry deleted from font path.
[    11.131] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    11.131]    Entry deleted from font path.
[    11.132] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    11.132]    Entry deleted from font path.
[    11.132] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    11.132]    Entry deleted from font path.
[    11.132] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    11.132]    Entry deleted from font path.
[    11.132] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    11.132] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    11.132] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    11.132] (II) Loader magic: 0x7e17e0
[    11.132] (II) Module ABI versions:
[    11.132]    X.Org ANSI C Emulation: 0.4
[    11.132]    X.Org Video Driver: 10.0
[    11.132]    X.Org XInput driver : 12.3
[    11.132]    X.Org Server Extension : 5.0
[    11.132] (--) PCI:*(0:2:0:0) 10de:06e4:10de:05cc rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/3355443$
[    11.132] (II) Open ACPI successful (/var/run/acpid.socket)
[    11.132] (II) LoadModule: "extmod"
[    11.132] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    11.133] (II) Module extmod: vendor="X.Org Foundation"
[    11.133]    compiled for 1.10.1, module version = 1.0.0
[    11.133]    Module class: X.Org Server Extension
[    11.133]    ABI class: X.Org Server Extension, version 5.0
[    11.133] (II) Loading extension MIT-SCREEN-SAVER
[    11.133] (II) Loading extension XFree86-VidModeExtension
[    11.133] (II) Loading extension XFree86-DGA
[    11.133] (II) Loading extension DPMS
[    11.133] (II) Loading extension XVideo
[    11.133] (II) Loading extension XVideo-MotionCompensation
[    11.133] (II) Loading extension X-Resource
[    11.133] (II) LoadModule: "dbe"
[    11.133] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    11.133] (II) Module dbe: vendor="X.Org Foundation"
[    11.133]    compiled for 1.10.1, module version = 1.0.0
[    11.133]    Module class: X.Org Server Extension
[    11.133]    ABI class: X.Org Server Extension, version 5.0
[    11.133] (II) Loading extension DOUBLE-BUFFER
[    11.133] (II) LoadModule: "glx"
[    11.133] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    11.138] (II) Module glx: vendor="NVIDIA Corporation"
[    11.138]    compiled for 4.0.2, module version = 1.0.0
[    11.138]    Module class: X.Org Server Extension
[    11.138] (II) NVIDIA GLX Module  173.14.30  Sat Apr 16 22:45:09 PDT 2011
[    11.138] (II) Loading extension GLX
[    11.138] (II) LoadModule: "record"
[    11.138] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    11.139] (II) Module record: vendor="X.Org Foundation"
[    11.139]    compiled for 1.10.1, module version = 1.13.0
[    11.139]    Module class: X.Org Server Extension
[    11.139]    ABI class: X.Org Server Extension, version 5.0
[    11.139] (II) Loading extension RECORD
[    11.139] (II) LoadModule: "dri"
[    11.139] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    11.139] (II) Module dri: vendor="X.Org Foundation"
[    11.139]    compiled for 1.10.1, module version = 1.0.0
[    11.139]    ABI class: X.Org Server Extension, version 5.0
[    11.139] (II) Loading extension XFree86-DRI
[    11.139] (II) LoadModule: "dri2"
[    11.139] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    11.139] (II) Module dri2: vendor="X.Org Foundation"
[    11.139]    compiled for 1.10.1, module version = 1.2.0
[    11.139]    ABI class: X.Org Server Extension, version 5.0
[    11.139] (II) Loading extension DRI2
[    11.139] (==) Matched nvidia as autoconfigured driver 0
[    11.139] (==) Matched nouveau as autoconfigured driver 1
[    11.139] (==) Matched nv as autoconfigured driver 2
[    11.139] (==) Matched vesa as autoconfigured driver 3
[    11.139] (==) Matched fbdev as autoconfigured driver 4
[    11.139] (==) Assigned the driver to the xf86ConfigLayout
[    11.139] (II) LoadModule: "nvidia"
[    11.139] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    11.140] (II) Module nvidia: vendor="NVIDIA Corporation"
[    11.140]    compiled for 4.0.2, module version = 1.0.0
[    11.140]    Module class: X.Org Video Driver
[    11.140] (II) LoadModule: "nouveau"
[    11.140] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    11.140] (II) Module nouveau: vendor="X.Org Foundation"
[    11.140]    compiled for 1.10.0, module version = 0.0.16
[    11.140]    Module class: X.Org Video Driver
[    11.140]    ABI class: X.Org Video Driver, version 10.0
[    11.140] (II) LoadModule: "nv"
[    11.152] (WW) Warning, couldn't open module nv
[    11.152] (II) UnloadModule: "nv"
[    11.152] (II) Unloading nv
[    11.152] (EE) Failed to load module "nv" (module does not exist, 0)
[    11.152] (II) LoadModule: "vesa"
[    11.152] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.152] (II) Module vesa: vendor="X.Org Foundation"
[    11.152]    compiled for 1.10.0, module version = 2.3.0
[    11.152]    Module class: X.Org Video Driver
[    11.152]    ABI class: X.Org Video Driver, version 10.0
[    11.152] (II) LoadModule: "fbdev"
[    11.152] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.152] (II) Module fbdev: vendor="X.Org Foundation"
[    11.152]    compiled for 1.10.0, module version = 0.4.2
[    11.152]    ABI class: X.Org Video Driver, version 10.0
[    11.152] (II) NVIDIA dlloader X Driver  173.14.30  Sat Apr 16 22:18:29 PDT 2011
[    11.152] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    11.152] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[    11.152] (II) NOUVEAU driver for NVIDIA chipset families :
[    11.152]    RIVA TNT    (NV04)
[    11.152]    RIVA TNT2   (NV05)
[    11.152]    GeForce 256 (NV10)
[    11.152]    GeForce 2   (NV11, NV15)
[    11.152]    GeForce 4MX (NV17, NV18)
[    11.152]    GeForce 3   (NV20)
[    11.152]    GeForce 4Ti (NV25, NV28)
[    11.152]    GeForce FX  (NV3x)
[    11.152]    GeForce 6   (NV4x)
[    11.152]    GeForce 7   (G7x)
[    11.152]    GeForce 8   (G8x)
[    11.152] (II) VESA: driver for VESA chipsets: vesa
[    11.152] (II) FBDEV: driver for framebuffer: fbdev
[    11.152] (++) using VT number 7

[    11.152] (II) Loading sub module "fb"
[    11.152] (II) LoadModule: "fb"
[    11.153] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.153] (II) Module fb: vendor="X.Org Foundation"
[    11.153]    compiled for 1.10.1, module version = 1.0.0
[    11.153]    ABI class: X.Org ANSI C Emulation, version 0.4
[    11.153] (II) Loading sub module "wfb"
[    11.153] (II) LoadModule: "wfb"
[    11.153] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    11.153] (II) Module wfb: vendor="X.Org Foundation"
[    11.153]    compiled for 1.10.1, module version = 1.0.0
[    11.153]    ABI class: X.Org ANSI C Emulation, version 0.4
[    11.153] (II) Loading sub module "ramdac"
[    11.153] (II) Module "ramdac" already built-in
[    11.153] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    11.153] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    11.153] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.153] (WW) Falling back to old probe method for vesa
[    11.153] (WW) Falling back to old probe method for fbdev
[    11.153] (II) Loading sub module "fbdevhw"
[    11.153] (II) LoadModule: "fbdevhw"
[    11.153] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    11.153] (II) Module fbdevhw: vendor="X.Org Foundation"
[    11.153]    compiled for 1.10.1, module version = 0.0.2
[    11.153]    ABI class: X.Org Video Driver, version 10.0
[    11.153] (II) NVIDIA(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    11.153] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    11.153] (==) NVIDIA(0): RGB weight 888
[    11.153] (==) NVIDIA(0): Default visual is TrueColor
[    11.153] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    11.153] (**) NVIDIA(0): Option "NoLogo" "True"
[    11.154] (**) NVIDIA(0): Enabling RENDER acceleration
[    11.154] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    11.154] (II) NVIDIA(0):     enabled.
[    12.645] (II) NVIDIA(0): NVIDIA GPU GeForce 8400 GS (G98) at PCI:2:0:0 (GPU-0)
[    12.645] (--) NVIDIA(0): Memory: 524288 kBytes
[    12.645] (--) NVIDIA(0): VideoBIOS: 62.98.29.00.00
[    12.645] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    12.645] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    12.645] (--) NVIDIA(0): Connected display device(s) on GeForce 8400 GS at PCI:2:0:0:
[    12.645] (--) NVIDIA(0):     DELL 2407WFP (CRT-1)
[    12.645] (--) NVIDIA(0): DELL 2407WFP (CRT-1): 400.0 MHz maximum pixel clock
[    12.711] (II) NVIDIA(0): Assigned Display Device: CRT-1
[    12.711] (==) NVIDIA(0):
[    12.711] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    12.711] (==) NVIDIA(0):     will be used as the requested mode.
[    12.711] (==) NVIDIA(0):
[    12.711] (II) NVIDIA(0): Validated modes:
[    12.711] (II) NVIDIA(0):     "nvidia-auto-select"
[    12.711] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[    12.746] (--) NVIDIA(0): DPI set to (93, 92); computed from "UseEdidDpi" X config
[    12.746] (--) NVIDIA(0):     option
[    12.746] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    12.746] (II) UnloadModule: "nouveau"
[    12.746] (II) Unloading nouveau
[    12.746] (II) UnloadModule: "vesa"
[    12.746] (II) Unloading vesa
[    12.746] (II) UnloadModule: "fbdev"
[    12.746] (II) Unloading fbdev
[    12.746] (II) UnloadModule: "fbdevhw"
[    12.746] (II) Unloading fbdevhw
[    12.746] (--) Depth 24 pixmap format is 32 bpp
[    12.748] (II) NVIDIA(0): Initialized GPU GART.
[    12.750] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    12.773] (II) Loading extension NV-GLX
[    12.790] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[    12.793] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[    12.793] (==) NVIDIA(0): Backing store disabled
[    12.793] (==) NVIDIA(0): Silken mouse enabled
[    12.801] (==) NVIDIA(0): DPMS enabled
[    12.801] (II) Loading extension NV-CONTROL
[    12.801] (==) RandR enabled
[    12.801] (II) Initializing built-in extension Generic Event Extension
[    12.801] (II) Initializing built-in extension SHAPE
[    12.801] (II) Initializing built-in extension MIT-SHM
[    12.801] (II) Initializing built-in extension XInputExtension
[    12.801] (II) Initializing built-in extension XTEST
[    12.801] (II) Initializing built-in extension BIG-REQUESTS
[    12.801] (II) Initializing built-in extension SYNC
[    12.801] (II) Initializing built-in extension XKEYBOARD
[    12.801] (II) Initializing built-in extension XC-MISC
[    12.801] (II) Initializing built-in extension SECURITY
[    12.801] (II) Initializing built-in extension XINERAMA
[    12.801] (II) Initializing built-in extension XFIXES
[    12.801] (II) Initializing built-in extension RENDER
[    12.801] (II) Initializing built-in extension RANDR
[    12.801] (II) Initializing built-in extension COMPOSITE
[    12.801] (II) Initializing built-in extension DAMAGE
[    12.801] (II) Initializing built-in extension GESTURE
[    12.802] (II) Initializing extension GLX
[    12.814] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    12.820] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    12.820] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.820] (II) LoadModule: "evdev"
[    12.820] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.820] (II) Module evdev: vendor="X.Org Foundation"
[    12.820]    compiled for 1.10.0.902, module version = 2.6.0
[    12.820]    Module class: X.Org XInput Driver
[    12.820]    ABI class: X.Org XInput driver, version 12.3
[    12.820] (II) Using input driver 'evdev' for 'Power Button'
[    12.820] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.820] (**) Power Button: always reports core events
[    12.820] (**) Power Button: Device: "/dev/input/event1"
[    12.821] (--) Power Button: Found keys
[    12.821] (II) Power Button: Configuring as keyboard
[    12.821] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    12.821] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    12.821] (**) Option "xkb_rules" "evdev"
[    12.821] (**) Option "xkb_model" "pc105"
[    12.821] (**) Option "xkb_layout" "us"
[    12.823] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    12.823] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.823] (II) Using input driver 'evdev' for 'Power Button'
[    12.823] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.823] (**) Power Button: always reports core events
[    12.823] (**) Power Button: Device: "/dev/input/event0"
[    12.823] (--) Power Button: Found keys
[    12.823] (II) Power Button: Configuring as keyboard
[    12.823] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    12.823] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    12.823] (**) Option "xkb_rules" "evdev"
[    12.823] (**) Option "xkb_model" "pc105"
[    12.823] (**) Option "xkb_layout" "us"
[    12.824] (II) config/udev: Adding input device Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) (/dev/input/event2)
[    12.824] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
[    12.824] (II) Using input driver 'evdev' for 'Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)'
[    12.824] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.824] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): always reports core events
[    12.824] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Device: "/dev/input/event2"
[    12.824] (--) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found 9 mouse buttons
[    12.824] (--) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
[    12.824] (--) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found relative axes
[    12.824] (--) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found x and y relative axes
[    12.824] (II) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Configuring as mouse
[    12.824] (II) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Adding scrollwheel support
[    12.824] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
[    12.824] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, Emulate$
[    12.825] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input2/event2"
[    12.825] (II) XINPUT: Adding extended input device "Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)" (type: MOUSE)
[    12.825] (II) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): initialized for relative axes.
[    12.825] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
[    12.825] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) acceleration profile 0
[    12.825] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) acceleration factor: 2.000
[    12.825] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) acceleration threshold: 4
[    12.825] (II) config/udev: Adding input device Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) (/dev/input/mouse0)
[    12.825] (II) No input driver/identifier specified (ignoring)
[    12.825] (II) config/udev: Adding input device Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ) (/de$
[    12.825] (**) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Applying InputClass "evdev keyboard $
[    12.825] (II) Using input driver 'evdev' for 'Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 )'
[    12.825] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.825] (**) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): always reports core events
[    12.825] (**) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Device: "/dev/input/event3"
[    12.830] (--) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Found keys
[    12.830] (II) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Configuring as keyboard
[    12.830] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4.1/2-4.1:1.0/input/input3/event3"
[    12.830] (II) XINPUT: Adding extended input device "Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 )$
[    12.830] (**) Option "xkb_rules" "evdev"
[    12.830] (**) Option "xkb_model" "pc105"
[    12.830] (**) Option "xkb_layout" "us"
[    12.830] (II) config/udev: Adding input device Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ) (/de$
[    12.830] (**) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Applying InputClass "evdev keyboard $
[    12.830] (II) Using input driver 'evdev' for 'Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 )'
[    12.830] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.830] (**) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): always reports core events
[    12.830] (**) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Device: "/dev/input/event4"
[    12.830] (--) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Found 12 mouse buttons
[    12.830] (--) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Found keys
[    12.830] (II) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Configuring as mouse
[    12.830] (II) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Configuring as keyboard
[    12.830] (**) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): YAxisMapping: buttons 4 and 5
[    12.830] (**) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): EmulateWheelButton: 4, EmulateWheelI$
[    12.830] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4.1/2-4.1:1.1/input/input4/event4"
[    12.831] (II) XINPUT: Adding extended input device "Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 )$
[    12.831] (**) Option "xkb_rules" "evdev"
[    12.831] (**) Option "xkb_model" "pc105"
[    12.831] (**) Option "xkb_layout" "us"
[   196.182] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[   235.823] [mi] EQ overflowing. The server is probably stuck in an infinite loop.
[   235.823]
Backtrace:
[   235.823] 0: /usr/bin/X (xorg_backtrace+0x26) [0x45cef6]
[   235.823] 1: /usr/bin/X (mieqEnqueue+0x1f4) [0x4593b4]
[   235.823] 2: /usr/bin/X (xf86PostMotionEventM+0x97) [0x489667]
[   235.823] 3: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f4b1293e000+0x5ff3) [0x7f4b12943ff3]
[   235.823] 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f4b1293e000+0x668d) [0x7f4b1294468d]
[   235.823] 5: /usr/bin/X (0x400000+0x6d7d7) [0x46d7d7]
[   235.823] 6: /usr/bin/X (0x400000+0x11a6de) [0x51a6de]
[   235.823] 7: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f4b28ccc000+0xfc60) [0x7f4b28cdbc60]
[   235.823] 8: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7f4b2443b000+0x5797a1) [0x7f4b249b47a1]


```

---

### Post by efflandt on 2011-11-25
See if that happens if you boot a (recovery) kernel and then "Resume".  If that works, maybe you need **nomodeset** as a kernel boot parameter, since that is included when doing a recovery boot.

---

### Post by z84976 on 2011-11-25
No love with the nomodeset parameter either....    argh....

---

### Post by z84976 on 2011-11-25
Oddly enough, I do-release-upgrade upgraded the faulty 11.04 I just installed this morning to 11.10 (instead of just re-doing it with the 11.10 ISO which would have been fine given that there's no data on the beast yet).  So far... it's working.  What has changed?  Uh, nothing that I know of.  11.10 off the ISO didn't work, nor did 11.04 off the ISO, even after updating.  I'll post again if this issue crops back up but as of right now it's been stable for an hour with a terminal window, a firefox session, and the software center (so I can install my goodies) running.  I'm going to keep track of what all I install because if it starts to freak out again maybe it's something I install.

---


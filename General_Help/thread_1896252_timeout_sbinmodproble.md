---
title: "timeout: /sbin/modproble"
date: 2011-12-16
forum: General Help
---

### Post by darqueness on 2011-12-16
I just installed 11.10 on my computer and it started up fine the first couple times.

But after installing the Nvidia drivers for my graphics card it goes into 'busybox' and i keep getting:

'timeout: killing: /sbin/modprobe'  

(or something to that effect)




I read something about "quiet splash" and "nomodeset"  But i don't know how to edit this if i can't boot.



I'm new to this and any help would be appreciated.

---

### Post by matt_symes on 2011-12-16
Hi
> 
'timeout: killing: /sbin/modprobe'  

(or something to that effect)


The exact error message please.

Make and model of your PC please.

Can you boot into recovery mode ?

Kind regards

---

### Post by darqueness on 2011-12-16
nforce 680i
cpu e8400
gforce 8800gts
4gb ram

the OS is the 11.10 64bit


udevd[###]: timeout: killing '/sbin/modprobe -bv usb:####################
udevd[###]: timeout: killing '/sbin/modprobe -bv pci:####################

it cycles through those very quickly (the ##### sections are changing)

When it stops it says:
udevd[###]: timeout: killing '/sbin/modprobe -bv pci:####################
[###] terminated by signal 9 (killed)


the recovery mode didnt work before, i'll try it again (its being slow)

---

### Post by darqueness on 2011-12-16
oh, ok i'm in the recovery menu.

it has 4 options:
resume
fsck
remount
root

---

### Post by darqueness on 2011-12-16
ok, this is random, but after restarting again, and just waiting a LONG time it decided to go through and boot.

what would i need to change so it won't get stuck again?

---

### Post by matt_symes on 2011-12-16
Hi

Now you have got in to Ubuntu please post the output of 

```
cat /var/log/Xorg.0.log
```

and

```
sudo lshw -c display
```

Assuming the problem is your video system as you suggested it happened after you installed the priority drivers.

Kind regards

---

### Post by darqueness on 2011-12-16
[   178.559] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[   178.559] X Protocol Version 11, Revision 0
[   178.559] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[   178.559] Current Operating System: Linux nim-122-CK-NF68 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64
[   178.559] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=1dcea141-8198-4448-972b-2d6f53bf4676 ro quiet splash vt.handoff=7
[   178.559] Build Date: 19 October 2011  05:21:26AM
[   178.559] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   178.559] Current version of pixman: 0.22.2
[   178.559] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[   178.559] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   178.559] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 16 13:53:15 2011
[   178.560] (==) Using config file: "/etc/X11/xorg.conf"
[   178.560] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   178.560] (==) No Layout section.  Using the first Screen section.
[   178.560] (==) No screen section available. Using defaults.
[   178.560] (**) |-->Screen "Default Screen Section" (0)
[   178.560] (**) |   |-->Monitor "<default monitor>"
[   178.560] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[   178.560] (**) |   |-->Device "Default Device"
[   178.560] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   178.560] (==) Automatically adding devices
[   178.560] (==) Automatically enabling devices
[   178.560] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   178.560] 	Entry deleted from font path.
[   178.560] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   178.560] 	Entry deleted from font path.
[   178.560] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   178.560] 	Entry deleted from font path.
[   178.560] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   178.560] 	Entry deleted from font path.
[   178.560] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   178.560] 	Entry deleted from font path.
[   178.560] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   178.560] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   178.560] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   178.560] (II) Loader magic: 0x7e0220
[   178.560] (II) Module ABI versions:
[   178.560] 	X.Org ANSI C Emulation: 0.4
[   178.560] 	X.Org Video Driver: 10.0
[   178.560] 	X.Org XInput driver : 12.3
[   178.560] 	X.Org Server Extension : 5.0
[   178.561] (--) PCI:*(0:1:0:0) 10de:0193:3842:c825 rev 162, Mem @ 0xcc000000/16777216, 0xb0000000/268435456, 0xca000000/33554432, I/O @ 0x00009c00/128, BIOS @ 0x????????/131072
[   178.561] (II) Open ACPI successful (/var/run/acpid.socket)
[   178.561] (II) LoadModule: "extmod"
[   178.578] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   178.578] (II) Module extmod: vendor="X.Org Foundation"
[   178.578] 	compiled for 1.10.4, module version = 1.0.0
[   178.578] 	Module class: X.Org Server Extension
[   178.578] 	ABI class: X.Org Server Extension, version 5.0
[   178.578] (II) Loading extension MIT-SCREEN-SAVER
[   178.578] (II) Loading extension XFree86-VidModeExtension
[   178.578] (II) Loading extension XFree86-DGA
[   178.578] (II) Loading extension DPMS
[   178.578] (II) Loading extension XVideo
[   178.578] (II) Loading extension XVideo-MotionCompensation
[   178.578] (II) Loading extension X-Resource
[   178.578] (II) LoadModule: "dbe"
[   178.578] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   178.578] (II) Module dbe: vendor="X.Org Foundation"
[   178.578] 	compiled for 1.10.4, module version = 1.0.0
[   178.578] 	Module class: X.Org Server Extension
[   178.578] 	ABI class: X.Org Server Extension, version 5.0
[   178.578] (II) Loading extension DOUBLE-BUFFER
[   178.578] (II) LoadModule: "glx"
[   178.578] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[   178.586] (II) Module glx: vendor="NVIDIA Corporation"
[   178.586] 	compiled for 4.0.2, module version = 1.0.0
[   178.586] 	Module class: X.Org Server Extension
[   178.586] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:12:07 PDT 2011
[   178.586] (II) Loading extension GLX
[   178.586] (II) LoadModule: "record"
[   178.586] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   178.586] (II) Module record: vendor="X.Org Foundation"
[   178.586] 	compiled for 1.10.4, module version = 1.13.0
[   178.586] 	Module class: X.Org Server Extension
[   178.586] 	ABI class: X.Org Server Extension, version 5.0
[   178.586] (II) Loading extension RECORD
[   178.586] (II) LoadModule: "dri"
[   178.587] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   178.587] (II) Module dri: vendor="X.Org Foundation"
[   178.587] 	compiled for 1.10.4, module version = 1.0.0
[   178.587] 	ABI class: X.Org Server Extension, version 5.0
[   178.587] (II) Loading extension XFree86-DRI
[   178.587] (II) LoadModule: "dri2"
[   178.587] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   178.587] (II) Module dri2: vendor="X.Org Foundation"
[   178.587] 	compiled for 1.10.4, module version = 1.2.0
[   178.587] 	ABI class: X.Org Server Extension, version 5.0
[   178.587] (II) Loading extension DRI2
[   178.587] (==) Matched nvidia as autoconfigured driver 0
[   178.587] (==) Matched nouveau as autoconfigured driver 1
[   178.587] (==) Matched nv as autoconfigured driver 2
[   178.587] (==) Matched vesa as autoconfigured driver 3
[   178.587] (==) Matched fbdev as autoconfigured driver 4
[   178.587] (==) Assigned the driver to the xf86ConfigLayout
[   178.587] (II) LoadModule: "nvidia"
[   178.587] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   178.587] (II) Module nvidia: vendor="NVIDIA Corporation"
[   178.587] 	compiled for 4.0.2, module version = 1.0.0
[   178.588] 	Module class: X.Org Video Driver
[   178.588] (II) LoadModule: "nouveau"
[   178.588] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   178.588] (II) Module nouveau: vendor="X.Org Foundation"
[   178.588] 	compiled for 1.10.1, module version = 0.0.16
[   178.588] 	Module class: X.Org Video Driver
[   178.588] 	ABI class: X.Org Video Driver, version 10.0
[   178.588] (II) LoadModule: "nv"
[   178.588] (WW) Warning, couldn't open module nv
[   178.588] (II) UnloadModule: "nv"
[   178.588] (II) Unloading nv
[   178.588] (EE) Failed to load module "nv" (module does not exist, 0)
[   178.588] (II) LoadModule: "vesa"
[   178.588] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   178.588] (II) Module vesa: vendor="X.Org Foundation"
[   178.588] 	compiled for 1.10.2, module version = 2.3.0
[   178.588] 	Module class: X.Org Video Driver
[   178.588] 	ABI class: X.Org Video Driver, version 10.0
[   178.588] (II) LoadModule: "fbdev"
[   178.589] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   178.589] (II) Module fbdev: vendor="X.Org Foundation"
[   178.589] 	compiled for 1.10.0, module version = 0.4.2
[   178.589] 	ABI class: X.Org Video Driver, version 10.0
[   178.589] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:55:26 PDT 2011
[   178.589] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   178.589] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[   178.589] (II) NOUVEAU driver for NVIDIA chipset families :
[   178.589] 	RIVA TNT        (NV04)
[   178.589] 	RIVA TNT2       (NV05)
[   178.589] 	GeForce 256     (NV10)
[   178.589] 	GeForce 2       (NV11, NV15)
[   178.589] 	GeForce 4MX     (NV17, NV18)
[   178.589] 	GeForce 3       (NV20)
[   178.589] 	GeForce 4Ti     (NV25, NV28)
[   178.589] 	GeForce FX      (NV3x)
[   178.589] 	GeForce 6       (NV4x)
[   178.589] 	GeForce 7       (G7x)
[   178.589] 	GeForce 8       (G8x)
[   178.589] 	GeForce GTX 200 (NVA0)
[   178.589] 	GeForce GTX 400 (NVC0)
[   178.589] (II) VESA: driver for VESA chipsets: vesa
[   178.589] (II) FBDEV: driver for framebuffer: fbdev
[   178.589] (++) using VT number 7

[   178.591] (II) Loading sub module "fb"
[   178.591] (II) LoadModule: "fb"
[   178.591] (II) Loading /usr/lib/xorg/modules/libfb.so
[   178.591] (II) Module fb: vendor="X.Org Foundation"
[   178.591] 	compiled for 1.10.4, module version = 1.0.0
[   178.591] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   178.591] (II) Loading sub module "wfb"
[   178.591] (II) LoadModule: "wfb"
[   178.591] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   178.591] (II) Module wfb: vendor="X.Org Foundation"
[   178.591] 	compiled for 1.10.4, module version = 1.0.0
[   178.591] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   178.591] (II) Loading sub module "ramdac"
[   178.591] (II) LoadModule: "ramdac"
[   178.591] (II) Module "ramdac" already built-in
[   178.591] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   178.591] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   178.591] (II) Loading /usr/lib/xorg/modules/libfb.so
[   178.591] (WW) Falling back to old probe method for vesa
[   178.591] (WW) Falling back to old probe method for fbdev
[   178.591] (II) Loading sub module "fbdevhw"
[   178.591] (II) LoadModule: "fbdevhw"
[   178.592] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   178.592] (II) Module fbdevhw: vendor="X.Org Foundation"
[   178.592] 	compiled for 1.10.4, module version = 0.0.2
[   178.592] 	ABI class: X.Org Video Driver, version 10.0
[   178.592] (EE) open /dev/fb0: No such file or directory
[   178.592] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   178.592] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[   178.592] (==) NVIDIA(0): RGB weight 888
[   178.592] (==) NVIDIA(0): Default visual is TrueColor
[   178.592] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   178.592] (**) NVIDIA(0): Option "NoLogo" "True"
[   179.569] (II) NVIDIA(GPU-0): Display (Acer P241W (DFP-0)) supports NVIDIA 3D Vision
[   179.569] (II) NVIDIA(GPU-0):     stereo.
[   179.571] (II) NVIDIA(0): NVIDIA GPU GeForce 8800 GTS (G80) at PCI:1:0:0 (GPU-0)
[   179.571] (--) NVIDIA(0): Memory: 655360 kBytes
[   179.571] (--) NVIDIA(0): VideoBIOS: 60.80.0a.00.05
[   179.571] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   179.571] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   179.571] (--) NVIDIA(0): Connected display device(s) on GeForce 8800 GTS at PCI:1:0:0
[   179.571] (--) NVIDIA(0):     Acer P241W (DFP-0)
[   179.571] (--) NVIDIA(0): Acer P241W (DFP-0): 330.0 MHz maximum pixel clock
[   179.571] (--) NVIDIA(0): Acer P241W (DFP-0): Internal Dual Link TMDS
[   179.651] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[   179.651] (**) NVIDIA(0):     enabled on all display devices.
[   179.670] (II) NVIDIA(0): Assigned Display Device: DFP-0
[   179.670] (==) NVIDIA(0): 
[   179.670] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[   179.670] (==) NVIDIA(0):     will be used as the requested mode.
[   179.670] (==) NVIDIA(0): 
[   179.670] (II) NVIDIA(0): Validated modes:
[   179.670] (II) NVIDIA(0):     "nvidia-auto-select"
[   179.671] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[   179.708] (--) NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
[   179.708] (--) NVIDIA(0):     option
[   179.708] (II) UnloadModule: "nouveau"
[   179.708] (II) Unloading nouveau
[   179.708] (II) UnloadModule: "vesa"
[   179.708] (II) Unloading vesa
[   179.708] (II) UnloadModule: "fbdev"
[   179.708] (II) Unloading fbdev
[   179.708] (II) UnloadModule: "fbdevhw"
[   179.708] (II) Unloading fbdevhw
[   179.708] (--) Depth 24 pixmap format is 32 bpp
[   179.708] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[   179.717] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[   179.739] (II) Loading extension NV-GLX
[   179.781] (==) NVIDIA(0): Disabling shared memory pixmaps
[   179.781] (==) NVIDIA(0): Backing store disabled
[   179.781] (==) NVIDIA(0): Silken mouse enabled
[   179.781] (==) NVIDIA(0): DPMS enabled
[   179.782] (II) Loading extension NV-CONTROL
[   179.782] (II) Loading extension XINERAMA
[   179.782] (II) Loading sub module "dri2"
[   179.782] (II) LoadModule: "dri2"
[   179.782] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   179.782] (II) Module dri2: vendor="X.Org Foundation"
[   179.782] 	compiled for 1.10.4, module version = 1.2.0
[   179.782] 	ABI class: X.Org Server Extension, version 5.0
[   179.782] (II) NVIDIA(0): [DRI2] Setup complete
[   179.782] (==) RandR enabled
[   179.782] (II) Initializing built-in extension Generic Event Extension
[   179.782] (II) Initializing built-in extension SHAPE
[   179.782] (II) Initializing built-in extension MIT-SHM
[   179.782] (II) Initializing built-in extension XInputExtension
[   179.782] (II) Initializing built-in extension XTEST
[   179.782] (II) Initializing built-in extension BIG-REQUESTS
[   179.782] (II) Initializing built-in extension SYNC
[   179.782] (II) Initializing built-in extension XKEYBOARD
[   179.782] (II) Initializing built-in extension XC-MISC
[   179.782] (II) Initializing built-in extension SECURITY
[   179.782] (II) Initializing built-in extension XINERAMA
[   179.782] (II) Initializing built-in extension XFIXES
[   179.782] (II) Initializing built-in extension RENDER
[   179.782] (II) Initializing built-in extension RANDR
[   179.782] (II) Initializing built-in extension COMPOSITE
[   179.782] (II) Initializing built-in extension DAMAGE
[   179.782] (II) Initializing built-in extension GESTURE
[   179.783] (II) Initializing extension GLX
[   179.797] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   179.803] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   179.803] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   179.803] (II) LoadModule: "evdev"
[   179.803] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   179.804] (II) Module evdev: vendor="X.Org Foundation"
[   179.804] 	compiled for 1.10.2, module version = 2.6.0
[   179.804] 	Module class: X.Org XInput Driver
[   179.804] 	ABI class: X.Org XInput driver, version 12.3
[   179.804] (II) Using input driver 'evdev' for 'Power Button'
[   179.804] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   179.804] (**) Power Button: always reports core events
[   179.804] (**) Power Button: Device: "/dev/input/event1"
[   179.804] (--) Power Button: Found keys
[   179.804] (II) Power Button: Configuring as keyboard
[   179.804] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   179.804] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   179.804] (**) Option "xkb_rules" "evdev"
[   179.804] (**) Option "xkb_model" "pc105"
[   179.804] (**) Option "xkb_layout" "us"
[   179.807] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   179.807] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   179.807] (II) Using input driver 'evdev' for 'Power Button'
[   179.807] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   179.807] (**) Power Button: always reports core events
[   179.807] (**) Power Button: Device: "/dev/input/event0"
[   179.807] (--) Power Button: Found keys
[   179.807] (II) Power Button: Configuring as keyboard
[   179.807] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   179.807] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   179.807] (**) Option "xkb_rules" "evdev"
[   179.807] (**) Option "xkb_model" "pc105"
[   179.807] (**) Option "xkb_layout" "us"
[   179.809] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event3)
[   179.809] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[   179.809] (II) Using input driver 'evdev' for 'Logitech Trackball'
[   179.809] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   179.809] (**) Logitech Trackball: always reports core events
[   179.809] (**) Logitech Trackball: Device: "/dev/input/event3"
[   179.809] (--) Logitech Trackball: Found 3 mouse buttons
[   179.809] (--) Logitech Trackball: Found scroll wheel(s)
[   179.809] (--) Logitech Trackball: Found relative axes
[   179.809] (--) Logitech Trackball: Found x and y relative axes
[   179.809] (II) Logitech Trackball: Configuring as mouse
[   179.809] (II) Logitech Trackball: Adding scrollwheel support
[   179.809] (**) Logitech Trackball: YAxisMapping: buttons 4 and 5
[   179.809] (**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   179.809] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input3/event3"
[   179.809] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
[   179.809] (II) Logitech Trackball: initialized for relative axes.
[   179.809] (**) Logitech Trackball: (accel) keeping acceleration scheme 1
[   179.809] (**) Logitech Trackball: (accel) acceleration profile 0
[   179.809] (**) Logitech Trackball: (accel) acceleration factor: 2.000
[   179.809] (**) Logitech Trackball: (accel) acceleration threshold: 4
[   179.809] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[   179.810] (II) No input driver/identifier specified (ignoring)
[   179.810] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event4)
[   179.810] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[   179.810] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[   179.810] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   179.810] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[   179.810] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
[   179.810] (--) Logitech USB-PS/2 Optical Mouse: Found 12 mouse buttons
[   179.810] (--) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[   179.810] (--) Logitech USB-PS/2 Optical Mouse: Found relative axes
[   179.810] (--) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[   179.810] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[   179.810] (II) Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[   179.810] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[   179.810] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   179.810] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2:1.0/input/input4/event4"
[   179.810] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[   179.810] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[   179.810] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[   179.810] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[   179.810] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[   179.810] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[   179.810] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse1)
[   179.810] (II) No input driver/identifier specified (ignoring)
[   179.814] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[   179.814] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   179.814] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   179.814] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   179.814] (**) AT Translated Set 2 keyboard: always reports core events
[   179.814] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[   179.814] (--) AT Translated Set 2 keyboard: Found keys
[   179.814] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   179.814] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[   179.814] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   179.814] (**) Option "xkb_rules" "evdev"
[   179.814] (**) Option "xkb_model" "pc105"
[   179.814] (**) Option "xkb_layout" "us"
[   181.707] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[   351.415] (II) config/udev: Adding input device HDA NVidia Headphone (/dev/input/event5)
[   351.415] (II) No input driver/identifier specified (ignoring)
[  1332.169] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[  3139.856] (II) config/udev: removing device Logitech Trackball
[  3139.858] (II) Logitech Trackball: Close
[  3139.858] (II) UnloadModule: "evdev"
[  3139.858] (II) Unloading evdev







 *-display               
       description: VGA compatible controller
       product: G80 [GeForce 8800 GTS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:cc000000-ccffffff memory:b0000000-bfffffff memory:ca000000-cbffffff ioport:9c00(size=128) memory:cd000000-cd01ffff

---

### Post by matt_symes on 2011-12-16
Hi

I can't see much wrong with that apart from the fact it's slow. 

Can you post the output of dmesg after a boot please. I think it's those modprobe timeouts that are causing you problems.

Kind regards

---


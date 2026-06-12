---
title: "Nvidia + Nouveau"
date: 2012-06-15
forum: General Help
---

### Post by deadpixel23 on 2012-06-15
Ok so I'm trying to get 11.10 running, but when I install the Nvidia driver I keep getting stuck on boot with this error in my kern.log

```
The NVIDIA probe routine was not called for 1 device(s).
This can occur when a driver such as nouveau, rivafb, 
nvidiafb, or rivatv was loaded and obtained ownership of 
the NVIDIA device(s)
```

Now the frustrating thing is I've added all of those to my blacklist yet they still seem to be hijacking.

This is with the nvidia 96 drivers (Gforce4 MX4000). Same situation with download from Nvidia, nvidia-96 and nvidia-96-updates.

I just can't seem to find a solution for this.

---

### Post by deadpixel23 on 2012-06-15
Bump

Really at a loss here...

---

### Post by Helkaluin on 2012-06-15
Are you sure you've blacklisted them from modprobe?

Check dmesg.  If you've blacklisted correctly there shouldn't be any lines of the nouveau module loading.

---

### Post by deadpixel23 on 2012-06-15
Nothing in dmesg about nouveau, rivafb, nvidiafb or rivatv. But I still have the same error.

---

### Post by deadpixel23 on 2012-06-15
For what it's worth, here is my Xorg.0.log

```
[     9.891] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[     9.891] X Protocol Version 11, Revision 0
[     9.891] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[     9.891] Current Operating System: Linux htpc 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686
[     9.891] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=8a3fe130-995a-486f-bfc1-df75eb37523d ro quiet splash vmalloc=256M vt.handoff=7
[     9.891] Build Date: 29 September 2011  12:48:48AM
[     9.891] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     9.891] Current version of pixman: 0.22.2
[     9.891]     Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
    to make sure that you have the latest version.
[     9.891] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     9.891] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun 15 10:49:44 2012
[     9.914] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     9.914] (==) No Layout section.  Using the first Screen section.
[     9.914] (==) No screen section available. Using defaults.
[     9.914] (**) |-->Screen "Default Screen Section" (0)
[     9.914] (**) |   |-->Monitor "<default monitor>"
[     9.914] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     9.915] (==) Automatically adding devices
[     9.915] (==) Automatically enabling devices
[     9.930] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     9.930]     Entry deleted from font path.
[     9.930] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     9.930]     Entry deleted from font path.
[     9.930] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     9.930]     Entry deleted from font path.
[     9.931] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     9.931]     Entry deleted from font path.
[     9.931] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     9.931]     Entry deleted from font path.
[     9.948] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[     9.948] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     9.948] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     9.948] (II) Loader magic: 0x823ada0
[     9.948] (II) Module ABI versions:
[     9.948]     X.Org ANSI C Emulation: 0.4
[     9.948]     X.Org Video Driver: 10.0
[     9.948]     X.Org XInput driver : 12.3
[     9.948]     X.Org Server Extension : 5.0
[     9.949] (--) PCI:*(0:3:1:0) 10de:0185:0000:0000 rev 193, Mem @ 0xde000000/16777216, 0xd0000000/134217728, BIOS @ 0x????????/131072
[     9.949] (II) Open ACPI successful (/var/run/acpid.socket)
[     9.949] (II) LoadModule: "extmod"
[     9.960] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     9.960] (II) Module extmod: vendor="X.Org Foundation"
[     9.960]     compiled for 1.10.4, module version = 1.0.0
[     9.960]     Module class: X.Org Server Extension
[     9.960]     ABI class: X.Org Server Extension, version 5.0
[     9.960] (II) Loading extension MIT-SCREEN-SAVER
[     9.960] (II) Loading extension XFree86-VidModeExtension
[     9.960] (II) Loading extension XFree86-DGA
[     9.960] (II) Loading extension DPMS
[     9.960] (II) Loading extension XVideo
[     9.960] (II) Loading extension XVideo-MotionCompensation
[     9.960] (II) Loading extension X-Resource
[     9.960] (II) LoadModule: "dbe"
[     9.960] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     9.960] (II) Module dbe: vendor="X.Org Foundation"
[     9.960]     compiled for 1.10.4, module version = 1.0.0
[     9.960]     Module class: X.Org Server Extension
[     9.960]     ABI class: X.Org Server Extension, version 5.0
[     9.960] (II) Loading extension DOUBLE-BUFFER
[     9.960] (II) LoadModule: "glx"
[     9.961] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    11.560] (II) Module glx: vendor="NVIDIA Corporation"
[    11.560]     compiled for 4.0.2, module version = 1.0.0
[    11.560]     Module class: X.Org Server Extension
[    11.560] (II) NVIDIA GLX Module  96.43.20  Sun Jul 17 23:48:16 PDT 2011
[    11.560] (II) Loading extension GLX
[    11.560] (II) LoadModule: "record"
[    11.560] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    11.560] (II) Module record: vendor="X.Org Foundation"
[    11.560]     compiled for 1.10.4, module version = 1.13.0
[    11.560]     Module class: X.Org Server Extension
[    11.560]     ABI class: X.Org Server Extension, version 5.0
[    11.560] (II) Loading extension RECORD
[    11.560] (II) LoadModule: "dri"
[    11.561] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    11.561] (II) Module dri: vendor="X.Org Foundation"
[    11.561]     compiled for 1.10.4, module version = 1.0.0
[    11.561]     ABI class: X.Org Server Extension, version 5.0
[    11.561] (II) Loading extension XFree86-DRI
[    11.561] (II) LoadModule: "dri2"
[    11.561] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    11.561] (II) Module dri2: vendor="X.Org Foundation"
[    11.561]     compiled for 1.10.4, module version = 1.2.0
[    11.561]     ABI class: X.Org Server Extension, version 5.0
[    11.561] (II) Loading extension DRI2
[    11.561] (==) Matched nvidia as autoconfigured driver 0
[    11.561] (==) Matched nouveau as autoconfigured driver 1
[    11.561] (==) Matched nv as autoconfigured driver 2
[    11.561] (==) Matched vesa as autoconfigured driver 3
[    11.561] (==) Matched fbdev as autoconfigured driver 4
[    11.561] (==) Assigned the driver to the xf86ConfigLayout
[    11.562] (II) LoadModule: "nvidia"
[    11.562] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    11.632] (II) Module nvidia: vendor="NVIDIA Corporation"
[    11.632]     compiled for 4.0.2, module version = 1.0.0
[    11.632]     Module class: X.Org Video Driver
[    11.651] (II) LoadModule: "nouveau"
[    11.652] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    11.664] (II) Module nouveau: vendor="X.Org Foundation"
[    11.664]     compiled for 1.10.1, module version = 0.0.16
[    11.664]     Module class: X.Org Video Driver
[    11.664]     ABI class: X.Org Video Driver, version 10.0
[    11.665] (II) LoadModule: "nv"
[    11.677] (WW) Warning, couldn't open module nv
[    11.677] (II) UnloadModule: "nv"
[    11.677] (II) Unloading nv
[    11.677] (EE) Failed to load module "nv" (module does not exist, 0)
[    11.677] (II) LoadModule: "vesa"
[    11.677] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.690] (II) Module vesa: vendor="X.Org Foundation"
[    11.690]     compiled for 1.10.2, module version = 2.3.0
[    11.690]     Module class: X.Org Video Driver
[    11.690]     ABI class: X.Org Video Driver, version 10.0
[    11.690] (II) LoadModule: "fbdev"
[    11.690] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.701] (II) Module fbdev: vendor="X.Org Foundation"
[    11.701]     compiled for 1.10.0, module version = 0.4.2
[    11.701]     ABI class: X.Org Video Driver, version 10.0
[    11.702] (II) NVIDIA dlloader X Driver  96.43.20  Sun Jul 17 23:35:47 PDT 2011
[    11.703] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    11.703] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[    11.703] (II) NOUVEAU driver for NVIDIA chipset families :
[    11.703]     RIVA TNT        (NV04)
[    11.703]     RIVA TNT2       (NV05)
[    11.703]     GeForce 256     (NV10)
[    11.703]     GeForce 2       (NV11, NV15)
[    11.703]     GeForce 4MX     (NV17, NV18)
[    11.703]     GeForce 3       (NV20)
[    11.703]     GeForce 4Ti     (NV25, NV28)
[    11.703]     GeForce FX      (NV3x)
[    11.703]     GeForce 6       (NV4x)
[    11.703]     GeForce 7       (G7x)
[    11.704]     GeForce 8       (G8x)
[    11.704]     GeForce GTX 200 (NVA0)
[    11.704]     GeForce GTX 400 (NVC0)
[    11.704] (II) VESA: driver for VESA chipsets: vesa
[    11.704] (II) FBDEV: driver for framebuffer: fbdev
[    11.704] (++) using VT number 7

[    11.704] (II) Loading sub module "fb"
[    11.704] (II) LoadModule: "fb"
[    11.704] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.704] (II) Module fb: vendor="X.Org Foundation"
[    11.704]     compiled for 1.10.4, module version = 1.0.0
[    11.704]     ABI class: X.Org ANSI C Emulation, version 0.4
[    11.705] (II) Loading sub module "ramdac"
[    11.705] (II) LoadModule: "ramdac"
[    11.705] (II) Module "ramdac" already built-in
[    11.728] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    11.728] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.728] (WW) Falling back to old probe method for vesa
[    11.728] (WW) Falling back to old probe method for fbdev
[    11.728] (II) Loading sub module "fbdevhw"
[    11.728] (II) LoadModule: "fbdevhw"
[    11.729] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    11.743] (II) Module fbdevhw: vendor="X.Org Foundation"
[    11.743]     compiled for 1.10.4, module version = 0.0.2
[    11.743]     ABI class: X.Org Video Driver, version 10.0
[    11.744] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    11.744] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    11.744] (==) NVIDIA(0): RGB weight 888
[    11.744] (==) NVIDIA(0): Default visual is TrueColor
[    11.744] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    11.744] (**) NVIDIA(0): Enabling RENDER acceleration
[    11.744] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    11.744] (II) NVIDIA(0):     enabled.
[    12.035] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:3:1:0. 
[    12.035] (EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
[    12.035] (EE) NVIDIA(0):     additional information.
[    12.035] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
[    12.035] (EE) NVIDIA(0):  *** Aborting ***
[    12.035] (II) UnloadModule: "nvidia"
[    12.035] (II) Unloading nvidia
[    12.035] (II) UnloadModule: "fb"
[    12.035] (II) Unloading fb
[    12.035] (EE) Screen(s) found, but none have a usable configuration.
[    12.035] 
Fatal server error:
[    12.035] no screens found
[    12.035] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org]("http://wiki.x.org/")
 for help. 
[    12.035] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    12.035] 
[    12.128]  ddxSigGiveUp: Closing log
```

---

### Post by Helkaluin on 2012-06-15
Have you updated your initramfs after amending  your modprobe blacklist?

If all else fails, try using the kernel boot line approach: add "nouveau.blacklist=true".  (The file you want is /etc/default/grub)

---

### Post by dodo3773 on 2012-06-15
Have you tried creating an xorg.conf file yourself with:
```

sudo nvidia-xconfig

```
and then rebooting? If it doesn't work you can always just delete it ( /etc/X11/xorg.conf ). 

Maybe check if you have one and then back it up first:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

Then if it does not work you can restore it the same way you created it:
```

sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```


My guess is that there is some sort of catch all in "/usr/share/X11/xorg.conf.d" that is loading those modules. I am not sure but that is where I would probably start.

---

### Post by deadpixel23 on 2012-06-15
Thanks for the replies, unfortunately I've tried all of those methods, error remains. May just have to give up on Ubuntu at least until I get a newer card.

---

### Post by idoitprone on 2012-06-15
```
lspci -nnk
```

checkin the driver that is loaded

---

### Post by dodo3773 on 2012-06-15
Have you tried dropping into a tty and unloading the problem module and modprobing nvidia to see if you run into any errors? That would be the next logical step for me.

---


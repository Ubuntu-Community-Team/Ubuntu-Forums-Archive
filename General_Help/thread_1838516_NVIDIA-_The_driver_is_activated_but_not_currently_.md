---
title: "NVIDIA- The driver is activated but not currently in use?"
date: 2011-09-03
forum: General Help
---

### Post by Bryan334 on 2011-09-03
I know this topic has been posted before but, I'm a beginner at Linux and I can't seem to find a clear answer. I have an NVIDIA graphics card and I can't get the driver to install. I go to system/administration/Additional Drivers, and I have the option to install 3 drivers, "NVIDIA accelerated graphics driver (version 173)", "NVIDIA  accelerated graphics driver (version current) [Recommended]", and an experimental driver. When I "activate" one of the drivers I follow instructions and restart the pc. I get the message, "The driver is activated but not currently in use."
   I found a threads that mention this, <http://askubuntu.com/questions/37084/nvidia-driver-activated-but-currently-not-in-use>, and I've tried searching on line but can't find any clear solutions. Please, if the solution involves using the terminal, take it step by step and be descriptive. Thanks :)

---

### Post by dave01945 on 2011-09-03
mine says the same thing but i am using it i believe it is a bug

if you type in a terminal

```
lshw -C display
```

it should show your display properties and under configuration it should say

**driver=nvidia**

if it does then you are using it


here is mine for reference

```
  *-display               
       description: VGA compatible controller
       product: C77 [GeForce 8200M G]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       **configuration: driver=nvidia latency=0**
       resources: irq:19 memory:c1000000-c1ffffff memory:d0000000-dfffffff memory:c4000000-c5ffffff ioport:4000(size=128) memory:c6000000-c601ffff
```

---

### Post by 23dornot23d on 2011-09-03
Go to Menu Administration Log-File viewer ....

There is a file called Xorg.0.log

Copy and paste the contents ...... here

Here is mine as an example ...... if nouveau appears all over yours ....... it may be that the
nouveau driver is taking over everything ........ usually blacklisting it would stop it doing this

But if you post your log ...... someone ...... may be able to help you ...... should it be
something else ......

```

[    34.285] 
X.Org X Server 1.10.2.902 (1.10.3 RC 2)
Release Date: 2011-07-01
[    34.334] X Protocol Version 11, Revision 0
[    34.334] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    34.334] Current Operating System: Linux keith-Aspire-7730ZG 3.0.0-9-generic #15-Ubuntu SMP Tue Aug 30 14:57:16 UTC 2011 x86_64
[    34.334] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-9-generic root=UUID=a03f92d2-bf55-469a-a86e-df81e1a06679 ro quiet splash vt.handoff=7
[    34.334] Build Date: 13 July 2011  12:29:54AM
[    34.334] xorg-server 2:1.10.2.902-1ubuntu3 (For technical support please see http://www.ubuntu.com/support) 
[    34.334] Current version of pixman: 0.22.2
[    34.334]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    34.334] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    34.334] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep  3 20:50:09 2011
[    34.334] (==) Using config file: "/etc/X11/xorg.conf"
[    34.334] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    34.334] (==) ServerLayout "Layout0"
[    34.334] (**) |-->Screen "Screen0" (0)
[    34.334] (**) |   |-->Monitor "Monitor0"
[    34.335] (**) |   |-->Device "Device0"
[    34.335] (**) |-->Input Device "Keyboard0"
[    34.335] (**) |-->Input Device "Mouse0"
[    34.335] (**) Option "Xinerama" "0"
[    34.335] (==) Automatically adding devices
[    34.335] (==) Automatically enabling devices
[    34.335] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    34.335]     Entry deleted from font path.
[    34.335] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    34.335]     Entry deleted from font path.
[    34.335] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    34.335]     Entry deleted from font path.
[    34.335] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    34.335]     Entry deleted from font path.
[    34.335] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    34.335]     Entry deleted from font path.
[    34.335] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    34.335] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    34.335] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    34.335] (WW) Disabling Keyboard0
[    34.335] (WW) Disabling Mouse0
[    34.335] (II) Loader magic: 0x7e0220
[    34.335] (II) Module ABI versions:
[    34.335]     X.Org ANSI C Emulation: 0.4
[    34.335]     X.Org Video Driver: 10.0
[    34.335]     X.Org XInput driver : 12.3
[    34.335]     X.Org Server Extension : 5.0
[    34.336] (--) PCI:*(0:1:0:0) 10de:06e9:1025:0142 rev 161, Mem @ 0xce000000/16777216, 0xd0000000/268435456, 0xcc000000/33554432, I/O @ 0x00002000/128
[    34.336] (II) Open ACPI successful (/var/run/acpid.socket)
[    34.336] (II) LoadModule: "extmod"
[    34.353] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    34.353] (II) Module extmod: vendor="X.Org Foundation"
[    34.353]     compiled for 1.10.2.902, module version = 1.0.0
[    34.353]     Module class: X.Org Server Extension
[    34.353]     ABI class: X.Org Server Extension, version 5.0
[    34.353] (II) Loading extension MIT-SCREEN-SAVER
[    34.353] (II) Loading extension XFree86-VidModeExtension
[    34.353] (II) Loading extension XFree86-DGA
[    34.353] (II) Loading extension DPMS
[    34.353] (II) Loading extension XVideo
[    34.353] (II) Loading extension XVideo-MotionCompensation
[    34.353] (II) Loading extension X-Resource
[    34.354] (II) LoadModule: "dbe"
[    34.354] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    34.354] (II) Module dbe: vendor="X.Org Foundation"
[    34.354]     compiled for 1.10.2.902, module version = 1.0.0
[    34.354]     Module class: X.Org Server Extension
[    34.354]     ABI class: X.Org Server Extension, version 5.0
[    34.354] (II) Loading extension DOUBLE-BUFFER
[    34.354] (II) LoadModule: "glx"
[    34.354] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    34.371] (II) Module glx: vendor="NVIDIA Corporation"
[    34.371]     compiled for 4.0.2, module version = 1.0.0
[    34.371]     Module class: X.Org Server Extension
[    34.371] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:12:07 PDT 2011
[    34.371] (II) Loading extension GLX
[    34.371] (II) LoadModule: "record"
[    34.371] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    34.372] (II) Module record: vendor="X.Org Foundation"
[    34.372]     compiled for 1.10.2.902, module version = 1.13.0
[    34.372]     Module class: X.Org Server Extension
[    34.372]     ABI class: X.Org Server Extension, version 5.0
[    34.372] (II) Loading extension RECORD
[    34.372] (II) LoadModule: "dri"
[    34.372] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    34.372] (II) Module dri: vendor="X.Org Foundation"
[    34.372]     compiled for 1.10.2.902, module version = 1.0.0
[    34.372]     ABI class: X.Org Server Extension, version 5.0
[    34.372] (II) Loading extension XFree86-DRI
[    34.372] (II) LoadModule: "dri2"
[    34.373] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    34.373] (II) Module dri2: vendor="X.Org Foundation"
[    34.373]     compiled for 1.10.2.902, module version = 1.2.0
[    34.373]     ABI class: X.Org Server Extension, version 5.0
[    34.373] (II) Loading extension DRI2
[    34.373] (II) LoadModule: "nvidia"
[    34.373] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    34.373] (II) Module nvidia: vendor="NVIDIA Corporation"
[    34.373]     compiled for 4.0.2, module version = 1.0.0
[    34.374]     Module class: X.Org Video Driver
[    34.374] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:55:26 PDT 2011
[    34.374] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    34.374] (++) using VT number 8

[    34.377] (II) Loading sub module "fb"
[    34.377] (II) LoadModule: "fb"
[    34.378] (II) Loading /usr/lib/xorg/modules/libfb.so
[    34.378] (II) Module fb: vendor="X.Org Foundation"
[    34.378]     compiled for 1.10.2.902, module version = 1.0.0
[    34.378]     ABI class: X.Org ANSI C Emulation, version 0.4
[    34.378] (II) Loading sub module "wfb"
[    34.378] (II) LoadModule: "wfb"
[    34.378] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    34.378] (II) Module wfb: vendor="X.Org Foundation"
[    34.378]     compiled for 1.10.2.902, module version = 1.0.0
[    34.378]     ABI class: X.Org ANSI C Emulation, version 0.4
[    34.378] (II) Loading sub module "ramdac"
[    34.378] (II) LoadModule: "ramdac"
[    34.378] (II) Module "ramdac" already built-in
[    34.378] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    34.378] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    34.378] (II) Loading /usr/lib/xorg/modules/libfb.so
[    34.379] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    34.379] (==) NVIDIA(0): RGB weight 888
[    34.379] (==) NVIDIA(0): Default visual is TrueColor
[    34.379] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    34.379] (**) NVIDIA(0): Option "TwinView" "1"
[    34.379] (**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +1920+0, DFP-1: 1920x1080 +0+0"
[    34.379] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-1"
[    35.878] (II) NVIDIA(GPU-0): Display (PHILIPS 107E (CRT-0)) does not support NVIDIA 3D
[    35.878] (II) NVIDIA(GPU-0):     Vision stereo.

```

Here is mine too ... for the above thread ...... looks like we posted at the same time .... will leave you with it

```

root@keith-Aspire-7730ZG:/home/keithg# lshw -C display
  *-display               
       description: VGA compatible controller
       product: G98 [GeForce 9300M GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:ce000000-ceffffff memory:d0000000-dfffffff memory:cc000000-cdffffff ioport:2000(size=128)
root@keith-Aspire-7730ZG:/home/keithg# 


```

---

### Post by Bryan334 on 2011-09-03
Here is my Xorg.0.log you mentioned.. 
[PHP]
[    15.714] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    15.715] X Protocol Version 11, Revision 0
[    15.715] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    15.715] Current Operating System: Linux bryancm-Dell-DM051 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686
[    15.715] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=4474f6d3-84ba-4373-b021-56ce8ee9db15 ro quiet splash vt.handoff=7
[    15.715] Build Date: 11 August 2011  03:47:56PM
[    15.715] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[    15.715] Current version of pixman: 0.20.2
[    15.715]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    15.715] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.715] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep  3 13:55:36 2011
[    15.715] (==) Using config file: "/etc/X11/xorg.conf"
[    15.715] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.779] (==) No Layout section.  Using the first Screen section.
[    15.779] (==) No screen section available. Using defaults.
[    15.779] (**) |-->Screen "Default Screen Section" (0)
[    15.779] (**) |   |-->Monitor "<default monitor>"
[    15.779] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    15.779] (**) |   |-->Device "Default Device"
[    15.779] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    15.780] (==) Automatically adding devices
[    15.780] (==) Automatically enabling devices
[    15.780] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.780]     Entry deleted from font path.
[    15.780] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    15.780]     Entry deleted from font path.
[    15.780] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    15.780]     Entry deleted from font path.
[    15.780] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    15.780]     Entry deleted from font path.
[    15.780] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    15.780]     Entry deleted from font path.
[    15.780] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    15.780] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.780] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.780] (II) Loader magic: 0x81ffde0
[    15.780] (II) Module ABI versions:
[    15.780]     X.Org ANSI C Emulation: 0.4
[    15.780]     X.Org Video Driver: 10.0
[    15.780]     X.Org XInput driver : 12.3
[    15.780]     X.Org Server Extension : 5.0
[    15.781] (--) PCI:*(0:1:0:0) 10de:01d3:0000:0483 rev 161, Mem @ 0xed000000/16777216, 0xd0000000/268435456, 0xee000000/16777216, BIOS @ 0x????????/131072
[    15.782] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.782] (II) LoadModule: "extmod"
[    15.880] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.880] (II) Module extmod: vendor="X.Org Foundation"
[    15.880]     compiled for 1.10.1, module version = 1.0.0
[    15.880]     Module class: X.Org Server Extension
[    15.880]     ABI class: X.Org Server Extension, version 5.0
[    15.880] (II) Loading extension MIT-SCREEN-SAVER
[    15.880] (II) Loading extension XFree86-VidModeExtension
[    15.880] (II) Loading extension XFree86-DGA
[    15.880] (II) Loading extension DPMS
[    15.880] (II) Loading extension XVideo
[    15.881] (II) Loading extension XVideo-MotionCompensation
[    15.881] (II) Loading extension X-Resource
[    15.881] (II) LoadModule: "dbe"
[    15.881] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.881] (II) Module dbe: vendor="X.Org Foundation"
[    15.881]     compiled for 1.10.1, module version = 1.0.0
[    15.881]     Module class: X.Org Server Extension
[    15.881]     ABI class: X.Org Server Extension, version 5.0
[    15.881] (II) Loading extension DOUBLE-BUFFER
[    15.881] (II) LoadModule: "glx"
[    15.881] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    17.844] (II) Module glx: vendor="NVIDIA Corporation"
[    17.844]     compiled for 4.0.2, module version = 1.0.0
[    17.844]     Module class: X.Org Server Extension
[    17.844] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    17.844] (II) Loading extension GLX
[    17.844] (II) LoadModule: "record"
[    17.845] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.845] (II) Module record: vendor="X.Org Foundation"
[    17.845]     compiled for 1.10.1, module version = 1.13.0
[    17.845]     Module class: X.Org Server Extension
[    17.845]     ABI class: X.Org Server Extension, version 5.0
[    17.845] (II) Loading extension RECORD
[    17.845] (II) LoadModule: "dri"
[    17.846] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.846] (II) Module dri: vendor="X.Org Foundation"
[    17.846]     compiled for 1.10.1, module version = 1.0.0
[    17.846]     ABI class: X.Org Server Extension, version 5.0
[    17.846] (II) Loading extension XFree86-DRI
[    17.846] (II) LoadModule: "dri2"
[    17.847] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.847] (II) Module dri2: vendor="X.Org Foundation"
[    17.847]     compiled for 1.10.1, module version = 1.2.0
[    17.847]     ABI class: X.Org Server Extension, version 5.0
[    17.847] (II) Loading extension DRI2
[    17.847] (==) Matched nvidia as autoconfigured driver 0
[    17.847] (==) Matched nouveau as autoconfigured driver 1
[    17.847] (==) Matched nv as autoconfigured driver 2
[    17.847] (==) Matched vesa as autoconfigured driver 3
[    17.847] (==) Matched fbdev as autoconfigured driver 4
[    17.847] (==) Assigned the driver to the xf86ConfigLayout
[    17.847] (II) LoadModule: "nvidia"
[    17.847] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    17.898] (II) Module nvidia: vendor="NVIDIA Corporation"
[    17.898]     compiled for 4.0.2, module version = 1.0.0
[    17.898]     Module class: X.Org Video Driver
[    17.923] (II) LoadModule: "nouveau"
[    17.934] (WW) Warning, couldn't open module nouveau
[    17.934] (II) UnloadModule: "nouveau"
[    17.934] (II) Unloading nouveau
[    17.934] (EE) Failed to load module "nouveau" (module does not exist, 0)
[    17.934] (II) LoadModule: "nv"
[    17.935] (WW) Warning, couldn't open module nv
[    17.935] (II) UnloadModule: "nv"
[    17.935] (II) Unloading nv
[    17.935] (EE) Failed to load module "nv" (module does not exist, 0)
[    17.935] (II) LoadModule: "vesa"
[    17.935] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.935] (II) Module vesa: vendor="X.Org Foundation"
[    17.935]     compiled for 1.10.0, module version = 2.3.0
[    17.935]     Module class: X.Org Video Driver
[    17.935]     ABI class: X.Org Video Driver, version 10.0
[    17.935] (II) LoadModule: "fbdev"
[    17.936] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.936] (II) Module fbdev: vendor="X.Org Foundation"
[    17.936]     compiled for 1.10.0, module version = 0.4.2
[    17.936]     ABI class: X.Org Video Driver, version 10.0
[    17.936] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[    17.947] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    17.948] (II) VESA: driver for VESA chipsets: vesa
[    17.948] (II) FBDEV: driver for framebuffer: fbdev
[    17.948] (++) using VT number 7

[    17.955] (II) Loading sub module "fb"
[    17.955] (II) LoadModule: "fb"
[    17.956] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.956] (II) Module fb: vendor="X.Org Foundation"
[    17.956]     compiled for 1.10.1, module version = 1.0.0
[    17.956]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.956] (II) Loading sub module "wfb"
[    17.956] (II) LoadModule: "wfb"
[    17.957] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    17.964] (II) Module wfb: vendor="X.Org Foundation"
[    17.964]     compiled for 1.10.1, module version = 1.0.0
[    17.964]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.964] (II) Loading sub module "ramdac"
[    17.964] (II) LoadModule: "ramdac"
[    17.964] (II) Module "ramdac" already built-in
[    17.985] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    17.985] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    17.985] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.996] (WW) Falling back to old probe method for vesa
[    17.996] (WW) Falling back to old probe method for fbdev
[    17.996] (II) Loading sub module "fbdevhw"
[    17.996] (II) LoadModule: "fbdevhw"
[    17.997] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    17.997] (II) Module fbdevhw: vendor="X.Org Foundation"
[    17.997]     compiled for 1.10.1, module version = 0.0.2
[    17.997]     ABI class: X.Org Video Driver, version 10.0
[    17.997] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    17.997] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    17.997] (==) NVIDIA(0): RGB weight 888
[    17.997] (==) NVIDIA(0): Default visual is TrueColor
[    17.997] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    17.997] (**) NVIDIA(0): Option "NoLogo" "True"
[    19.376] (II) NVIDIA(GPU-0): Display (DELL E196FP (CRT-0)) does not support NVIDIA 3D
[    19.376] (II) NVIDIA(GPU-0):     Vision stereo.
[    19.379] (II) NVIDIA(0): NVIDIA GPU GeForce 7300 SE/7200 GS (G72) at PCI:1:0:0 (GPU-0)
[    19.379] (--) NVIDIA(0): Memory: 524288 kBytes
[    19.379] (--) NVIDIA(0): VideoBIOS: 05.72.22.81.00
[    19.379] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    19.379] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    19.379] (--) NVIDIA(0): Connected display device(s) on GeForce 7300 SE/7200 GS at
[    19.379] (--) NVIDIA(0):     PCI:1:0:0
[    19.379] (--) NVIDIA(0):     DELL E196FP (CRT-0)
[    19.379] (--) NVIDIA(0): DELL E196FP (CRT-0): 400.0 MHz maximum pixel clock
[    19.380] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    19.380] (==) NVIDIA(0): 
[    19.380] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    19.380] (==) NVIDIA(0):     will be used as the requested mode.
[    19.380] (==) NVIDIA(0): 
[    19.380] (II) NVIDIA(0): Validated modes:
[    19.380] (II) NVIDIA(0):     "nvidia-auto-select"
[    19.380] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
[    19.383] (--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
[    19.383] (--) NVIDIA(0):     option
[    19.383] (II) UnloadModule: "vesa"
[    19.383] (II) Unloading vesa
[    19.383] (II) UnloadModule: "fbdev"
[    19.383] (II) Unloading fbdev
[    19.383] (II) UnloadModule: "fbdevhw"
[    19.383] (II) Unloading fbdevhw
[    19.383] (--) Depth 24 pixmap format is 32 bpp
[    19.389] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    19.469] (II) Loading extension NV-GLX
[    19.514] (==) NVIDIA(0): Disabling shared memory pixmaps
[    19.514] (==) NVIDIA(0): Backing store disabled
[    19.514] (==) NVIDIA(0): Silken mouse enabled
[    19.514] (==) NVIDIA(0): DPMS enabled
[    19.514] (II) Loading extension NV-CONTROL
[    19.515] (II) Loading extension XINERAMA
[    19.515] (II) Loading sub module "dri2"
[    19.515] (II) LoadModule: "dri2"
[    19.515] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.515] (II) Module dri2: vendor="X.Org Foundation"
[    19.515]     compiled for 1.10.1, module version = 1.2.0
[    19.515]     ABI class: X.Org Server Extension, version 5.0
[    19.516] (II) NVIDIA(0): [DRI2] Setup complete
[    19.516] (==) RandR enabled
[    19.516] (II) Initializing built-in extension Generic Event Extension
[    19.516] (II) Initializing built-in extension SHAPE
[    19.516] (II) Initializing built-in extension MIT-SHM
[    19.516] (II) Initializing built-in extension XInputExtension
[    19.516] (II) Initializing built-in extension XTEST
[    19.516] (II) Initializing built-in extension BIG-REQUESTS
[    19.516] (II) Initializing built-in extension SYNC
[    19.516] (II) Initializing built-in extension XKEYBOARD
[    19.516] (II) Initializing built-in extension XC-MISC
[    19.516] (II) Initializing built-in extension SECURITY
[    19.516] (II) Initializing built-in extension XINERAMA
[    19.516] (II) Initializing built-in extension XFIXES
[    19.516] (II) Initializing built-in extension RENDER
[    19.516] (II) Initializing built-in extension RANDR
[    19.516] (II) Initializing built-in extension COMPOSITE
[    19.516] (II) Initializing built-in extension DAMAGE
[    19.516] (II) Initializing built-in extension GESTURE
[    19.520] (II) Initializing extension GLX
[    19.554] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.569] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    19.570] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.570] (II) LoadModule: "evdev"
[    19.570] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.571] (II) Module evdev: vendor="X.Org Foundation"
[    19.571]     compiled for 1.10.0.902, module version = 2.6.0
[    19.571]     Module class: X.Org XInput Driver
[    19.571]     ABI class: X.Org XInput driver, version 12.3
[    19.571] (II) Using input driver 'evdev' for 'Power Button'
[    19.571] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.571] (**) Power Button: always reports core events
[    19.571] (**) Power Button: Device: "/dev/input/event1"
[    19.571] (--) Power Button: Found keys
[    19.571] (II) Power Button: Configuring as keyboard
[    19.571] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    19.571] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.571] (**) Option "xkb_rules" "evdev"
[    19.571] (**) Option "xkb_model" "pc105"
[    19.571] (**) Option "xkb_layout" "us"
[    19.574] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.574] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.574] (II) Using input driver 'evdev' for 'Power Button'
[    19.574] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.574] (**) Power Button: always reports core events
[    19.574] (**) Power Button: Device: "/dev/input/event0"
[    19.574] (--) Power Button: Found keys
[    19.574] (II) Power Button: Configuring as keyboard
[    19.574] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    19.574] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.574] (**) Option "xkb_rules" "evdev"
[    19.574] (**) Option "xkb_model" "pc105"
[    19.574] (**) Option "xkb_layout" "us"
[    19.577] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event10)
[    19.577] (II) No input driver/identifier specified (ignoring)
[    19.577] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event11)
[    19.577] (II) No input driver/identifier specified (ignoring)
[    19.578] (II) config/udev: Adding input device HDA Intel Line In at Ext Rear Jack (/dev/input/event5)
[    19.578] (II) No input driver/identifier specified (ignoring)
[    19.578] (II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event6)
[    19.578] (II) No input driver/identifier specified (ignoring)
[    19.579] (II) config/udev: Adding input device HDA Intel Mic at Ext Rear Jack (/dev/input/event7)
[    19.579] (II) No input driver/identifier specified (ignoring)
[    19.579] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event8)
[    19.579] (II) No input driver/identifier specified (ignoring)
[    19.580] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event9)
[    19.580] (II) No input driver/identifier specified (ignoring)
[    19.582] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event2)
[    19.582] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    19.582] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    19.582] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.582] (**) USB Optical Mouse: always reports core events
[    19.582] (**) USB Optical Mouse: Device: "/dev/input/event2"
[    19.582] (--) USB Optical Mouse: Found 3 mouse buttons
[    19.582] (--) USB Optical Mouse: Found scroll wheel(s)
[    19.582] (--) USB Optical Mouse: Found relative axes
[    19.582] (--) USB Optical Mouse: Found x and y relative axes
[    19.582] (II) USB Optical Mouse: Configuring as mouse
[    19.582] (II) USB Optical Mouse: Adding scrollwheel support
[    19.582] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    19.582] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.582] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input2/event2"
[    19.582] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[    19.583] (II) USB Optical Mouse: initialized for relative axes.
[    19.583] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    19.583] (**) USB Optical Mouse: (accel) acceleration profile 0
[    19.583] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    19.583] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    19.583] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    19.583] (II) No input driver/identifier specified (ignoring)
[    19.585] (II) config/udev: Adding input device Saitek AV8R Joystick (/dev/input/event3)
[    19.585] (II) No input driver/identifier specified (ignoring)
[    19.585] (II) config/udev: Adding input device Saitek AV8R Joystick (/dev/input/js0)
[    19.585] (II) No input driver/identifier specified (ignoring)
[    19.586] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event4)
[    19.586] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    19.586] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard'
[    19.586] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.586] (**) Dell Dell USB Keyboard: always reports core events
[    19.586] (**) Dell Dell USB Keyboard: Device: "/dev/input/event4"
[    19.586] (--) Dell Dell USB Keyboard: Found keys
[    19.586] (II) Dell Dell USB Keyboard: Configuring as keyboard
[    19.587] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input4/event4"
[    19.587] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
[    19.587] (**) Option "xkb_rules" "evdev"
[    19.587] (**) Option "xkb_model" "pc105"
[    19.587] (**) Option "xkb_layout" "us"
[  1327.580] (II) NVIDIA(0): Setting mode "1024x768"
[  1364.484] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[/PHP]
Any help?

---

### Post by dave01945 on 2011-09-03
it looks like you are using the nvidia drivers i wouldn't worry about it the message is wrong

---

### Post by 23dornot23d on 2011-09-03
Looks as if its setup ok

also if you want - just to be sure it is working ok ....

type in a terminal

**glxinfo**

and if you have nvidia-settings installed ......

**nvidia-settings**

let me know what you see ,,,,,

[IMG]http://img534.imageshack.us/img534/6554/nvidiaxs.jpg[/IMG]

you should see something similar to the above ....

If you do see similar to above it is in use ..... and is set up ...... to check further try using k3dsurf ...... it uses a 3D window
and is a small application that will demonstrate it is working ok .

---

### Post by Bryan334 on 2011-09-03
Dave, I got this in the terminal after I put in the command you said..
[PHP]
bryancm@bryancm-Dell-DM051:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display               [D^[[D
       description: VGA compatible controller
       product: G72 [GeForce 7300 SE/7200 GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:ed000000-edffffff memory:d0000000-dfffffff memory:ee000000-eeffffff memory:efe00000-efe1ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
bryancm@bryancm-Dell-DM051:~$ [/PHP]So I guess it most likely is a successful install.

---

### Post by Bryan334 on 2011-09-03
> **23dornot23d said:**
> Looks as if its setup ok

also if you want - just to be sure it is working ok ....

type in a terminal

**glxinfo**

and if you have nvidia-settings installed ......

**nvidia-settings**

let me know what you see ,,,,,


Apparently I don't have "glxinfo", but when I put in "nvidia-settings" the program opened like in the picture.

---

### Post by dave01945 on 2011-09-03
yeah that looks good to me mine also says that it is activated but not in use it's that message that is wrong not the install 

all is good

---

### Post by 23dornot23d on 2011-09-03
Yep alls well your all set up ......  :)

---

### Post by Bryan334 on 2011-09-03
Okay, thanks for all the help. Have a good night or day, wherever you are. :)

---


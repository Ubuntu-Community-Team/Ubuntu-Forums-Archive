---
title: "Upgraded to 12.04 can only use Ubuntu2D"
date: 2012-04-28
forum: General Help
---

### Post by Spc 4 on 2012-04-28
I just upgraded to 12.04 64bit from 11.01 64bit. After I restarted my computer my screen was blank, I had a cursor, and icons on my desktop started blinking off and on, and blank screen no boarders or Unity. A box popped up that said "compiz crashed with SIGSEGV" "Do you want to send an error report?' I sent the bug report, logged out. I logged back in with Ubuntu2D, works fine. How can fix Ubuntu compiz when im logged in ubuntu2D? Is there a way to re-upgrade and try again? Am I stuck with Ubuntu2D?

---

### Post by Splashmania on 2012-04-28
Just like me, and i've tried a clean install with the same results.

---

### Post by its_jon on 2012-04-28
Exactly the same problem. I also had to do a fresh install after the upgrade showed exactly the same symptoms before refusing to boot a second time.
(all Home files intact)

I tried reinstalling compiz gnome UI and the alternitive Nvidea driver... still not working

Both unity 2d and gnome classic (no fx) appear to work

KI am also getting a randon '12.04' internal failure message although I have not seen it for a while now.

---

### Post by K4NEB on 2012-04-28
same here just upgraded to 12.04 32 bit and can only use 2D :(

same message compiz crashed

any fixy wixys for this yet?

i was just about to try a fresh install but now youve said its the same i dont hink ill bother untill this problemo is fixed.

i shall carry on searching

---

### Post by K4NEB on 2012-04-28
found this in another post it worked for me ):P

Sorry your having problems, This is a know bug with Nvidia Drivers.

The solution for now is to uninstall the Nvidia propriety Drivers and it  will work ok the Nvidia Drivers are causing Compiz to crash.

here's how to do it:

boot up to log in screen  click on the little ubuntu logo up right corner of log in box, click ubuntu 2d and login.

Now once you have the 2d desktop up go to system menu Additonal Drivers  and uninstall Nvidia Drivers. Then reboot you should be good to go.

Cheers,
d :smile:

---

### Post by Splashmania on 2012-04-28
But this fix must be like nothing, the desktop will be to slow then i prefer stay in 2d and almost run fast

---

### Post by its_jon on 2012-04-28
Thanks !....

Both Gnome and Unity 3D now working :)


fixed it for me... although a bit slow... no doubt as the Nvidea driver is not in place..

but... that was the problem for me !

at least we know what the problem is now :)

---

### Post by Splashmania on 2012-04-29
I am reading what downgrade nvidia 295.33, will fix the problem until nvidia realease a fix, i gonna try

---

### Post by bogan on 2012-04-29
Hi! **All**,
From a tty Text Terminal [Ctrl_Alt+ F1 or F2]
Try```
sudo nvidia-installer --latest  # just checks what is installed and what is recomended [295.49]
sudo nvidia-installer -f  # this will un-install existing  driver and install 295.49
```Edit [Fri 4th April]:
There is a new nvidia driver version 295.49 available from nvidia downloads, I've tried it with GeForce 7650 GTS & GT520 cards and it works, for me.

So i have edited the code above.

NVNews says of version295.49:
Quote:
Please note: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs

Chao!, **bogan**.

---

### Post by kelvin spratt on 2012-04-29
Its a problem with jockey not removing the Nouveau driver as it starts at boot time manually removing does the trick you ma have a wobbly login screen but its not a big problem

---

### Post by Splashmania on 2012-04-29
its not working, the process is freez and is dont doing anything

---

### Post by Spc 4 on 2012-04-29
What is the consensus on this?
1.Even if I tried a fresh install of 12.04 I would Have the same problem?
2.If I uninstall Nvidia Drivers, that will fix the problem, but Ubuntu will run slower?

I all so found this, I am reluctant to try it because I don't know how to change it back if it does not work. [http://askubuntu.com/questions/125608/unity-3d-no-longer-works-after-installing-12-04](http://askubuntu.com/questions/125608/unity-3d-no-longer-works-after-installing-12-04)

---

### Post by Splashmania on 2012-04-29
Yeah that is what im trying, but i am doing it manually and im having problems with xorg.conf because the system dont cacht it well and start with the vesa drivers

---

### Post by Splashmania on 2012-04-29
But is not working i dont know why my nvdia wont start, only start with vesa

```
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    17.289] X Protocol Version 11, Revision 0
[    17.289] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    17.289] Current Operating System: Linux system 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64
[    17.289] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=2316b211-d6a7-4fa0-a61c-e49c0760c94a ro quiet splash vt.handoff=7
[    17.289] Build Date: 05 April 2012  04:32:37AM
[    17.289] xorg-server 2:1.11.4-0ubuntu10 (For technical support please see http://www.ubuntu.com/support) 
[    17.289] Current version of pixman: 0.24.4
[    17.289]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    17.289] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.289] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 30 03:21:35 2012
[    17.308] (==) Using config file: "/etc/X11/xorg.conf"
[    17.308] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.334] (==) ServerLayout "Layout0"
[    17.334] (**) |-->Screen "Screen0" (0)
[    17.334] (**) |   |-->Monitor "Monitor0"
[    17.353] (**) |   |-->Device "Device0"
[    17.356] (**) |-->Input Device "Keyboard0"
[    17.356] (**) |-->Input Device "Mouse0"
[    17.356] (**) Option "Xinerama" "0"
[    17.356] (==) Automatically adding devices
[    17.356] (==) Automatically enabling devices
[    17.369] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.369]     Entry deleted from font path.
[    17.369] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    17.369]     Entry deleted from font path.
[    17.369] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    17.369]     Entry deleted from font path.
[    17.380] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    17.380]     Entry deleted from font path.
[    17.380] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    17.380]     Entry deleted from font path.
[    17.380] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    17.380]     Entry deleted from font path.
[    17.380] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    17.380] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.380] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    17.380] (WW) Disabling Keyboard0
[    17.380] (WW) Disabling Mouse0
[    17.380] (II) Loader magic: 0x7f7fa56dfb00
[    17.380] (II) Module ABI versions:
[    17.380]     X.Org ANSI C Emulation: 0.4
[    17.380]     X.Org Video Driver: 11.0
[    17.380]     X.Org XInput driver : 16.0
[    17.380]     X.Org Server Extension : 6.0
[    17.381] (--) PCI:*(0:0:16:0) 10de:07e3:1043:82ae rev 162, Mem @ 0xed000000/16777216, 0xd0000000/268435456, 0xee000000/16777216, BIOS @ 0x????????/131072
[    17.381] (II) Open ACPI successful (/var/run/acpid.socket)
[    17.381] (II) LoadModule: "extmod"
[    17.434] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.445] (II) Module extmod: vendor="X.Org Foundation"
[    17.445]     compiled for 1.11.3, module version = 1.0.0
[    17.445]     Module class: X.Org Server Extension
[    17.445]     ABI class: X.Org Server Extension, version 6.0
[    17.445] (II) Loading extension MIT-SCREEN-SAVER
[    17.445] (II) Loading extension XFree86-VidModeExtension
[    17.445] (II) Loading extension XFree86-DGA
[    17.446] (II) Loading extension DPMS
[    17.446] (II) Loading extension XVideo
[    17.446] (II) Loading extension XVideo-MotionCompensation
[    17.446] (II) Loading extension X-Resource
[    17.446] (II) LoadModule: "dbe"
[    17.446] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.450] (II) Module dbe: vendor="X.Org Foundation"
[    17.450]     compiled for 1.11.3, module version = 1.0.0
[    17.450]     Module class: X.Org Server Extension
[    17.450]     ABI class: X.Org Server Extension, version 6.0
[    17.450] (II) Loading extension DOUBLE-BUFFER
[    17.450] (II) LoadModule: "glx"
[    17.450] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    18.902] (II) Module glx: vendor="NVIDIA Corporation"
[    18.917]     compiled for 4.0.2, module version = 1.0.0
[    18.917]     Module class: X.Org Server Extension
[    18.917] (II) NVIDIA GLX Module  295.33  Sat Mar 17 15:16:17 PDT 2012
[    18.917] (II) Loading extension GLX
[    18.917] (II) LoadModule: "record"
[    18.918] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.928] (II) Module record: vendor="X.Org Foundation"
[    18.928]     compiled for 1.11.3, module version = 1.13.0
[    18.928]     Module class: X.Org Server Extension
[    18.928]     ABI class: X.Org Server Extension, version 6.0
[    18.928] (II) Loading extension RECORD
[    18.928] (II) LoadModule: "dri"
[    18.928] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.933] (II) Module dri: vendor="X.Org Foundation"
[    18.933]     compiled for 1.11.3, module version = 1.0.0
[    18.933]     ABI class: X.Org Server Extension, version 6.0
[    18.933] (II) Loading extension XFree86-DRI
[    18.933] (II) LoadModule: "dri2"
[    18.934] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.934] (II) Module dri2: vendor="X.Org Foundation"
[    18.934]     compiled for 1.11.3, module version = 1.2.0
[    18.934]     ABI class: X.Org Server Extension, version 6.0
[    18.934] (II) Loading extension DRI2
[    18.934] (II) LoadModule: "nvidia"
[    18.934] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    19.007] (II) Module nvidia: vendor="NVIDIA Corporation"
[    19.015]     compiled for 4.0.2, module version = 1.0.0
[    19.015]     Module class: X.Org Video Driver
[    19.048] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    19.048] (EE) NVIDIA:     system's kernel log for additional error messages.
[    19.048] (II) UnloadModule: "nvidia"
[    19.048] (II) Unloading nvidia
[    19.048] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    19.048] (==) Matched nvidia as autoconfigured driver 0
[    19.048] (==) Matched nouveau as autoconfigured driver 1
[    19.048] (==) Matched nv as autoconfigured driver 2
[    19.048] (==) Matched vesa as autoconfigured driver 3
[    19.048] (==) Matched fbdev as autoconfigured driver 4
[    19.048] (==) Assigned the driver to the xf86ConfigLayout
[    19.049] (II) LoadModule: "nvidia"
[    19.049] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    19.049] (II) Module nvidia: vendor="NVIDIA Corporation"
[    19.049]     compiled for 4.0.2, module version = 1.0.0
[    19.049]     Module class: X.Org Video Driver
[    19.049] (II) UnloadModule: "nvidia"
[    19.049] (II) Unloading nvidia
[    19.049] (II) Failed to load module "nvidia" (already loaded, 32639)
[    19.049] (II) LoadModule: "nouveau"
[    19.074] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    19.094] (II) Module nouveau: vendor="X.Org Foundation"
[    19.094]     compiled for 1.11.3, module version = 0.0.16
[    19.094]     Module class: X.Org Video Driver
[    19.094]     ABI class: X.Org Video Driver, version 11.0
[    19.094] (II) LoadModule: "nv"
[    19.107] (WW) Warning, couldn't open module nv
[    19.107] (II) UnloadModule: "nv"
[    19.107] (II) Unloading nv
[    19.107] (EE) Failed to load module "nv" (module does not exist, 0)
[    19.107] (II) LoadModule: "vesa"
[    19.107] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.119] (II) Module vesa: vendor="X.Org Foundation"
[    19.119]     compiled for 1.11.3, module version = 2.3.0
[    19.119]     Module class: X.Org Video Driver
[    19.119]     ABI class: X.Org Video Driver, version 11.0
[    19.119] (II) LoadModule: "fbdev"
[    19.119] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.122] (II) Module fbdev: vendor="X.Org Foundation"
[    19.122]     compiled for 1.11.3, module version = 0.4.2
[    19.122]     ABI class: X.Org Video Driver, version 11.0
[    19.122] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[    19.122] (II) NOUVEAU driver for NVIDIA chipset families :
[    19.122]     RIVA TNT        (NV04)
[    19.122]     RIVA TNT2       (NV05)
[    19.122]     GeForce 256     (NV10)
[    19.122]     GeForce 2       (NV11, NV15)
[    19.122]     GeForce 4MX     (NV17, NV18)
[    19.122]     GeForce 3       (NV20)
[    19.122]     GeForce 4Ti     (NV25, NV28)
[    19.122]     GeForce FX      (NV3x)
[    19.122]     GeForce 6       (NV4x)
[    19.122]     GeForce 7       (G7x)
[    19.122]     GeForce 8       (G8x)
[    19.122]     GeForce GTX 200 (NVA0)
[    19.122]     GeForce GTX 400 (NVC0)
[    19.122] (II) VESA: driver for VESA chipsets: vesa
[    19.122] (II) FBDEV: driver for framebuffer: fbdev
[    19.122] (++) using VT number 7

[    19.122] drmOpenDevice: node name is /dev/dri/card0
[    19.129] [drm] failed to load kernel module "nouveau"
[    19.129] (EE) [drm] failed to open device
[    19.129] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.129] (WW) Falling back to old probe method for fbdev
[    19.129] (II) Loading sub module "fbdevhw"
[    19.129] (II) LoadModule: "fbdevhw"
[    19.129] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    19.152] (II) Module fbdevhw: vendor="X.Org Foundation"
[    19.152]     compiled for 1.11.3, module version = 0.0.2
[    19.152]     ABI class: X.Org Video Driver, version 11.0
[    19.152] (II) Loading sub module "vbe"
[    19.152] (II) LoadModule: "vbe"
[    19.152] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    19.157] (II) Module vbe: vendor="X.Org Foundation"
[    19.157]     compiled for 1.11.3, module version = 1.1.0
[    19.157]     ABI class: X.Org Video Driver, version 11.0
[    19.157] (II) Loading sub module "int10"
[    19.157] (II) LoadModule: "int10"
[    19.158] (II) Loading /usr/lib/xorg/modules/libint10.so
[    19.160] (II) Module int10: vendor="X.Org Foundation"
[    19.160]     compiled for 1.11.3, module version = 1.0.0
[    19.160]     ABI class: X.Org Video Driver, version 11.0
[    19.160] (II) VESA(0): initializing int10
[    19.160] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    19.164] (II) VESA(0): VESA BIOS detected
[    19.164] (II) VESA(0): VESA VBE Version 3.0
[    19.164] (II) VESA(0): VESA VBE Total Mem: 131072 kB
[    19.164] (II) VESA(0): VESA VBE OEM: NVIDIA
[    19.164] (II) VESA(0): VESA VBE OEM Software Rev: 5.115
[    19.164] (II) VESA(0): VESA VBE OEM Vendor: Build    071127.1 

[    19.164] (II) VESA(0): VESA VBE OEM Product: MCP73 - mcp73-81
[    19.164] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    19.184] (**) VESA(0): Depth 24, (--) framebuffer bpp 32
[    19.184] (==) VESA(0): RGB weight 888
[    19.184] (==) VESA(0): Default visual is TrueColor
[    19.184] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    19.184] (II) Loading sub module "ddc"
[    19.184] (II) LoadModule: "ddc"
[    19.184] (II) Module "ddc" already built-in
[    19.186] (II) VESA(0): VESA VBE DDC supported
[    19.186] (II) VESA(0): VESA VBE DDC Level none
[    19.186] (II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
[    19.187] (II) VESA(0): VESA VBE DDC read failed
[    19.188] (II) VESA(0): VESA VBE PanelID read failed
[    19.188] (II) VESA(0): Searching for matching VESA mode(s):
[    19.188] Mode: 100 (640x400)
[    19.188]     ModeAttributes: 0x39f
[    19.188]     WinAAttributes: 0x7
[    19.188]     WinBAttributes: 0x0
[    19.188]     WinGranularity: 64
[    19.188]     WinSize: 64
[    19.188]     WinASegment: 0xa000
[    19.188]     WinBSegment: 0x0
[    19.188]     WinFuncPtr: 0xc0009d3f
[    19.188]     BytesPerScanline: 640
etc..

[    19.214]     LinBlueMaskSize: 8
[    19.214]     LinBlueFieldPosition: 0
[    19.214]     LinRsvdMaskSize: 8
[    19.214]     LinRsvdFieldPosition: 24
[    19.214]     MaxPixelClock: 229500000
[    19.214] 
[    19.214] (II) VESA(0): Total Memory: 2048 64KB banks (131072kB)
[    19.214] (II) VESA(0): Monitor0: Using hsync range of 28.00-67.00 kHz
[    19.214] (II) VESA(0): Monitor0: Using vrefresh range of 50.00-75.00 Hz
[    19.214] (WW) VESA(0): Unable to estimate virtual size
[    19.214] (II) VESA(0): Not using built-in mode "2048x1536" (no mode of this name)
[    19.214] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[    19.214] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    19.214] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    19.214] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    19.214] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    19.214] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    19.214] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    19.214] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    19.214] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    19.214] (II) VESA(0): Monitor0: Using hsync range of 28.00-67.00 kHz
[    19.214] (II) VESA(0): Monitor0: Using vrefresh range of 50.00-75.00 Hz
[    19.214] (WW) VESA(0): Unable to estimate virtual size
[    19.433] (II) VESA(0): Not using built-in mode "2048x1536" (hsync out of range)
[    19.478] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[    19.478] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[    19.478] (--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
[    19.478] (**) VESA(0): *Built-in mode "1280x1024"
[    19.478] (**) VESA(0): *Built-in mode "1024x768"
[    19.478] (**) VESA(0): *Built-in mode "800x600"
[    19.478] (**) VESA(0): *Built-in mode "640x480"
[    19.478] (**) VESA(0): *Built-in mode "640x400"
[    19.478] (**) VESA(0): *Built-in mode "320x400"
[    19.478] (==) VESA(0): DPI set to (96, 96)
[    19.478] (II) VESA(0): Attempting to use 60Hz refresh for mode "1280x1024" (11b)
[    19.479] (II) VESA(0): Attempting to use 75Hz refresh for mode "1024x768" (118)
[    19.480] (II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (115)
[    19.481] (II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (112)
[    19.482] (**) VESA(0): Using "Shadow Framebuffer"
[    19.482] (II) Loading sub module "shadow"
[    19.482] (II) LoadModule: "shadow"
[    19.483] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    19.718] (II) Module shadow: vendor="X.Org Foundation"
[    19.718]     compiled for 1.11.3, module version = 1.1.0
[    19.718]     ABI class: X.Org ANSI C Emulation, version 0.4
[    19.718] (II) Loading sub module "fb"
[    19.718] (II) LoadModule: "fb"
[    19.719] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.735] (II) Module fb: vendor="X.Org Foundation"
[    19.735]     compiled for 1.11.3, module version = 1.0.0
[    19.735]     ABI class: X.Org ANSI C Emulation, version 0.4
[    19.735] (II) UnloadModule: "fbdev"
[    19.735] (II) Unloading fbdev
[    19.735] (II) UnloadModule: "fbdevhw"
[    19.735] (II) Unloading fbdevhw
[    19.735] (==) Depth 24 pixmap format is 32 bpp
[    19.735] (II) Loading sub module "int10"
[    19.735] (II) LoadModule: "int10"
[    19.736] (II) Loading /usr/lib/xorg/modules/libint10.so
[    19.736] (II) Module int10: vendor="X.Org Foundation"
[    19.736]     compiled for 1.11.3, module version = 1.0.0
[    19.736]     ABI class: X.Org Video Driver, version 11.0
[    19.736] (II) VESA(0): initializing int10
[    19.736] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    19.740] (II) VESA(0): VESA BIOS detected
[    19.740] (II) VESA(0): VESA VBE Version 3.0
[    19.740] (II) VESA(0): VESA VBE Total Mem: 131072 kB
[    19.740] (II) VESA(0): VESA VBE OEM: NVIDIA
[    19.740] (II) VESA(0): VESA VBE OEM Software Rev: 5.115
[    19.740] (II) VESA(0): VESA VBE OEM Vendor: Build    071127.1 

[    19.740] (II) VESA(0): VESA VBE OEM Product: MCP73 - mcp73-81
[    19.740] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    19.767] (II) VESA(0): virtual address = 0x7f7f94fc8000,
    physical address = 0xd0000000, size = 134217728
[    19.772] (II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)
[    19.822] (==) VESA(0): Default visual is TrueColor
[    19.830] (==) VESA(0): Backing store disabled
[    19.831] (**) VESA(0): DPMS enabled
[    19.831] (WW) VESA(0): Option "TwinView" is not used
[    19.831] (WW) VESA(0): Option "TwinViewXineramaInfoOrder" is not used
[    19.831] (WW) VESA(0): Option "metamodes" is not used
[    19.831] (==) RandR enabled
[    19.831] (II) Initializing built-in extension Generic Event Extension
[    19.831] (II) Initializing built-in extension SHAPE
[    19.831] (II) Initializing built-in extension MIT-SHM
[    19.831] (II) Initializing built-in extension XInputExtension
[    19.831] (II) Initializing built-in extension XTEST
[    19.831] (II) Initializing built-in extension BIG-REQUESTS
[    19.831] (II) Initializing built-in extension SYNC
[    19.831] (II) Initializing built-in extension XKEYBOARD
[    19.831] (II) Initializing built-in extension XC-MISC
[    19.831] (II) Initializing built-in extension SECURITY
[    19.831] (II) Initializing built-in extension XINERAMA
[    19.831] (II) Initializing built-in extension XFIXES
[    19.831] (II) Initializing built-in extension RENDER
[    19.831] (II) Initializing built-in extension RANDR
[    19.831] (II) Initializing built-in extension COMPOSITE
[    19.831] (II) Initializing built-in extension DAMAGE
[    19.848] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    19.971] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.979] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    19.979] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.979] (II) LoadModule: "evdev"
[    19.979] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.007] (II) Module evdev: vendor="X.Org Foundation"
[    20.007]     compiled for 1.11.3, module version = 2.7.0
[    20.007]     Module class: X.Org XInput Driver
[    20.007]     ABI class: X.Org XInput driver, version 16.0
[    20.007] (II) Using input driver 'evdev' for 'Power Button'
[    20.007] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.007] (**) Power Button: always reports core events
[    20.007] (**) evdev: Power Button: Device: "/dev/input/event1"
[    20.007] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.007] (--) evdev: Power Button: Found keys
[    20.007] (II) evdev: Power Button: Configuring as keyboard
[    20.007] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    20.007] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    20.007] (**) Option "xkb_rules" "evdev"
[    20.007] (**) Option "xkb_model" "pc105"
[    20.007] (**) Option "xkb_layout" "es"
[    20.009] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[    20.023] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    20.023] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.023] (II) Using input driver 'evdev' for 'Power Button'
[    20.023] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.023] (**) Power Button: always reports core events
[    20.023] (**) evdev: Power Button: Device: "/dev/input/event0"
[    20.023] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.023] (--) evdev: Power Button: Found keys
[    20.023] (II) evdev: Power Button: Configuring as keyboard
[    20.023] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    20.023] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    20.023] (**) Option "xkb_rules" "evdev"
[    20.023] (**) Option "xkb_model" "pc105"
[    20.023] (**) Option "xkb_layout" "es"
[    20.024] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    20.024] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    20.024] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    20.024] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.024] (**) AT Translated Set 2 keyboard: always reports core events
[    20.024] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    20.024] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    20.024] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    20.024] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    20.024] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    20.024] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 8)
[    20.024] (**) Option "xkb_rules" "evdev"
[    20.024] (**) Option "xkb_model" "pc105"
[    20.024] (**) Option "xkb_layout" "es"
[    20.025] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/event3)
[    20.025] (**) ImExPS/2 Generic Explorer Mouse: Applying InputClass "evdev pointer catchall"
[    20.025] (II) Using input driver 'evdev' for 'ImExPS/2 Generic Explorer Mouse'
[    20.025] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.025] (**) ImExPS/2 Generic Explorer Mouse: always reports core events
[    20.025] (**) evdev: ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event3"
[    20.025] (--) evdev: ImExPS/2 Generic Explorer Mouse: Vendor 0x2 Product 0x6
[    20.025] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
[    20.025] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
[    20.025] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found relative axes
[    20.025] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
[    20.025] (II) evdev: ImExPS/2 Generic Explorer Mouse: Configuring as mouse
[    20.025] (II) evdev: ImExPS/2 Generic Explorer Mouse: Adding scrollwheel support
[    20.025] (**) evdev: ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
[    20.025] (**) evdev: ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.025] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[    20.025] (II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE, id 9)
[    20.025] (II) evdev: ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
[    20.026] (**) ImExPS/2 Generic Explorer Mouse: (accel) keeping acceleration scheme 1
[    20.026] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration profile 0
[    20.026] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration factor: 2.000
[    20.026] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration threshold: 4
[    20.026] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/mouse0)
[    20.026] (II) No input driver specified, ignoring this device.
[    20.026] (II) This device may have been added with another device file.
[    46.658] (II) XKB: reuse xkmfile /var/lib/xkb/server-718511B28EE83035776F86B5B8BD8C9A5D1FC433.xkm



```

---

### Post by Splashmania on 2012-04-30
Ok i got it now, its working but i think unity3d charges too much to the cpu's, are alwais flipping when the dash is open

---

### Post by Spc 4 on 2012-04-30
In just going to keep my 2D until the drivers get updated.

---

### Post by Splashmania on 2012-04-30
Go for the 295.33 it dont work bad and 2d mode fly. just adjust the settings of the compiz manager to put it right with your machine and thats it, the thing what more cpu get is the back blurr of the dash

---

### Post by Joanllm on 2012-04-30
I have the same problem with a GeForce 7000M will not let me enter Unity 3D since I left the screen and black and only see the mouse on the screen, whereas the 2D is perfect mind, I hope that they get a fix for this problem ...

---

### Post by Spc 4 on 2012-04-30
> **Splashmania said:**
> Go for the 295.33 it dont work bad and 2d mode fly. just adjust the settings of the compiz manager to put it right with your machine and thats it, the thing what more cpu get is the back blurr of the dash Thank you Splash, but I am a bit weary of monkeying around with to much. I always end up breaking something and doing a fresh install.

---

### Post by bogan on 2012-05-03
Hi!, All,

There is a new nvidia driver version 295.49 available from nvidia  downloads, I've tried it with a GeForce 7650 GTS card and it works. You  can not install it with 'sudo nvidia-installer -f', as that still  installs 295.33. [But see Edit note below]

EDIT: Noon Friday May 4th; ```
nvidia-installer --latest 
``` now  returns: v295.49 and     ```
nvidia-installer -f 
``` will install  295.49 after un-installing the previous version.

 NVNews says of version295.49:> **Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**Chao!, bogan

---

### Post by bogan on 2012-05-04
Hi!,** All**.

[COLOR=Blue]There is a new nvidia driver version 295.49 available [/COLOR]from nvidia downloads, See Edit in Post #20.  This Link is for the 32 bit version, check you get the correct one.
[http://www.nvidia.co.uk/object/linux-display-ia32-295.49-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.49-driver-uk.html)
[B]
bogan.[/B]

---

### Post by bogan on 2012-05-04
Hi!, **All**,
Deleted, duplicated!
 [COLOR=Blue][/COLOR]**bogan**.

---

### Post by bogan on 2012-05-04
Hi!, **All**,

 [COLOR=Blue]There is a new driver, 295.49 available from nvidia[/COLOR] downloads
 [http://www.nvidia.co.uk/object/linux...driver-uk.html]("http://www.nvidia.co.uk/object/linux-display-ia32-295.49-driver-uk.html")
This Link is for the 32 bit version, check you get the correct one. See the Edit note in Post #9.

Chao!, **bogan**.

---

### Post by pjcdawkins on 2012-05-09
Thanks to the advice in this thread, I now finally have Ubuntu 12.04 / Unity 3D working on my single nVidia graphics card connected to two screens (DVI & VGA), by using TwinView as opposed to Xinerama (and the nvidia-current driver).

---

### Post by bogan on 2012-05-17
Hi!,** All**.

[COLOR=Blue]There is a new nvidia driver version 295.53 available [/COLOR]from nvidia downloads.  This Link is for the 32 bit version, check you get the correct one.
[http://www.nvidia.co.uk/object/linux...driver-uk.html]("http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html")

[COLOR=RoyalBlue]**Edit: Updated Thursday May 17th; **[/COLOR]     

      	Code:
 	nvidia-installer --latest 
 now returns: v295.53 and the currently installed version, without altering anything.
     

      	Code:
 	nvidia-installer -f 
 will install 295.53 after un-installing the previous version.

NVNews says of version 295.53:
QUOTE:
**Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**,
 [GeForce4]("http://viglink.pgpartner.com/rd.php?r=10313&m=878281881&q=o&priceret=87.73&pg=%7E%7E3&k=2b6229593608c3c1fb499d0ca9880634&source=feed&url=http%3A%2F%2Fmicropartsusa%2Ecom%2F31p6953%2Dibm%2Dnvidia%2Dgeforce4%2Dmx440%2D64mb%2Dagp8x%2Datx%2Dgraphics%2Dcard%2Dw%2Do%2Dcable%2Dnew%2Dbulk%2Din%2Dstock%2Ehtml&st=feed&mt=%7E%7E%7E%7E%7E%7E%7E%7En%7E%7E%7E") and older GPUs are supported through the **96.43.xx** and **71.86.xx** [NVIDIA]("http://www.nvidia.com/") legacy graphics drivers.
 GeForce FX GPUs are supported through the **173.14.xx** NVIDIA legacy graphics drivers.

[B]
bogan.[/B]

---


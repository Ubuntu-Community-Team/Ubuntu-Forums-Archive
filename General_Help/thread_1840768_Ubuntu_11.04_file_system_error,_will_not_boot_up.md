---
title: "Ubuntu 11.04 file system error, will not boot up"
date: 2011-09-08
forum: General Help
---

### Post by suang on 2011-09-08
I locked my computer screen by pressing Ctrl Alt U, the screen went black, my parent thought it has shut down, so they turn off the stabilizer which shut down the computer.
My ubuntu 11.04 still running Firefox at that time.
I turned it on and run in recovery console, typing sudo fsck -t vfat /dev/sda1
It said file system error, fix(y)? I pressed y
But the errors keep coming up and i finally gave up on pressing yes button. Now, the computer will not boot anymore, the screen goes black with cursor blinking on top.
I tried search for solution in Google, I found one that asks to type sudo gedit /etc/default/grub
I run the command from Ubuntu live usb flash disk.
Then I typed GRUB_GFXPAYLOAD_LINUX=text at the bottom of the file. After saved, then sudo update-grub but cannot update grub, error again.
Please help me...........Thanks alot. ^_^

---

### Post by Quackers on 2011-09-08
Why vfat in that first command you tried?

I'm not sure if that will have done some damage or not, assuming that your file system was ext3 or ext4 rather than vfat.
Have a look at this thread and in particular post #3 and give that a try.

[http://ubuntuforums.org/showthread.php?t=1839932](http://ubuntuforums.org/showthread.php?t=1839932)

---

### Post by suang on 2011-09-08
I tried the sudo fsck -t vfat /dev/sda1 just because i found it on the internet. i don't know what it means.
Just now, i tried sudo mount/dev/sda1 /mnt
then sudo e2fsck -fvy /mnt
Error: the superblock could not read or does not describe a correct ext2 filesystem
sudo fsck.ext3 -f /dev/sda1
Error: missing in directory inode 402385
sudo fsck /dev/sda1 -p
Error:inconsistency, try without -p
Oh my God, looks like everything does not work here.
Before this problem, my screen has been blank before, then i cleaned up the ram memory, after that everything works.
I have read in other ubuntu forum that after using ubuntu for a while, there will be bad ram.
Should i switch back to windows?

---

### Post by Bodsda on 2011-09-08
> **suang said:**
> I tried the sudo fsck -t vfat /dev/sda1 just because i found it on the internet. i don't know what it means.
Don't ever do that, if your unsure what a command does, ask.
> 
Just now, i tried sudo mount/dev/sda1 /mnt
then sudo e2fsck -fvy /mnt
Error: the superblock could not read or does not describe a correct ext2 filesystem
sudo fsck.ext3 -f /dev/sda1
Error: missing in directory inode 402385
sudo fsck /dev/sda1 -p
Error:inconsistency, try without -p

Try
```

fsck.ext3 -f /dev/sda1 -p

```
> 
Oh my God, looks like everything does not work here.

To be fair, you have only tried 4 things, and the first and third worked as expected. 2 and 4 where never going to work on your filesystem anyway. In short, everything 'works' here.
> 
Before this problem, my screen has been blank before, then i cleaned up the ram memory, after that everything works.

What do you mean, 'cleaned up the ram'?
> 
I have read in other ubuntu forum that after using ubuntu for a while, there will be bad ram.

That's not true
> 
Should i switch back to windows?
Depends, want to learn and have fun fixing things?

---

### Post by suang on 2011-09-08
Here is the boot.log of my ubuntu 11.04:
umount: can't umount /cdrom: Device or resource busy 
/init: line 7: can't open /dev/sr0: No medium found 
Warning: Unable to find the persistent medium 
umount: can't umount /cdrom: Device or resource busy 
/init: line 7: can't open /dev/sr0: No medium found 
Warning: Unable to find the persistent home medium 
/init: line 7: can't open /dev/sr0: No medium found 
umount: can't umount /cdrom: Device or resource busy 
/init: line 7: can't open /dev/sr0: No medium found 
Warning: Impossible to include the casper-sn Snapshot 
/init: line 7: can't open /dev/sr0: No medium found 
umount: can't umount /cdrom: Device or resource busy 
/init: line 7: can't open /dev/sr0: No medium found 
Warning: Impossible to include the home-sn Snapshot 
done.

Below is the Xorg.0.log:
[    28.139] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    28.139] X Protocol Version 11, Revision 0
[    28.139] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    28.139] Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    28.139] Kernel command line: noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz splash -- BOOT_IMAGE=/casper/vmlinuz 
[    28.139] Build Date: 19 April 2011  03:33:17PM
[    28.139] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    28.141] Current version of pixman: 0.20.2
[    28.141]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    28.141] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.142] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  9 02:17:36 2011
[    28.171] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.176] (==) No Layout section.  Using the first Screen section.
[    28.176] (==) No screen section available. Using defaults.
[    28.176] (**) |-->Screen "Default Screen Section" (0)
[    28.176] (**) |   |-->Monitor "<default monitor>"
[    28.177] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    28.177] (==) Automatically adding devices
[    28.177] (==) Automatically enabling devices
[    28.179] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.179]     Entry deleted from font path.
[    28.179] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    28.179]     Entry deleted from font path.
[    28.179] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    28.179]     Entry deleted from font path.
[    28.181] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    28.181]     Entry deleted from font path.
[    28.181] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    28.181]     Entry deleted from font path.
[    28.184] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    28.184] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.184] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.184] (II) Loader magic: 0x81ffde0
[    28.184] (II) Module ABI versions:
[    28.184]     X.Org ANSI C Emulation: 0.4
[    28.184]     X.Org Video Driver: 10.0
[    28.184]     X.Org XInput driver : 12.3
[    28.184]     X.Org Server Extension : 5.0
[    28.186] (--) PCI:*(0:0:2:0) 8086:2772:8086:d607 rev 2, Mem @ 0x30100000/524288, 0x20000000/268435456, 0x30180000/262144, I/O @ 0x000030e0/8
[    28.188] (II) Open ACPI successful (/var/run/acpid.socket)
[    28.188] (II) LoadModule: "extmod"
[    28.226] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    28.245] (II) Module extmod: vendor="X.Org Foundation"
[    28.245]     compiled for 1.10.1, module version = 1.0.0
[    28.246]     Module class: X.Org Server Extension
[    28.246]     ABI class: X.Org Server Extension, version 5.0
[    28.246] (II) Loading extension MIT-SCREEN-SAVER
[    28.246] (II) Loading extension XFree86-VidModeExtension
[    28.246] (II) Loading extension XFree86-DGA
[    28.246] (II) Loading extension DPMS
[    28.246] (II) Loading extension XVideo
[    28.246] (II) Loading extension XVideo-MotionCompensation
[    28.246] (II) Loading extension X-Resource
[    28.246] (II) LoadModule: "dbe"
[    28.246] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    28.263] (II) Module dbe: vendor="X.Org Foundation"
[    28.263]     compiled for 1.10.1, module version = 1.0.0
[    28.263]     Module class: X.Org Server Extension
[    28.263]     ABI class: X.Org Server Extension, version 5.0
[    28.263] (II) Loading extension DOUBLE-BUFFER
[    28.263] (II) LoadModule: "glx"
[    28.264] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    28.275] (II) Module glx: vendor="X.Org Foundation"
[    28.275]     compiled for 1.10.1, module version = 1.0.0
[    28.275]     ABI class: X.Org Server Extension, version 5.0
[    28.283] (==) AIGLX enabled
[    28.283] (II) Loading extension GLX
[    28.283] (II) LoadModule: "record"
[    28.284] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    28.297] (II) Module record: vendor="X.Org Foundation"
[    28.297]     compiled for 1.10.1, module version = 1.13.0
[    28.297]     Module class: X.Org Server Extension
[    28.297]     ABI class: X.Org Server Extension, version 5.0
[    28.297] (II) Loading extension RECORD
[    28.297] (II) LoadModule: "dri"
[    28.298] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    28.322] (II) Module dri: vendor="X.Org Foundation"
[    28.322]     compiled for 1.10.1, module version = 1.0.0
[    28.322]     ABI class: X.Org Server Extension, version 5.0
[    28.322] (II) Loading extension XFree86-DRI
[    28.322] (II) LoadModule: "dri2"
[    28.323] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    28.335] (II) Module dri2: vendor="X.Org Foundation"
[    28.335]     compiled for 1.10.1, module version = 1.2.0
[    28.335]     ABI class: X.Org Server Extension, version 5.0
[    28.335] (II) Loading extension DRI2
[    28.335] (==) Matched intel as autoconfigured driver 0
[    28.335] (==) Matched vesa as autoconfigured driver 1
[    28.335] (==) Matched fbdev as autoconfigured driver 2
[    28.335] (==) Assigned the driver to the xf86ConfigLayout
[    28.335] (II) LoadModule: "intel"
[    28.335] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    28.399] (II) Module intel: vendor="X.Org Foundation"
[    28.399]     compiled for 1.10.0.902, module version = 2.14.0
[    28.399]     Module class: X.Org Video Driver
[    28.399]     ABI class: X.Org Video Driver, version 10.0
[    28.399] (II) LoadModule: "vesa"
[    28.401] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.423] (II) Module vesa: vendor="X.Org Foundation"
[    28.423]     compiled for 1.10.0, module version = 2.3.0
[    28.423]     Module class: X.Org Video Driver
[    28.423]     ABI class: X.Org Video Driver, version 10.0
[    28.423] (II) LoadModule: "fbdev"
[    28.424] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.447] (II) Module fbdev: vendor="X.Org Foundation"
[    28.447]     compiled for 1.10.0, module version = 0.4.2
[    28.447]     ABI class: X.Org Video Driver, version 10.0
[    28.447] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    28.448] (II) VESA: driver for VESA chipsets: vesa
[    28.448] (II) FBDEV: driver for framebuffer: fbdev
[    28.448] (++) using VT number 7

[    28.451] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    28.451] (WW) Falling back to old probe method for vesa
[    28.451] (WW) Falling back to old probe method for fbdev
[    28.451] (II) Loading sub module "fbdevhw"
[    28.451] (II) LoadModule: "fbdevhw"
[    28.465] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    28.465] (II) Module fbdevhw: vendor="X.Org Foundation"
[    28.465]     compiled for 1.10.1, module version = 0.0.2
[    28.465]     ABI class: X.Org Video Driver, version 10.0
[    28.465] drmOpenDevice: node name is /dev/dri/card0
[    28.465] drmOpenDevice: open result is 9, (OK)
[    28.465] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    28.466] drmOpenDevice: node name is /dev/dri/card0
[    28.466] drmOpenDevice: open result is 9, (OK)
[    28.466] drmOpenByBusid: drmOpenMinor returns 9
[    28.466] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    28.466] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    28.466] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    28.466] (==) intel(0): RGB weight 888
[    28.466] (==) intel(0): Default visual is TrueColor
[    28.466] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945G
[    28.466] (--) intel(0): Chipset: "945G"
[    28.466] (**) intel(0): Tiling enabled
[    28.466] (**) intel(0): SwapBuffers wait enabled
[    28.466] (==) intel(0): video overlay key set to 0x101fe
[    28.490] (II) intel(0): Output VGA1 has no monitor section
[    28.506] (II) intel(0): EDID for output VGA1
[    28.506] (II) intel(0): Printing probed modes for output VGA1
[    28.506] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    28.506] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    28.506] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    28.506] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    28.506] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    28.506] (II) intel(0): Output VGA1 connected
[    28.506] (II) intel(0): Using fuzzy aspect match for initial modes
[    28.506] (II) intel(0): Output VGA1 using initial mode 1024x768
[    28.506] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    28.506] (II) intel(0): Kernel page flipping support detected, enabling
[    28.506] (==) intel(0): DPI set to (96, 96)
[    28.506] (II) Loading sub module "fb"
[    28.506] (II) LoadModule: "fb"
[    28.507] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.517] (II) Module fb: vendor="X.Org Foundation"
[    28.517]     compiled for 1.10.1, module version = 1.0.0
[    28.517]     ABI class: X.Org ANSI C Emulation, version 0.4
[    28.517] (II) UnloadModule: "vesa"
[    28.517] (II) Unloading vesa
[    28.517] (II) UnloadModule: "fbdev"
[    28.517] (II) Unloading fbdev
[    28.517] (II) UnloadModule: "fbdevhw"
[    28.517] (II) Unloading fbdevhw
[    28.517] (==) Depth 24 pixmap format is 32 bpp
[    28.517] (==) intel(0): VideoRam: 262144 KB
[    28.517] (II) intel(0): [DRI2] Setup complete
[    28.517] (II) intel(0): [DRI2]   DRI driver: i915
[    28.517] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    28.536] (II) UXA(0): Driver registered support for the following operations:
[    28.536] (II)         solid
[    28.536] (II)         copy
[    28.536] (II)         composite (RENDER acceleration)
[    28.536] (II)         put_image
[    28.536] (II)         get_image
[    28.536] (==) intel(0): Backing store disabled
[    28.537] (==) intel(0): Silken mouse enabled
[    28.537] (II) intel(0): Initializing HW Cursor
[    28.568] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    28.568] (==) intel(0): DPMS enabled
[    28.568] (==) intel(0): Intel XvMC decoder disabled
[    28.568] (II) intel(0): Set up textured video
[    28.568] (II) intel(0): Set up overlay video
[    28.568] (II) intel(0): direct rendering: DRI2 Enabled
[    28.568] (==) intel(0): hotplug detection: "enabled"
[    28.568] (--) RandR disabled
[    28.568] (II) Initializing built-in extension Generic Event Extension
[    28.568] (II) Initializing built-in extension SHAPE
[    28.568] (II) Initializing built-in extension MIT-SHM
[    28.568] (II) Initializing built-in extension XInputExtension
[    28.568] (II) Initializing built-in extension XTEST
[    28.568] (II) Initializing built-in extension BIG-REQUESTS
[    28.568] (II) Initializing built-in extension SYNC
[    28.568] (II) Initializing built-in extension XKEYBOARD
[    28.568] (II) Initializing built-in extension XC-MISC
[    28.569] (II) Initializing built-in extension SECURITY
[    28.569] (II) Initializing built-in extension XINERAMA
[    28.569] (II) Initializing built-in extension XFIXES
[    28.569] (II) Initializing built-in extension RENDER
[    28.569] (II) Initializing built-in extension RANDR
[    28.569] (II) Initializing built-in extension COMPOSITE
[    28.569] (II) Initializing built-in extension DAMAGE
[    28.569] (II) Initializing built-in extension GESTURE
[    28.640] (II) AIGLX: Trying DRI driver /usr/lib/dri/i915_dri.so
[    28.834] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    28.834] (II) AIGLX: enabled GLX_INTEL_swap_event
[    28.834] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    28.834] (II) AIGLX: enabled GLX_SGI_make_current_read
[    28.834] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    28.834] (II) AIGLX: Loaded and initialized i915
[    28.834] (II) GLX: Initialized DRI2 GL provider for screen 0
[    28.835] (II) intel(0): Setting screen physical size to 270 x 203
[    28.984] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.143] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    29.143] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.143] (II) LoadModule: "evdev"
[    29.144] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.168] (II) Module evdev: vendor="X.Org Foundation"
[    29.168]     compiled for 1.10.0.902, module version = 2.6.0
[    29.168]     Module class: X.Org XInput Driver
[    29.168]     ABI class: X.Org XInput driver, version 12.3
[    29.168] (II) Using input driver 'evdev' for 'Power Button'
[    29.169] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.169] (**) Power Button: always reports core events
[    29.169] (**) Power Button: Device: "/dev/input/event1"
[    29.184] (--) Power Button: Found keys
[    29.184] (II) Power Button: Configuring as keyboard
[    29.184] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    29.184] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    29.184] (**) Option "xkb_rules" "evdev"
[    29.184] (**) Option "xkb_model" "pc105"
[    29.184] (**) Option "xkb_layout" "us"
[    29.191] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    29.191] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    29.191] (II) Using input driver 'evdev' for 'Sleep Button'
[    29.191] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.191] (**) Sleep Button: always reports core events
[    29.191] (**) Sleep Button: Device: "/dev/input/event0"
[    29.208] (--) Sleep Button: Found keys
[    29.208] (II) Sleep Button: Configuring as keyboard
[    29.208] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    29.208] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    29.208] (**) Option "xkb_rules" "evdev"
[    29.208] (**) Option "xkb_model" "pc105"
[    29.208] (**) Option "xkb_layout" "us"
[    29.211] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event4)
[    29.211] (II) No input driver/identifier specified (ignoring)
[    29.230] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    29.230] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    29.230] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    29.230] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.230] (**) AT Translated Set 2 keyboard: always reports core events
[    29.230] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    29.247] (--) AT Translated Set 2 keyboard: Found keys
[    29.247] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    29.247] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    29.247] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    29.247] (**) Option "xkb_rules" "evdev"
[    29.247] (**) Option "xkb_model" "pc105"
[    29.247] (**) Option "xkb_layout" "us"
[    29.248] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event3)
[    29.248] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    29.248] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    29.249] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.249] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    29.249] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event3"
[    29.265] (--) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    29.265] (--) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    29.265] (--) ImPS/2 Generic Wheel Mouse: Found relative axes
[    29.265] (--) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    29.265] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    29.265] (II) ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    29.265] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    29.265] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.265] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[    29.265] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    29.265] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    29.265] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    29.265] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    29.265] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    29.265] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    29.266] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    29.266] (II) No input driver/identifier specified (ignoring)

---

### Post by fdrake on 2011-09-08
if you still have problem booting use a live cd and do

```
sudo fisk -l
```

and paste here the output

after you did that go to this url and (in a separate post) follow the instruction and post the results file.
link: [http://en.sourceforge.jp/projects/sfnet_bootinfoscript/downloads/bootinfoscript/0.60/boot_info_script060.zip/](http://en.sourceforge.jp/projects/sfnet_bootinfoscript/downloads/bootinfoscript/0.60/boot_info_script060.zip/)
while you are doing this we will give you some commands to try to fix the problem.

---

### Post by suang on 2011-09-10
Thanks for all the help. Now, i have already reinstalled my ubuntu.

---


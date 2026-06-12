---
title: "Doesn't boot"
date: 2012-02-21
forum: General Help
---

### Post by ric1321 on 2012-02-21
Hi to everyone. Since yesterday my ubuntu hasn't been able to boot due to a graphics issue. I boot it, Grub's fine, the plymuth (?? I think) page is ok, then there are some system messages and the monitor flashed, however I wanna post what I tried to read:

```
starting save kernel message ok
starting the winbird daemon winbird ok
starting bluetooth
*pulseaudio configured for pre-user session sane disabled

```

followed by (more or less):

```
anacronistic cron starting
anacronistic cron stopping ....
```

I booted into recovery mod and when switching off I saw in the screen:
```
load fallback graphics devices FAIL
```

I even tried to boot with an older kernel, but with the same result.

A hint, yesterday, I installed some libraries to compile a software, can it be the root.

---

### Post by roelforg on 2012-02-21
> **ric1321 said:**
> Hi to everyone. Since yesterday my ubuntu hasn't been able to boot due to a graphics issue. I boot it, Grub's fine, the plymuth (?? I think) page is ok, then there are some system messages and the monitor flashed, however I wanna post what I tried to read:

```
starting save kernel message ok
starting the winbird daemon winbird ok
starting bluetooth
*pulseaudio configured for pre-user session sane disabled

```followed by (more or less):

```
anacronistic cron starting
anacronistic cron stopping ....
```I booted into recovery mod and when switching off I saw in the screen:
```
load fallback graphics devices FAIL
```I even tried to boot with an older kernel, but with the same result.

A hint, yesterday, I installed some libraries to compile a software, can it be the root.

The fallback graphic shouldn't be a problem; ubuntu sometimes try's to load it twice; the second one will fail; don't worry; it should only be activated when something crashes.

That root install might; unless you've changed your prefix for compiling it should've installed in /usr/local

Try this:
When booting (after grub) press ESC.
it should display kernel messages.
If it crashes after init is done; you might be able to do the following:
Press and hold CTRL-ALT-F1 for a few secs; it should switch to VT1, log in with your normal account.
Run:
```

sudo ls /dev | grep "sd"

```
Note the output down.
insert your usb drive. repeat the command above.
There should be 2 extra entry's; note the one ending in a number (like /dev/sdb1  --- the /dev/prefix is important).
For example,
my pc lists:
```

sda
sda1
sdb
sdb1

```
before usb,
after:
```

sda
sda1
sdb
sdb1
sdc
sdc1

```
We're interested in sdc1 as it's the one that's appeared and ends in a number.
The device path is /dev/sdc1 in my case; replace /dev/sdc1 in the rest of the post with the path your system gives (e.g when sdb and sdb1 are the ones appearing, the path is /dev/sdb1 get it?)

Right, remember to replace the /dev/sdc1 with what we just found out!
Run (lines starting with # are comments, read them, don't execute them):
```

sudo bash
umount /dev/sdc
#ignore what umount will say, i'll be along the lines of "/dev/sdc1 is not mounted", i only want you to enter this to prevent errors down the line
mkdir /media/usbtmp
mount /dev/sdc1 /media/usbtmp
cd /media/usbtmp
dmesg > dmesg.log
cp /var/log/Xorg.* .
# if you have a usb-drive that's big enough (i'd say 2-3gb free space is enough), execute the following 2 commands
mkdir logs
cp -R /var/log/* ./logs/
cd ..
umount /dev/sdc1
exit

```
Remove the usb-drive
Now, shut the pc down (sudo poweroff).
Use a different pc to post the last 30-40 lines of dmesg.log and the whole Xorg log (all files starting with Xorg are logs, please each of them in a differen [ code ] block (no spaces))
Keep the file's on the drive; depending on the info uncovered from the logs i'm asking you to post, i might or might not need info from other logs (they are in the logs directory).

---

### Post by roelforg on 2012-02-21
FYI: Please PM me when you post; i'm bad at keeping up with threads so the PM will alert me.

---

### Post by ric1321 on 2012-02-21
Sorry, my output for ```
sudo ls /dev | grep "sd"
``` is first all in sda (from 1 to 6), then with the usb drive finishes in sdb (1 ), while in your prompt i have to ```
umount /dev/sdc
```, do I have to respect this? or do i have to do according to my output?

---

### Post by ric1321 on 2012-02-21
I managed to do that, I have logs, but dmesg.log seems to be .tar.gz, is it possible? Then, Xorg log seems a mess to me reading that with the windows notepad. I really can't understand it.

---

### Post by ric1321 on 2012-02-21
tell me if this the correct Xorg log
```
[   118.824] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[   118.824] X Protocol Version 11, Revision 0
[   118.824] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[   118.824] Current Operating System: Linux riccardo-Inspiron-N5010 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64
[   118.824] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=34ef44cf-3cee-4aea-8cfd-59352f3c5ac8 ro quiet splash vt.handoff=7
[   118.824] Build Date: 19 October 2011  05:21:26AM
[   118.824] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[   118.824] Current version of pixman: 0.22.2
[   118.824] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   118.824] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   118.825] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 21 17:19:23 2012
[   118.825] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   118.825] (==) No Layout section.  Using the first Screen section.
[   118.825] (==) No screen section available. Using defaults.
[   118.825] (**) |-->Screen "Default Screen Section" (0)
[   118.825] (**) |   |-->Monitor "<default monitor>"
[   118.825] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   118.825] (==) Automatically adding devices
[   118.825] (==) Automatically enabling devices
[   118.825] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   118.825] 	Entry deleted from font path.
[   118.825] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   118.825] 	Entry deleted from font path.
[   118.825] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   118.825] 	Entry deleted from font path.
[   118.825] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   118.825] 	Entry deleted from font path.
[   118.825] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   118.825] 	Entry deleted from font path.
[   118.825] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   118.825] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   118.825] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   118.825] (II) Loader magic: 0x7e0220
[   118.825] (II) Module ABI versions:
[   118.825] 	X.Org ANSI C Emulation: 0.4
[   118.825] 	X.Org Video Driver: 10.0
[   118.825] 	X.Org XInput driver : 12.3
[   118.825] 	X.Org Server Extension : 5.0
[   118.826] (--) PCI:*(0:0:2:0) 8086:0046:1028:0447 rev 24, Mem @ 0xfa400000/4194304, 0xc0000000/268435456, I/O @ 0x0000f080/8
[   118.826] (II) Open ACPI successful (/var/run/acpid.socket)
[   118.826] (II) LoadModule: "extmod"
[   118.827] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   118.827] (II) Module extmod: vendor="X.Org Foundation"
[   118.827] 	compiled for 1.10.4, module version = 1.0.0
[   118.827] 	Module class: X.Org Server Extension
[   118.827] 	ABI class: X.Org Server Extension, version 5.0
[   118.827] (II) Loading extension MIT-SCREEN-SAVER
[   118.827] (II) Loading extension XFree86-VidModeExtension
[   118.827] (II) Loading extension XFree86-DGA
[   118.827] (II) Loading extension DPMS
[   118.827] (II) Loading extension XVideo
[   118.827] (II) Loading extension XVideo-MotionCompensation
[   118.827] (II) Loading extension X-Resource
[   118.827] (II) LoadModule: "dbe"
[   118.827] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   118.827] (II) Module dbe: vendor="X.Org Foundation"
[   118.827] 	compiled for 1.10.4, module version = 1.0.0
[   118.827] 	Module class: X.Org Server Extension
[   118.827] 	ABI class: X.Org Server Extension, version 5.0
[   118.827] (II) Loading extension DOUBLE-BUFFER
[   118.827] (II) LoadModule: "glx"
[   118.828] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   118.828] (II) Module glx: vendor="X.Org Foundation"
[   118.828] 	compiled for 1.10.4, module version = 1.0.0
[   118.828] 	ABI class: X.Org Server Extension, version 5.0
[   118.828] (==) AIGLX enabled
[   118.828] (II) Loading extension GLX
[   118.828] (II) LoadModule: "record"
[   118.828] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   118.828] (II) Module record: vendor="X.Org Foundation"
[   118.828] 	compiled for 1.10.4, module version = 1.13.0
[   118.828] 	Module class: X.Org Server Extension
[   118.828] 	ABI class: X.Org Server Extension, version 5.0
[   118.828] (II) Loading extension RECORD
[   118.828] (II) LoadModule: "dri"
[   118.829] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   118.829] (II) Module dri: vendor="X.Org Foundation"
[   118.829] 	compiled for 1.10.4, module version = 1.0.0
[   118.829] 	ABI class: X.Org Server Extension, version 5.0
[   118.829] (II) Loading extension XFree86-DRI
[   118.829] (II) LoadModule: "dri2"
[   118.829] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   118.829] (II) Module dri2: vendor="X.Org Foundation"
[   118.829] 	compiled for 1.10.4, module version = 1.2.0
[   118.829] 	ABI class: X.Org Server Extension, version 5.0
[   118.829] (II) Loading extension DRI2
[   118.829] (==) Matched intel as autoconfigured driver 0
[   118.829] (==) Matched vesa as autoconfigured driver 1
[   118.829] (==) Matched fbdev as autoconfigured driver 2
[   118.829] (==) Assigned the driver to the xf86ConfigLayout
[   118.829] (II) LoadModule: "intel"
[   118.830] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   118.830] (II) Module intel: vendor="X.Org Foundation"
[   118.830] 	compiled for 1.10.4, module version = 2.15.901
[   118.830] 	Module class: X.Org Video Driver
[   118.830] 	ABI class: X.Org Video Driver, version 10.0
[   118.830] (II) LoadModule: "vesa"
[   118.830] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   118.830] (II) Module vesa: vendor="X.Org Foundation"
[   118.830] 	compiled for 1.10.2, module version = 2.3.0
[   118.830] 	Module class: X.Org Video Driver
[   118.830] 	ABI class: X.Org Video Driver, version 10.0
[   118.830] (II) LoadModule: "fbdev"
[   118.831] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   118.831] (II) Module fbdev: vendor="X.Org Foundation"
[   118.831] 	compiled for 1.10.0, module version = 0.4.2
[   118.831] 	ABI class: X.Org Video Driver, version 10.0
[   118.831] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[   118.831] (II) VESA: driver for VESA chipsets: vesa
[   118.831] (II) FBDEV: driver for framebuffer: fbdev
[   118.831] (++) using VT number 7

[   118.833] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   118.833] (WW) Falling back to old probe method for vesa
[   118.833] (WW) Falling back to old probe method for fbdev
[   118.833] (II) Loading sub module "fbdevhw"
[   118.833] (II) LoadModule: "fbdevhw"
[   118.834] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   118.834] (II) Module fbdevhw: vendor="X.Org Foundation"
[   118.834] 	compiled for 1.10.4, module version = 0.0.2
[   118.834] 	ABI class: X.Org Video Driver, version 10.0
[   118.834] drmOpenDevice: node name is /dev/dri/card0
[   118.834] drmOpenDevice: open result is 12, (OK)
[   118.834] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[   118.834] drmOpenDevice: node name is /dev/dri/card0
[   118.834] drmOpenDevice: open result is 12, (OK)
[   118.834] drmOpenByBusid: drmOpenMinor returns 12
[   118.834] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[   118.834] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   118.834] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   118.834] (==) intel(0): RGB weight 888
[   118.834] (==) intel(0): Default visual is TrueColor
[   118.834] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[   118.834] (--) intel(0): Chipset: "Arrandale"
[   118.834] (**) intel(0): Relaxed fencing enabled
[   118.834] (**) intel(0): Wait on SwapBuffers? enabled
[   118.834] (**) intel(0): Triple buffering? enabled
[   118.834] (**) intel(0): Framebuffer tiled
[   118.834] (**) intel(0): Pixmaps tiled
[   118.834] (**) intel(0): 3D buffers tiled
[   118.834] (**) intel(0): SwapBuffers wait enabled
[   118.834] (==) intel(0): video overlay key set to 0x101fe
[   118.834] (II) intel(0): Output LVDS1 has no monitor section
[   118.834] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[   118.834] (II) intel(0): Output VGA1 has no monitor section
[   118.857] (II) intel(0): Output HDMI1 has no monitor section
[   118.904] (II) intel(0): Output DP1 has no monitor section
[   118.904] (II) intel(0): EDID for output LVDS1
[   118.904] (II) intel(0): Manufacturer: SEC  Model: 5441  Serial#: 0
[   118.904] (II) intel(0): Year: 2010  Week: 0
[   118.904] (II) intel(0): EDID Version: 1.3
[   118.904] (II) intel(0): Digital Display Input
[   118.904] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[   118.904] (II) intel(0): Gamma: 2.20
[   118.904] (II) intel(0): No DPMS capabilities specified
[   118.904] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   118.904] (II) intel(0): First detailed timing is preferred mode
[   118.904] (II) intel(0): redX: 0.620 redY: 0.340   greenX: 0.330 greenY: 0.570
[   118.904] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[   118.904] (II) intel(0): Manufacturer's mask: 0
[   118.904] (II) intel(0): Supported detailed timing:
[   118.904] (II) intel(0): clock: 71.6 MHz   Image Size:  344 x 194 mm
[   118.904] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1510 h_border: 0
[   118.904] (II) intel(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 789 v_border: 0
[   118.904] (II) intel(0): Supported detailed timing:
[   118.904] (II) intel(0): clock: 71.6 MHz   Image Size:  344 x 194 mm
[   118.904] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1510 h_border: 0
[   118.904] (II) intel(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 789 v_border: 0
[   118.904] (II) intel(0):  8MN61€156AT
[   118.904] (II) intel(0): Unknown vendor-specific block 0
[   118.904] (II) intel(0): EDID (in hex):
[   118.904] (II) intel(0): 	00ffffffffffff004ca3415400000000
[   118.904] (II) intel(0): 	00140103902213780ac8959e57549226
[   118.904] (II) intel(0): 	0f505400000001010101010101010101
[   118.904] (II) intel(0): 	010101010101f41b5690500015303020
[   118.904] (II) intel(0): 	250058c21000001af41b569050001530
[   118.904] (II) intel(0): 	3020250058c21000001a000000fe0038
[   118.904] (II) intel(0): 	4d4e36318031353641540a2000000000
[   118.904] (II) intel(0): 	00000000000000000001010a2020001d
[   118.904] (II) intel(0): EDID vendor "SEC", prod id 21569
[   118.904] (II) intel(0): Printing DDC gathered Modelines:
[   118.904] (II) intel(0): Modeline "1366x768"x0.0   71.56  1366 1414 1446 1510  768 770 775 789 +hsync -vsync (47.4 kHz)
[   118.904] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[   118.905] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[   118.905] (II) intel(0): Printing probed modes for output LVDS1
[   118.905] (II) intel(0): Modeline "1366x768"x60.1   71.56  1366 1414 1446 1510  768 770 775 789 +hsync -vsync (47.4 kHz)
[   118.905] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[   118.905] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[   118.905] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   118.905] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   118.905] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   118.905] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   118.905] (II) intel(0): EDID for output VGA1
[   118.927] (II) intel(0): EDID for output HDMI1
[   118.976] (II) intel(0): EDID for output DP1
[   118.976] (II) intel(0): Output LVDS1 connected
[   118.976] (II) intel(0): Output VGA1 disconnected
[   118.976] (II) intel(0): Output HDMI1 disconnected
[   118.976] (II) intel(0): Output DP1 disconnected
[   118.976] (II) intel(0): Using exact sizes for initial modes
[   118.976] (II) intel(0): Output LVDS1 using initial mode 1366x768
[   118.976] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   118.976] (II) intel(0): Kernel page flipping support detected, enabling
[   118.976] (**) intel(0): Display dimensions: (340, 190) mm
[   118.976] (**) intel(0): DPI set to (102, 102)
[   118.976] (II) Loading sub module "fb"
[   118.976] (II) LoadModule: "fb"
[   118.976] (II) Loading /usr/lib/xorg/modules/libfb.so
[   118.976] (II) Module fb: vendor="X.Org Foundation"
[   118.976] 	compiled for 1.10.4, module version = 1.0.0
[   118.976] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   118.976] (II) Loading sub module "dri2"
[   118.976] (II) LoadModule: "dri2"
[   118.977] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   118.977] (II) Module dri2: vendor="X.Org Foundation"
[   118.977] 	compiled for 1.10.4, module version = 1.2.0
[   118.977] 	ABI class: X.Org Server Extension, version 5.0
[   118.977] (II) UnloadModule: "vesa"
[   118.977] (II) Unloading vesa
[   118.977] (II) UnloadModule: "fbdev"
[   118.977] (II) Unloading fbdev
[   118.977] (II) UnloadModule: "fbdevhw"
[   118.977] (II) Unloading fbdevhw
[   118.977] (==) Depth 24 pixmap format is 32 bpp
[   118.977] (II) intel(0): [DRI2] Setup complete
[   118.977] (II) intel(0): [DRI2]   DRI driver: i965
[   118.977] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[   118.989] (II) UXA(0): Driver registered support for the following operations:
[   118.989] (II)         solid
[   118.989] (II)         copy
[   118.989] (II)         composite (RENDER acceleration)
[   118.989] (II)         put_image
[   118.989] (II)         get_image
[   118.989] (==) intel(0): Backing store disabled
[   118.989] (==) intel(0): Silken mouse enabled
[   118.989] (II) intel(0): Initializing HW Cursor
[   119.056] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   119.067] (==) intel(0): DPMS enabled
[   119.067] (==) intel(0): Intel XvMC decoder enabled
[   119.067] (II) intel(0): Set up textured video
[   119.067] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[   119.067] (II) intel(0): direct rendering: DRI2 Enabled
[   119.067] (==) intel(0): hotplug detection: "enabled"
[   119.067] (--) RandR disabled
[   119.067] (II) Initializing built-in extension Generic Event Extension
[   119.067] (II) Initializing built-in extension SHAPE
[   119.067] (II) Initializing built-in extension MIT-SHM
[   119.067] (II) Initializing built-in extension XInputExtension
[   119.067] (II) Initializing built-in extension XTEST
[   119.067] (II) Initializing built-in extension BIG-REQUESTS
[   119.067] (II) Initializing built-in extension SYNC
[   119.067] (II) Initializing built-in extension XKEYBOARD
[   119.067] (II) Initializing built-in extension XC-MISC
[   119.067] (II) Initializing built-in extension SECURITY
[   119.067] (II) Initializing built-in extension XINERAMA
[   119.067] (II) Initializing built-in extension XFIXES
[   119.067] (II) Initializing built-in extension RENDER
[   119.067] (II) Initializing built-in extension RANDR
[   119.067] (II) Initializing built-in extension COMPOSITE
[   119.067] (II) Initializing built-in extension DAMAGE
[   119.067] (II) Initializing built-in extension GESTURE
[   119.075] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
[   119.078] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   119.078] (II) AIGLX: enabled GLX_INTEL_swap_event
[   119.078] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   119.078] (II) AIGLX: enabled GLX_SGI_make_current_read
[   119.078] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   119.078] (II) AIGLX: Loaded and initialized i965
[   119.078] (II) GLX: Initialized DRI2 GL provider for screen 0
[   119.078] (II) intel(0): Setting screen physical size to 361 x 203
[   119.086] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   119.092] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   119.093] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   119.093] (II) LoadModule: "evdev"
[   119.093] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.093] (II) Module evdev: vendor="X.Org Foundation"
[   119.093] 	compiled for 1.10.2, module version = 2.6.0
[   119.093] 	Module class: X.Org XInput Driver
[   119.093] 	ABI class: X.Org XInput driver, version 12.3
[   119.093] (II) Using input driver 'evdev' for 'Power Button'
[   119.093] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.093] (**) Power Button: always reports core events
[   119.094] (**) Power Button: Device: "/dev/input/event3"
[   119.094] (--) Power Button: Found keys
[   119.094] (II) Power Button: Configuring as keyboard
[   119.094] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[   119.094] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   119.094] (**) Option "xkb_rules" "evdev"
[   119.094] (**) Option "xkb_model" "pc105"
[   119.094] (**) Option "xkb_layout" "it"
[   119.095] (II) XKB: reuse xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.xkm
[   119.096] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[   119.096] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   119.096] (II) Using input driver 'evdev' for 'Video Bus'
[   119.096] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.096] (**) Video Bus: always reports core events
[   119.096] (**) Video Bus: Device: "/dev/input/event9"
[   119.096] (--) Video Bus: Found keys
[   119.096] (II) Video Bus: Configuring as keyboard
[   119.096] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input10/event9"
[   119.096] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   119.096] (**) Option "xkb_rules" "evdev"
[   119.096] (**) Option "xkb_model" "pc105"
[   119.097] (**) Option "xkb_layout" "it"
[   119.099] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   119.099] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   119.099] (II) Using input driver 'evdev' for 'Power Button'
[   119.099] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.099] (**) Power Button: always reports core events
[   119.099] (**) Power Button: Device: "/dev/input/event0"
[   119.099] (--) Power Button: Found keys
[   119.099] (II) Power Button: Configuring as keyboard
[   119.099] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   119.099] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   119.099] (**) Option "xkb_rules" "evdev"
[   119.099] (**) Option "xkb_model" "pc105"
[   119.099] (**) Option "xkb_layout" "it"
[   119.100] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[   119.100] (II) No input driver/identifier specified (ignoring)
[   119.100] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[   119.100] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   119.100] (II) Using input driver 'evdev' for 'Sleep Button'
[   119.100] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.100] (**) Sleep Button: always reports core events
[   119.100] (**) Sleep Button: Device: "/dev/input/event2"
[   119.100] (--) Sleep Button: Found keys
[   119.100] (II) Sleep Button: Configuring as keyboard
[   119.100] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[   119.100] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   119.100] (**) Option "xkb_rules" "evdev"
[   119.100] (**) Option "xkb_model" "pc105"
[   119.100] (**) Option "xkb_layout" "it"
[   119.102] (II) config/udev: Adding input device HP Wireless Optical Mobile Mouse (/dev/input/event5)
[   119.102] (**) HP Wireless Optical Mobile Mouse: Applying InputClass "evdev pointer catchall"
[   119.102] (II) Using input driver 'evdev' for 'HP Wireless Optical Mobile Mouse'
[   119.102] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.102] (**) HP Wireless Optical Mobile Mouse: always reports core events
[   119.102] (**) HP Wireless Optical Mobile Mouse: Device: "/dev/input/event5"
[   119.102] (--) HP Wireless Optical Mobile Mouse: Found 3 mouse buttons
[   119.102] (--) HP Wireless Optical Mobile Mouse: Found scroll wheel(s)
[   119.102] (--) HP Wireless Optical Mobile Mouse: Found relative axes
[   119.102] (--) HP Wireless Optical Mobile Mouse: Found x and y relative axes
[   119.102] (II) HP Wireless Optical Mobile Mouse: Configuring as mouse
[   119.102] (II) HP Wireless Optical Mobile Mouse: Adding scrollwheel support
[   119.102] (**) HP Wireless Optical Mobile Mouse: YAxisMapping: buttons 4 and 5
[   119.102] (**) HP Wireless Optical Mobile Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   119.102] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input5/event5"
[   119.102] (II) XINPUT: Adding extended input device "HP Wireless Optical Mobile Mouse" (type: MOUSE)
[   119.102] (II) HP Wireless Optical Mobile Mouse: initialized for relative axes.
[   119.102] (**) HP Wireless Optical Mobile Mouse: (accel) keeping acceleration scheme 1
[   119.102] (**) HP Wireless Optical Mobile Mouse: (accel) acceleration profile 0
[   119.102] (**) HP Wireless Optical Mobile Mouse: (accel) acceleration factor: 2.000
[   119.102] (**) HP Wireless Optical Mobile Mouse: (accel) acceleration threshold: 4
[   119.102] (II) config/udev: Adding input device HP Wireless Optical Mobile Mouse (/dev/input/mouse0)
[   119.102] (II) No input driver/identifier specified (ignoring)
[   119.103] (II) config/udev: Adding input device Laptop_Integrated_Webcam_1.3M (/dev/input/event8)
[   119.103] (**) Laptop_Integrated_Webcam_1.3M: Applying InputClass "evdev keyboard catchall"
[   119.103] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_1.3M'
[   119.103] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.103] (**) Laptop_Integrated_Webcam_1.3M: always reports core events
[   119.103] (**) Laptop_Integrated_Webcam_1.3M: Device: "/dev/input/event8"
[   119.103] (--) Laptop_Integrated_Webcam_1.3M: Found keys
[   119.103] (II) Laptop_Integrated_Webcam_1.3M: Configuring as keyboard
[   119.103] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input8/event8"
[   119.103] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_1.3M" (type: KEYBOARD)
[   119.103] (**) Option "xkb_rules" "evdev"
[   119.103] (**) Option "xkb_model" "pc105"
[   119.103] (**) Option "xkb_layout" "it"
[   119.104] (II) config/udev: Adding input device HDA Intel HDMI/DP,pcm=3 (/dev/input/event10)
[   119.104] (II) No input driver/identifier specified (ignoring)
[   119.104] (II) config/udev: Adding input device HDA Intel Mic at Ext Left Jack (/dev/input/event11)
[   119.104] (II) No input driver/identifier specified (ignoring)
[   119.104] (II) config/udev: Adding input device HDA Intel HP Out at Ext Left Jack (/dev/input/event12)
[   119.104] (II) No input driver/identifier specified (ignoring)
[   119.106] (II) config/udev: Adding input device HID 413c:8161 (/dev/input/event6)
[   119.106] (**) HID 413c:8161: Applying InputClass "evdev keyboard catchall"
[   119.106] (II) Using input driver 'evdev' for 'HID 413c:8161'
[   119.106] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.106] (**) HID 413c:8161: always reports core events
[   119.106] (**) HID 413c:8161: Device: "/dev/input/event6"
[   119.106] (--) HID 413c:8161: Found keys
[   119.106] (II) HID 413c:8161: Configuring as keyboard
[   119.106] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.1/2-1.6.1:1.0/input/input6/event6"
[   119.106] (II) XINPUT: Adding extended input device "HID 413c:8161" (type: KEYBOARD)
[   119.106] (**) Option "xkb_rules" "evdev"
[   119.106] (**) Option "xkb_model" "pc105"
[   119.106] (**) Option "xkb_layout" "it"
[   119.110] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   119.110] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   119.110] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   119.110] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.110] (**) AT Translated Set 2 keyboard: always reports core events
[   119.110] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[   119.110] (--) AT Translated Set 2 keyboard: Found keys
[   119.110] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   119.110] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[   119.110] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   119.110] (**) Option "xkb_rules" "evdev"
[   119.110] (**) Option "xkb_model" "pc105"
[   119.110] (**) Option "xkb_layout" "it"
[   119.110] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event13)
[   119.110] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   119.110] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   119.110] (II) LoadModule: "synaptics"
[   119.110] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   119.111] (II) Module synaptics: vendor="X.Org Foundation"
[   119.111] 	compiled for 1.10.4, module version = 1.4.1
[   119.111] 	Module class: X.Org XInput Driver
[   119.111] 	ABI class: X.Org XInput driver, version 12.3
[   119.111] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   119.111] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   119.111] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   119.111] (**) Option "Device" "/dev/input/event13"
[   119.132] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5650
[   119.132] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4710
[   119.132] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   119.132] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   119.132] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[   119.136] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   119.136] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   119.140] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input14/event13"
[   119.140] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[   119.140] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   119.140] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[   119.140] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.038
[   119.140] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   119.140] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   119.140] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   119.140] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   119.141] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   119.141] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[   119.141] (II) No input driver/identifier specified (ignoring)
[   119.150] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event7)
[   119.150] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[   119.150] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[   119.151] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.151] (**) Dell WMI hotkeys: always reports core events
[   119.151] (**) Dell WMI hotkeys: Device: "/dev/input/event7"
[   119.151] (--) Dell WMI hotkeys: Found keys
[   119.151] (II) Dell WMI hotkeys: Configuring as keyboard
[   119.151] (**) Option "config_info" "udev:/sys/devices/virtual/input/input9/event7"
[   119.151] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[   119.151] (**) Option "xkb_rules" "evdev"
[   119.151] (**) Option "xkb_model" "pc105"
[   119.151] (**) Option "xkb_layout" "it"
[   135.240] (II) AIGLX: Suspending AIGLX clients for VT switch
```

---

### Post by dino99 on 2012-02-21
might be due to Optimus, make your graphic choice into the bios. Then google about ubuntu+blumblebee

---

### Post by ric1321 on 2012-02-21
Sorry, I don't get it. What you mean for "graphic choice". Do I have to install bumblebee?

---

### Post by roelforg on 2012-02-21
> **ric1321 said:**
> tell me if this the correct Xorg log
```
[   118.824] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[   118.824] X Protocol Version 11, Revision 0
[   118.824] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[   118.824] Current Operating System: Linux riccardo-Inspiron-N5010 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64
[   118.824] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=34ef44cf-3cee-4aea-8cfd-59352f3c5ac8 ro quiet splash vt.handoff=7
[   118.824] Build Date: 19 October 2011  05:21:26AM
[   118.824] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[   118.824] Current version of pixman: 0.22.2
[   118.824]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   118.824] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   118.825] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 21 17:19:23 2012
[   118.825] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   118.825] (==) No Layout section.  Using the first Screen section.
[   118.825] (==) No screen section available. Using defaults.
[   118.825] (**) |-->Screen "Default Screen Section" (0)
[   118.825] (**) |   |-->Monitor "<default monitor>"
[   118.825] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   118.825] (==) Automatically adding devices
[   118.825] (==) Automatically enabling devices
[   118.825] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   118.825]     Entry deleted from font path.
[   118.825] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   118.825]     Entry deleted from font path.
[   118.825] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   118.825]     Entry deleted from font path.
[   118.825] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   118.825]     Entry deleted from font path.
[   118.825] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   118.825]     Entry deleted from font path.
[   118.825] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   118.825] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   118.825] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   118.825] (II) Loader magic: 0x7e0220
[   118.825] (II) Module ABI versions:
[   118.825]     X.Org ANSI C Emulation: 0.4
[   118.825]     X.Org Video Driver: 10.0
[   118.825]     X.Org XInput driver : 12.3
[   118.825]     X.Org Server Extension : 5.0
[   118.826] (--) PCI:*(0:0:2:0) 8086:0046:1028:0447 rev 24, Mem @ 0xfa400000/4194304, 0xc0000000/268435456, I/O @ 0x0000f080/8
[   118.826] (II) Open ACPI successful (/var/run/acpid.socket)
[   118.826] (II) LoadModule: "extmod"
[   118.827] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   118.827] (II) Module extmod: vendor="X.Org Foundation"
[   118.827]     compiled for 1.10.4, module version = 1.0.0
[   118.827]     Module class: X.Org Server Extension
[   118.827]     ABI class: X.Org Server Extension, version 5.0
[   118.827] (II) Loading extension MIT-SCREEN-SAVER
[   118.827] (II) Loading extension XFree86-VidModeExtension
[   118.827] (II) Loading extension XFree86-DGA
[   118.827] (II) Loading extension DPMS
[   118.827] (II) Loading extension XVideo
[   118.827] (II) Loading extension XVideo-MotionCompensation
[   118.827] (II) Loading extension X-Resource
[   118.827] (II) LoadModule: "dbe"
[   118.827] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   118.827] (II) Module dbe: vendor="X.Org Foundation"
[   118.827]     compiled for 1.10.4, module version = 1.0.0
[   118.827]     Module class: X.Org Server Extension
[   118.827]     ABI class: X.Org Server Extension, version 5.0
[   118.827] (II) Loading extension DOUBLE-BUFFER
[   118.827] (II) LoadModule: "glx"
[   118.828] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   118.828] (II) Module glx: vendor="X.Org Foundation"
[   118.828]     compiled for 1.10.4, module version = 1.0.0
[   118.828]     ABI class: X.Org Server Extension, version 5.0
[   118.828] (==) AIGLX enabled
[   118.828] (II) Loading extension GLX
[   118.828] (II) LoadModule: "record"
[   118.828] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   118.828] (II) Module record: vendor="X.Org Foundation"
[   118.828]     compiled for 1.10.4, module version = 1.13.0
[   118.828]     Module class: X.Org Server Extension
[   118.828]     ABI class: X.Org Server Extension, version 5.0
[   118.828] (II) Loading extension RECORD
[   118.828] (II) LoadModule: "dri"
[   118.829] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   118.829] (II) Module dri: vendor="X.Org Foundation"
[   118.829]     compiled for 1.10.4, module version = 1.0.0
[   118.829]     ABI class: X.Org Server Extension, version 5.0
[   118.829] (II) Loading extension XFree86-DRI
[   118.829] (II) LoadModule: "dri2"
[   118.829] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   118.829] (II) Module dri2: vendor="X.Org Foundation"
[   118.829]     compiled for 1.10.4, module version = 1.2.0
[   118.829]     ABI class: X.Org Server Extension, version 5.0
[   118.829] (II) Loading extension DRI2
[   118.829] (==) Matched intel as autoconfigured driver 0
[   118.829] (==) Matched vesa as autoconfigured driver 1
[   118.829] (==) Matched fbdev as autoconfigured driver 2
[   118.829] (==) Assigned the driver to the xf86ConfigLayout
[   118.829] (II) LoadModule: "intel"
[   118.830] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   118.830] (II) Module intel: vendor="X.Org Foundation"
[   118.830]     compiled for 1.10.4, module version = 2.15.901
[   118.830]     Module class: X.Org Video Driver
[   118.830]     ABI class: X.Org Video Driver, version 10.0
[   118.830] (II) LoadModule: "vesa"
[   118.830] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   118.830] (II) Module vesa: vendor="X.Org Foundation"
[   118.830]     compiled for 1.10.2, module version = 2.3.0
[   118.830]     Module class: X.Org Video Driver
[   118.830]     ABI class: X.Org Video Driver, version 10.0
[   118.830] (II) LoadModule: "fbdev"
[   118.831] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   118.831] (II) Module fbdev: vendor="X.Org Foundation"
[   118.831]     compiled for 1.10.0, module version = 0.4.2
[   118.831]     ABI class: X.Org Video Driver, version 10.0
[   118.831] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[   118.831] (II) VESA: driver for VESA chipsets: vesa
[   118.831] (II) FBDEV: driver for framebuffer: fbdev
[   118.831] (++) using VT number 7

[   118.833] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   118.833] (WW) Falling back to old probe method for vesa
[   118.833] (WW) Falling back to old probe method for fbdev
[   118.833] (II) Loading sub module "fbdevhw"
[   118.833] (II) LoadModule: "fbdevhw"
[   118.834] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   118.834] (II) Module fbdevhw: vendor="X.Org Foundation"
[   118.834]     compiled for 1.10.4, module version = 0.0.2
[   118.834]     ABI class: X.Org Video Driver, version 10.0
[   118.834] drmOpenDevice: node name is /dev/dri/card0
[   118.834] drmOpenDevice: open result is 12, (OK)
[   118.834] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[   118.834] drmOpenDevice: node name is /dev/dri/card0
[   118.834] drmOpenDevice: open result is 12, (OK)
[   118.834] drmOpenByBusid: drmOpenMinor returns 12
[   118.834] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[   118.834] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   118.834] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   118.834] (==) intel(0): RGB weight 888
[   118.834] (==) intel(0): Default visual is TrueColor
[   118.834] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[   118.834] (--) intel(0): Chipset: "Arrandale"
[   118.834] (**) intel(0): Relaxed fencing enabled
[   118.834] (**) intel(0): Wait on SwapBuffers? enabled
[   118.834] (**) intel(0): Triple buffering? enabled
[   118.834] (**) intel(0): Framebuffer tiled
[   118.834] (**) intel(0): Pixmaps tiled
[   118.834] (**) intel(0): 3D buffers tiled
[   118.834] (**) intel(0): SwapBuffers wait enabled
[   118.834] (==) intel(0): video overlay key set to 0x101fe
[   118.834] (II) intel(0): Output LVDS1 has no monitor section
[   118.834] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[   118.834] (II) intel(0): Output VGA1 has no monitor section
[   118.857] (II) intel(0): Output HDMI1 has no monitor section
[   118.904] (II) intel(0): Output DP1 has no monitor section
[   118.904] (II) intel(0): EDID for output LVDS1
[   118.904] (II) intel(0): Manufacturer: SEC  Model: 5441  Serial#: 0
[   118.904] (II) intel(0): Year: 2010  Week: 0
[   118.904] (II) intel(0): EDID Version: 1.3
[   118.904] (II) intel(0): Digital Display Input
[   118.904] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[   118.904] (II) intel(0): Gamma: 2.20
[   118.904] (II) intel(0): No DPMS capabilities specified
[   118.904] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   118.904] (II) intel(0): First detailed timing is preferred mode
[   118.904] (II) intel(0): redX: 0.620 redY: 0.340   greenX: 0.330 greenY: 0.570
[   118.904] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[   118.904] (II) intel(0): Manufacturer's mask: 0
[   118.904] (II) intel(0): Supported detailed timing:
[   118.904] (II) intel(0): clock: 71.6 MHz   Image Size:  344 x 194 mm
[   118.904] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1510 h_border: 0
[   118.904] (II) intel(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 789 v_border: 0
[   118.904] (II) intel(0): Supported detailed timing:
[   118.904] (II) intel(0): clock: 71.6 MHz   Image Size:  344 x 194 mm
[   118.904] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1510 h_border: 0
[   118.904] (II) intel(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 789 v_border: 0
[   118.904] (II) intel(0):  8MN61€156AT
[   118.904] (II) intel(0): Unknown vendor-specific block 0
[   118.904] (II) intel(0): EDID (in hex):
[   118.904] (II) intel(0):     00ffffffffffff004ca3415400000000
[   118.904] (II) intel(0):     00140103902213780ac8959e57549226
[   118.904] (II) intel(0):     0f505400000001010101010101010101
[   118.904] (II) intel(0):     010101010101f41b5690500015303020
[   118.904] (II) intel(0):     250058c21000001af41b569050001530
[   118.904] (II) intel(0):     3020250058c21000001a000000fe0038
[   118.904] (II) intel(0):     4d4e36318031353641540a2000000000
[   118.904] (II) intel(0):     00000000000000000001010a2020001d
[   118.904] (II) intel(0): EDID vendor "SEC", prod id 21569
[   118.904] (II) intel(0): Printing DDC gathered Modelines:
[   118.904] (II) intel(0): Modeline "1366x768"x0.0   71.56  1366 1414 1446 1510  768 770 775 789 +hsync -vsync (47.4 kHz)
[   118.904] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[   118.904] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[   118.905] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[   118.905] (II) intel(0): Printing probed modes for output LVDS1
[   118.905] (II) intel(0): Modeline "1366x768"x60.1   71.56  1366 1414 1446 1510  768 770 775 789 +hsync -vsync (47.4 kHz)
[   118.905] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[   118.905] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[   118.905] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   118.905] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   118.905] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   118.905] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   118.905] (II) intel(0): EDID for output VGA1
[   118.927] (II) intel(0): EDID for output HDMI1
[   118.976] (II) intel(0): EDID for output DP1
[   118.976] (II) intel(0): Output LVDS1 connected
[   118.976] (II) intel(0): Output VGA1 disconnected
[   118.976] (II) intel(0): Output HDMI1 disconnected
[   118.976] (II) intel(0): Output DP1 disconnected
[   118.976] (II) intel(0): Using exact sizes for initial modes
[   118.976] (II) intel(0): Output LVDS1 using initial mode 1366x768
[   118.976] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   118.976] (II) intel(0): Kernel page flipping support detected, enabling
[   118.976] (**) intel(0): Display dimensions: (340, 190) mm
[   118.976] (**) intel(0): DPI set to (102, 102)
[   118.976] (II) Loading sub module "fb"
[   118.976] (II) LoadModule: "fb"
[   118.976] (II) Loading /usr/lib/xorg/modules/libfb.so
[   118.976] (II) Module fb: vendor="X.Org Foundation"
[   118.976]     compiled for 1.10.4, module version = 1.0.0
[   118.976]     ABI class: X.Org ANSI C Emulation, version 0.4
[   118.976] (II) Loading sub module "dri2"
[   118.976] (II) LoadModule: "dri2"
[   118.977] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   118.977] (II) Module dri2: vendor="X.Org Foundation"
[   118.977]     compiled for 1.10.4, module version = 1.2.0
[   118.977]     ABI class: X.Org Server Extension, version 5.0
[   118.977] (II) UnloadModule: "vesa"
[   118.977] (II) Unloading vesa
[   118.977] (II) UnloadModule: "fbdev"
[   118.977] (II) Unloading fbdev
[   118.977] (II) UnloadModule: "fbdevhw"
[   118.977] (II) Unloading fbdevhw
[   118.977] (==) Depth 24 pixmap format is 32 bpp
[   118.977] (II) intel(0): [DRI2] Setup complete
[   118.977] (II) intel(0): [DRI2]   DRI driver: i965
[   118.977] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[   118.989] (II) UXA(0): Driver registered support for the following operations:
[   118.989] (II)         solid
[   118.989] (II)         copy
[   118.989] (II)         composite (RENDER acceleration)
[   118.989] (II)         put_image
[   118.989] (II)         get_image
[   118.989] (==) intel(0): Backing store disabled
[   118.989] (==) intel(0): Silken mouse enabled
[   118.989] (II) intel(0): Initializing HW Cursor
[   119.056] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   119.067] (==) intel(0): DPMS enabled
[   119.067] (==) intel(0): Intel XvMC decoder enabled
[   119.067] (II) intel(0): Set up textured video
[   119.067] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[   119.067] (II) intel(0): direct rendering: DRI2 Enabled
[   119.067] (==) intel(0): hotplug detection: "enabled"
[   119.067] (--) RandR disabled
[   119.067] (II) Initializing built-in extension Generic Event Extension
[   119.067] (II) Initializing built-in extension SHAPE
[   119.067] (II) Initializing built-in extension MIT-SHM
[   119.067] (II) Initializing built-in extension XInputExtension
[   119.067] (II) Initializing built-in extension XTEST
[   119.067] (II) Initializing built-in extension BIG-REQUESTS
[   119.067] (II) Initializing built-in extension SYNC
[   119.067] (II) Initializing built-in extension XKEYBOARD
[   119.067] (II) Initializing built-in extension XC-MISC
[   119.067] (II) Initializing built-in extension SECURITY
[   119.067] (II) Initializing built-in extension XINERAMA
[   119.067] (II) Initializing built-in extension XFIXES
[   119.067] (II) Initializing built-in extension RENDER
[   119.067] (II) Initializing built-in extension RANDR
[   119.067] (II) Initializing built-in extension COMPOSITE
[   119.067] (II) Initializing built-in extension DAMAGE
[   119.067] (II) Initializing built-in extension GESTURE
[   119.075] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
[   119.078] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   119.078] (II) AIGLX: enabled GLX_INTEL_swap_event
[   119.078] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   119.078] (II) AIGLX: enabled GLX_SGI_make_current_read
[   119.078] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   119.078] (II) AIGLX: Loaded and initialized i965
[   119.078] (II) GLX: Initialized DRI2 GL provider for screen 0
[   119.078] (II) intel(0): Setting screen physical size to 361 x 203
[   119.086] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   119.092] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   119.093] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   119.093] (II) LoadModule: "evdev"
[   119.093] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.093] (II) Module evdev: vendor="X.Org Foundation"
[   119.093]     compiled for 1.10.2, module version = 2.6.0
[   119.093]     Module class: X.Org XInput Driver
[   119.093]     ABI class: X.Org XInput driver, version 12.3
[   119.093] (II) Using input driver 'evdev' for 'Power Button'
[   119.093] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.093] (**) Power Button: always reports core events
[   119.094] (**) Power Button: Device: "/dev/input/event3"
[   119.094] (--) Power Button: Found keys
[   119.094] (II) Power Button: Configuring as keyboard
[   119.094] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[   119.094] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   119.094] (**) Option "xkb_rules" "evdev"
[   119.094] (**) Option "xkb_model" "pc105"
[   119.094] (**) Option "xkb_layout" "it"
[   119.095] (II) XKB: reuse xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.xkm
[   119.096] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[   119.096] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   119.096] (II) Using input driver 'evdev' for 'Video Bus'
[   119.096] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.096] (**) Video Bus: always reports core events
[   119.096] (**) Video Bus: Device: "/dev/input/event9"
[   119.096] (--) Video Bus: Found keys
[   119.096] (II) Video Bus: Configuring as keyboard
[   119.096] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input10/event9"
[   119.096] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   119.096] (**) Option "xkb_rules" "evdev"
[   119.096] (**) Option "xkb_model" "pc105"
[   119.097] (**) Option "xkb_layout" "it"
[   119.099] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   119.099] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   119.099] (II) Using input driver 'evdev' for 'Power Button'
[   119.099] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.099] (**) Power Button: always reports core events
[   119.099] (**) Power Button: Device: "/dev/input/event0"
[   119.099] (--) Power Button: Found keys
[   119.099] (II) Power Button: Configuring as keyboard
[   119.099] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   119.099] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   119.099] (**) Option "xkb_rules" "evdev"
[   119.099] (**) Option "xkb_model" "pc105"
[   119.099] (**) Option "xkb_layout" "it"
[   119.100] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[   119.100] (II) No input driver/identifier specified (ignoring)
[   119.100] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[   119.100] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   119.100] (II) Using input driver 'evdev' for 'Sleep Button'
[   119.100] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.100] (**) Sleep Button: always reports core events
[   119.100] (**) Sleep Button: Device: "/dev/input/event2"
[   119.100] (--) Sleep Button: Found keys
[   119.100] (II) Sleep Button: Configuring as keyboard
[   119.100] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[   119.100] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   119.100] (**) Option "xkb_rules" "evdev"
[   119.100] (**) Option "xkb_model" "pc105"
[   119.100] (**) Option "xkb_layout" "it"
[   119.102] (II) config/udev: Adding input device HP Wireless Optical Mobile Mouse (/dev/input/event5)
[   119.102] (**) HP Wireless Optical Mobile Mouse: Applying InputClass "evdev pointer catchall"
[   119.102] (II) Using input driver 'evdev' for 'HP Wireless Optical Mobile Mouse'
[   119.102] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.102] (**) HP Wireless Optical Mobile Mouse: always reports core events
[   119.102] (**) HP Wireless Optical Mobile Mouse: Device: "/dev/input/event5"
[   119.102] (--) HP Wireless Optical Mobile Mouse: Found 3 mouse buttons
[   119.102] (--) HP Wireless Optical Mobile Mouse: Found scroll wheel(s)
[   119.102] (--) HP Wireless Optical Mobile Mouse: Found relative axes
[   119.102] (--) HP Wireless Optical Mobile Mouse: Found x and y relative axes
[   119.102] (II) HP Wireless Optical Mobile Mouse: Configuring as mouse
[   119.102] (II) HP Wireless Optical Mobile Mouse: Adding scrollwheel support
[   119.102] (**) HP Wireless Optical Mobile Mouse: YAxisMapping: buttons 4 and 5
[   119.102] (**) HP Wireless Optical Mobile Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   119.102] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input5/event5"
[   119.102] (II) XINPUT: Adding extended input device "HP Wireless Optical Mobile Mouse" (type: MOUSE)
[   119.102] (II) HP Wireless Optical Mobile Mouse: initialized for relative axes.
[   119.102] (**) HP Wireless Optical Mobile Mouse: (accel) keeping acceleration scheme 1
[   119.102] (**) HP Wireless Optical Mobile Mouse: (accel) acceleration profile 0
[   119.102] (**) HP Wireless Optical Mobile Mouse: (accel) acceleration factor: 2.000
[   119.102] (**) HP Wireless Optical Mobile Mouse: (accel) acceleration threshold: 4
[   119.102] (II) config/udev: Adding input device HP Wireless Optical Mobile Mouse (/dev/input/mouse0)
[   119.102] (II) No input driver/identifier specified (ignoring)
[   119.103] (II) config/udev: Adding input device Laptop_Integrated_Webcam_1.3M (/dev/input/event8)
[   119.103] (**) Laptop_Integrated_Webcam_1.3M: Applying InputClass "evdev keyboard catchall"
[   119.103] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_1.3M'
[   119.103] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.103] (**) Laptop_Integrated_Webcam_1.3M: always reports core events
[   119.103] (**) Laptop_Integrated_Webcam_1.3M: Device: "/dev/input/event8"
[   119.103] (--) Laptop_Integrated_Webcam_1.3M: Found keys
[   119.103] (II) Laptop_Integrated_Webcam_1.3M: Configuring as keyboard
[   119.103] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input8/event8"
[   119.103] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_1.3M" (type: KEYBOARD)
[   119.103] (**) Option "xkb_rules" "evdev"
[   119.103] (**) Option "xkb_model" "pc105"
[   119.103] (**) Option "xkb_layout" "it"
[   119.104] (II) config/udev: Adding input device HDA Intel HDMI/DP,pcm=3 (/dev/input/event10)
[   119.104] (II) No input driver/identifier specified (ignoring)
[   119.104] (II) config/udev: Adding input device HDA Intel Mic at Ext Left Jack (/dev/input/event11)
[   119.104] (II) No input driver/identifier specified (ignoring)
[   119.104] (II) config/udev: Adding input device HDA Intel HP Out at Ext Left Jack (/dev/input/event12)
[   119.104] (II) No input driver/identifier specified (ignoring)
[   119.106] (II) config/udev: Adding input device HID 413c:8161 (/dev/input/event6)
[   119.106] (**) HID 413c:8161: Applying InputClass "evdev keyboard catchall"
[   119.106] (II) Using input driver 'evdev' for 'HID 413c:8161'
[   119.106] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.106] (**) HID 413c:8161: always reports core events
[   119.106] (**) HID 413c:8161: Device: "/dev/input/event6"
[   119.106] (--) HID 413c:8161: Found keys
[   119.106] (II) HID 413c:8161: Configuring as keyboard
[   119.106] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.1/2-1.6.1:1.0/input/input6/event6"
[   119.106] (II) XINPUT: Adding extended input device "HID 413c:8161" (type: KEYBOARD)
[   119.106] (**) Option "xkb_rules" "evdev"
[   119.106] (**) Option "xkb_model" "pc105"
[   119.106] (**) Option "xkb_layout" "it"
[   119.110] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   119.110] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   119.110] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   119.110] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.110] (**) AT Translated Set 2 keyboard: always reports core events
[   119.110] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[   119.110] (--) AT Translated Set 2 keyboard: Found keys
[   119.110] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   119.110] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[   119.110] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   119.110] (**) Option "xkb_rules" "evdev"
[   119.110] (**) Option "xkb_model" "pc105"
[   119.110] (**) Option "xkb_layout" "it"
[   119.110] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event13)
[   119.110] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   119.110] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   119.110] (II) LoadModule: "synaptics"
[   119.110] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   119.111] (II) Module synaptics: vendor="X.Org Foundation"
[   119.111]     compiled for 1.10.4, module version = 1.4.1
[   119.111]     Module class: X.Org XInput Driver
[   119.111]     ABI class: X.Org XInput driver, version 12.3
[   119.111] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   119.111] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   119.111] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   119.111] (**) Option "Device" "/dev/input/event13"
[   119.132] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5650
[   119.132] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4710
[   119.132] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   119.132] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   119.132] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[   119.136] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   119.136] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   119.140] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input14/event13"
[   119.140] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[   119.140] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   119.140] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[   119.140] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.038
[   119.140] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   119.140] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   119.140] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   119.140] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   119.141] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   119.141] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[   119.141] (II) No input driver/identifier specified (ignoring)
[   119.150] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event7)
[   119.150] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[   119.150] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[   119.151] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   119.151] (**) Dell WMI hotkeys: always reports core events
[   119.151] (**) Dell WMI hotkeys: Device: "/dev/input/event7"
[   119.151] (--) Dell WMI hotkeys: Found keys
[   119.151] (II) Dell WMI hotkeys: Configuring as keyboard
[   119.151] (**) Option "config_info" "udev:/sys/devices/virtual/input/input9/event7"
[   119.151] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[   119.151] (**) Option "xkb_rules" "evdev"
[   119.151] (**) Option "xkb_model" "pc105"
[   119.151] (**) Option "xkb_layout" "it"
[   135.240] (II) AIGLX: Suspending AIGLX clients for VT switch
```

Glad you figured out how to mount usb drives (there's a wiki page about that if you need more info).

dmesg.log is just a text file,
are you sure you did
```

dmesg > dmesg.log

```
as root from your usb dir?

It seems as if Xorg crashes so i need the dmesg log and both Xorg logs.

I don't think the dmesg.log is tar.gz,
you cant read either file in windows notepad...
Let me explain why:
In text files there are special ascii codes inserted for a new line, the one windows uses is different from the standard (Yep, windows ignores the ascii standard).
Windows: \r\n
Linux/ASCII_standard: \n
Windows isn't filling in the new line, i recommend getting notepad++, it handles them just fine.

I have 1 thing i want you to try:
when grub comes on, press e
use the arrow keys to navigate to the longest line (should start with vmlinux-), after the word quiet insert space and insert nomodeset
Press CTRL-X.
If it works, i'll give you instructions to make it permanent.

---

### Post by ric1321 on 2012-02-21
Ok, thank you. I did ```
dmesg > dmesg.log
``` but i have no dmesg.log, just a dmesg pure, which i can't read with windows. What am I supposed to do, working on this dmesg problem or "nomodeset"?

---

### Post by roelforg on 2012-02-21
> **ric1321 said:**
> Ok, thank you. I did ```
dmesg > dmesg.log
``` but i have no dmesg.log, just a dmesg pure, which i can't read with windows. What am I supposed to do, working on this dmesg problem or "nomodeset"?
May i add that windows hides file extensions?
Try this: open word/notepad, scribble a bit in the file and save it; open explorer and visit the folder, i don't think your gonna see the .docx/.doc/.txt extension, same thing goes for the dmesg.log file, or as explorer will show it: dmesg.
Just upload the dmesg file.
The nomodeset is something that might help, one of my pc's needs it as well (some odd chipset).

---

### Post by ric1321 on 2012-02-21
it doesn't work with nomodeset

---

### Post by roelforg on 2012-02-21
> **ric1321 said:**
> it doesn't work with nomodeset
Can i see dmesg?

---

### Post by roelforg on 2012-02-21
The reason i think Xorg is crashing is this:

A correctly functioning Xorg would produce the following as the last log entry's when shutting down.
```

[  3684.610] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  3684.610] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  3684.610] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[  3684.610] (II) intel(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[ 26608.538] (II) Power Button: Close
[ 26608.769] (II) UnloadModule: "evdev"
[ 26608.769] (II) Unloading evdev
[ 26608.769] (II) Power Button: Close
[ 26608.769] (II) UnloadModule: "evdev"
[ 26608.769] (II) Unloading evdev
[ 26608.771] (II) Quanta Computer Inc. Optical Touch Screen: Close
[ 26608.774] (II) UnloadModule: "evdev"
[ 26608.774] (II) Unloading evdev
[ 26608.774] (II) AT Translated Set 2 keyboard: Close
[ 26608.774] (II) UnloadModule: "evdev"
[ 26608.774] (II) Unloading evdev
[ 26608.775] (II) ImPS/2 Logitech Wheel Mouse: Close
[ 26608.775] (II) UnloadModule: "evdev"
[ 26608.775] (II) Unloading evdev
[ 26609.009]  ddxSigGiveUp: Closing log

```(the first 4 lines are boot entry's, note the difference in time stamps to see when i shut my pc down)

Your's just ends w/o that last line in the log (or any shutdown messages at all), it's the line Xorg outputs when it shuts is logger down.

FYI. My screen is also a touch screen so that explains the Messages about the Quanta HW.

---

### Post by ric1321 on 2012-02-21
Here I have some lines of dmesg log:
```
[   12.790983] [drm] Initialized drm 1.1.0 20060810
[   12.791156] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   12.791583] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.791591] mei 0000:00:16.0: setting latency timer to 64
[   12.793950] lp: driver loaded but no devices found
[   12.800651] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.800658] i915 0000:00:02.0: setting latency timer to 64
[   12.801149] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.801152] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   12.801233] iwlagn 0000:12:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.801242] iwlagn 0000:12:00.0: setting latency timer to 64
[   12.801275] iwlagn 0000:12:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   12.821871] iwlagn 0000:12:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   12.821876] iwlagn 0000:12:00.0: Device SKU: 0X9
[   12.821878] iwlagn 0000:12:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   12.823202] type=1400 audit(1329841057.155:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=414 comm="apparmor_parser"
[   12.823591] type=1400 audit(1329841057.155:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=414 comm="apparmor_parser"
[   12.823852] type=1400 audit(1329841057.155:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=414 comm="apparmor_parser"
[   12.826094] Adding 6394876k swap on /dev/sda6.  Priority:-1 extents:1 across:6394876k 
[   12.826269] iwlagn 0000:12:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   12.826366] iwlagn 0000:12:00.0: irq 46 for MSI/MSI-X
[   12.856753] i915 0000:00:02.0: irq 47 for MSI/MSI-X
[   12.856761] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.856763] [drm] Driver supports precise vblank timestamp query.
[   12.856817] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.879859] wmi: Mapper loaded
[   12.920475] Linux video capture interface: v2.00
[   12.921193] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:6480)
[   12.943217] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input8
[   12.943368] usbcore: registered new interface driver uvcvideo
[   12.943370] USB Video Class driver (v1.1.0)
[   13.002542] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   13.106548] cfg80211: World regulatory domain updated:
[   13.106552] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.106555] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.106558] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.106561] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.106564] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.106566] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.113033] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   13.136433] iwlagn 0000:12:00.0: loaded firmware version 39.31.5.1 build 35138
[   13.136602] Registered led device: phy0-led
[   13.136633] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   13.140618] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.171263] fbcon: inteldrmfb (fb0) is primary device
[   13.171360] Console: switching to colour frame buffer device 170x48
[   13.171389] fb0: inteldrmfb frame buffer device
[   13.171391] drm: registered panic notifier
[   13.181492] acpi device:2e: registered as cooling_device4
[   13.181654] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input10
[   13.181706] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.181765] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.181787] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   13.181803] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   13.182002] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   13.182048] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.182106] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   13.182137] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.214178] usb 2-1.6.3: new full speed USB device number 6 using ehci_hcd
[   13.242807] HDMI status: Pin=4 Presence_Detect=0 ELD_Valid=0
[   13.243082] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   13.243200] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   13.243253] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   13.299514] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   13.317429] Bluetooth: Core ver 2.16
[   13.317458] NET: Registered protocol family 31
[   13.317460] Bluetooth: HCI device and connection manager initialized
[   13.317463] Bluetooth: HCI socket layer initialized
[   13.317464] Bluetooth: L2CAP socket layer initialized
[   13.318161] Bluetooth: SCO socket layer initialized
[   13.318511] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   13.318946] usbcore: registered new interface driver btusb
[   13.979468] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   14.055125] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input14
[   14.218511] ppdev: user-space parallel port driver
[   14.226781] type=1400 audit(1329841058.559:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1019 comm="apparmor_parser"
[   14.227199] type=1400 audit(1329841058.559:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1019 comm="apparmor_parser"
[   14.455738] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.461414] r8169 0000:13:00.0: eth0: link down
[   14.462205] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.570215] wlan0: authenticate with 00:0d:f0:2d:99:30 (try 1)
[   16.572528] wlan0: authenticated
[   16.586100] wlan0: associate with 00:0d:f0:2d:99:30 (try 1)
[   16.588933] wlan0: RX AssocResp from 00:0d:f0:2d:99:30 (capab=0x421 status=0 aid=2)
[   16.588940] wlan0: associated
[   16.594129] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.456598] type=1400 audit(1329841068.795:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1105 comm="apparmor_parser"
[   24.457126] type=1400 audit(1329841068.795:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1105 comm="apparmor_parser"
[   24.457299] type=1400 audit(1329841068.795:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1104 comm="apparmor_parser"
[   24.457464] type=1400 audit(1329841068.795:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1105 comm="apparmor_parser"
[   24.457622] type=1400 audit(1329841068.795:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1108 comm="apparmor_parser"
[   24.458056] type=1400 audit(1329841068.795:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1108 comm="apparmor_parser"
[   24.459643] type=1400 audit(1329841068.795:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1110 comm="apparmor_parser"
[   24.460007] type=1400 audit(1329841068.799:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1109 comm="apparmor_parser"
[   24.460444] type=1400 audit(1329841068.799:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1109 comm="apparmor_parser"
[   24.461637] type=1400 audit(1329841068.799:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1106 comm="apparmor_parser"
[   24.542251] init: failsafe main process (953) killed by TERM signal
[   24.543379] init: apport pre-start process (1141) terminated with status 1
[   24.564662] init: apport post-stop process (1174) terminated with status 1
```

---

### Post by roelforg on 2012-02-21
> **ric1321 said:**
> Here I have some lines of dmesg log:
```
[   12.790983] [drm] Initialized drm 1.1.0 20060810
[   12.791156] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   12.791583] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.791591] mei 0000:00:16.0: setting latency timer to 64
[   12.793950] lp: driver loaded but no devices found
[   12.800651] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.800658] i915 0000:00:02.0: setting latency timer to 64
[   12.801149] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.801152] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   12.801233] iwlagn 0000:12:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.801242] iwlagn 0000:12:00.0: setting latency timer to 64
[   12.801275] iwlagn 0000:12:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   12.821871] iwlagn 0000:12:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   12.821876] iwlagn 0000:12:00.0: Device SKU: 0X9
[   12.821878] iwlagn 0000:12:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   12.823202] type=1400 audit(1329841057.155:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=414 comm="apparmor_parser"
[   12.823591] type=1400 audit(1329841057.155:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=414 comm="apparmor_parser"
[   12.823852] type=1400 audit(1329841057.155:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=414 comm="apparmor_parser"
[   12.826094] Adding 6394876k swap on /dev/sda6.  Priority:-1 extents:1 across:6394876k 
[   12.826269] iwlagn 0000:12:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   12.826366] iwlagn 0000:12:00.0: irq 46 for MSI/MSI-X
[   12.856753] i915 0000:00:02.0: irq 47 for MSI/MSI-X
[   12.856761] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.856763] [drm] Driver supports precise vblank timestamp query.
[   12.856817] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.879859] wmi: Mapper loaded
[   12.920475] Linux video capture interface: v2.00
[   12.921193] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:6480)
[   12.943217] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input8
[   12.943368] usbcore: registered new interface driver uvcvideo
[   12.943370] USB Video Class driver (v1.1.0)
[   13.002542] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   13.106548] cfg80211: World regulatory domain updated:
[   13.106552] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.106555] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.106558] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.106561] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.106564] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.106566] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.113033] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   13.136433] iwlagn 0000:12:00.0: loaded firmware version 39.31.5.1 build 35138
[   13.136602] Registered led device: phy0-led
[   13.136633] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   13.140618] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.171263] fbcon: inteldrmfb (fb0) is primary device
[   13.171360] Console: switching to colour frame buffer device 170x48
[   13.171389] fb0: inteldrmfb frame buffer device
[   13.171391] drm: registered panic notifier
[   13.181492] acpi device:2e: registered as cooling_device4
[   13.181654] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input10
[   13.181706] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.181765] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.181787] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   13.181803] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   13.182002] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   13.182048] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.182106] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   13.182137] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.214178] usb 2-1.6.3: new full speed USB device number 6 using ehci_hcd
[   13.242807] HDMI status: Pin=4 Presence_Detect=0 ELD_Valid=0
[   13.243082] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   13.243200] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   13.243253] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   13.299514] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   13.317429] Bluetooth: Core ver 2.16
[   13.317458] NET: Registered protocol family 31
[   13.317460] Bluetooth: HCI device and connection manager initialized
[   13.317463] Bluetooth: HCI socket layer initialized
[   13.317464] Bluetooth: L2CAP socket layer initialized
[   13.318161] Bluetooth: SCO socket layer initialized
[   13.318511] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   13.318946] usbcore: registered new interface driver btusb
[   13.979468] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   14.055125] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input14
[   14.218511] ppdev: user-space parallel port driver
[   14.226781] type=1400 audit(1329841058.559:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1019 comm="apparmor_parser"
[   14.227199] type=1400 audit(1329841058.559:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1019 comm="apparmor_parser"
[   14.455738] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.461414] r8169 0000:13:00.0: eth0: link down
[   14.462205] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.570215] wlan0: authenticate with 00:0d:f0:2d:99:30 (try 1)
[   16.572528] wlan0: authenticated
[   16.586100] wlan0: associate with 00:0d:f0:2d:99:30 (try 1)
[   16.588933] wlan0: RX AssocResp from 00:0d:f0:2d:99:30 (capab=0x421 status=0 aid=2)
[   16.588940] wlan0: associated
[   16.594129] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.456598] type=1400 audit(1329841068.795:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1105 comm="apparmor_parser"
[   24.457126] type=1400 audit(1329841068.795:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1105 comm="apparmor_parser"
[   24.457299] type=1400 audit(1329841068.795:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1104 comm="apparmor_parser"
[   24.457464] type=1400 audit(1329841068.795:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1105 comm="apparmor_parser"
[   24.457622] type=1400 audit(1329841068.795:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1108 comm="apparmor_parser"
[   24.458056] type=1400 audit(1329841068.795:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1108 comm="apparmor_parser"
[   24.459643] type=1400 audit(1329841068.795:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1110 comm="apparmor_parser"
[   24.460007] type=1400 audit(1329841068.799:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1109 comm="apparmor_parser"
[   24.460444] type=1400 audit(1329841068.799:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1109 comm="apparmor_parser"
[   24.461637] type=1400 audit(1329841068.799:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1106 comm="apparmor_parser"
[   24.542251] init: failsafe main process (953) killed by TERM signal
[   24.543379] init: apport pre-start process (1141) terminated with status 1
[   24.564662] init: apport post-stop process (1174) terminated with status 1
```

What you show me worries me, please post the entire file (try the upload option when replying).
It appears that something is stopping init of init is crashing by itself.
One dangerous option might solve it (i'm not responsible for the outcome), but i'd wait with this until someone tells you to, it's really really dangerous:
```

sudo apt-get install -reinstall -y upstart

```Let me explain what it does,
linux uses the program init to control the starting and stopping of programs and daemons, the command will reinstall upstart (init) but it might break some configs so it's kinda the last possible solution one might try before reinstalling...
But i really want the dmesg logs so i can find out what is causing it, or at least i hope to.

---

### Post by ric1321 on 2012-02-21
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-16-generic (buildd@allspice) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 (Ubuntu 3.0.0-16.28-generic 3.0.17)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=34ef44cf-3cee-4aea-8cfd-59352f3c5ac8 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
[    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b75a6000 (usable)
[    0.000000]  BIOS-e820: 00000000b75a6000 - 00000000b75ee000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b75ee000 - 00000000b75f9000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b75f9000 - 00000000b75fc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b75fc000 - 00000000b7620000 (reserved)
[    0.000000]  BIOS-e820: 00000000b7620000 - 00000000b7621000 (usable)
[    0.000000]  BIOS-e820: 00000000b7621000 - 00000000b7629000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7629000 - 00000000b762c000 (reserved)
[    0.000000]  BIOS-e820: 00000000b762c000 - 00000000b7631000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7631000 - 00000000b7651000 (reserved)
[    0.000000]  BIOS-e820: 00000000b7651000 - 00000000b7694000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7694000 - 00000000b7800000 (usable)
[    0.000000]  BIOS-e820: 00000000b9e00000 - 00000000bc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Dell Inc. Inspiron N5010/0WXY9J, BIOS A10 11/17/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0xb7800 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 0B8000000 mask FF8000000 uncachable
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 2944MB, range: 128MB, type UC
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 2944M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 256M 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 2944MB, range: 128MB, type UC
[    0.000000] found SMP MP-table at [ffff8800000fcda0] fcda0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000b7800000
[    0.000000]  0000000000 - 00b7800000 page 2M
[    0.000000] kernel direct mapping tables up to b7800000 @ 1fffc000-20000000
[    0.000000] RAMDISK: 365c2000 - 372d9000
[    0.000000] ACPI: RSDP 00000000000f0410 00024 (v03 DELL  )
[    0.000000] ACPI: XSDT 00000000b75ee088 0005C (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000b75f7a50 000F4 (v04 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110413/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xB762CF40/0x00000000B762CF80, using 32 (20110413/tbfadt-489)
[    0.000000] ACPI: DSDT 00000000b75ee170 098DF (v02 DELL    WN09    00005010 INTL 20051117)
[    0.000000] ACPI: FACS 00000000b762cf40 00040
[    0.000000] ACPI: APIC 00000000b75f7b48 00072 (v01 DELL   WN09     01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 00000000b75f7bc0 0014E (v01 AMICPU     PROC 00000001 MSFT 03000001)
[    0.000000] ACPI: MCFG 00000000b75f7d10 0003C (v01   DELL     WN09 01072009 MSFT 00000097)
[    0.000000] ACPI: SLIC 00000000b75f7d50 00176 (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: HPET 00000000b75f7ec8 00038 (v01   DELL     WN09 01072009 AMI. 00000003)
[    0.000000] ACPI: OSFR 00000000b75f7f00 0008C (v01 DELL    M08     07DA0B11 ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000000b7800000
[    0.000000] Initmem setup node 0 0000000000000000-00000000b7800000
[    0.000000]   NODE_DATA [00000000b77fb000 - 00000000b77fffff]
[    0.000000]  [ffffea0000000000-ffffea00029fffff] PMD -> [ffff8800b3e00000-ffff8800b67fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000b75a6
[    0.000000]     0: 0x000b7620 -> 0x000b7621
[    0.000000]     0: 0x000b7694 -> 0x000b7800
[    0.000000] On node 0 totalpages: 751264
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3920 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10220 pages used for memmap
[    0.000000]   DMA32 zone: 737063 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000b75a6000 - 00000000b75ee000
[    0.000000] PM: Registered nosave memory: 00000000b75ee000 - 00000000b75f9000
[    0.000000] PM: Registered nosave memory: 00000000b75f9000 - 00000000b75fc000
[    0.000000] PM: Registered nosave memory: 00000000b75fc000 - 00000000b7620000
[    0.000000] PM: Registered nosave memory: 00000000b7621000 - 00000000b7629000
[    0.000000] PM: Registered nosave memory: 00000000b7629000 - 00000000b762c000
[    0.000000] PM: Registered nosave memory: 00000000b762c000 - 00000000b7631000
[    0.000000] PM: Registered nosave memory: 00000000b7631000 - 00000000b7651000
[    0.000000] PM: Registered nosave memory: 00000000b7651000 - 00000000b7694000
[    0.000000] Allocating PCI resources starting at bc000000 (gap: bc000000:24000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff8800b7200000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 740983
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=34ef44cf-3cee-4aea-8cfd-59352f3c5ac8 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2932592k/3006464k available (6138k kernel code, 1408k absent, 72464k reserved, 6896k data, 988k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 24117248 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2526.980 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5053.96 BogoMIPS (lpj=10107920)
[    0.000008] pid_max: default: 32768 minimum: 301
[    0.000035] Security Framework initialized
[    0.000052] AppArmor: AppArmor initialized
[    0.000053] Yama: becoming mindful.
[    0.000476] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002172] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002925] Mount-cache hash table entries: 256
[    0.003058] Initializing cgroup subsys cpuacct
[    0.003063] Initializing cgroup subsys memory
[    0.003071] Initializing cgroup subsys devices
[    0.003073] Initializing cgroup subsys freezer
[    0.003075] Initializing cgroup subsys net_cls
[    0.003077] Initializing cgroup subsys blkio
[    0.003084] Initializing cgroup subsys perf_event
[    0.003113] CPU: Physical Processor ID: 0
[    0.003114] CPU: Processor Core ID: 0
[    0.003120] mce: CPU supports 9 MCE banks
[    0.003133] CPU0: Thermal monitoring enabled (TM1)
[    0.003142] using mwait in idle threads.
[    0.005449] ACPI: Core revision 20110413
[    0.018717] ftrace: allocating 25737 entries in 101 pages
[    0.027385] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067048] CPU0: Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz stepping 05
[    0.171555] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.171563] ... version:                3
[    0.171564] ... bit width:              48
[    0.171565] ... generic registers:      4
[    0.171567] ... value mask:             0000ffffffffffff
[    0.171568] ... max period:             000000007fffffff
[    0.171569] ... fixed-purpose events:   3
[    0.171571] ... event mask:             000000070000000f
[    0.172007] Booting Node   0, Processors  #1
[    0.172010] smpboot cpu 1: start_ip = 98000
[    0.279664]  #2
[    0.279667] smpboot cpu 2: start_ip = 98000
[    0.387679]  #3 Ok.
[    0.387683] smpboot cpu 3: start_ip = 98000
[    0.495512] Brought up 4 CPUs
[    0.495516] Total of 4 processors activated (20215.66 BogoMIPS).
[    0.497876] devtmpfs: initialized
[    0.498002] PM: Registering ACPI NVS region at b75a6000 (294912 bytes)
[    0.498009] PM: Registering ACPI NVS region at b75f9000 (12288 bytes)
[    0.498011] PM: Registering ACPI NVS region at b7621000 (32768 bytes)
[    0.498013] PM: Registering ACPI NVS region at b762c000 (20480 bytes)
[    0.498014] PM: Registering ACPI NVS region at b7651000 (274432 bytes)
[    0.499401] print_constraints: dummy: 
[    0.499429] Time: 17:17:24  Date: 02/21/12
[    0.499460] NET: Registered protocol family 16
[    0.499561] Trying to unpack rootfs image as initramfs...
[    0.499565] ACPI: bus type pci registered
[    0.499620] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.499623] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.540031] PCI: Using configuration type 1 for base access
[    0.540753] bio: create slab <bio-0> at 0
[    0.542111] ACPI: EC: Look up EC in DSDT
[    0.543408] ACPI: Executed 1 blocks of module-level executable AML code
[    0.547463] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.583738] ACPI: SSDT 00000000b7621c18 003A4 (v01    AMI      IST 00000001 MSFT 03000001)
[    0.584087] ACPI: Dynamic OEM Table Load:
[    0.584089] ACPI: SSDT           (null) 003A4 (v01    AMI      IST 00000001 MSFT 03000001)
[    0.584495] ACPI: Interpreter enabled
[    0.584498] ACPI: (supports S0 S3 S4 S5)
[    0.584517] ACPI: Using IOAPIC for interrupt routing
[    0.584743] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.601972] ACPI: No dock devices found.
[    0.601975] HEST: Table not found.
[    0.601978] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.602094] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.602181] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.602183] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.602185] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.602187] pci_root PNP0A08:00: host bridge window [mem 0xbc000000-0xffffffff]
[    0.602199] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
[    0.602217] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.602235] pci 0000:00:02.0: [8086:0046] type 0 class 0x000300
[    0.602245] pci 0000:00:02.0: reg 10: [mem 0xfa400000-0xfa7fffff 64bit]
[    0.602251] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.602256] pci 0000:00:02.0: reg 20: [io  0xf080-0xf087]
[    0.602314] pci 0000:00:16.0: [8086:3b64] type 0 class 0x000780
[    0.602342] pci 0000:00:16.0: reg 10: [mem 0xfbd09000-0xfbd0900f 64bit]
[    0.602423] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.602427] pci 0000:00:16.0: PME# disabled
[    0.602467] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    0.602492] pci 0000:00:1a.0: reg 10: [mem 0xfbd08000-0xfbd083ff]
[    0.602579] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.602583] pci 0000:00:1a.0: PME# disabled
[    0.602612] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    0.602632] pci 0000:00:1b.0: reg 10: [mem 0xfbd00000-0xfbd03fff 64bit]
[    0.602708] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.602712] pci 0000:00:1b.0: PME# disabled
[    0.602739] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    0.602816] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.602820] pci 0000:00:1c.0: PME# disabled
[    0.602847] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
[    0.602923] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.602928] pci 0000:00:1c.1: PME# disabled
[    0.602955] pci 0000:00:1c.2: [8086:3b46] type 1 class 0x000604
[    0.603031] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.603035] pci 0000:00:1c.2: PME# disabled
[    0.603065] pci 0000:00:1c.4: [8086:3b4a] type 1 class 0x000604
[    0.603142] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.603147] pci 0000:00:1c.4: PME# disabled
[    0.603183] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    0.603207] pci 0000:00:1d.0: reg 10: [mem 0xfbd07000-0xfbd073ff]
[    0.603294] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.603298] pci 0000:00:1d.0: PME# disabled
[    0.603329] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.603403] pci 0000:00:1f.0: [8086:3b0b] type 0 class 0x000601
[    0.603521] pci 0000:00:1f.2: [8086:3b2f] type 0 class 0x000106
[    0.603548] pci 0000:00:1f.2: reg 10: [io  0xf070-0xf077]
[    0.603559] pci 0000:00:1f.2: reg 14: [io  0xf060-0xf063]
[    0.603569] pci 0000:00:1f.2: reg 18: [io  0xf050-0xf057]
[    0.603580] pci 0000:00:1f.2: reg 1c: [io  0xf040-0xf043]
[    0.603591] pci 0000:00:1f.2: reg 20: [io  0xf020-0xf03f]
[    0.603602] pci 0000:00:1f.2: reg 24: [mem 0xfbd06000-0xfbd067ff]
[    0.603648] pci 0000:00:1f.2: PME# supported from D3hot
[    0.603652] pci 0000:00:1f.2: PME# disabled
[    0.603674] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
[    0.603695] pci 0000:00:1f.3: reg 10: [mem 0xfbd05000-0xfbd050ff 64bit]
[    0.603724] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
[    0.603769] pci 0000:00:1f.6: [8086:3b32] type 0 class 0x001180
[    0.603796] pci 0000:00:1f.6: reg 10: [mem 0xfbd04000-0xfbd04fff 64bit]
[    0.603930] pci 0000:00:1c.0: PCI bridge to [bus 11-11]
[    0.603935] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.603940] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.603948] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.604031] pci 0000:12:00.0: [8086:0083] type 0 class 0x000280
[    0.604070] pci 0000:12:00.0: reg 10: [mem 0xfbc00000-0xfbc01fff 64bit]
[    0.604220] pci 0000:12:00.0: PME# supported from D0 D3hot D3cold
[    0.604227] pci 0000:12:00.0: PME# disabled
[    0.611331] pci 0000:00:1c.1: PCI bridge to [bus 12-12]
[    0.611337] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.611343] pci 0000:00:1c.1:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.611350] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.611479] pci 0000:13:00.0: [10ec:8136] type 0 class 0x000200
[    0.611543] pci 0000:13:00.0: reg 10: [io  0xe000-0xe0ff]
[    0.611633] pci 0000:13:00.0: reg 18: [mem 0xd0b10000-0xd0b10fff 64bit pref]
[    0.611679] pci 0000:13:00.0: reg 20: [mem 0xd0b00000-0xd0b0ffff 64bit pref]
[    0.611724] pci 0000:13:00.0: reg 30: [mem 0xfb200000-0xfb21ffff pref]
[    0.611869] pci 0000:13:00.0: supports D1 D2
[    0.611871] pci 0000:13:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.611885] pci 0000:13:00.0: PME# disabled
[    0.612032] pci 0000:00:1c.2: PCI bridge to [bus 13-13]
[    0.612037] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
[    0.612041] pci 0000:00:1c.2:   bridge window [mem 0xfb200000-0xfbbfffff]
[    0.612048] pci 0000:00:1c.2:   bridge window [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.612105] pci 0000:00:1c.4: PCI bridge to [bus 15-15]
[    0.612109] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.612114] pci 0000:00:1c.4:   bridge window [mem 0xfa800000-0xfb1fffff]
[    0.612121] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.612198] pci 0000:00:1e.0: PCI bridge to [bus 20-20] (subtractive decode)
[    0.612203] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.612207] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.612215] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.612217] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.612219] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.612221] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.612223] pci 0000:00:1e.0:   bridge window [mem 0xbc000000-0xffffffff] (subtractive decode)
[    0.612258] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.612413] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    0.612478] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.612506] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.612534] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.612559] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.612676]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.612847]  pci0000:00: ACPI _OSC control (0x19) granted
[    0.615727] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.615769] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.615808] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.615847] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.615885] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.615924] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.615963] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.616000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.616096] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.616102] vgaarb: loaded
[    0.616103] vgaarb: bridge control possible 0000:00:02.0
[    0.616255] SCSI subsystem initialized
[    0.616324] libata version 3.00 loaded.
[    0.616368] usbcore: registered new interface driver usbfs
[    0.616376] usbcore: registered new interface driver hub
[    0.616402] usbcore: registered new device driver usb
[    0.616474] PCI: Using ACPI for IRQ routing
[    0.626222] PCI: Discovered peer bus ff
[    0.626266] pci 0000:ff:00.0: [8086:2c62] type 0 class 0x000600
[    0.626288] pci 0000:ff:00.1: [8086:2d01] type 0 class 0x000600
[    0.626306] pci 0000:ff:02.0: [8086:2d10] type 0 class 0x000600
[    0.626322] pci 0000:ff:02.1: [8086:2d11] type 0 class 0x000600
[    0.626338] pci 0000:ff:02.2: [8086:2d12] type 0 class 0x000600
[    0.626354] pci 0000:ff:02.3: [8086:2d13] type 0 class 0x000600
[    0.626487] PCI: pci_cache_line_size set to 64 bytes
[    0.626594] reserve RAM buffer: 000000000009d400 - 000000000009ffff 
[    0.626596] reserve RAM buffer: 00000000b75a6000 - 00000000b7ffffff 
[    0.626599] reserve RAM buffer: 00000000b7621000 - 00000000b7ffffff 
[    0.626601] reserve RAM buffer: 00000000b7800000 - 00000000b7ffffff 
[    0.626698] NetLabel: Initializing
[    0.626699] NetLabel:  domain hash size = 128
[    0.626700] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.626711] NetLabel:  unlabeled traffic allowed by default
[    0.626770] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.626776] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.628795] Switching to clocksource hpet
[    0.631310] Switched to NOHz mode on CPU #0
[    0.631364] Switched to NOHz mode on CPU #1
[    0.631437] Switched to NOHz mode on CPU #3
[    0.631448] Switched to NOHz mode on CPU #2
[    0.634245] AppArmor: AppArmor Filesystem Enabled
[    0.634274] pnp: PnP ACPI init
[    0.634289] ACPI: bus type pnp registered
[    0.634380] pnp 00:00: [bus 00-ff]
[    0.634382] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.634384] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.634386] pnp 00:00: [io  0x0d00-0xffff window]
[    0.634388] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.634389] pnp 00:00: [mem 0x00000000 window]
[    0.634391] pnp 00:00: [mem 0xbc000000-0xffffffff window]
[    0.634479] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.634523] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.634524] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.634526] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.634527] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.634529] pnp 00:01: [mem 0xfee00000-0xfee0ffff]
[    0.634579] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.634581] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.634583] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.634586] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.634588] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.634590] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.634618] pnp 00:02: [dma 4]
[    0.634619] pnp 00:02: [io  0x0000-0x000f]
[    0.634621] pnp 00:02: [io  0x0081-0x0083]
[    0.634622] pnp 00:02: [io  0x0087]
[    0.634623] pnp 00:02: [io  0x0089-0x008b]
[    0.634624] pnp 00:02: [io  0x008f]
[    0.634626] pnp 00:02: [io  0x00c0-0x00df]
[    0.634644] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.634653] pnp 00:03: [io  0x0070-0x0071]
[    0.634666] pnp 00:03: [irq 8]
[    0.634684] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.634691] pnp 00:04: [io  0x0061]
[    0.634710] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.634717] pnp 00:05: [io  0x00f0-0x00ff]
[    0.634722] pnp 00:05: [irq 13]
[    0.634746] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.634766] pnp 00:06: [io  0x0010-0x001f]
[    0.634767] pnp 00:06: [io  0x0022-0x003f]
[    0.634769] pnp 00:06: [io  0x0044-0x005f]
[    0.634770] pnp 00:06: [io  0x0068-0x006f]
[    0.634771] pnp 00:06: [io  0x0072-0x007f]
[    0.634773] pnp 00:06: [io  0x0080]
[    0.634774] pnp 00:06: [io  0x0084-0x0086]
[    0.634775] pnp 00:06: [io  0x0088]
[    0.634777] pnp 00:06: [io  0x008c-0x008e]
[    0.634778] pnp 00:06: [io  0x0090-0x009f]
[    0.634779] pnp 00:06: [io  0x00a2-0x00bf]
[    0.634781] pnp 00:06: [io  0x00e0-0x00ef]
[    0.634782] pnp 00:06: [io  0x04d0-0x04d1]
[    0.634784] pnp 00:06: [mem 0xfe800000-0xfe8001ff]
[    0.634821] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.634824] system 00:06: [mem 0xfe800000-0xfe8001ff] has been reserved
[    0.634827] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.634843] pnp 00:07: [irq 12]
[    0.634864] pnp 00:07: Plug and Play ACPI device, IDs DLL0447 SYN0600 SYN0002 PNP0f13 (active)
[    0.634877] pnp 00:08: [io  0x0060]
[    0.634879] pnp 00:08: [io  0x0064]
[    0.634880] pnp 00:08: [io  0x0062]
[    0.634881] pnp 00:08: [io  0x0066]
[    0.634886] pnp 00:08: [irq 1]
[    0.634905] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.635015] pnp 00:09: [io  0x0400-0x047f]
[    0.635016] pnp 00:09: [io  0x1180-0x119f]
[    0.635018] pnp 00:09: [io  0x0500-0x057f]
[    0.635019] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.635021] pnp 00:09: [mem 0xfec00000-0xfecfffff]
[    0.635022] pnp 00:09: [mem 0xfed08000-0xfed08fff]
[    0.635024] pnp 00:09: [mem 0xff000000-0xffffffff]
[    0.635061] system 00:09: [io  0x0400-0x047f] has been reserved
[    0.635064] system 00:09: [io  0x1180-0x119f] has been reserved
[    0.635066] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.635068] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.635071] system 00:09: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.635073] system 00:09: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.635075] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
[    0.635078] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.635152] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.635178] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.635363] pnp: PnP ACPI: found 11 devices
[    0.635364] ACPI: ACPI bus type pnp unregistered
[    0.641007] PCI: max bus depth: 1 pci_try_num: 2
[    0.641064] pci 0000:00:1c.1: BAR 15: assigned [mem 0xbc000000-0xbc1fffff 64bit pref]
[    0.641066] pci 0000:00:1c.1: BAR 13: assigned [io  0x2000-0x2fff]
[    0.641069] pci 0000:00:1c.0: BAR 14: assigned [mem 0xbc200000-0xbc3fffff]
[    0.641071] pci 0000:00:1c.0: BAR 15: assigned [mem 0xbc400000-0xbc5fffff 64bit pref]
[    0.641074] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.641076] pci 0000:00:1c.0: PCI bridge to [bus 11-11]
[    0.641079] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.641085] pci 0000:00:1c.0:   bridge window [mem 0xbc200000-0xbc3fffff]
[    0.641090] pci 0000:00:1c.0:   bridge window [mem 0xbc400000-0xbc5fffff 64bit pref]
[    0.641098] pci 0000:00:1c.1: PCI bridge to [bus 12-12]
[    0.641101] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.641106] pci 0000:00:1c.1:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.641111] pci 0000:00:1c.1:   bridge window [mem 0xbc000000-0xbc1fffff 64bit pref]
[    0.641118] pci 0000:00:1c.2: PCI bridge to [bus 13-13]
[    0.641122] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
[    0.641128] pci 0000:00:1c.2:   bridge window [mem 0xfb200000-0xfbbfffff]
[    0.641132] pci 0000:00:1c.2:   bridge window [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.641140] pci 0000:00:1c.4: PCI bridge to [bus 15-15]
[    0.641143] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.641149] pci 0000:00:1c.4:   bridge window [mem 0xfa800000-0xfb1fffff]
[    0.641154] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.641162] pci 0000:00:1e.0: PCI bridge to [bus 20-20]
[    0.641163] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.641169] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.641173] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.641198] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.641203] pci 0000:00:1c.0: setting latency timer to 64
[    0.641219] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.641224] pci 0000:00:1c.1: setting latency timer to 64
[    0.641234] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.641238] pci 0000:00:1c.2: setting latency timer to 64
[    0.641246] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.641250] pci 0000:00:1c.4: setting latency timer to 64
[    0.641259] pci 0000:00:1e.0: setting latency timer to 64
[    0.641263] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.641264] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.641266] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.641268] pci_bus 0000:00: resource 7 [mem 0xbc000000-0xffffffff]
[    0.641270] pci_bus 0000:11: resource 0 [io  0x3000-0x3fff]
[    0.641272] pci_bus 0000:11: resource 1 [mem 0xbc200000-0xbc3fffff]
[    0.641274] pci_bus 0000:11: resource 2 [mem 0xbc400000-0xbc5fffff 64bit pref]
[    0.641275] pci_bus 0000:12: resource 0 [io  0x2000-0x2fff]
[    0.641277] pci_bus 0000:12: resource 1 [mem 0xfbc00000-0xfbcfffff]
[    0.641279] pci_bus 0000:12: resource 2 [mem 0xbc000000-0xbc1fffff 64bit pref]
[    0.641281] pci_bus 0000:13: resource 0 [io  0xe000-0xefff]
[    0.641283] pci_bus 0000:13: resource 1 [mem 0xfb200000-0xfbbfffff]
[    0.641285] pci_bus 0000:13: resource 2 [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.641287] pci_bus 0000:15: resource 0 [io  0xd000-0xdfff]
[    0.641288] pci_bus 0000:15: resource 1 [mem 0xfa800000-0xfb1fffff]
[    0.641290] pci_bus 0000:15: resource 2 [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.641292] pci_bus 0000:20: resource 4 [io  0x0000-0x0cf7]
[    0.641294] pci_bus 0000:20: resource 5 [io  0x0d00-0xffff]
[    0.641296] pci_bus 0000:20: resource 6 [mem 0x000a0000-0x000bffff]
[    0.641297] pci_bus 0000:20: resource 7 [mem 0xbc000000-0xffffffff]
[    0.641299] pci_bus 0000:ff: resource 0 [io  0x0000-0xffff]
[    0.641301] pci_bus 0000:ff: resource 1 [mem 0x00000000-0xfffffffff]
[    0.641337] NET: Registered protocol family 2
[    0.641475] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.642387] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.645737] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.646149] TCP: Hash tables configured (established 524288 bind 65536)
[    0.646151] TCP reno registered
[    0.646161] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.646194] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.646325] NET: Registered protocol family 1
[    0.646341] pci 0000:00:02.0: Boot video device
[    0.900824] PCI: CLS 64 bytes, default 64
[    0.901301] audit: initializing netlink socket (disabled)
[    0.901312] type=2000 audit(1329844643.736:1): initialized
[    0.926259] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.939243] VFS: Disk quotas dquot_6.5.2
[    0.939294] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.939828] fuse init (API version 7.16)
[    0.939905] msgmni has been set to 5727
[    0.940277] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.940308] io scheduler noop registered
[    0.940311] io scheduler deadline registered
[    0.940349] io scheduler cfq registered (default)
[    0.940457] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.940517] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.940598] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.940647] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.940749] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.940799] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.940876] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.940925] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
[    0.941007] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.941111] pciehp: Using ACPI for slot detection.
[    0.941168] pciehp 0000:00:1c.4:pcie04: HPC vendor_id 8086 device_id 3b4a ss_vid 1028 ss_did 447
[    0.941202] pciehp 0000:00:1c.4:pcie04: service driver pciehp loaded
[    0.941207] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.941241] intel_idle: MWAIT substates: 0x1120
[    0.941242] intel_idle: v0.4 model 0x25
[    0.941243] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.941331] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.941368] ACPI: AC Adapter [AC] (on-line)
[    0.941455] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.941460] ACPI: Power Button [PWRB]
[    0.941492] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.943510] ACPI: Lid Switch [LID0]
[    0.943541] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.943544] ACPI: Sleep Button [SBTN]
[    0.943572] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.943574] ACPI: Power Button [PWRF]
[    0.943598] ACPI: acpi_idle yielding to intel_idle
[    0.955334] thermal LNXTHERM:00: registered as thermal_zone0
[    0.955337] ACPI: Thermal Zone [THM] (53 C)
[    0.955365] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.955393] ERST: Table is not found!
[    0.955439] ACPI: Battery Slot [BAT0] (battery absent)
[    0.955473] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.999980] Freeing initrd memory: 13404k freed
[    1.076987] Linux agpgart interface v0.103
[    1.077058] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.077157] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.078231] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.078378] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.079199] brd: module loaded
[    1.079570] loop: module loaded
[    1.079913] Fixed MDIO Bus: probed
[    1.079930] PPP generic driver version 2.4.2
[    1.079956] tun: Universal TUN/TAP device driver, 1.6
[    1.079957] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.080016] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.080037] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.080055] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.080059] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.080087] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.080118] ehci_hcd 0000:00:1a.0: debug port 2
[    1.084101] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.084119] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfbd08000
[    1.096654] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.096780] hub 1-0:1.0: USB hub found
[    1.096784] hub 1-0:1.0: 2 ports detected
[    1.096846] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.096857] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.096860] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.096892] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.096918] ehci_hcd 0000:00:1d.0: debug port 2
[    1.100903] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.100917] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfbd07000
[    1.116640] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.116750] hub 2-0:1.0: USB hub found
[    1.116753] hub 2-0:1.0: 2 ports detected
[    1.116796] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.116806] uhci_hcd: USB Universal Host Controller Interface driver
[    1.116853] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2] at 0x60,0x64 irq 1,12
[    1.153579] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.153586] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.153694] mousedev: PS/2 mouse device common for all mice
[    1.155540] rtc_cmos 00:03: RTC can wake from S4
[    1.155631] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.155662] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.155741] device-mapper: uevent: version 1.0.3
[    1.155797] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.155875] cpuidle: using governor ladder
[    1.155994] cpuidle: using governor menu
[    1.155996] EFI Variables Facility v0.08 2004-May-17
[    1.156194] TCP cubic registered
[    1.156288] NET: Registered protocol family 10
[    1.156687] NET: Registered protocol family 17
[    1.156701] Registering the dns_resolver key type
[    1.156776] PM: Hibernation image not present or could not be loaded.
[    1.156785] registered taskstats version 1
[    1.169817]   Magic number: 0:77:290
[    1.169863] tty tty23: hash matches
[    1.169973] rtc_cmos 00:03: setting system clock to 2012-02-21 17:17:25 UTC (1329844645)
[    1.171081] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.171083] EDD information not available.
[    1.172747] Freeing unused kernel memory: 988k freed
[    1.172916] Write protecting the kernel read-only data: 12288k
[    1.178712] Freeing unused kernel memory: 2036k freed
[    1.182961] Freeing unused kernel memory: 1388k freed
[    1.190113] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.200262] udevd[90]: starting version 173
[    1.241862] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.241910] r8169 0000:13:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.241959] r8169 0000:13:00.0: setting latency timer to 64
[    1.242022] r8169 0000:13:00.0: irq 44 for MSI/MSI-X
[    1.242537] r8169 0000:13:00.0: eth0: RTL8102e at 0xffffc90000654000, 78:2b:cb:c6:df:17, XID 04e00000 IRQ 44
[    1.246292] ahci 0000:00:1f.2: version 3.0
[    1.246324] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.246390] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.246483] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x13 impl SATA mode
[    1.246487] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems sxs apst 
[    1.246493] ahci 0000:00:1f.2: setting latency timer to 64
[    1.261430] scsi0 : ahci
[    1.261643] scsi1 : ahci
[    1.261745] scsi2 : ahci
[    1.261968] scsi3 : ahci
[    1.262066] scsi4 : ahci
[    1.262307] scsi5 : ahci
[    1.262436] ata1: SATA max UDMA/133 abar m2048@0xfbd06000 port 0xfbd06100 irq 45
[    1.262440] ata2: SATA max UDMA/133 abar m2048@0xfbd06000 port 0xfbd06180 irq 45
[    1.262441] ata3: DUMMY
[    1.262442] ata4: DUMMY
[    1.262445] ata5: SATA max UDMA/133 abar m2048@0xfbd06000 port 0xfbd06300 irq 45
[    1.262447] ata6: DUMMY
[    1.408553] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.541227] hub 1-1:1.0: USB hub found
[    1.541427] hub 1-1:1.0: 6 ports detected
[    1.580477] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.584463] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.584495] ata5: SATA link down (SStatus 0 SControl 300)
[    1.594506] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L633J, D200, max UDMA/100
[    1.606855] ata2.00: configured for UDMA/100
[    1.627254] ata1.00: ATA-8: TOSHIBA MK3265GSX, GJ002D, max UDMA/100
[    1.627259] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.628369] ata1.00: configured for UDMA/100
[    1.628669] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3265GS GJ00 PQ: 0 ANSI: 5
[    1.628793] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.628849] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.629027] sd 0:0:0:0: [sda] Write Protect is off
[    1.629030] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.629120] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.633311] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L633J D200 PQ: 0 ANSI: 5
[    1.643020] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.643025] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.643152] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.643202] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.652443] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    1.722817]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.723352] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.785432] hub 2-1:1.0: USB hub found
[    1.785502] hub 2-1:1.0: 8 ports detected
[    1.856534] usb 1-1.2: new low speed USB device number 3 using ehci_hcd
[    1.900306] Refined TSC clocksource calibration: 2526.999 MHz.
[    1.900315] Switching to clocksource tsc
[    1.974734] input: HP Wireless Optical Mobile Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input5
[    1.974816] generic-usb 0003:03F0:8107.0001: input,hidraw0: USB HID v1.11 Mouse [HP Wireless Optical Mobile Mouse] on usb-0000:00:1a.0-1.2/input0
[    1.974827] usbcore: registered new interface driver usbhid
[    1.974828] usbhid: USB HID core driver
[    2.032474] usb 1-1.6: new high speed USB device number 4 using ehci_hcd
[    2.236299] usb 2-1.6: new full speed USB device number 3 using ehci_hcd
[    2.334614] hub 2-1.6:1.0: USB hub found
[    2.334830] hub 2-1.6:1.0: 3 ports detected
[    2.370933] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    2.604112] usb 2-1.6.1: new full speed USB device number 4 using ehci_hcd
[    2.701386] input: HID 413c:8161 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.1/2-1.6.1:1.0/input/input6
[    2.701457] generic-usb 0003:413C:8161.0002: input,hidraw1: USB HID v1.11 Keyboard [HID 413c:8161] on usb-0000:00:1d.0-1.6.1/input0
[    2.772011] usb 2-1.6.2: new full speed USB device number 5 using ehci_hcd
[    2.874475] input: HID 413c:8162 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.2/2-1.6.2:1.0/input/input7
[    2.874552] generic-usb 0003:413C:8162.0003: input,hidraw2: USB HID v1.11 Mouse [HID 413c:8162] on usb-0000:00:1d.0-1.6.2/input0
[   12.748016] udevd[346]: starting version 173
[   12.788939] cfg80211: Calling CRDA to update world regulatory domain
[   12.790983] [drm] Initialized drm 1.1.0 20060810
[   12.791156] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   12.791583] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.791591] mei 0000:00:16.0: setting latency timer to 64
[   12.793950] lp: driver loaded but no devices found
[   12.800651] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.800658] i915 0000:00:02.0: setting latency timer to 64
[   12.801149] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.801152] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   12.801233] iwlagn 0000:12:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.801242] iwlagn 0000:12:00.0: setting latency timer to 64
[   12.801275] iwlagn 0000:12:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   12.821871] iwlagn 0000:12:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   12.821876] iwlagn 0000:12:00.0: Device SKU: 0X9
[   12.821878] iwlagn 0000:12:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   12.823202] type=1400 audit(1329841057.155:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=414 comm="apparmor_parser"
[   12.823591] type=1400 audit(1329841057.155:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=414 comm="apparmor_parser"
[   12.823852] type=1400 audit(1329841057.155:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=414 comm="apparmor_parser"
[   12.826094] Adding 6394876k swap on /dev/sda6.  Priority:-1 extents:1 across:6394876k 
[   12.826269] iwlagn 0000:12:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   12.826366] iwlagn 0000:12:00.0: irq 46 for MSI/MSI-X
[   12.856753] i915 0000:00:02.0: irq 47 for MSI/MSI-X
[   12.856761] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.856763] [drm] Driver supports precise vblank timestamp query.
[   12.856817] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.879859] wmi: Mapper loaded
[   12.920475] Linux video capture interface: v2.00
[   12.921193] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:6480)
[   12.943217] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input8
[   12.943368] usbcore: registered new interface driver uvcvideo
[   12.943370] USB Video Class driver (v1.1.0)
[   13.002542] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   13.106548] cfg80211: World regulatory domain updated:
[   13.106552] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.106555] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.106558] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.106561] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.106564] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.106566] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.113033] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   13.136433] iwlagn 0000:12:00.0: loaded firmware version 39.31.5.1 build 35138
[   13.136602] Registered led device: phy0-led
[   13.136633] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   13.140618] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.171263] fbcon: inteldrmfb (fb0) is primary device
[   13.171360] Console: switching to colour frame buffer device 170x48
[   13.171389] fb0: inteldrmfb frame buffer device
[   13.171391] drm: registered panic notifier
[   13.181492] acpi device:2e: registered as cooling_device4
[   13.181654] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input10
[   13.181706] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.181765] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.181787] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   13.181803] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   13.182002] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   13.182048] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.182106] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   13.182137] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.214178] usb 2-1.6.3: new full speed USB device number 6 using ehci_hcd
[   13.242807] HDMI status: Pin=4 Presence_Detect=0 ELD_Valid=0
[   13.243082] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   13.243200] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   13.243253] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   13.299514] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   13.317429] Bluetooth: Core ver 2.16
[   13.317458] NET: Registered protocol family 31
[   13.317460] Bluetooth: HCI device and connection manager initialized
[   13.317463] Bluetooth: HCI socket layer initialized
[   13.317464] Bluetooth: L2CAP socket layer initialized
[   13.318161] Bluetooth: SCO socket layer initialized
[   13.318511] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   13.318946] usbcore: registered new interface driver btusb
[   13.979468] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   14.055125] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input14
[   14.218511] ppdev: user-space parallel port driver
[   14.226781] type=1400 audit(1329841058.559:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1019 comm="apparmor_parser"
[   14.227199] type=1400 audit(1329841058.559:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1019 comm="apparmor_parser"
[   14.455738] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.461414] r8169 0000:13:00.0: eth0: link down
[   14.462205] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.570215] wlan0: authenticate with 00:0d:f0:2d:99:30 (try 1)
[   16.572528] wlan0: authenticated
[   16.586100] wlan0: associate with 00:0d:f0:2d:99:30 (try 1)
[   16.588933] wlan0: RX AssocResp from 00:0d:f0:2d:99:30 (capab=0x421 status=0 aid=2)
[   16.588940] wlan0: associated
[   16.594129] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.456598] type=1400 audit(1329841068.795:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1105 comm="apparmor_parser"
[   24.457126] type=1400 audit(1329841068.795:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1105 comm="apparmor_parser"
[   24.457299] type=1400 audit(1329841068.795:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1104 comm="apparmor_parser"
[   24.457464] type=1400 audit(1329841068.795:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1105 comm="apparmor_parser"
[   24.457622] type=1400 audit(1329841068.795:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1108 comm="apparmor_parser"
[   24.458056] type=1400 audit(1329841068.795:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1108 comm="apparmor_parser"
[   24.459643] type=1400 audit(1329841068.795:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1110 comm="apparmor_parser"
[   24.460007] type=1400 audit(1329841068.799:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1109 comm="apparmor_parser"
[   24.460444] type=1400 audit(1329841068.799:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1109 comm="apparmor_parser"
[   24.461637] type=1400 audit(1329841068.799:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1106 comm="apparmor_parser"
[   24.542251] init: failsafe main process (953) killed by TERM signal
[   24.543379] init: apport pre-start process (1141) terminated with status 1
[   24.564662] init: apport post-stop process (1174) terminated with status 1

```

---

### Post by roelforg on 2012-02-21
> **ric1321 said:**
> ```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-16-generic (buildd@allspice) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 (Ubuntu 3.0.0-16.28-generic 3.0.17)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=34ef44cf-3cee-4aea-8cfd-59352f3c5ac8 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
[    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b75a6000 (usable)
[    0.000000]  BIOS-e820: 00000000b75a6000 - 00000000b75ee000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b75ee000 - 00000000b75f9000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b75f9000 - 00000000b75fc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b75fc000 - 00000000b7620000 (reserved)
[    0.000000]  BIOS-e820: 00000000b7620000 - 00000000b7621000 (usable)
[    0.000000]  BIOS-e820: 00000000b7621000 - 00000000b7629000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7629000 - 00000000b762c000 (reserved)
[    0.000000]  BIOS-e820: 00000000b762c000 - 00000000b7631000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7631000 - 00000000b7651000 (reserved)
[    0.000000]  BIOS-e820: 00000000b7651000 - 00000000b7694000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7694000 - 00000000b7800000 (usable)
[    0.000000]  BIOS-e820: 00000000b9e00000 - 00000000bc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Dell Inc. Inspiron N5010/0WXY9J, BIOS A10 11/17/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0xb7800 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 0B8000000 mask FF8000000 uncachable
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 2944MB, range: 128MB, type UC
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 2944M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 2944MB, range: 128MB, type UC
[    0.000000] found SMP MP-table at [ffff8800000fcda0] fcda0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000b7800000
[    0.000000]  0000000000 - 00b7800000 page 2M
[    0.000000] kernel direct mapping tables up to b7800000 @ 1fffc000-20000000
[    0.000000] RAMDISK: 365c2000 - 372d9000
[    0.000000] ACPI: RSDP 00000000000f0410 00024 (v03 DELL  )
[    0.000000] ACPI: XSDT 00000000b75ee088 0005C (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000b75f7a50 000F4 (v04 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110413/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xB762CF40/0x00000000B762CF80, using 32 (20110413/tbfadt-489)
[    0.000000] ACPI: DSDT 00000000b75ee170 098DF (v02 DELL    WN09    00005010 INTL 20051117)
[    0.000000] ACPI: FACS 00000000b762cf40 00040
[    0.000000] ACPI: APIC 00000000b75f7b48 00072 (v01 DELL   WN09     01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 00000000b75f7bc0 0014E (v01 AMICPU     PROC 00000001 MSFT 03000001)
[    0.000000] ACPI: MCFG 00000000b75f7d10 0003C (v01   DELL     WN09 01072009 MSFT 00000097)
[    0.000000] ACPI: SLIC 00000000b75f7d50 00176 (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: HPET 00000000b75f7ec8 00038 (v01   DELL     WN09 01072009 AMI. 00000003)
[    0.000000] ACPI: OSFR 00000000b75f7f00 0008C (v01 DELL    M08     07DA0B11 ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000000b7800000
[    0.000000] Initmem setup node 0 0000000000000000-00000000b7800000
[    0.000000]   NODE_DATA [00000000b77fb000 - 00000000b77fffff]
[    0.000000]  [ffffea0000000000-ffffea00029fffff] PMD -> [ffff8800b3e00000-ffff8800b67fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000b75a6
[    0.000000]     0: 0x000b7620 -> 0x000b7621
[    0.000000]     0: 0x000b7694 -> 0x000b7800
[    0.000000] On node 0 totalpages: 751264
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3920 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10220 pages used for memmap
[    0.000000]   DMA32 zone: 737063 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000b75a6000 - 00000000b75ee000
[    0.000000] PM: Registered nosave memory: 00000000b75ee000 - 00000000b75f9000
[    0.000000] PM: Registered nosave memory: 00000000b75f9000 - 00000000b75fc000
[    0.000000] PM: Registered nosave memory: 00000000b75fc000 - 00000000b7620000
[    0.000000] PM: Registered nosave memory: 00000000b7621000 - 00000000b7629000
[    0.000000] PM: Registered nosave memory: 00000000b7629000 - 00000000b762c000
[    0.000000] PM: Registered nosave memory: 00000000b762c000 - 00000000b7631000
[    0.000000] PM: Registered nosave memory: 00000000b7631000 - 00000000b7651000
[    0.000000] PM: Registered nosave memory: 00000000b7651000 - 00000000b7694000
[    0.000000] Allocating PCI resources starting at bc000000 (gap: bc000000:24000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff8800b7200000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 740983
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=34ef44cf-3cee-4aea-8cfd-59352f3c5ac8 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2932592k/3006464k available (6138k kernel code, 1408k absent, 72464k reserved, 6896k data, 988k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 24117248 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2526.980 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5053.96 BogoMIPS (lpj=10107920)
[    0.000008] pid_max: default: 32768 minimum: 301
[    0.000035] Security Framework initialized
[    0.000052] AppArmor: AppArmor initialized
[    0.000053] Yama: becoming mindful.
[    0.000476] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002172] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002925] Mount-cache hash table entries: 256
[    0.003058] Initializing cgroup subsys cpuacct
[    0.003063] Initializing cgroup subsys memory
[    0.003071] Initializing cgroup subsys devices
[    0.003073] Initializing cgroup subsys freezer
[    0.003075] Initializing cgroup subsys net_cls
[    0.003077] Initializing cgroup subsys blkio
[    0.003084] Initializing cgroup subsys perf_event
[    0.003113] CPU: Physical Processor ID: 0
[    0.003114] CPU: Processor Core ID: 0
[    0.003120] mce: CPU supports 9 MCE banks
[    0.003133] CPU0: Thermal monitoring enabled (TM1)
[    0.003142] using mwait in idle threads.
[    0.005449] ACPI: Core revision 20110413
[    0.018717] ftrace: allocating 25737 entries in 101 pages
[    0.027385] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067048] CPU0: Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz stepping 05
[    0.171555] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.171563] ... version:                3
[    0.171564] ... bit width:              48
[    0.171565] ... generic registers:      4
[    0.171567] ... value mask:             0000ffffffffffff
[    0.171568] ... max period:             000000007fffffff
[    0.171569] ... fixed-purpose events:   3
[    0.171571] ... event mask:             000000070000000f
[    0.172007] Booting Node   0, Processors  #1
[    0.172010] smpboot cpu 1: start_ip = 98000
[    0.279664]  #2
[    0.279667] smpboot cpu 2: start_ip = 98000
[    0.387679]  #3 Ok.
[    0.387683] smpboot cpu 3: start_ip = 98000
[    0.495512] Brought up 4 CPUs
[    0.495516] Total of 4 processors activated (20215.66 BogoMIPS).
[    0.497876] devtmpfs: initialized
[    0.498002] PM: Registering ACPI NVS region at b75a6000 (294912 bytes)
[    0.498009] PM: Registering ACPI NVS region at b75f9000 (12288 bytes)
[    0.498011] PM: Registering ACPI NVS region at b7621000 (32768 bytes)
[    0.498013] PM: Registering ACPI NVS region at b762c000 (20480 bytes)
[    0.498014] PM: Registering ACPI NVS region at b7651000 (274432 bytes)
[    0.499401] print_constraints: dummy: 
[    0.499429] Time: 17:17:24  Date: 02/21/12
[    0.499460] NET: Registered protocol family 16
[    0.499561] Trying to unpack rootfs image as initramfs...
[    0.499565] ACPI: bus type pci registered
[    0.499620] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.499623] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.540031] PCI: Using configuration type 1 for base access
[    0.540753] bio: create slab <bio-0> at 0
[    0.542111] ACPI: EC: Look up EC in DSDT
[    0.543408] ACPI: Executed 1 blocks of module-level executable AML code
[    0.547463] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.583738] ACPI: SSDT 00000000b7621c18 003A4 (v01    AMI      IST 00000001 MSFT 03000001)
[    0.584087] ACPI: Dynamic OEM Table Load:
[    0.584089] ACPI: SSDT           (null) 003A4 (v01    AMI      IST 00000001 MSFT 03000001)
[    0.584495] ACPI: Interpreter enabled
[    0.584498] ACPI: (supports S0 S3 S4 S5)
[    0.584517] ACPI: Using IOAPIC for interrupt routing
[    0.584743] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.601972] ACPI: No dock devices found.
[    0.601975] HEST: Table not found.
[    0.601978] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.602094] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.602181] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.602183] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.602185] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.602187] pci_root PNP0A08:00: host bridge window [mem 0xbc000000-0xffffffff]
[    0.602199] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
[    0.602217] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.602235] pci 0000:00:02.0: [8086:0046] type 0 class 0x000300
[    0.602245] pci 0000:00:02.0: reg 10: [mem 0xfa400000-0xfa7fffff 64bit]
[    0.602251] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.602256] pci 0000:00:02.0: reg 20: [io  0xf080-0xf087]
[    0.602314] pci 0000:00:16.0: [8086:3b64] type 0 class 0x000780
[    0.602342] pci 0000:00:16.0: reg 10: [mem 0xfbd09000-0xfbd0900f 64bit]
[    0.602423] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.602427] pci 0000:00:16.0: PME# disabled
[    0.602467] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    0.602492] pci 0000:00:1a.0: reg 10: [mem 0xfbd08000-0xfbd083ff]
[    0.602579] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.602583] pci 0000:00:1a.0: PME# disabled
[    0.602612] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    0.602632] pci 0000:00:1b.0: reg 10: [mem 0xfbd00000-0xfbd03fff 64bit]
[    0.602708] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.602712] pci 0000:00:1b.0: PME# disabled
[    0.602739] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    0.602816] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.602820] pci 0000:00:1c.0: PME# disabled
[    0.602847] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
[    0.602923] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.602928] pci 0000:00:1c.1: PME# disabled
[    0.602955] pci 0000:00:1c.2: [8086:3b46] type 1 class 0x000604
[    0.603031] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.603035] pci 0000:00:1c.2: PME# disabled
[    0.603065] pci 0000:00:1c.4: [8086:3b4a] type 1 class 0x000604
[    0.603142] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.603147] pci 0000:00:1c.4: PME# disabled
[    0.603183] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    0.603207] pci 0000:00:1d.0: reg 10: [mem 0xfbd07000-0xfbd073ff]
[    0.603294] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.603298] pci 0000:00:1d.0: PME# disabled
[    0.603329] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.603403] pci 0000:00:1f.0: [8086:3b0b] type 0 class 0x000601
[    0.603521] pci 0000:00:1f.2: [8086:3b2f] type 0 class 0x000106
[    0.603548] pci 0000:00:1f.2: reg 10: [io  0xf070-0xf077]
[    0.603559] pci 0000:00:1f.2: reg 14: [io  0xf060-0xf063]
[    0.603569] pci 0000:00:1f.2: reg 18: [io  0xf050-0xf057]
[    0.603580] pci 0000:00:1f.2: reg 1c: [io  0xf040-0xf043]
[    0.603591] pci 0000:00:1f.2: reg 20: [io  0xf020-0xf03f]
[    0.603602] pci 0000:00:1f.2: reg 24: [mem 0xfbd06000-0xfbd067ff]
[    0.603648] pci 0000:00:1f.2: PME# supported from D3hot
[    0.603652] pci 0000:00:1f.2: PME# disabled
[    0.603674] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
[    0.603695] pci 0000:00:1f.3: reg 10: [mem 0xfbd05000-0xfbd050ff 64bit]
[    0.603724] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
[    0.603769] pci 0000:00:1f.6: [8086:3b32] type 0 class 0x001180
[    0.603796] pci 0000:00:1f.6: reg 10: [mem 0xfbd04000-0xfbd04fff 64bit]
[    0.603930] pci 0000:00:1c.0: PCI bridge to [bus 11-11]
[    0.603935] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.603940] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.603948] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.604031] pci 0000:12:00.0: [8086:0083] type 0 class 0x000280
[    0.604070] pci 0000:12:00.0: reg 10: [mem 0xfbc00000-0xfbc01fff 64bit]
[    0.604220] pci 0000:12:00.0: PME# supported from D0 D3hot D3cold
[    0.604227] pci 0000:12:00.0: PME# disabled
[    0.611331] pci 0000:00:1c.1: PCI bridge to [bus 12-12]
[    0.611337] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.611343] pci 0000:00:1c.1:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.611350] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.611479] pci 0000:13:00.0: [10ec:8136] type 0 class 0x000200
[    0.611543] pci 0000:13:00.0: reg 10: [io  0xe000-0xe0ff]
[    0.611633] pci 0000:13:00.0: reg 18: [mem 0xd0b10000-0xd0b10fff 64bit pref]
[    0.611679] pci 0000:13:00.0: reg 20: [mem 0xd0b00000-0xd0b0ffff 64bit pref]
[    0.611724] pci 0000:13:00.0: reg 30: [mem 0xfb200000-0xfb21ffff pref]
[    0.611869] pci 0000:13:00.0: supports D1 D2
[    0.611871] pci 0000:13:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.611885] pci 0000:13:00.0: PME# disabled
[    0.612032] pci 0000:00:1c.2: PCI bridge to [bus 13-13]
[    0.612037] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
[    0.612041] pci 0000:00:1c.2:   bridge window [mem 0xfb200000-0xfbbfffff]
[    0.612048] pci 0000:00:1c.2:   bridge window [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.612105] pci 0000:00:1c.4: PCI bridge to [bus 15-15]
[    0.612109] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.612114] pci 0000:00:1c.4:   bridge window [mem 0xfa800000-0xfb1fffff]
[    0.612121] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.612198] pci 0000:00:1e.0: PCI bridge to [bus 20-20] (subtractive decode)
[    0.612203] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.612207] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.612215] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.612217] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.612219] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.612221] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.612223] pci 0000:00:1e.0:   bridge window [mem 0xbc000000-0xffffffff] (subtractive decode)
[    0.612258] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.612413] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    0.612478] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.612506] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.612534] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.612559] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.612676]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.612847]  pci0000:00: ACPI _OSC control (0x19) granted
[    0.615727] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.615769] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.615808] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.615847] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.615885] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.615924] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.615963] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.616000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.616096] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.616102] vgaarb: loaded
[    0.616103] vgaarb: bridge control possible 0000:00:02.0
[    0.616255] SCSI subsystem initialized
[    0.616324] libata version 3.00 loaded.
[    0.616368] usbcore: registered new interface driver usbfs
[    0.616376] usbcore: registered new interface driver hub
[    0.616402] usbcore: registered new device driver usb
[    0.616474] PCI: Using ACPI for IRQ routing
[    0.626222] PCI: Discovered peer bus ff
[    0.626266] pci 0000:ff:00.0: [8086:2c62] type 0 class 0x000600
[    0.626288] pci 0000:ff:00.1: [8086:2d01] type 0 class 0x000600
[    0.626306] pci 0000:ff:02.0: [8086:2d10] type 0 class 0x000600
[    0.626322] pci 0000:ff:02.1: [8086:2d11] type 0 class 0x000600
[    0.626338] pci 0000:ff:02.2: [8086:2d12] type 0 class 0x000600
[    0.626354] pci 0000:ff:02.3: [8086:2d13] type 0 class 0x000600
[    0.626487] PCI: pci_cache_line_size set to 64 bytes
[    0.626594] reserve RAM buffer: 000000000009d400 - 000000000009ffff 
[    0.626596] reserve RAM buffer: 00000000b75a6000 - 00000000b7ffffff 
[    0.626599] reserve RAM buffer: 00000000b7621000 - 00000000b7ffffff 
[    0.626601] reserve RAM buffer: 00000000b7800000 - 00000000b7ffffff 
[    0.626698] NetLabel: Initializing
[    0.626699] NetLabel:  domain hash size = 128
[    0.626700] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.626711] NetLabel:  unlabeled traffic allowed by default
[    0.626770] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.626776] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.628795] Switching to clocksource hpet
[    0.631310] Switched to NOHz mode on CPU #0
[    0.631364] Switched to NOHz mode on CPU #1
[    0.631437] Switched to NOHz mode on CPU #3
[    0.631448] Switched to NOHz mode on CPU #2
[    0.634245] AppArmor: AppArmor Filesystem Enabled
[    0.634274] pnp: PnP ACPI init
[    0.634289] ACPI: bus type pnp registered
[    0.634380] pnp 00:00: [bus 00-ff]
[    0.634382] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.634384] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.634386] pnp 00:00: [io  0x0d00-0xffff window]
[    0.634388] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.634389] pnp 00:00: [mem 0x00000000 window]
[    0.634391] pnp 00:00: [mem 0xbc000000-0xffffffff window]
[    0.634479] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.634523] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.634524] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.634526] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.634527] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.634529] pnp 00:01: [mem 0xfee00000-0xfee0ffff]
[    0.634579] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.634581] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.634583] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.634586] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.634588] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.634590] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.634618] pnp 00:02: [dma 4]
[    0.634619] pnp 00:02: [io  0x0000-0x000f]
[    0.634621] pnp 00:02: [io  0x0081-0x0083]
[    0.634622] pnp 00:02: [io  0x0087]
[    0.634623] pnp 00:02: [io  0x0089-0x008b]
[    0.634624] pnp 00:02: [io  0x008f]
[    0.634626] pnp 00:02: [io  0x00c0-0x00df]
[    0.634644] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.634653] pnp 00:03: [io  0x0070-0x0071]
[    0.634666] pnp 00:03: [irq 8]
[    0.634684] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.634691] pnp 00:04: [io  0x0061]
[    0.634710] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.634717] pnp 00:05: [io  0x00f0-0x00ff]
[    0.634722] pnp 00:05: [irq 13]
[    0.634746] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.634766] pnp 00:06: [io  0x0010-0x001f]
[    0.634767] pnp 00:06: [io  0x0022-0x003f]
[    0.634769] pnp 00:06: [io  0x0044-0x005f]
[    0.634770] pnp 00:06: [io  0x0068-0x006f]
[    0.634771] pnp 00:06: [io  0x0072-0x007f]
[    0.634773] pnp 00:06: [io  0x0080]
[    0.634774] pnp 00:06: [io  0x0084-0x0086]
[    0.634775] pnp 00:06: [io  0x0088]
[    0.634777] pnp 00:06: [io  0x008c-0x008e]
[    0.634778] pnp 00:06: [io  0x0090-0x009f]
[    0.634779] pnp 00:06: [io  0x00a2-0x00bf]
[    0.634781] pnp 00:06: [io  0x00e0-0x00ef]
[    0.634782] pnp 00:06: [io  0x04d0-0x04d1]
[    0.634784] pnp 00:06: [mem 0xfe800000-0xfe8001ff]
[    0.634821] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.634824] system 00:06: [mem 0xfe800000-0xfe8001ff] has been reserved
[    0.634827] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.634843] pnp 00:07: [irq 12]
[    0.634864] pnp 00:07: Plug and Play ACPI device, IDs DLL0447 SYN0600 SYN0002 PNP0f13 (active)
[    0.634877] pnp 00:08: [io  0x0060]
[    0.634879] pnp 00:08: [io  0x0064]
[    0.634880] pnp 00:08: [io  0x0062]
[    0.634881] pnp 00:08: [io  0x0066]
[    0.634886] pnp 00:08: [irq 1]
[    0.634905] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.635015] pnp 00:09: [io  0x0400-0x047f]
[    0.635016] pnp 00:09: [io  0x1180-0x119f]
[    0.635018] pnp 00:09: [io  0x0500-0x057f]
[    0.635019] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.635021] pnp 00:09: [mem 0xfec00000-0xfecfffff]
[    0.635022] pnp 00:09: [mem 0xfed08000-0xfed08fff]
[    0.635024] pnp 00:09: [mem 0xff000000-0xffffffff]
[    0.635061] system 00:09: [io  0x0400-0x047f] has been reserved
[    0.635064] system 00:09: [io  0x1180-0x119f] has been reserved
[    0.635066] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.635068] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.635071] system 00:09: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.635073] system 00:09: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.635075] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
[    0.635078] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.635152] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.635178] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.635363] pnp: PnP ACPI: found 11 devices
[    0.635364] ACPI: ACPI bus type pnp unregistered
[    0.641007] PCI: max bus depth: 1 pci_try_num: 2
[    0.641064] pci 0000:00:1c.1: BAR 15: assigned [mem 0xbc000000-0xbc1fffff 64bit pref]
[    0.641066] pci 0000:00:1c.1: BAR 13: assigned [io  0x2000-0x2fff]
[    0.641069] pci 0000:00:1c.0: BAR 14: assigned [mem 0xbc200000-0xbc3fffff]
[    0.641071] pci 0000:00:1c.0: BAR 15: assigned [mem 0xbc400000-0xbc5fffff 64bit pref]
[    0.641074] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.641076] pci 0000:00:1c.0: PCI bridge to [bus 11-11]
[    0.641079] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.641085] pci 0000:00:1c.0:   bridge window [mem 0xbc200000-0xbc3fffff]
[    0.641090] pci 0000:00:1c.0:   bridge window [mem 0xbc400000-0xbc5fffff 64bit pref]
[    0.641098] pci 0000:00:1c.1: PCI bridge to [bus 12-12]
[    0.641101] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.641106] pci 0000:00:1c.1:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.641111] pci 0000:00:1c.1:   bridge window [mem 0xbc000000-0xbc1fffff 64bit pref]
[    0.641118] pci 0000:00:1c.2: PCI bridge to [bus 13-13]
[    0.641122] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
[    0.641128] pci 0000:00:1c.2:   bridge window [mem 0xfb200000-0xfbbfffff]
[    0.641132] pci 0000:00:1c.2:   bridge window [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.641140] pci 0000:00:1c.4: PCI bridge to [bus 15-15]
[    0.641143] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.641149] pci 0000:00:1c.4:   bridge window [mem 0xfa800000-0xfb1fffff]
[    0.641154] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.641162] pci 0000:00:1e.0: PCI bridge to [bus 20-20]
[    0.641163] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.641169] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.641173] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.641198] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.641203] pci 0000:00:1c.0: setting latency timer to 64
[    0.641219] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.641224] pci 0000:00:1c.1: setting latency timer to 64
[    0.641234] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.641238] pci 0000:00:1c.2: setting latency timer to 64
[    0.641246] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.641250] pci 0000:00:1c.4: setting latency timer to 64
[    0.641259] pci 0000:00:1e.0: setting latency timer to 64
[    0.641263] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.641264] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.641266] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.641268] pci_bus 0000:00: resource 7 [mem 0xbc000000-0xffffffff]
[    0.641270] pci_bus 0000:11: resource 0 [io  0x3000-0x3fff]
[    0.641272] pci_bus 0000:11: resource 1 [mem 0xbc200000-0xbc3fffff]
[    0.641274] pci_bus 0000:11: resource 2 [mem 0xbc400000-0xbc5fffff 64bit pref]
[    0.641275] pci_bus 0000:12: resource 0 [io  0x2000-0x2fff]
[    0.641277] pci_bus 0000:12: resource 1 [mem 0xfbc00000-0xfbcfffff]
[    0.641279] pci_bus 0000:12: resource 2 [mem 0xbc000000-0xbc1fffff 64bit pref]
[    0.641281] pci_bus 0000:13: resource 0 [io  0xe000-0xefff]
[    0.641283] pci_bus 0000:13: resource 1 [mem 0xfb200000-0xfbbfffff]
[    0.641285] pci_bus 0000:13: resource 2 [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.641287] pci_bus 0000:15: resource 0 [io  0xd000-0xdfff]
[    0.641288] pci_bus 0000:15: resource 1 [mem 0xfa800000-0xfb1fffff]
[    0.641290] pci_bus 0000:15: resource 2 [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.641292] pci_bus 0000:20: resource 4 [io  0x0000-0x0cf7]
[    0.641294] pci_bus 0000:20: resource 5 [io  0x0d00-0xffff]
[    0.641296] pci_bus 0000:20: resource 6 [mem 0x000a0000-0x000bffff]
[    0.641297] pci_bus 0000:20: resource 7 [mem 0xbc000000-0xffffffff]
[    0.641299] pci_bus 0000:ff: resource 0 [io  0x0000-0xffff]
[    0.641301] pci_bus 0000:ff: resource 1 [mem 0x00000000-0xfffffffff]
[    0.641337] NET: Registered protocol family 2
[    0.641475] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.642387] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.645737] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.646149] TCP: Hash tables configured (established 524288 bind 65536)
[    0.646151] TCP reno registered
[    0.646161] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.646194] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.646325] NET: Registered protocol family 1
[    0.646341] pci 0000:00:02.0: Boot video device
[    0.900824] PCI: CLS 64 bytes, default 64
[    0.901301] audit: initializing netlink socket (disabled)
[    0.901312] type=2000 audit(1329844643.736:1): initialized
[    0.926259] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.939243] VFS: Disk quotas dquot_6.5.2
[    0.939294] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.939828] fuse init (API version 7.16)
[    0.939905] msgmni has been set to 5727
[    0.940277] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.940308] io scheduler noop registered
[    0.940311] io scheduler deadline registered
[    0.940349] io scheduler cfq registered (default)
[    0.940457] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.940517] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.940598] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.940647] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.940749] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.940799] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.940876] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.940925] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
[    0.941007] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.941111] pciehp: Using ACPI for slot detection.
[    0.941168] pciehp 0000:00:1c.4:pcie04: HPC vendor_id 8086 device_id 3b4a ss_vid 1028 ss_did 447
[    0.941202] pciehp 0000:00:1c.4:pcie04: service driver pciehp loaded
[    0.941207] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.941241] intel_idle: MWAIT substates: 0x1120
[    0.941242] intel_idle: v0.4 model 0x25
[    0.941243] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.941331] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.941368] ACPI: AC Adapter [AC] (on-line)
[    0.941455] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.941460] ACPI: Power Button [PWRB]
[    0.941492] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.943510] ACPI: Lid Switch [LID0]
[    0.943541] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.943544] ACPI: Sleep Button [SBTN]
[    0.943572] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.943574] ACPI: Power Button [PWRF]
[    0.943598] ACPI: acpi_idle yielding to intel_idle
[    0.955334] thermal LNXTHERM:00: registered as thermal_zone0
[    0.955337] ACPI: Thermal Zone [THM] (53 C)
[    0.955365] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.955393] ERST: Table is not found!
[    0.955439] ACPI: Battery Slot [BAT0] (battery absent)
[    0.955473] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.999980] Freeing initrd memory: 13404k freed
[    1.076987] Linux agpgart interface v0.103
[    1.077058] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.077157] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.078231] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.078378] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.079199] brd: module loaded
[    1.079570] loop: module loaded
[    1.079913] Fixed MDIO Bus: probed
[    1.079930] PPP generic driver version 2.4.2
[    1.079956] tun: Universal TUN/TAP device driver, 1.6
[    1.079957] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.080016] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.080037] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.080055] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.080059] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.080087] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.080118] ehci_hcd 0000:00:1a.0: debug port 2
[    1.084101] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.084119] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfbd08000
[    1.096654] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.096780] hub 1-0:1.0: USB hub found
[    1.096784] hub 1-0:1.0: 2 ports detected
[    1.096846] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.096857] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.096860] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.096892] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.096918] ehci_hcd 0000:00:1d.0: debug port 2
[    1.100903] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.100917] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfbd07000
[    1.116640] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.116750] hub 2-0:1.0: USB hub found
[    1.116753] hub 2-0:1.0: 2 ports detected
[    1.116796] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.116806] uhci_hcd: USB Universal Host Controller Interface driver
[    1.116853] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2] at 0x60,0x64 irq 1,12
[    1.153579] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.153586] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.153694] mousedev: PS/2 mouse device common for all mice
[    1.155540] rtc_cmos 00:03: RTC can wake from S4
[    1.155631] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.155662] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.155741] device-mapper: uevent: version 1.0.3
[    1.155797] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.155875] cpuidle: using governor ladder
[    1.155994] cpuidle: using governor menu
[    1.155996] EFI Variables Facility v0.08 2004-May-17
[    1.156194] TCP cubic registered
[    1.156288] NET: Registered protocol family 10
[    1.156687] NET: Registered protocol family 17
[    1.156701] Registering the dns_resolver key type
[    1.156776] PM: Hibernation image not present or could not be loaded.
[    1.156785] registered taskstats version 1
[    1.169817]   Magic number: 0:77:290
[    1.169863] tty tty23: hash matches
[    1.169973] rtc_cmos 00:03: setting system clock to 2012-02-21 17:17:25 UTC (1329844645)
[    1.171081] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.171083] EDD information not available.
[    1.172747] Freeing unused kernel memory: 988k freed
[    1.172916] Write protecting the kernel read-only data: 12288k
[    1.178712] Freeing unused kernel memory: 2036k freed
[    1.182961] Freeing unused kernel memory: 1388k freed
[    1.190113] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.200262] udevd[90]: starting version 173
[    1.241862] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.241910] r8169 0000:13:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.241959] r8169 0000:13:00.0: setting latency timer to 64
[    1.242022] r8169 0000:13:00.0: irq 44 for MSI/MSI-X
[    1.242537] r8169 0000:13:00.0: eth0: RTL8102e at 0xffffc90000654000, 78:2b:cb:c6:df:17, XID 04e00000 IRQ 44
[    1.246292] ahci 0000:00:1f.2: version 3.0
[    1.246324] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.246390] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.246483] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x13 impl SATA mode
[    1.246487] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems sxs apst 
[    1.246493] ahci 0000:00:1f.2: setting latency timer to 64
[    1.261430] scsi0 : ahci
[    1.261643] scsi1 : ahci
[    1.261745] scsi2 : ahci
[    1.261968] scsi3 : ahci
[    1.262066] scsi4 : ahci
[    1.262307] scsi5 : ahci
[    1.262436] ata1: SATA max UDMA/133 abar m2048@0xfbd06000 port 0xfbd06100 irq 45
[    1.262440] ata2: SATA max UDMA/133 abar m2048@0xfbd06000 port 0xfbd06180 irq 45
[    1.262441] ata3: DUMMY
[    1.262442] ata4: DUMMY
[    1.262445] ata5: SATA max UDMA/133 abar m2048@0xfbd06000 port 0xfbd06300 irq 45
[    1.262447] ata6: DUMMY
[    1.408553] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.541227] hub 1-1:1.0: USB hub found
[    1.541427] hub 1-1:1.0: 6 ports detected
[    1.580477] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.584463] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.584495] ata5: SATA link down (SStatus 0 SControl 300)
[    1.594506] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L633J, D200, max UDMA/100
[    1.606855] ata2.00: configured for UDMA/100
[    1.627254] ata1.00: ATA-8: TOSHIBA MK3265GSX, GJ002D, max UDMA/100
[    1.627259] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.628369] ata1.00: configured for UDMA/100
[    1.628669] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3265GS GJ00 PQ: 0 ANSI: 5
[    1.628793] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.628849] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.629027] sd 0:0:0:0: [sda] Write Protect is off
[    1.629030] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.629120] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.633311] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L633J D200 PQ: 0 ANSI: 5
[    1.643020] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.643025] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.643152] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.643202] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.652443] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    1.722817]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.723352] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.785432] hub 2-1:1.0: USB hub found
[    1.785502] hub 2-1:1.0: 8 ports detected
[    1.856534] usb 1-1.2: new low speed USB device number 3 using ehci_hcd
[    1.900306] Refined TSC clocksource calibration: 2526.999 MHz.
[    1.900315] Switching to clocksource tsc
[    1.974734] input: HP Wireless Optical Mobile Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input5
[    1.974816] generic-usb 0003:03F0:8107.0001: input,hidraw0: USB HID v1.11 Mouse [HP Wireless Optical Mobile Mouse] on usb-0000:00:1a.0-1.2/input0
[    1.974827] usbcore: registered new interface driver usbhid
[    1.974828] usbhid: USB HID core driver
[    2.032474] usb 1-1.6: new high speed USB device number 4 using ehci_hcd
[    2.236299] usb 2-1.6: new full speed USB device number 3 using ehci_hcd
[    2.334614] hub 2-1.6:1.0: USB hub found
[    2.334830] hub 2-1.6:1.0: 3 ports detected
[    2.370933] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    2.604112] usb 2-1.6.1: new full speed USB device number 4 using ehci_hcd
[    2.701386] input: HID 413c:8161 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.1/2-1.6.1:1.0/input/input6
[    2.701457] generic-usb 0003:413C:8161.0002: input,hidraw1: USB HID v1.11 Keyboard [HID 413c:8161] on usb-0000:00:1d.0-1.6.1/input0
[    2.772011] usb 2-1.6.2: new full speed USB device number 5 using ehci_hcd
[    2.874475] input: HID 413c:8162 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.2/2-1.6.2:1.0/input/input7
[    2.874552] generic-usb 0003:413C:8162.0003: input,hidraw2: USB HID v1.11 Mouse [HID 413c:8162] on usb-0000:00:1d.0-1.6.2/input0
[   12.748016] udevd[346]: starting version 173
[   12.788939] cfg80211: Calling CRDA to update world regulatory domain
[   12.790983] [drm] Initialized drm 1.1.0 20060810
[   12.791156] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   12.791583] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.791591] mei 0000:00:16.0: setting latency timer to 64
[   12.793950] lp: driver loaded but no devices found
[   12.800651] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.800658] i915 0000:00:02.0: setting latency timer to 64
[   12.801149] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.801152] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   12.801233] iwlagn 0000:12:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.801242] iwlagn 0000:12:00.0: setting latency timer to 64
[   12.801275] iwlagn 0000:12:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   12.821871] iwlagn 0000:12:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   12.821876] iwlagn 0000:12:00.0: Device SKU: 0X9
[   12.821878] iwlagn 0000:12:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   12.823202] type=1400 audit(1329841057.155:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=414 comm="apparmor_parser"
[   12.823591] type=1400 audit(1329841057.155:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=414 comm="apparmor_parser"
[   12.823852] type=1400 audit(1329841057.155:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=414 comm="apparmor_parser"
[   12.826094] Adding 6394876k swap on /dev/sda6.  Priority:-1 extents:1 across:6394876k 
[   12.826269] iwlagn 0000:12:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   12.826366] iwlagn 0000:12:00.0: irq 46 for MSI/MSI-X
[   12.856753] i915 0000:00:02.0: irq 47 for MSI/MSI-X
[   12.856761] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.856763] [drm] Driver supports precise vblank timestamp query.
[   12.856817] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.879859] wmi: Mapper loaded
[   12.920475] Linux video capture interface: v2.00
[   12.921193] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:6480)
[   12.943217] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input8
[   12.943368] usbcore: registered new interface driver uvcvideo
[   12.943370] USB Video Class driver (v1.1.0)
[   13.002542] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   13.106548] cfg80211: World regulatory domain updated:
[   13.106552] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.106555] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.106558] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.106561] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.106564] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.106566] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.113033] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   13.136433] iwlagn 0000:12:00.0: loaded firmware version 39.31.5.1 build 35138
[   13.136602] Registered led device: phy0-led
[   13.136633] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   13.140618] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.171263] fbcon: inteldrmfb (fb0) is primary device
[   13.171360] Console: switching to colour frame buffer device 170x48
[   13.171389] fb0: inteldrmfb frame buffer device
[   13.171391] drm: registered panic notifier
[   13.181492] acpi device:2e: registered as cooling_device4
[   13.181654] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input10
[   13.181706] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.181765] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.181787] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   13.181803] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   13.182002] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   13.182048] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.182106] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   13.182137] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.214178] usb 2-1.6.3: new full speed USB device number 6 using ehci_hcd
[   13.242807] HDMI status: Pin=4 Presence_Detect=0 ELD_Valid=0
[   13.243082] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   13.243200] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   13.243253] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   13.299514] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   13.317429] Bluetooth: Core ver 2.16
[   13.317458] NET: Registered protocol family 31
[   13.317460] Bluetooth: HCI device and connection manager initialized
[   13.317463] Bluetooth: HCI socket layer initialized
[   13.317464] Bluetooth: L2CAP socket layer initialized
[   13.318161] Bluetooth: SCO socket layer initialized
[   13.318511] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   13.318946] usbcore: registered new interface driver btusb
[   13.979468] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   14.055125] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input14
[   14.218511] ppdev: user-space parallel port driver
[   14.226781] type=1400 audit(1329841058.559:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1019 comm="apparmor_parser"
[   14.227199] type=1400 audit(1329841058.559:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1019 comm="apparmor_parser"
[   14.455738] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.461414] r8169 0000:13:00.0: eth0: link down
[   14.462205] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.570215] wlan0: authenticate with 00:0d:f0:2d:99:30 (try 1)
[   16.572528] wlan0: authenticated
[   16.586100] wlan0: associate with 00:0d:f0:2d:99:30 (try 1)
[   16.588933] wlan0: RX AssocResp from 00:0d:f0:2d:99:30 (capab=0x421 status=0 aid=2)
[   16.588940] wlan0: associated
[   16.594129] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.456598] type=1400 audit(1329841068.795:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1105 comm="apparmor_parser"
[   24.457126] type=1400 audit(1329841068.795:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1105 comm="apparmor_parser"
[   24.457299] type=1400 audit(1329841068.795:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1104 comm="apparmor_parser"
[   24.457464] type=1400 audit(1329841068.795:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1105 comm="apparmor_parser"
[   24.457622] type=1400 audit(1329841068.795:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1108 comm="apparmor_parser"
[   24.458056] type=1400 audit(1329841068.795:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1108 comm="apparmor_parser"
[   24.459643] type=1400 audit(1329841068.795:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1110 comm="apparmor_parser"
[   24.460007] type=1400 audit(1329841068.799:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1109 comm="apparmor_parser"
[   24.460444] type=1400 audit(1329841068.799:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1109 comm="apparmor_parser"
[   24.461637] type=1400 audit(1329841068.799:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1106 comm="apparmor_parser"
[   24.542251] init: failsafe main process (953) killed by TERM signal
[   24.543379] init: apport pre-start process (1141) terminated with status 1
[   24.564662] init: apport post-stop process (1174) terminated with status 1

```

Is there anything important on the machine?
If so, back it up to a usb drive.

I'm gonna have to ask you to execute this (i'm not reponsible for errors or problems as a result of this):
```

sudo apt-get update
sudo apt-get install --reinstall -y upstart

```
Don't forget to reboot!

---

### Post by ric1321 on 2012-02-21
I did. What do I have to do then?

---

### Post by roelforg on 2012-02-21
> **ric1321 said:**
> I did. What do I have to do then?
Does it boot correctly once rebooted?
If not, create a new copy of dmesg and post it.

---

### Post by ric1321 on 2012-02-21
It doesn't.
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-16-generic (buildd@allspice) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 (Ubuntu 3.0.0-16.28-generic 3.0.17)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=34ef44cf-3cee-4aea-8cfd-59352f3c5ac8 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
[    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b75a6000 (usable)
[    0.000000]  BIOS-e820: 00000000b75a6000 - 00000000b75ee000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b75ee000 - 00000000b75f9000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b75f9000 - 00000000b75fc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b75fc000 - 00000000b7620000 (reserved)
[    0.000000]  BIOS-e820: 00000000b7620000 - 00000000b7621000 (usable)
[    0.000000]  BIOS-e820: 00000000b7621000 - 00000000b7629000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7629000 - 00000000b762c000 (reserved)
[    0.000000]  BIOS-e820: 00000000b762c000 - 00000000b7631000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7631000 - 00000000b7651000 (reserved)
[    0.000000]  BIOS-e820: 00000000b7651000 - 00000000b7694000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7694000 - 00000000b7800000 (usable)
[    0.000000]  BIOS-e820: 00000000b9e00000 - 00000000bc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Dell Inc. Inspiron N5010/0WXY9J, BIOS A10 11/17/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0xb7800 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 0B8000000 mask FF8000000 uncachable
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 2944MB, range: 128MB, type UC
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 2944M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 256M 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 2944MB, range: 128MB, type UC
[    0.000000] found SMP MP-table at [ffff8800000fcda0] fcda0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000b7800000
[    0.000000]  0000000000 - 00b7800000 page 2M
[    0.000000] kernel direct mapping tables up to b7800000 @ 1fffc000-20000000
[    0.000000] RAMDISK: 365c2000 - 372d9000
[    0.000000] ACPI: RSDP 00000000000f0410 00024 (v03 DELL  )
[    0.000000] ACPI: XSDT 00000000b75ee088 0005C (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000b75f7a50 000F4 (v04 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110413/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xB762CF40/0x00000000B762CF80, using 32 (20110413/tbfadt-489)
[    0.000000] ACPI: DSDT 00000000b75ee170 098DF (v02 DELL    WN09    00005010 INTL 20051117)
[    0.000000] ACPI: FACS 00000000b762cf40 00040
[    0.000000] ACPI: APIC 00000000b75f7b48 00072 (v01 DELL   WN09     01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 00000000b75f7bc0 0014E (v01 AMICPU     PROC 00000001 MSFT 03000001)
[    0.000000] ACPI: MCFG 00000000b75f7d10 0003C (v01   DELL     WN09 01072009 MSFT 00000097)
[    0.000000] ACPI: SLIC 00000000b75f7d50 00176 (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: HPET 00000000b75f7ec8 00038 (v01   DELL     WN09 01072009 AMI. 00000003)
[    0.000000] ACPI: OSFR 00000000b75f7f00 0008C (v01 DELL    M08     07DA0B11 ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000000b7800000
[    0.000000] Initmem setup node 0 0000000000000000-00000000b7800000
[    0.000000]   NODE_DATA [00000000b77fb000 - 00000000b77fffff]
[    0.000000]  [ffffea0000000000-ffffea00029fffff] PMD -> [ffff8800b3e00000-ffff8800b67fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000b75a6
[    0.000000]     0: 0x000b7620 -> 0x000b7621
[    0.000000]     0: 0x000b7694 -> 0x000b7800
[    0.000000] On node 0 totalpages: 751264
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3920 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10220 pages used for memmap
[    0.000000]   DMA32 zone: 737063 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000b75a6000 - 00000000b75ee000
[    0.000000] PM: Registered nosave memory: 00000000b75ee000 - 00000000b75f9000
[    0.000000] PM: Registered nosave memory: 00000000b75f9000 - 00000000b75fc000
[    0.000000] PM: Registered nosave memory: 00000000b75fc000 - 00000000b7620000
[    0.000000] PM: Registered nosave memory: 00000000b7621000 - 00000000b7629000
[    0.000000] PM: Registered nosave memory: 00000000b7629000 - 00000000b762c000
[    0.000000] PM: Registered nosave memory: 00000000b762c000 - 00000000b7631000
[    0.000000] PM: Registered nosave memory: 00000000b7631000 - 00000000b7651000
[    0.000000] PM: Registered nosave memory: 00000000b7651000 - 00000000b7694000
[    0.000000] Allocating PCI resources starting at bc000000 (gap: bc000000:24000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff8800b7200000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 740983
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=34ef44cf-3cee-4aea-8cfd-59352f3c5ac8 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2932592k/3006464k available (6138k kernel code, 1408k absent, 72464k reserved, 6896k data, 988k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 24117248 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2526.960 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5053.92 BogoMIPS (lpj=10107840)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000034] Security Framework initialized
[    0.000051] AppArmor: AppArmor initialized
[    0.000053] Yama: becoming mindful.
[    0.000473] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002171] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002926] Mount-cache hash table entries: 256
[    0.003060] Initializing cgroup subsys cpuacct
[    0.003066] Initializing cgroup subsys memory
[    0.003073] Initializing cgroup subsys devices
[    0.003076] Initializing cgroup subsys freezer
[    0.003078] Initializing cgroup subsys net_cls
[    0.003080] Initializing cgroup subsys blkio
[    0.003087] Initializing cgroup subsys perf_event
[    0.003115] CPU: Physical Processor ID: 0
[    0.003116] CPU: Processor Core ID: 0
[    0.003123] mce: CPU supports 9 MCE banks
[    0.003136] CPU0: Thermal monitoring enabled (TM1)
[    0.003145] using mwait in idle threads.
[    0.005442] ACPI: Core revision 20110413
[    0.018606] ftrace: allocating 25737 entries in 101 pages
[    0.027272] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066939] CPU0: Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz stepping 05
[    0.171128] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.171136] ... version:                3
[    0.171137] ... bit width:              48
[    0.171138] ... generic registers:      4
[    0.171139] ... value mask:             0000ffffffffffff
[    0.171141] ... max period:             000000007fffffff
[    0.171142] ... fixed-purpose events:   3
[    0.171143] ... event mask:             000000070000000f
[    0.171578] Booting Node   0, Processors  #1
[    0.171581] smpboot cpu 1: start_ip = 98000
[    0.279237]  #2
[    0.279240] smpboot cpu 2: start_ip = 98000
[    0.387246]  #3 Ok.
[    0.387249] smpboot cpu 3: start_ip = 98000
[    0.495080] Brought up 4 CPUs
[    0.495083] Total of 4 processors activated (20215.61 BogoMIPS).
[    0.497441] devtmpfs: initialized
[    0.497566] PM: Registering ACPI NVS region at b75a6000 (294912 bytes)
[    0.497574] PM: Registering ACPI NVS region at b75f9000 (12288 bytes)
[    0.497576] PM: Registering ACPI NVS region at b7621000 (32768 bytes)
[    0.497578] PM: Registering ACPI NVS region at b762c000 (20480 bytes)
[    0.497579] PM: Registering ACPI NVS region at b7651000 (274432 bytes)
[    0.498968] print_constraints: dummy: 
[    0.498996] Time: 20:27:18  Date: 02/21/12
[    0.499028] NET: Registered protocol family 16
[    0.499129] Trying to unpack rootfs image as initramfs...
[    0.499133] ACPI: bus type pci registered
[    0.499188] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.499191] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.539602] PCI: Using configuration type 1 for base access
[    0.540322] bio: create slab <bio-0> at 0
[    0.541680] ACPI: EC: Look up EC in DSDT
[    0.542977] ACPI: Executed 1 blocks of module-level executable AML code
[    0.547067] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.582312] ACPI: SSDT 00000000b7621c18 003A4 (v01    AMI      IST 00000001 MSFT 03000001)
[    0.582661] ACPI: Dynamic OEM Table Load:
[    0.582664] ACPI: SSDT           (null) 003A4 (v01    AMI      IST 00000001 MSFT 03000001)
[    0.583080] ACPI: Interpreter enabled
[    0.583083] ACPI: (supports S0 S3 S4 S5)
[    0.583103] ACPI: Using IOAPIC for interrupt routing
[    0.583328] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.600200] ACPI: No dock devices found.
[    0.600203] HEST: Table not found.
[    0.600206] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.600323] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.600410] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.600412] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.600414] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.600416] pci_root PNP0A08:00: host bridge window [mem 0xbc000000-0xffffffff]
[    0.600428] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
[    0.600446] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.600463] pci 0000:00:02.0: [8086:0046] type 0 class 0x000300
[    0.600473] pci 0000:00:02.0: reg 10: [mem 0xfa400000-0xfa7fffff 64bit]
[    0.600479] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.600483] pci 0000:00:02.0: reg 20: [io  0xf080-0xf087]
[    0.600542] pci 0000:00:16.0: [8086:3b64] type 0 class 0x000780
[    0.600569] pci 0000:00:16.0: reg 10: [mem 0xfbd09000-0xfbd0900f 64bit]
[    0.600644] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.600649] pci 0000:00:16.0: PME# disabled
[    0.600688] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    0.600713] pci 0000:00:1a.0: reg 10: [mem 0xfbd08000-0xfbd083ff]
[    0.600800] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.600805] pci 0000:00:1a.0: PME# disabled
[    0.600834] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    0.600855] pci 0000:00:1b.0: reg 10: [mem 0xfbd00000-0xfbd03fff 64bit]
[    0.600932] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.600936] pci 0000:00:1b.0: PME# disabled
[    0.600962] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    0.601039] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.601044] pci 0000:00:1c.0: PME# disabled
[    0.601070] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
[    0.601148] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.601152] pci 0000:00:1c.1: PME# disabled
[    0.601179] pci 0000:00:1c.2: [8086:3b46] type 1 class 0x000604
[    0.601256] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.601261] pci 0000:00:1c.2: PME# disabled
[    0.601291] pci 0000:00:1c.4: [8086:3b4a] type 1 class 0x000604
[    0.601368] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.601373] pci 0000:00:1c.4: PME# disabled
[    0.601409] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    0.601433] pci 0000:00:1d.0: reg 10: [mem 0xfbd07000-0xfbd073ff]
[    0.601520] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.601524] pci 0000:00:1d.0: PME# disabled
[    0.601548] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.601621] pci 0000:00:1f.0: [8086:3b0b] type 0 class 0x000601
[    0.601739] pci 0000:00:1f.2: [8086:3b2f] type 0 class 0x000106
[    0.601765] pci 0000:00:1f.2: reg 10: [io  0xf070-0xf077]
[    0.601775] pci 0000:00:1f.2: reg 14: [io  0xf060-0xf063]
[    0.601786] pci 0000:00:1f.2: reg 18: [io  0xf050-0xf057]
[    0.601798] pci 0000:00:1f.2: reg 1c: [io  0xf040-0xf043]
[    0.601808] pci 0000:00:1f.2: reg 20: [io  0xf020-0xf03f]
[    0.601819] pci 0000:00:1f.2: reg 24: [mem 0xfbd06000-0xfbd067ff]
[    0.601866] pci 0000:00:1f.2: PME# supported from D3hot
[    0.601871] pci 0000:00:1f.2: PME# disabled
[    0.601893] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
[    0.601914] pci 0000:00:1f.3: reg 10: [mem 0xfbd05000-0xfbd050ff 64bit]
[    0.601943] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
[    0.601989] pci 0000:00:1f.6: [8086:3b32] type 0 class 0x001180
[    0.602016] pci 0000:00:1f.6: reg 10: [mem 0xfbd04000-0xfbd04fff 64bit]
[    0.602150] pci 0000:00:1c.0: PCI bridge to [bus 11-11]
[    0.602154] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.602159] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.602166] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.602303] pci 0000:12:00.0: [8086:0083] type 0 class 0x000280
[    0.602351] pci 0000:12:00.0: reg 10: [mem 0xfbc00000-0xfbc01fff 64bit]
[    0.602552] pci 0000:12:00.0: PME# supported from D0 D3hot D3cold
[    0.602579] pci 0000:12:00.0: PME# disabled
[    0.606927] pci 0000:00:1c.1: PCI bridge to [bus 12-12]
[    0.606932] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.606937] pci 0000:00:1c.1:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.606944] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.607061] pci 0000:13:00.0: [10ec:8136] type 0 class 0x000200
[    0.607126] pci 0000:13:00.0: reg 10: [io  0xe000-0xe0ff]
[    0.607238] pci 0000:13:00.0: reg 18: [mem 0xd0b10000-0xd0b10fff 64bit pref]
[    0.607308] pci 0000:13:00.0: reg 20: [mem 0xd0b00000-0xd0b0ffff 64bit pref]
[    0.607354] pci 0000:13:00.0: reg 30: [mem 0xfb200000-0xfb21ffff pref]
[    0.607474] pci 0000:13:00.0: supports D1 D2
[    0.607475] pci 0000:13:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.607490] pci 0000:13:00.0: PME# disabled
[    0.607573] pci 0000:00:1c.2: PCI bridge to [bus 13-13]
[    0.607578] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
[    0.607582] pci 0000:00:1c.2:   bridge window [mem 0xfb200000-0xfbbfffff]
[    0.607589] pci 0000:00:1c.2:   bridge window [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.607645] pci 0000:00:1c.4: PCI bridge to [bus 15-15]
[    0.607650] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.607654] pci 0000:00:1c.4:   bridge window [mem 0xfa800000-0xfb1fffff]
[    0.607662] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.607739] pci 0000:00:1e.0: PCI bridge to [bus 20-20] (subtractive decode)
[    0.607744] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.607749] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.607756] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.607759] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.607761] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.607763] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.607765] pci 0000:00:1e.0:   bridge window [mem 0xbc000000-0xffffffff] (subtractive decode)
[    0.607799] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.607943] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    0.608008] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.608035] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.608062] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.608086] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.608199]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.608371]  pci0000:00: ACPI _OSC control (0x19) granted
[    0.611239] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.611280] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.611320] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.611358] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.611397] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.611436] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.611475] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.611513] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.611608] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.611614] vgaarb: loaded
[    0.611615] vgaarb: bridge control possible 0000:00:02.0
[    0.611769] SCSI subsystem initialized
[    0.611841] libata version 3.00 loaded.
[    0.611885] usbcore: registered new interface driver usbfs
[    0.611893] usbcore: registered new interface driver hub
[    0.611919] usbcore: registered new device driver usb
[    0.611992] PCI: Using ACPI for IRQ routing
[    0.621749] PCI: Discovered peer bus ff
[    0.621793] pci 0000:ff:00.0: [8086:2c62] type 0 class 0x000600
[    0.621814] pci 0000:ff:00.1: [8086:2d01] type 0 class 0x000600
[    0.621833] pci 0000:ff:02.0: [8086:2d10] type 0 class 0x000600
[    0.621849] pci 0000:ff:02.1: [8086:2d11] type 0 class 0x000600
[    0.621865] pci 0000:ff:02.2: [8086:2d12] type 0 class 0x000600
[    0.621881] pci 0000:ff:02.3: [8086:2d13] type 0 class 0x000600
[    0.622014] PCI: pci_cache_line_size set to 64 bytes
[    0.622152] reserve RAM buffer: 000000000009d400 - 000000000009ffff 
[    0.622154] reserve RAM buffer: 00000000b75a6000 - 00000000b7ffffff 
[    0.622157] reserve RAM buffer: 00000000b7621000 - 00000000b7ffffff 
[    0.622159] reserve RAM buffer: 00000000b7800000 - 00000000b7ffffff 
[    0.622256] NetLabel: Initializing
[    0.622258] NetLabel:  domain hash size = 128
[    0.622259] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.622270] NetLabel:  unlabeled traffic allowed by default
[    0.622329] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.622334] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.624357] Switching to clocksource hpet
[    0.626882] Switched to NOHz mode on CPU #0
[    0.626937] Switched to NOHz mode on CPU #1
[    0.627007] Switched to NOHz mode on CPU #3
[    0.627019] Switched to NOHz mode on CPU #2
[    0.629677] AppArmor: AppArmor Filesystem Enabled
[    0.629714] pnp: PnP ACPI init
[    0.629728] ACPI: bus type pnp registered
[    0.629820] pnp 00:00: [bus 00-ff]
[    0.629822] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.629824] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.629825] pnp 00:00: [io  0x0d00-0xffff window]
[    0.629827] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.629829] pnp 00:00: [mem 0x00000000 window]
[    0.629831] pnp 00:00: [mem 0xbc000000-0xffffffff window]
[    0.629922] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.629966] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.629968] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.629969] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.629971] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.629972] pnp 00:01: [mem 0xfee00000-0xfee0ffff]
[    0.630024] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.630026] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.630028] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.630030] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.630032] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.630035] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.630062] pnp 00:02: [dma 4]
[    0.630064] pnp 00:02: [io  0x0000-0x000f]
[    0.630065] pnp 00:02: [io  0x0081-0x0083]
[    0.630066] pnp 00:02: [io  0x0087]
[    0.630068] pnp 00:02: [io  0x0089-0x008b]
[    0.630069] pnp 00:02: [io  0x008f]
[    0.630071] pnp 00:02: [io  0x00c0-0x00df]
[    0.630089] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.630097] pnp 00:03: [io  0x0070-0x0071]
[    0.630110] pnp 00:03: [irq 8]
[    0.630128] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.630135] pnp 00:04: [io  0x0061]
[    0.630154] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.630161] pnp 00:05: [io  0x00f0-0x00ff]
[    0.630167] pnp 00:05: [irq 13]
[    0.630192] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.630211] pnp 00:06: [io  0x0010-0x001f]
[    0.630213] pnp 00:06: [io  0x0022-0x003f]
[    0.630214] pnp 00:06: [io  0x0044-0x005f]
[    0.630215] pnp 00:06: [io  0x0068-0x006f]
[    0.630217] pnp 00:06: [io  0x0072-0x007f]
[    0.630218] pnp 00:06: [io  0x0080]
[    0.630219] pnp 00:06: [io  0x0084-0x0086]
[    0.630221] pnp 00:06: [io  0x0088]
[    0.630222] pnp 00:06: [io  0x008c-0x008e]
[    0.630223] pnp 00:06: [io  0x0090-0x009f]
[    0.630225] pnp 00:06: [io  0x00a2-0x00bf]
[    0.630226] pnp 00:06: [io  0x00e0-0x00ef]
[    0.630228] pnp 00:06: [io  0x04d0-0x04d1]
[    0.630229] pnp 00:06: [mem 0xfe800000-0xfe8001ff]
[    0.630266] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.630269] system 00:06: [mem 0xfe800000-0xfe8001ff] has been reserved
[    0.630272] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.630289] pnp 00:07: [irq 12]
[    0.630309] pnp 00:07: Plug and Play ACPI device, IDs DLL0447 SYN0600 SYN0002 PNP0f13 (active)
[    0.630322] pnp 00:08: [io  0x0060]
[    0.630324] pnp 00:08: [io  0x0064]
[    0.630325] pnp 00:08: [io  0x0062]
[    0.630326] pnp 00:08: [io  0x0066]
[    0.630331] pnp 00:08: [irq 1]
[    0.630350] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.630459] pnp 00:09: [io  0x0400-0x047f]
[    0.630461] pnp 00:09: [io  0x1180-0x119f]
[    0.630462] pnp 00:09: [io  0x0500-0x057f]
[    0.630464] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.630466] pnp 00:09: [mem 0xfec00000-0xfecfffff]
[    0.630467] pnp 00:09: [mem 0xfed08000-0xfed08fff]
[    0.630469] pnp 00:09: [mem 0xff000000-0xffffffff]
[    0.630504] system 00:09: [io  0x0400-0x047f] has been reserved
[    0.630506] system 00:09: [io  0x1180-0x119f] has been reserved
[    0.630508] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.630511] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.630513] system 00:09: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.630515] system 00:09: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.630517] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
[    0.630520] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.630594] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.630621] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.630804] pnp: PnP ACPI: found 11 devices
[    0.630805] ACPI: ACPI bus type pnp unregistered
[    0.636448] PCI: max bus depth: 1 pci_try_num: 2
[    0.636505] pci 0000:00:1c.1: BAR 15: assigned [mem 0xbc000000-0xbc1fffff 64bit pref]
[    0.636508] pci 0000:00:1c.1: BAR 13: assigned [io  0x2000-0x2fff]
[    0.636511] pci 0000:00:1c.0: BAR 14: assigned [mem 0xbc200000-0xbc3fffff]
[    0.636513] pci 0000:00:1c.0: BAR 15: assigned [mem 0xbc400000-0xbc5fffff 64bit pref]
[    0.636516] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.636518] pci 0000:00:1c.0: PCI bridge to [bus 11-11]
[    0.636521] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.636527] pci 0000:00:1c.0:   bridge window [mem 0xbc200000-0xbc3fffff]
[    0.636532] pci 0000:00:1c.0:   bridge window [mem 0xbc400000-0xbc5fffff 64bit pref]
[    0.636539] pci 0000:00:1c.1: PCI bridge to [bus 12-12]
[    0.636542] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.636548] pci 0000:00:1c.1:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.636553] pci 0000:00:1c.1:   bridge window [mem 0xbc000000-0xbc1fffff 64bit pref]
[    0.636560] pci 0000:00:1c.2: PCI bridge to [bus 13-13]
[    0.636564] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
[    0.636569] pci 0000:00:1c.2:   bridge window [mem 0xfb200000-0xfbbfffff]
[    0.636574] pci 0000:00:1c.2:   bridge window [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.636581] pci 0000:00:1c.4: PCI bridge to [bus 15-15]
[    0.636584] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.636590] pci 0000:00:1c.4:   bridge window [mem 0xfa800000-0xfb1fffff]
[    0.636595] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.636603] pci 0000:00:1e.0: PCI bridge to [bus 20-20]
[    0.636604] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.636610] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.636614] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.636641] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.636646] pci 0000:00:1c.0: setting latency timer to 64
[    0.636661] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.636666] pci 0000:00:1c.1: setting latency timer to 64
[    0.636676] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.636681] pci 0000:00:1c.2: setting latency timer to 64
[    0.636688] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.636692] pci 0000:00:1c.4: setting latency timer to 64
[    0.636700] pci 0000:00:1e.0: setting latency timer to 64
[    0.636704] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.636706] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.636708] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.636710] pci_bus 0000:00: resource 7 [mem 0xbc000000-0xffffffff]
[    0.636712] pci_bus 0000:11: resource 0 [io  0x3000-0x3fff]
[    0.636713] pci_bus 0000:11: resource 1 [mem 0xbc200000-0xbc3fffff]
[    0.636715] pci_bus 0000:11: resource 2 [mem 0xbc400000-0xbc5fffff 64bit pref]
[    0.636717] pci_bus 0000:12: resource 0 [io  0x2000-0x2fff]
[    0.636719] pci_bus 0000:12: resource 1 [mem 0xfbc00000-0xfbcfffff]
[    0.636721] pci_bus 0000:12: resource 2 [mem 0xbc000000-0xbc1fffff 64bit pref]
[    0.636723] pci_bus 0000:13: resource 0 [io  0xe000-0xefff]
[    0.636724] pci_bus 0000:13: resource 1 [mem 0xfb200000-0xfbbfffff]
[    0.636726] pci_bus 0000:13: resource 2 [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.636728] pci_bus 0000:15: resource 0 [io  0xd000-0xdfff]
[    0.636730] pci_bus 0000:15: resource 1 [mem 0xfa800000-0xfb1fffff]
[    0.636732] pci_bus 0000:15: resource 2 [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.636734] pci_bus 0000:20: resource 4 [io  0x0000-0x0cf7]
[    0.636736] pci_bus 0000:20: resource 5 [io  0x0d00-0xffff]
[    0.636737] pci_bus 0000:20: resource 6 [mem 0x000a0000-0x000bffff]
[    0.636739] pci_bus 0000:20: resource 7 [mem 0xbc000000-0xffffffff]
[    0.636741] pci_bus 0000:ff: resource 0 [io  0x0000-0xffff]
[    0.636743] pci_bus 0000:ff: resource 1 [mem 0x00000000-0xfffffffff]
[    0.636779] NET: Registered protocol family 2
[    0.636913] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.637830] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.641129] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.641548] TCP: Hash tables configured (established 524288 bind 65536)
[    0.641550] TCP reno registered
[    0.641559] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.641591] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.641718] NET: Registered protocol family 1
[    0.641734] pci 0000:00:02.0: Boot video device
[    0.896307] PCI: CLS 64 bytes, default 64
[    0.896783] audit: initializing netlink socket (disabled)
[    0.896799] type=2000 audit(1329856038.732:1): initialized
[    0.921498] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.934521] VFS: Disk quotas dquot_6.5.2
[    0.934575] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.935106] fuse init (API version 7.16)
[    0.935184] msgmni has been set to 5727
[    0.935554] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.935586] io scheduler noop registered
[    0.935589] io scheduler deadline registered
[    0.935626] io scheduler cfq registered (default)
[    0.935735] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.935793] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.935876] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.935924] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.936003] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.936051] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.936128] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.936200] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
[    0.936283] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.936391] pciehp: Using ACPI for slot detection.
[    0.936447] pciehp 0000:00:1c.4:pcie04: HPC vendor_id 8086 device_id 3b4a ss_vid 1028 ss_did 447
[    0.936479] pciehp 0000:00:1c.4:pcie04: service driver pciehp loaded
[    0.936485] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.936521] intel_idle: MWAIT substates: 0x1120
[    0.936522] intel_idle: v0.4 model 0x25
[    0.936523] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.936610] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.936648] ACPI: AC Adapter [AC] (on-line)
[    0.936735] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.936740] ACPI: Power Button [PWRB]
[    0.936772] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.938679] ACPI: Lid Switch [LID0]
[    0.938711] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.938714] ACPI: Sleep Button [SBTN]
[    0.938741] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.938743] ACPI: Power Button [PWRF]
[    0.938767] ACPI: acpi_idle yielding to intel_idle
[    0.951426] thermal LNXTHERM:00: registered as thermal_zone0
[    0.951429] ACPI: Thermal Zone [THM] (58 C)
[    0.951460] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.951490] ERST: Table is not found!
[    0.951534] ACPI: Battery Slot [BAT0] (battery absent)
[    0.951574] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.997909] Freeing initrd memory: 13404k freed
[    1.072448] Linux agpgart interface v0.103
[    1.072520] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.072618] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.073697] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.073843] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.074667] brd: module loaded
[    1.075039] loop: module loaded
[    1.075384] Fixed MDIO Bus: probed
[    1.075401] PPP generic driver version 2.4.2
[    1.075427] tun: Universal TUN/TAP device driver, 1.6
[    1.075429] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.075488] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.075508] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.075526] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.075531] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.075558] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.075588] ehci_hcd 0000:00:1a.0: debug port 2
[    1.079557] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.079575] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfbd08000
[    1.092114] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.092243] hub 1-0:1.0: USB hub found
[    1.092247] hub 1-0:1.0: 2 ports detected
[    1.092310] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.092320] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.092324] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.092355] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.092381] ehci_hcd 0000:00:1d.0: debug port 2
[    1.096365] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.096378] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfbd07000
[    1.112102] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.112213] hub 2-0:1.0: USB hub found
[    1.112216] hub 2-0:1.0: 2 ports detected
[    1.112259] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.112269] uhci_hcd: USB Universal Host Controller Interface driver
[    1.112318] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2] at 0x60,0x64 irq 1,12
[    1.134730] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.134737] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.134846] mousedev: PS/2 mouse device common for all mice
[    1.135805] rtc_cmos 00:03: RTC can wake from S4
[    1.135896] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.135927] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.136007] device-mapper: uevent: version 1.0.3
[    1.136073] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.136152] cpuidle: using governor ladder
[    1.136271] cpuidle: using governor menu
[    1.136273] EFI Variables Facility v0.08 2004-May-17
[    1.136471] TCP cubic registered
[    1.136566] NET: Registered protocol family 10
[    1.136956] NET: Registered protocol family 17
[    1.136970] Registering the dns_resolver key type
[    1.137040] PM: Hibernation image not present or could not be loaded.
[    1.137050] registered taskstats version 1
[    1.150282]   Magic number: 0:601:498
[    1.150436] rtc_cmos 00:03: setting system clock to 2012-02-21 20:27:19 UTC (1329856039)
[    1.151547] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.151549] EDD information not available.
[    1.153229] Freeing unused kernel memory: 988k freed
[    1.153387] Write protecting the kernel read-only data: 12288k
[    1.159219] Freeing unused kernel memory: 2036k freed
[    1.163478] Freeing unused kernel memory: 1388k freed
[    1.168013] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.184627] udevd[89]: starting version 173
[    1.229731] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.229781] r8169 0000:13:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.229830] r8169 0000:13:00.0: setting latency timer to 64
[    1.229896] r8169 0000:13:00.0: irq 44 for MSI/MSI-X
[    1.230770] r8169 0000:13:00.0: eth0: RTL8102e at 0xffffc90000654000, 78:2b:cb:c6:df:17, XID 04e00000 IRQ 44
[    1.237380] ahci 0000:00:1f.2: version 3.0
[    1.237407] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.237463] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.237545] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x13 impl SATA mode
[    1.237548] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems sxs apst 
[    1.237553] ahci 0000:00:1f.2: setting latency timer to 64
[    1.252540] scsi0 : ahci
[    1.252754] scsi1 : ahci
[    1.252907] scsi2 : ahci
[    1.253047] scsi3 : ahci
[    1.253210] scsi4 : ahci
[    1.253381] scsi5 : ahci
[    1.253594] ata1: SATA max UDMA/133 abar m2048@0xfbd06000 port 0xfbd06100 irq 45
[    1.253598] ata2: SATA max UDMA/133 abar m2048@0xfbd06000 port 0xfbd06180 irq 45
[    1.253600] ata3: DUMMY
[    1.253601] ata4: DUMMY
[    1.253603] ata5: SATA max UDMA/133 abar m2048@0xfbd06000 port 0xfbd06300 irq 45
[    1.253605] ata6: DUMMY
[    1.412041] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.544670] hub 1-1:1.0: USB hub found
[    1.544874] hub 1-1:1.0: 6 ports detected
[    1.571941] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.571976] ata5: SATA link down (SStatus 0 SControl 300)
[    1.572019] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.583558] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L633J, D200, max UDMA/100
[    1.595975] ata2.00: configured for UDMA/100
[    1.619916] ata1.00: ATA-8: TOSHIBA MK3265GSX, GJ002D, max UDMA/100
[    1.619921] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.620967] ata1.00: configured for UDMA/100
[    1.621239] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3265GS GJ00 PQ: 0 ANSI: 5
[    1.621347] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.621428] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.621612] sd 0:0:0:0: [sda] Write Protect is off
[    1.621617] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.621785] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.627956] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L633J D200 PQ: 0 ANSI: 5
[    1.637336] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.637342] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.637489] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.637550] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.655876] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    1.715489]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.716057] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.788907] hub 2-1:1.0: USB hub found
[    1.789138] hub 2-1:1.0: 8 ports detected
[    1.859983] usb 1-1.2: new low speed USB device number 3 using ehci_hcd
[    1.895713] Refined TSC clocksource calibration: 2526.999 MHz.
[    1.895722] Switching to clocksource tsc
[    1.979205] input: HP Wireless Optical Mobile Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input5
[    1.979285] generic-usb 0003:03F0:8107.0001: input,hidraw0: USB HID v1.11 Mouse [HP Wireless Optical Mobile Mouse] on usb-0000:00:1a.0-1.2/input0
[    1.979297] usbcore: registered new interface driver usbhid
[    1.979298] usbhid: USB HID core driver
[    2.035904] usb 1-1.6: new high speed USB device number 4 using ehci_hcd
[    2.243796] usb 2-1.2: new high speed USB device number 3 using ehci_hcd
[    2.339774] usbcore: registered new interface driver uas
[    2.340399] Initializing USB Mass Storage driver...
[    2.340515] scsi6 : usb-storage 2-1.2:1.0
[    2.340615] usbcore: registered new interface driver usb-storage
[    2.340618] USB Mass Storage support registered.
[    2.407723] usb 2-1.6: new full speed USB device number 4 using ehci_hcd
[    2.502312] hub 2-1.6:1.0: USB hub found
[    2.502444] hub 2-1.6:1.0: 3 ports detected
[    2.541189] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    2.771499] usb 2-1.6.1: new full speed USB device number 5 using ehci_hcd
[    2.868499] input: HID 413c:8161 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.1/2-1.6.1:1.0/input/input6
[    2.868571] generic-usb 0003:413C:8161.0002: input,hidraw1: USB HID v1.11 Keyboard [HID 413c:8161] on usb-0000:00:1d.0-1.6.1/input0
[    2.939281] usb 2-1.6.2: new full speed USB device number 6 using ehci_hcd
[    3.037523] input: HID 413c:8162 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.2/2-1.6.2:1.0/input/input7
[    3.037594] generic-usb 0003:413C:8162.0003: input,hidraw2: USB HID v1.11 Mouse [HID 413c:8162] on usb-0000:00:1d.0-1.6.2/input0
[    3.381955] scsi 6:0:0:0: Direct-Access     ST950032 5AS                   PQ: 0 ANSI: 2 CCS
[    3.754832] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    3.755944] sd 6:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.756833] sd 6:0:0:0: [sdb] Write Protect is off
[    3.756840] sd 6:0:0:0: [sdb] Mode Sense: 28 00 00 00
[    3.757685] sd 6:0:0:0: [sdb] No Caching mode page present
[    3.757690] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.760299] sd 6:0:0:0: [sdb] No Caching mode page present
[    3.760314] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.760954]  sdb: sdb1
[    3.763967] sd 6:0:0:0: [sdb] No Caching mode page present
[    3.763974] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.763979] sd 6:0:0:0: [sdb] Attached SCSI disk
[    4.962815] Adding 6394876k swap on /dev/sda6.  Priority:-1 extents:1 across:6394876k 
[    5.044462] udevd[332]: starting version 173
[    5.843998] lp: driver loaded but no devices found
[    7.545585] wmi: Mapper loaded
[    7.546999] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[    7.547016] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    7.547062] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[    7.548107] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[    7.656239] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    7.801402] cfg80211: Calling CRDA to update world regulatory domain
[    7.866759] mei: module is from the staging directory, the quality is unknown, you have been warned.
[    7.867098] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.867105] mei 0000:00:16.0: setting latency timer to 64
[    7.901228] input: Dell WMI hotkeys as /devices/virtual/input/input8
[    7.933450] [drm] Initialized drm 1.1.0 20060810
[    8.549586] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.549591] i915 0000:00:02.0: setting latency timer to 64
[    8.594005] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[    8.594011] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    8.594012] [drm] Driver supports precise vblank timestamp query.
[    8.594052] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    8.755417] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    8.889376] fbcon: inteldrmfb (fb0) is primary device
[    8.889486] Console: switching to colour frame buffer device 170x48
[    8.889515] fb0: inteldrmfb frame buffer device
[    8.889517] drm: registered panic notifier
[    8.900204] acpi device:2e: registered as cooling_device4
[    8.900377] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input9
[    8.900433] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    8.900496] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    9.250638] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[    9.325498] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[    9.483588] cfg80211: World regulatory domain updated:
[    9.483591] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.483593] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.483596] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.483597] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.483599] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.483601] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.487758] usb 2-1.6.3: new full speed USB device number 7 using ehci_hcd
[    9.847562] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    9.847566] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[    9.847685] iwlagn 0000:12:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.847695] iwlagn 0000:12:00.0: setting latency timer to 64
[    9.847731] iwlagn 0000:12:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[    9.868272] iwlagn 0000:12:00.0: device EEPROM VER=0x15d, CALIB=0x6
[    9.868274] iwlagn 0000:12:00.0: Device SKU: 0X9
[    9.868276] iwlagn 0000:12:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[    9.868283] iwlagn 0000:12:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[    9.868360] iwlagn 0000:12:00.0: irq 47 for MSI/MSI-X
[   10.232643] type=1400 audit(1329852448.584:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=728 comm="apparmor_parser"
[   10.232654] type=1400 audit(1329852448.584:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=613 comm="apparmor_parser"
[   10.232983] type=1400 audit(1329852448.584:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=613 comm="apparmor_parser"
[   10.232990] type=1400 audit(1329852448.584:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=728 comm="apparmor_parser"
[   10.233189] type=1400 audit(1329852448.584:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=613 comm="apparmor_parser"
[   10.233204] type=1400 audit(1329852448.584:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=728 comm="apparmor_parser"
[   10.248345] Linux video capture interface: v2.00
[   10.335617] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:6480)
[   10.342447] iwlagn 0000:12:00.0: loaded firmware version 39.31.5.1 build 35138
[   10.342610] Registered led device: phy0-led
[   10.342637] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   10.357606] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input11
[   10.357705] usbcore: registered new interface driver uvcvideo
[   10.357708] USB Video Class driver (v1.1.0)
[   10.675581] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   10.926174] Bluetooth: Core ver 2.16
[   10.926208] NET: Registered protocol family 31
[   10.926210] Bluetooth: HCI device and connection manager initialized
[   10.926213] Bluetooth: HCI socket layer initialized
[   10.926215] Bluetooth: L2CAP socket layer initialized
[   10.926283] Bluetooth: SCO socket layer initialized
[   10.995976] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   10.996217] usbcore: registered new interface driver btusb
[   11.044797] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.044865] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   11.044899] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.411317] HDMI status: Pin=4 Presence_Detect=0 ELD_Valid=0
[   11.411574] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   11.411708] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   11.411783] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   11.562871] init: failsafe main process (928) killed by TERM signal
[   12.745809] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
[   14.668281] type=1400 audit(1329852453.020:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1047 comm="apparmor_parser"
[   14.668787] type=1400 audit(1329852453.024:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1047 comm="apparmor_parser"
[   14.669065] type=1400 audit(1329852453.024:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1047 comm="apparmor_parser"
[   14.789661] type=1400 audit(1329852453.144:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1046 comm="apparmor_parser"
[   15.178826] ppdev: user-space parallel port driver
[   15.326432] audit_printk_skb: 24 callbacks suppressed
[   15.326435] type=1400 audit(1329852453.680:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1080 comm="apparmor_parser"
[   15.326932] type=1400 audit(1329852453.680:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1080 comm="apparmor_parser"
[   16.366691] init: apport pre-start process (1106) terminated with status 1
[   16.369631] init: apport post-stop process (1126) terminated with status 1
```

---

### Post by ric1321 on 2012-02-21
What about reinstalling ubuntu?

---

### Post by roelforg on 2012-02-22
> **ric1321 said:**
> What about reinstalling ubuntu?

I can't figure this one out.
So i'm afraid you're on your own, sorry.
Reinstalling might be your only option,
Backup your files first though...

I'm sorry i couldn't help you.
:-(

I hope to see you again some day...

-- Roelforg, out...
<disconnected>

FYI: The rules here say that i've got to tell you that this is dangerous as it'll wipe your hd.

---

### Post by ric1321 on 2012-02-22
Thank you for everything, you're awesome! And don't feel sorry, you're the only one who tried to help me. Thank you again!

---


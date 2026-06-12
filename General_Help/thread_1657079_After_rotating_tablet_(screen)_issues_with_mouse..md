---
title: "After rotating tablet (screen) issues with mouse."
date: 2010-12-31
forum: General Help
---

### Post by WG- on 2010-12-31
Hello,

I am in the possession of a tablet, Toshiba Portégé m750. Since about the beginning October I am running ubuntu on my tablet. I had some problems at first 
- [http://ubuntuforums.org/showthread.php?t=1587413](http://ubuntuforums.org/showthread.php?t=1587413)

But other then that nothing big. Now since quiet a while I have the following problem (I already have it pretty long maybe even since of October but because it didn't occur that much I didn't bother it to solve, nowadays however it happens always).

The problem is as followed. When I run my bash script (see at the bottom of this post) to put my tablet into tablet mode (resize panels for better touching with fingers + rotate screen, mouse) everything is fine. Mouse works correctly, tabletpen works correctly. Now when I put my tablet back into normal mode the mouse is often (not always) messed up. 
- It starts moving by itself (always horizontally to the right)
- It starts to use the left/right mouse buttons, uncontrollably, and then holds the click.

For clearance my mouse isn't doing anything, the computer "thinks" the mouse is doing it or something.

Now as far as I remember this "bug" didn't occur always but nowadays it nearly always happens when I change back from tablet mode to normal mode. 

I want to get rid of this very strange behavior of my mouse. I do not know however how I can fix this or where the problem comes from. Anyone who can help me backtracing the cause of the problem and to fix it?

My script to go from normal mode to tablet and vice versa.
```
orientation=`xrandr --query | grep LVDS | awk '{print $4}'`

if [ "$orientation" = "(normal" ]; then
    # tablet mode
    # resize top and bottom panel for touch with fingers
    gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 50
    gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 50
    # rotate
    xrandr -o inverted
        xsetwacom set "Serial Wacom Tablet" Rotate HALF
        xsetwacom set "Serial Wacom Tablet eraser" Rotate HALF
        xsetwacom set "Serial Wacom Tablet touch" Rotate HALF
    # start onboard
    onboard
else
    # normal mode
    # restore top and botom panel sizes
    gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 24
    gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 30
    # put everything back to normal
    xrandr -o normal
        xsetwacom set "Serial Wacom Tablet" Rotate None
        xsetwacom set "Serial Wacom Tablet eraser" Rotate None
        xsetwacom set "Serial Wacom Tablet touch" Rotate None
    # kill onboard
    killall onboard
fi
```

---

### Post by WG- on 2011-01-01
Hmmm I found out something interesting. I now know for sure the problem is not located in my script but in rotating my screen and putting it from tablet mode to normal mode (psychically)

Apparently (I would guess) a script is being run when I go from tablet mode to normal mode (again psychically rotating my screen). How can I find out what code is being executed then?

---

### Post by Favux on 2011-01-01
Hi WG-,

Are you talking about a usb mouse you are plugging into the M750 or are you talking about the touch pad?  Either way you can look at the driver and the properties it has by entering in a terminal:
```
xinput --list
```
and then find the "Device name" of the mouse.  Using the "Device name" in quotes enter:
```
xinput list-props "Device name"
```

---

### Post by WG- on 2011-01-02
I think the cause could be in the mouse yes, not the touchpad. Because when I shutdown the power of the mouse and use my touchpad the problem often doesn't occur anymore. (However I'm not 100% certain I need to test it when the problem occurs again)

Anyway my xinput list
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch               	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=17	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; CNA7157                                 	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Toshiba input device                    	id=18	[slave  keyboard (3)]

```

Logitech USB Receiver, ID=9
```
Device 'Logitech USB Receiver':
	Device Enabled (125):	1
	Coordinate Transformation Matrix (127):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (251):	0
	Device Accel Constant Deceleration (252):	1.000000
	Device Accel Adaptive Deceleration (253):	1.000000
	Device Accel Velocity Scaling (254):	10.000000
	Evdev Reopen Attempts (244):	10
	Evdev Axis Inversion (255):	0, 0
	Evdev Axes Swap (257):	0
	Axis Labels (258):	"Rel X" (135), "Rel Y" (136)
	Button Labels (259):	"Button Left" (128), "Button Middle" (129), "Button Right" (130), "Button Wheel Up" (131), "Button Wheel Down" (132), "Button Horiz Wheel Left" (133), "Button Horiz Wheel Right" (134), "Button Side" (246), "Button Extra" (247), "Button Forward" (248), "Button Back" (249), "Button Task" (250), "Button Unknown" (245), "Button Unknown" (245), "Button Unknown" (245), "Button Unknown" (245), "Button Unknown" (245), "Button Unknown" (245), "Button Unknown" (245), "Button Unknown" (245), "Button Unknown" (245), "Button Unknown" (245), "Button Unknown" (245), "Button Unknown" (245)
	Evdev Middle Button Emulation (260):	2
	Evdev Middle Button Timeout (261):	50
	Evdev Wheel Emulation (262):	0
	Evdev Wheel Emulation Axes (263):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (264):	10
	Evdev Wheel Emulation Timeout (265):	200
	Evdev Wheel Emulation Button (266):	4
	Evdev Drag Lock Buttons (267):	0
```

Logitech USB Receiver, ID=10
```
Device 'Logitech USB Receiver':
	Device Enabled (125):	1
	Coordinate Transformation Matrix (127):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (251):	0
	Device Accel Constant Deceleration (252):	1.000000
	Device Accel Adaptive Deceleration (253):	1.000000
	Device Accel Velocity Scaling (254):	10.000000
	Evdev Reopen Attempts (244):	10
	Evdev Axis Inversion (255):	0, 0
	Evdev Axis Calibration (256):	<no items>
	Evdev Axes Swap (257):	0
	Axis Labels (258):	"Abs Volume" (269)
	Button Labels (259):	"Button 0" (268), "Button Unknown" (245), "Button Unknown" (245), "Button Wheel Up" (131), "Button Wheel Down" (132), "Button Horiz Wheel Left" (133), "Button Horiz Wheel Right" (134)
	Evdev Middle Button Emulation (260):	2
	Evdev Middle Button Timeout (261):	50
	Evdev Wheel Emulation (262):	0
	Evdev Wheel Emulation Axes (263):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (264):	10
	Evdev Wheel Emulation Timeout (265):	200
	Evdev Wheel Emulation Button (266):	4
	Evdev Drag Lock Buttons (267):	0

```

PS/2 Mouse, ID=13
```
Device 'PS/2 Mouse':
	Device Enabled (125):	1
	Coordinate Transformation Matrix (127):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (251):	0
	Device Accel Constant Deceleration (252):	1.000000
	Device Accel Adaptive Deceleration (253):	1.000000
	Device Accel Velocity Scaling (254):	10.000000
	Evdev Reopen Attempts (244):	10
	Evdev Axis Inversion (255):	0, 0
	Evdev Axes Swap (257):	0
	Axis Labels (258):	"Rel X" (135), "Rel Y" (136)
	Button Labels (259):	"Button Left" (128), "Button Middle" (129), "Button Right" (130), "Button Wheel Up" (131), "Button Wheel Down" (132)
	Evdev Middle Button Emulation (260):	2
	Evdev Middle Button Timeout (261):	50
	Evdev Wheel Emulation (262):	0
	Evdev Wheel Emulation Axes (263):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (264):	10
	Evdev Wheel Emulation Timeout (265):	200
	Evdev Wheel Emulation Button (266):	4
	Evdev Drag Lock Buttons (267):	0
```

I'm not sure which one is the mouse actually. Because I have a logitech wireless mouse and as you can see 3 mouses are listed...

---

### Post by Favux on 2011-01-02
I don't think you are suppose to have two "Logitech USB Receiver" on two separate events.  I don't know what to make of the PS/2 Mouse entry, but it sure looks like the Logitech from it's list-props on yet a third event.  We'd need a mouse guru to tell us for sure what's what.

You could look at your Xorg.0.log in /var/log and find out if evdev is using different snippets to set up the Logitech on different events.  If so we could try blocking one of the snippets and see if that fixes the problem.

---

### Post by WG- on 2011-01-02
I just had the 'bug' again. And I checked xinput list-props again to see if there were any changes but the properties are the same.

I also checked the Xorg.0.log file and there seems certainly some activity of "evdev" (don't know what evdev is though).

> [    24.396] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    24.416] (II) evdev-grail: failed to open grail, no gesture support
[    24.418] (**) CNA7157: Applying InputClass "evdev keyboard catchall"
[    24.449] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"

also a lot of:
[ 51861.017] (WW) Serial Wacom Tablet stylus: bad data at 8 v=91 l=9
and 
[ 55979.141] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
in the log

```
[    23.670] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    23.670] X Protocol Version 11, Revision 0
[    23.670] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    23.670] Current Operating System: Linux WG-Tablet 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686
[    23.670] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=c34df9d0-57ce-44ba-8da2-09ba39b1111c ro quiet splash
[    23.670] Build Date: 16 September 2010  05:39:22PM
[    23.670] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    23.670] Current version of pixman: 0.18.4
[    23.670] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    23.670] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.670] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan  1 23:30:01 2011
[    23.774] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.801] (==) No Layout section.  Using the first Screen section.
[    23.801] (==) No screen section available. Using defaults.
[    23.801] (**) |-->Screen "Default Screen Section" (0)
[    23.801] (**) |   |-->Monitor "<default monitor>"
[    23.801] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    23.801] (==) Automatically adding devices
[    23.801] (==) Automatically enabling devices
[    23.801] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.801] 	Entry deleted from font path.
[    23.801] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    23.801] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    23.801] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    23.801] (II) Loader magic: 0x81f8e00
[    23.801] (II) Module ABI versions:
[    23.801] 	X.Org ANSI C Emulation: 0.4
[    23.801] 	X.Org Video Driver: 8.0
[    23.802] 	X.Org XInput driver : 11.0
[    23.802] 	X.Org Server Extension : 4.0
[    23.803] (--) PCI:*(0:0:2:0) 8086:2a42:1179:000b rev 7, Mem @ 0xff400000/4194304, 0xe0000000/268435456, I/O @ 0x0000cff8/8
[    23.803] (--) PCI: (0:0:2:1) 8086:2a43:1179:000b rev 7, Mem @ 0xca000000/1048576
[    23.803] (II) Open ACPI successful (/var/run/acpid.socket)
[    23.803] (II) LoadModule: "extmod"
[    24.140] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    24.140] (II) Module extmod: vendor="X.Org Foundation"
[    24.140] 	compiled for 1.9.0, module version = 1.0.0
[    24.140] 	Module class: X.Org Server Extension
[    24.140] 	ABI class: X.Org Server Extension, version 4.0
[    24.140] (II) Loading extension MIT-SCREEN-SAVER
[    24.140] (II) Loading extension XFree86-VidModeExtension
[    24.140] (II) Loading extension XFree86-DGA
[    24.140] (II) Loading extension DPMS
[    24.140] (II) Loading extension XVideo
[    24.140] (II) Loading extension XVideo-MotionCompensation
[    24.140] (II) Loading extension X-Resource
[    24.140] (II) LoadModule: "dbe"
[    24.140] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    24.140] (II) Module dbe: vendor="X.Org Foundation"
[    24.140] 	compiled for 1.9.0, module version = 1.0.0
[    24.140] 	Module class: X.Org Server Extension
[    24.140] 	ABI class: X.Org Server Extension, version 4.0
[    24.140] (II) Loading extension DOUBLE-BUFFER
[    24.140] (II) LoadModule: "glx"
[    24.141] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    24.141] (II) Module glx: vendor="X.Org Foundation"
[    24.141] 	compiled for 1.9.0, module version = 1.0.0
[    24.141] 	ABI class: X.Org Server Extension, version 4.0
[    24.141] (==) AIGLX enabled
[    24.141] (II) Loading extension GLX
[    24.141] (II) LoadModule: "record"
[    24.141] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    24.141] (II) Module record: vendor="X.Org Foundation"
[    24.141] 	compiled for 1.9.0, module version = 1.13.0
[    24.141] 	Module class: X.Org Server Extension
[    24.141] 	ABI class: X.Org Server Extension, version 4.0
[    24.141] (II) Loading extension RECORD
[    24.141] (II) LoadModule: "dri"
[    24.141] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    24.141] (II) Module dri: vendor="X.Org Foundation"
[    24.141] 	compiled for 1.9.0, module version = 1.0.0
[    24.141] 	ABI class: X.Org Server Extension, version 4.0
[    24.141] (II) Loading extension XFree86-DRI
[    24.141] (II) LoadModule: "dri2"
[    24.142] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.142] (II) Module dri2: vendor="X.Org Foundation"
[    24.142] 	compiled for 1.9.0, module version = 1.2.0
[    24.142] 	ABI class: X.Org Server Extension, version 4.0
[    24.142] (II) Loading extension DRI2
[    24.142] (==) Matched intel as autoconfigured driver 0
[    24.142] (==) Matched vesa as autoconfigured driver 1
[    24.142] (==) Matched fbdev as autoconfigured driver 2
[    24.142] (==) Assigned the driver to the xf86ConfigLayout
[    24.142] (II) LoadModule: "intel"
[    24.142] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    24.142] (II) Module intel: vendor="X.Org Foundation"
[    24.142] 	compiled for 1.9.0, module version = 2.12.0
[    24.142] 	Module class: X.Org Video Driver
[    24.142] 	ABI class: X.Org Video Driver, version 8.0
[    24.142] (II) LoadModule: "vesa"
[    24.143] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.143] (II) Module vesa: vendor="X.Org Foundation"
[    24.143] 	compiled for 1.8.99.905, module version = 2.3.0
[    24.143] 	Module class: X.Org Video Driver
[    24.143] 	ABI class: X.Org Video Driver, version 8.0
[    24.143] (II) LoadModule: "fbdev"
[    24.143] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.143] (II) Module fbdev: vendor="X.Org Foundation"
[    24.143] 	compiled for 1.8.99.905, module version = 0.4.2
[    24.143] 	ABI class: X.Org Video Driver, version 8.0
[    24.143] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    24.144] (II) VESA: driver for VESA chipsets: vesa
[    24.144] (II) FBDEV: driver for framebuffer: fbdev
[    24.144] (++) using VT number 7

[    24.144] (WW) Falling back to old probe method for vesa
[    24.144] (WW) Falling back to old probe method for fbdev
[    24.144] (II) Loading sub module "fbdevhw"
[    24.144] (II) LoadModule: "fbdevhw"
[    24.144] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.144] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.144] 	compiled for 1.9.0, module version = 0.0.2
[    24.144] 	ABI class: X.Org Video Driver, version 8.0
[    24.146] drmOpenDevice: node name is /dev/dri/card0
[    24.146] drmOpenDevice: open result is 9, (OK)
[    24.158] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    24.160] drmOpenDevice: node name is /dev/dri/card0
[    24.160] drmOpenDevice: open result is 9, (OK)
[    24.160] drmOpenByBusid: drmOpenMinor returns 9
[    24.160] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    24.160] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    24.160] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    24.160] (==) intel(0): RGB weight 888
[    24.160] (==) intel(0): Default visual is TrueColor
[    24.160] (II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[    24.161] (--) intel(0): Chipset: "GM45"
[    24.161] (==) intel(0): video overlay key set to 0x101fe
[    24.176] (II) intel(0): Output VGA1 has no monitor section
[    24.176] (II) intel(0): Output LVDS1 has no monitor section
[    24.176] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    24.205] (II) intel(0): Output DVI1 has no monitor section
[    24.220] (II) intel(0): EDID for output VGA1
[    24.220] (II) intel(0): EDID for output LVDS1
[    24.220] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "1024x768i" (interlace mode not supported)
[    24.220] (II) intel(0): Not using default mode "512x384i" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    24.220] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[    24.220] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[    24.220] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    24.220] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    24.220] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    24.221] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1792x1344" (hsync out of range)
[    24.221] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1856x1392" (hsync out of range)
[    24.221] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1920x1440" (hsync out of range)
[    24.221] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    24.221] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
[    24.221] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
[    24.221] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
[    24.221] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "1920x1440" (hsync out of range)
[    24.221] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
[    24.221] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "2048x1536" (hsync out of range)
[    24.221] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    24.221] (II) intel(0): Not using default mode "2048x1536" (hsync out of range)
[    24.221] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    24.221] (II) intel(0): Printing probed modes for output LVDS1
[    24.221] (II) intel(0): Modeline "1280x800"x60.0   68.93  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (49.0 kHz)
[    24.221] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[    24.221] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    24.222] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    24.222] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.222] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    24.222] (II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[    24.222] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    24.222] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    24.222] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    24.222] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    24.222] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[    24.222] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    24.222] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    24.222] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    24.222] (II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[    24.222] (II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[    24.222] (II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[    24.250] (II) intel(0): EDID for output DVI1
[    24.250] (II) intel(0): Output VGA1 disconnected
[    24.250] (II) intel(0): Output LVDS1 connected
[    24.250] (II) intel(0): Output DVI1 disconnected
[    24.250] (II) intel(0): Using exact sizes for initial modes
[    24.250] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    24.250] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    24.250] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    24.250] (==) intel(0): DPI set to (96, 96)
[    24.250] (II) Loading sub module "fb"
[    24.250] (II) LoadModule: "fb"
[    24.250] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.251] (II) Module fb: vendor="X.Org Foundation"
[    24.251] 	compiled for 1.9.0, module version = 1.0.0
[    24.251] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    24.251] (II) UnloadModule: "vesa"
[    24.251] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.251] (II) UnloadModule: "fbdev"
[    24.251] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.251] (II) UnloadModule: "fbdevhw"
[    24.251] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    24.251] (==) Depth 24 pixmap format is 32 bpp
[    24.251] (II) intel(0): [DRI2] Setup complete
[    24.251] (II) intel(0): [DRI2]   DRI driver: i965
[    24.251] (**) intel(0): Tiling enabled
[    24.251] (**) intel(0): SwapBuffers wait enabled
[    24.251] (==) intel(0): VideoRam: 262144 KB
[    24.251] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[    24.261] (II) UXA(0): Driver registered support for the following operations:
[    24.261] (II)         solid
[    24.261] (II)         copy
[    24.261] (II)         composite (RENDER acceleration)
[    24.261] (II)         put_image
[    24.261] (II)         get_image
[    24.261] (==) intel(0): Backing store disabled
[    24.261] (==) intel(0): Silken mouse enabled
[    24.261] (II) intel(0): Initializing HW Cursor
[    24.292] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    24.293] (==) intel(0): DPMS enabled
[    24.293] (==) intel(0): Intel XvMC decoder enabled
[    24.293] (II) intel(0): Set up textured video
[    24.293] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    24.293] (II) intel(0): direct rendering: DRI2 Enabled
[    24.293] (--) RandR disabled
[    24.293] (II) Initializing built-in extension Generic Event Extension
[    24.293] (II) Initializing built-in extension SHAPE
[    24.293] (II) Initializing built-in extension MIT-SHM
[    24.293] (II) Initializing built-in extension XInputExtension
[    24.293] (II) Initializing built-in extension XTEST
[    24.293] (II) Initializing built-in extension BIG-REQUESTS
[    24.293] (II) Initializing built-in extension SYNC
[    24.293] (II) Initializing built-in extension XKEYBOARD
[    24.293] (II) Initializing built-in extension XC-MISC
[    24.293] (II) Initializing built-in extension SECURITY
[    24.293] (II) Initializing built-in extension XINERAMA
[    24.293] (II) Initializing built-in extension XFIXES
[    24.293] (II) Initializing built-in extension RENDER
[    24.293] (II) Initializing built-in extension RANDR
[    24.293] (II) Initializing built-in extension COMPOSITE
[    24.293] (II) Initializing built-in extension DAMAGE
[    24.293] (II) Initializing built-in extension GESTURE
[    24.305] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    24.305] (II) AIGLX: enabled GLX_INTEL_swap_event
[    24.305] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    24.305] (II) AIGLX: enabled GLX_SGI_make_current_read
[    24.305] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    24.305] (II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
[    24.305] (II) GLX: Initialized DRI2 GL provider for screen 0
[    24.306] (II) intel(0): Setting screen physical size to 338 x 211
[    24.325] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    24.334] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    24.334] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.334] (II) LoadModule: "evdev"
[    24.334] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.334] (II) Module evdev: vendor="X.Org Foundation"
[    24.334] 	compiled for 1.9.0, module version = 2.3.2
[    24.334] 	Module class: X.Org XInput Driver
[    24.334] 	ABI class: X.Org XInput driver, version 11.0
[    24.335] (**) Power Button: always reports core events
[    24.335] (**) Power Button: Device: "/dev/input/event2"
[    24.344] (II) Power Button: Found keys
[    24.344] (II) Power Button: Configuring as keyboard
[    24.344] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    24.344] (**) Option "xkb_rules" "evdev"
[    24.344] (**) Option "xkb_model" "evdev"
[    24.344] (**) Option "xkb_layout" "us"
[    24.344] (**) Option "xkb_variant" "intl"
[    24.344] (**) Option "xkb_options" "lv3:ralt_switch"
[    24.346] (II) XKB: reuse xkmfile /var/lib/xkb/server-A7FBDFA18BF6567675489BB56C6CA005DE143B04.xkm
[    24.347] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    24.347] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    24.347] (**) Video Bus: always reports core events
[    24.347] (**) Video Bus: Device: "/dev/input/event10"
[    24.364] (II) Video Bus: Found keys
[    24.364] (II) Video Bus: Configuring as keyboard
[    24.364] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    24.364] (**) Option "xkb_rules" "evdev"
[    24.364] (**) Option "xkb_model" "evdev"
[    24.364] (**) Option "xkb_layout" "us"
[    24.364] (**) Option "xkb_variant" "intl"
[    24.364] (**) Option "xkb_options" "lv3:ralt_switch"
[    24.365] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    24.365] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.365] (**) Power Button: always reports core events
[    24.365] (**) Power Button: Device: "/dev/input/event1"
[    24.380] (II) Power Button: Found keys
[    24.380] (II) Power Button: Configuring as keyboard
[    24.380] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    24.380] (**) Option "xkb_rules" "evdev"
[    24.380] (**) Option "xkb_model" "evdev"
[    24.380] (**) Option "xkb_layout" "us"
[    24.380] (**) Option "xkb_variant" "intl"
[    24.380] (**) Option "xkb_options" "lv3:ralt_switch"
[    24.380] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    24.380] (II) No input driver/identifier specified (ignoring)
[    24.384] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[    24.384] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    24.384] (**) Logitech USB Receiver: always reports core events
[    24.384] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[    24.396] (II) Logitech USB Receiver: Found 20 mouse buttons
[    24.396] (II) Logitech USB Receiver: Found scroll wheel(s)
[    24.396] (II) Logitech USB Receiver: Found relative axes
[    24.396] (II) Logitech USB Receiver: Found x and y relative axes
[    24.396] (II) Logitech USB Receiver: Configuring as mouse
[    24.396] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    24.396] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.396] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
[    24.396] (II) Logitech USB Receiver: initialized for relative axes.
[    24.396] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    24.396] (II) No input driver/identifier specified (ignoring)
[    24.396] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
[    24.396] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    24.397] (**) Logitech USB Receiver: always reports core events
[    24.397] (**) Logitech USB Receiver: Device: "/dev/input/event6"
[    24.413] (II) Logitech USB Receiver: Found 1 mouse buttons
[    24.416] (II) Logitech USB Receiver: Found scroll wheel(s)
[    24.416] (II) Logitech USB Receiver: Found relative axes
[    24.416] (II) Logitech USB Receiver: Found absolute axes
[    24.416] (II) evdev-grail: failed to open grail, no gesture support
[    24.416] (II) Logitech USB Receiver: Found keys
[    24.416] (II) Logitech USB Receiver: Configuring as mouse
[    24.416] (II) Logitech USB Receiver: Configuring as keyboard
[    24.416] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    24.416] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.416] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    24.416] (**) Option "xkb_rules" "evdev"
[    24.416] (**) Option "xkb_model" "evdev"
[    24.416] (**) Option "xkb_layout" "us"
[    24.416] (**) Option "xkb_variant" "intl"
[    24.416] (**) Option "xkb_options" "lv3:ralt_switch"
[    24.417] (EE) Logitech USB Receiver: failed to initialize for relative axes.
[    24.417] (II) Logitech USB Receiver: initialized for absolute axes.
[    24.418] (II) config/udev: Adding input device CNA7157 (/dev/input/event7)
[    24.418] (**) CNA7157: Applying InputClass "evdev keyboard catchall"
[    24.418] (**) CNA7157: always reports core events
[    24.418] (**) CNA7157: Device: "/dev/input/event7"
[    24.433] (II) CNA7157: Found keys
[    24.433] (II) CNA7157: Configuring as keyboard
[    24.433] (II) XINPUT: Adding extended input device "CNA7157" (type: KEYBOARD)
[    24.433] (**) Option "xkb_rules" "evdev"
[    24.433] (**) Option "xkb_model" "evdev"
[    24.433] (**) Option "xkb_layout" "us"
[    24.433] (**) Option "xkb_variant" "intl"
[    24.433] (**) Option "xkb_options" "lv3:ralt_switch"
[    24.436] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    24.436] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    24.436] (**) AT Translated Set 2 keyboard: always reports core events
[    24.436] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    24.449] (II) AT Translated Set 2 keyboard: Found keys
[    24.449] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    24.449] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    24.449] (**) Option "xkb_rules" "evdev"
[    24.449] (**) Option "xkb_model" "evdev"
[    24.449] (**) Option "xkb_layout" "us"
[    24.449] (**) Option "xkb_variant" "intl"
[    24.449] (**) Option "xkb_options" "lv3:ralt_switch"
[    24.449] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event8)
[    24.449] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    24.449] (**) PS/2 Mouse: always reports core events
[    24.449] (**) PS/2 Mouse: Device: "/dev/input/event8"
[    24.465] (II) PS/2 Mouse: Found 3 mouse buttons
[    24.465] (II) PS/2 Mouse: Found relative axes
[    24.465] (II) PS/2 Mouse: Found x and y relative axes
[    24.465] (II) PS/2 Mouse: Configuring as mouse
[    24.465] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    24.465] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.465] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[    24.465] (II) PS/2 Mouse: initialized for relative axes.
[    24.465] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
[    24.465] (II) No input driver/identifier specified (ignoring)
[    24.465] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event9)
[    24.465] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    24.465] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    24.465] (II) LoadModule: "synaptics"
[    24.465] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    24.466] (II) Module synaptics: vendor="X.Org Foundation"
[    24.466] 	compiled for 1.9.0, module version = 1.2.2
[    24.466] 	Module class: X.Org XInput Driver
[    24.466] 	ABI class: X.Org XInput driver, version 11.0
[    24.466] (II) Synaptics touchpad driver version 1.2.2
[    24.466] (**) Option "Device" "/dev/input/event9"
[    24.500] (II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    24.500] (II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    24.500] (II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    24.500] (II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
[    24.500] (II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    24.532] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    24.532] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    24.548] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
[    24.548] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    24.548] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 0
[    24.548] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    24.548] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    24.580] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    24.580] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
[    24.580] (II) No input driver/identifier specified (ignoring)
[    24.581] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
[    24.581] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    24.581] (II) LoadModule: "wacom"
[    24.581] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    24.581] (II) Module wacom: vendor="X.Org Foundation"
[    24.581] 	compiled for 1.8.99.905, module version = 0.10.8
[    24.581] 	Module class: X.Org XInput Driver
[    24.581] 	ABI class: X.Org XInput driver, version 11.0
[    24.581] (**) Option "Device" "/dev/ttyS0"
[    24.581] (**) Option "StopBits" "1"
[    24.581] (**) Option "DataBits" "8"
[    24.581] (**) Option "Parity" "None"
[    24.581] (**) Option "Vmin" "1"
[    24.581] (**) Option "Vtime" "10"
[    24.581] (**) Option "FlowControl" "Xoff"
[    24.581] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    24.581] (II) Serial Wacom Tablet: other types will be automatically added.
[    24.581] (**) Serial Wacom Tablet stylus: always reports core events
[    25.092] (II) Serial Wacom Tablet stylus: serial tablet id 0x93.
[    25.092] (--) Serial Wacom Tablet stylus: using pressure threshold of 27 for button 1
[    25.092] (--) Serial Wacom Tablet stylus: Wacom General ISDV4 tablet maxX=26112 maxY=16320 maxZ=127 resX=2540 resY=2540  tilt=disabled
[    25.092] (II) Serial Wacom Tablet stylus: hotplugging dependent devices.
[    25.092] (**) Serial Wacom Tablet eraser: Applying InputClass "Wacom serial class"
[    25.092] (**) Option "Device" "/dev/ttyS0"
[    25.092] (**) Option "BaudRate" "38400"
[    25.092] (**) Option "StopBits" "1"
[    25.092] (**) Option "DataBits" "8"
[    25.092] (**) Option "Parity" "None"
[    25.092] (**) Option "Vmin" "1"
[    25.092] (**) Option "Vtime" "10"
[    25.092] (**) Option "FlowControl" "Xoff"
[    25.092] (**) Serial Wacom Tablet eraser: always reports core events
[    25.092] (--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet maxX=26112 maxY=16320 maxZ=127 resX=2540 resY=2540  tilt=disabled
[    25.092] (II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
[    25.092] (--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=26112 bottom Y=16320 resol X=2540 resol Y=2540
[    25.093] (**) Option "BaudRate" "38400"
[    25.093] (**) Serial Wacom Tablet touch: Applying InputClass "Wacom serial class"
[    25.093] (**) Option "Device" "/dev/ttyS0"
[    25.093] (**) Option "BaudRate" "38400"
[    25.093] (**) Option "StopBits" "1"
[    25.093] (**) Option "DataBits" "8"
[    25.093] (**) Option "Parity" "None"
[    25.093] (**) Option "Vmin" "1"
[    25.093] (**) Option "Vtime" "10"
[    25.093] (**) Option "FlowControl" "Xoff"
[    25.093] (**) Serial Wacom Tablet touch: always reports core events
[    25.093] (--) Serial Wacom Tablet touch: Wacom General ISDV4 tablet maxX=26112 maxY=16320 maxZ=127 resX=2540 resY=2540  tilt=disabled
[    25.093] (II) XINPUT: Adding extended input device "Serial Wacom Tablet touch" (type: TOUCH)
[    25.093] (--) Serial Wacom Tablet touch: top X=0 top Y=0 bottom X=4096 bottom Y=4096 resol X=2540 resol Y=2540
[    25.093] (II) Serial Wacom Tablet stylus: hotplugging completed.
[    25.093] (II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS)
[    25.094] (--) Serial Wacom Tablet stylus: top X=0 top Y=0 bottom X=26112 bottom Y=16320 resol X=2540 resol Y=2540
[    25.096] (II) config/udev: Adding input device Toshiba input device (/dev/input/event4)
[    25.096] (**) Toshiba input device: Applying InputClass "evdev keyboard catchall"
[    25.096] (**) Toshiba input device: always reports core events
[    25.096] (**) Toshiba input device: Device: "/dev/input/event4"
[    25.109] (II) Toshiba input device: Found keys
[    25.109] (II) Toshiba input device: Configuring as keyboard
[    25.109] (II) XINPUT: Adding extended input device "Toshiba input device" (type: KEYBOARD)
[    25.109] (**) Option "xkb_rules" "evdev"
[    25.109] (**) Option "xkb_model" "evdev"
[    25.109] (**) Option "xkb_layout" "us"
[    25.109] (**) Option "xkb_variant" "intl"
[    25.109] (**) Option "xkb_options" "lv3:ralt_switch"
[ 51663.456] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[ 51668.282] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 51668.313] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 51861.017] (WW) Serial Wacom Tablet stylus: bad data at 8 v=91 l=9
[ 52181.022] (WW) Serial Wacom Tablet stylus: bad data at 8 v=91 l=9
[ 54321.075] (WW) Serial Wacom Tablet stylus: bad data at 8 v=91 l=9
[ 55186.024] (WW) Serial Wacom Tablet stylus: bad data at 7 v=91 l=9
[ 55979.132] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 55979.138] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 55979.141] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 55979.144] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 55979.147] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 56036.647] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 56036.652] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 56036.656] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 56036.661] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 56036.665] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 56156.039] (WW) Serial Wacom Tablet stylus: bad data at 8 v=91 l=9
[ 56161.016] (WW) Serial Wacom Tablet stylus: bad data at 7 v=91 l=9
[ 56321.020] (WW) Serial Wacom Tablet stylus: bad data at 7 v=91 l=9
[ 56436.024] (WW) Serial Wacom Tablet stylus: bad data at 8 v=91 l=9
[ 57361.016] (WW) Serial Wacom Tablet stylus: bad data at 7 v=91 l=9
[ 57406.025] (WW) Serial Wacom Tablet stylus: bad data at 8 v=91 l=9
[ 58016.029] (WW) Serial Wacom Tablet stylus: bad data at 7 v=91 l=9
[ 58947.810] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59016.028] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59018.565] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59018.569] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59198.339] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[ 59198.952] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59198.956] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59202.455] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59202.459] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59212.366] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[ 59212.757] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59212.760] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59218.317] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59218.321] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59259.763] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[ 59260.175] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59260.193] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59268.697] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59268.710] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59294.931] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[ 59295.323] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59295.342] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59307.095] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59307.099] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59326.109] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[ 59326.498] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59326.516] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59339.610] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 59339.614] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 60003.992] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[ 60004.634] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 60004.650] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 60426.025] (WW) Serial Wacom Tablet stylus: bad data at 8 v=91 l=9
[ 60641.017] (WW) Serial Wacom Tablet stylus: bad data at 7 v=91 l=9
[ 62148.053] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 62456.043] (WW) Serial Wacom Tablet stylus: bad data at 8 v=91 l=9
[ 62511.017] (WW) Serial Wacom Tablet stylus: bad data at 8 v=91 l=9
[ 62836.025] (WW) Serial Wacom Tablet stylus: bad data at 7 v=91 l=9
[ 62866.032] (WW) Serial Wacom Tablet stylus: bad data at 8 v=91 l=9
[ 63691.024] (WW) Serial Wacom Tablet stylus: bad data at 7 v=91 l=9
[ 63726.029] (WW) Serial Wacom Tablet stylus: bad data at 7 v=91 l=9
[ 64291.029] (WW) Serial Wacom Tablet stylus: bad data at 7 v=a0 l=9
[ 64674.105] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 64679.926] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 64679.933] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 64750.078] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[ 64752.770] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 64752.774] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 64759.735] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
[ 64759.747] (II) XKB: reuse xkmfile /var/lib/xkb/server-5B10860367BEB087D0062353E9B4A95B159762A1.xkm
```

---

### Post by Favux on 2011-01-02
evdev is a general purpose driver for pointing devices and keyboards and is also the driver of last resort if a device hasn't matched any other .conf file and found a driver.

The Xorg.0.log shows:
```
[    24.384] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[    24.384] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    24.384] (**) Logitech USB Receiver: always reports core events
[    24.384] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[    24.396] (II) Logitech USB Receiver: Found 20 mouse buttons
[    24.396] (II) Logitech USB Receiver: Found scroll wheel(s)
[    24.396] (II) Logitech USB Receiver: Found relative axes
[    24.396] (II) Logitech USB Receiver: Found x and y relative axes
[    24.396] (II) Logitech USB Receiver: Configuring as mouse
[    24.396] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    24.396] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.396] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
[    24.396] (II) Logitech USB Receiver: initialized for relative axes.
[    24.396] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    24.396] (II) No input driver/identifier specified (ignoring)
[    24.396] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
[    24.396] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    24.397] (**) Logitech USB Receiver: always reports core events
[    24.397] (**) Logitech USB Receiver: Device: "/dev/input/event6"
[    24.413] (II) Logitech USB Receiver: Found 1 mouse buttons
[    24.416] (II) Logitech USB Receiver: Found scroll wheel(s)
[    24.416] (II) Logitech USB Receiver: Found relative axes
[    24.416] (II) Logitech USB Receiver: Found absolute axes
[    24.416] (II) evdev-grail: failed to open grail, no gesture support
[    24.416] (II) Logitech USB Receiver: Found keys
[    24.416] (II) Logitech USB Receiver: Configuring as mouse
[    24.416] (II) Logitech USB Receiver: Configuring as keyboard
[    24.416] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    24.416] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.416] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    24.416] (**) Option "xkb_rules" "evdev"
[    24.416] (**) Option "xkb_model" "evdev"
[    24.416] (**) Option "xkb_layout" "us"
[    24.416] (**) Option "xkb_variant" "intl"
[    24.416] (**) Option "xkb_options" "lv3:ralt_switch"
[    24.417] (EE) Logitech USB Receiver: failed to initialize for relative axes.
[    24.417] (II) Logitech USB Receiver: initialized for absolute axes.
```
Having the "evdev pointer catchall" match seems right so I would guess the problem is the match in the "evdev keyboard catchall" snippet.  Let's try to block that one.  You also see:
```
[    24.449] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event8)
[    24.449] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    24.449] (**) PS/2 Mouse: always reports core events
[    24.449] (**) PS/2 Mouse: Device: "/dev/input/event8"
[    24.465] (II) PS/2 Mouse: Found 3 mouse buttons
[    24.465] (II) PS/2 Mouse: Found relative axes
[    24.465] (II) PS/2 Mouse: Found x and y relative axes
[    24.465] (II) PS/2 Mouse: Configuring as mouse
[    24.465] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    24.465] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.465] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[    24.465] (II) PS/2 Mouse: initialized for relative axes.
```
But at least that seems to be the correct snippet, so let's ignore it for now.

So edit 10-evdev.conf:
```
gksudo gedit /usr/share/X11/xorg.conf.d/10-evdev.conf
```
and change the snippet from:
```
Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection
```
to
```
Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
	MatchProduct "Logitech"
        Option "Ignore" "yes"
EndSection
```
Reboot and cross your fingers.

---

### Post by WG- on 2011-01-02
lol :P that broke my laptop keyboard. Glad I had onboard installed :D otherwise I'm not sure how I was going to get logged in and undo the change I did. 

So changing that section into the one you purposed certainly wasn't a fix. But I was already wondering about that because why would we need to change that section which is for the keyboard? I mean the problem is something with the mouse as far as I know...

---

### Post by Favux on 2011-01-02
Ouch!  Sorry.  Perhaps it is too late for me to deliver the usual warning of backing up any working .conf file before you make changes so you can restore it from the command line in case the changes break X or whatever?

I didn't think the keyboard would be a Logitech.  Maybe we aren't being specific enough.  Instead of:
```
	MatchProduct "Logitech"
```
try
```
	MatchProduct "Logitech USB Receiver"
```
We're not trying to block your keyboard, we're trying to block the keyboard snippet from setting up your Logitech mouse and eliminate the duplicate entry you're seeing in xinput.

Since xinput sees Logitech USB Receiver not Logitech mouse it's possible the Receiver is suppose to be handled by the keyboard snippet and we should instead be trying to block the "evdev pointer catchall" snippet?

---

### Post by WG- on 2011-01-03
Thanks for the explenation Favux. 

Unfortunatly changing 'MatchProduct "Logitech"' to 'MatchProduct "Logitech USB Receiver"' didn't work either...

---

### Post by WG- on 2011-01-07
So there are no mouse guru's here?

---


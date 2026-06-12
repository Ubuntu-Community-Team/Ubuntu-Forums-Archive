---
title: "How to get Nouveau driver working????  I'm going frickin' bananas"
date: 2010-08-13
forum: General Help
---

### Post by itsjustarumour on 2010-08-13
Help!

Came back from 2 weeks holiday, installed the automatic updates for both my NVidia-based Lucid 10.04 systems and its knackered both - can't go for more than 3 or 4 minutes without either system completely freezing and having to reboot.

Long story short, its the latest 256.44 NVidia driver causing the problem. So I figured I'd revert to an older driver.  Except - no way can I find any way to actually do this... or get it to work. Surely something so simple and basic shouldn't be this difficult, in this day and age????!  I've been trying for 2 days now.  Every how-to I can find... no joy.

So after 2 days I gave up and decided to go back to the default Nouveau driver.  Again, surely it should be easy???  No - after another day, I still can't get the Nouveau driver to work.  I've now tried so many how-tos, package reinstalls, re-configurations, purges, and kernel-module changes that I've mangled my brain and completely lost track of whats going on.

I've purged everything NVidia, all Nouveau packages are installed (I think), Nouveau isn't blacklisted in blacklist.conf, I even see the Ubuntu logo in high resolution when I shut the machine down which suggests the Nouveau driver is working momentarily, but the rest of the time I can't get out of 800x600.

Surely there has to be a way, right?

---

### Post by itsjustarumour on 2010-08-13
Bump - anyone got any advice to offer?

FWIW, 

```
sudo lshw -c display
```

gives me:

ian@COOLERMASTER:~$ sudo lshw -c display
  *-display               
       description: VGA compatible controller
       product: GT215 [GeForce GT 240]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:ce000000-cfffffff(prefetchable) ioport:cc00(size=128) memory:fe800000-fe87ffff(prefetchable)
ian@COOLERMASTER:~$ 


... which says nouveau is in use.  Or am I missing something here?  If Nouveau IS working, why am I stuck at 800x600?  :confused:

---

### Post by davidmohammed on 2010-08-13
can I suggest you boot with nomodeset as your grub option - that should fix your freezes.  Then reinstall the recommended nvidia driver from administration - hardware drivers.

---

### Post by itsjustarumour on 2010-08-13
> **davidmohammed said:**
> can I suggest you boot with nomodeset as your grub option - that should fix your freezes.  Then reinstall the recommended nvidia driver from administration - hardware drivers.

Hi David,

Many thanks for your post, I'll giving that a try.  Might be better off trying to get a properly-functioning NVidia driver after all.

Will let you know how I get on...

Best,

itsjustarumour

---

### Post by HermanAB on 2010-08-13
Howdy,

The Nvidia drivers are so crummy that I am using the VESA driver on my Toshiba laptop.  So, if all else fails, select VESA.

---

### Post by itsjustarumour on 2010-08-13
> **davidmohammed said:**
> can I suggest you boot with nomodeset as your grub option - that should fix your freezes.  Then reinstall the recommended nvidia driver from administration - hardware drivers.

Well, alas that didn't work. 3 minutes in, and my system completely froze up again...

Before I'd edited and updated my GRUB2 conf file to include nomodeset, there were no NVidia drivers available to install in Administration>Hardware Drivers (that was one thing that made things more difficult originally), so I did

```
sudo apt-get install Nvidia*
```

to install everything NVidia again.  After that Administration>Hardware Drivers showed 3 NVidia drivers available, 96.xxx, 173.xxx and "Current" (ie 256.44).  No sign of the 185.xxx which is the one I wanted which was previously working fine with my graphics card, and when I tried the 173.xxx driver my system would only boot in 640x480 low graphics mode with an error message that my "NVidia GPU was not compatible with this driver".

I tried

```
sudo apt-get install Nvidia-185*
```

which seemed to install the NVidia 185.xxx driver, but I couldn't find a way to force my system to use it...  :confused:

---

### Post by lidex on 2010-08-14
What about nvidia-xconfig? Have you tried it?
```
sudo nvidia-xconfig
```
Reboot. No joy?
Post this output please:
```
cat /etc/X11/xorg.conf
cat /var/log/Xorg.0.log
```

---

### Post by davidmohammed on 2010-08-14
how did you install the 256 drivers initially?  e.g. did you install via a ppa or compile the drivers manually?

have you "upgraded" x-server etc via adding the edgers or x-swat ppa?

may be the issue is that you need to "sudo apt-get purge" your nvidia & X driver installs, remove the ppas before reinstalling the nvidia drivers.

---

### Post by itsjustarumour on 2010-08-14
> **lidex said:**
> What about nvidia-xconfig? Have you tried it?
```
sudo nvidia-xconfig
```


Thanks for the post.  Crikey, I'd completely forgotten about running that command, haven't had to use it since about 2006!  :)

Gave it a try, thought that had fixed it - system ran fine for about 2 hours, but then froze up again.  Have had 2 further lockups in less than an hour, and had to reboot the machine on each occasion.

---

### Post by itsjustarumour on 2010-08-14
Hi David,

> **davidmohammed said:**
> how did you install the 256 drivers initially?  e.g. did you install via a ppa or compile the drivers manually?

Nope, I've only ever done "vanilla" installs of the NVidia driver using the Ubuntu "Hardware Drivers" app (Jockey), and let any driver upgrades just come through with the normal package updates.

> may be the issue is that you need to "sudo apt-get purge" your nvidia & X driver installs

Hmmm, I've already tried that..

---

### Post by itsjustarumour on 2010-08-15
Well, still having problems, machine locking up sometimes as little as 30 seconds after loading my desktop.  Having real trouble, I've had to reboot 6 times (!) whist just running these terminal commands and creating this post, system is almost unusable...

```
cat /etc/X11/xorg.conf
```

gives:

> ian@COOLERMASTER:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 256.44  (buildmeister@builder97.nvidia.com)  Thu Jul 29 02:00:07 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

	# generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

ian@COOLERMASTER:~$


```
cat /var/log/Xorg.0.log
```

gives:

> ian@COOLERMASTER:~$ cat /var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux COOLERMASTER 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=0571278e-b289-4835-be71-6798d9b64e62 ro quiet vga=769 nomodeset
Build Date: 16 June 2010  09:31:32AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug 15 16:26:01 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0ca3:10b0:0401 nVidia Corporation GT215 [GeForce GT 240] rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  256.44  Thu Jul 29 01:55:11 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  256.44  Thu Jul 29 01:32:42 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) Aug 15 16:26:02 NVIDIA(0): Enabling RENDER acceleration
(II) Aug 15 16:26:02 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Aug 15 16:26:02 NVIDIA(0):     enabled.
(II) Aug 15 16:26:02 NVIDIA(0): NVIDIA GPU GeForce GT 240 (GT215) at PCI:1:0:0 (GPU-0)
(--) Aug 15 16:26:02 NVIDIA(0): Memory: 1048576 kBytes
(--) Aug 15 16:26:02 NVIDIA(0): VideoBIOS: 70.15.1e.00.00
(II) Aug 15 16:26:02 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Aug 15 16:26:02 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Aug 15 16:26:02 NVIDIA(0): Connected display device(s) on GeForce GT 240 at PCI:1:0:0:
(--) Aug 15 16:26:02 NVIDIA(0):     Samsung SyncMaster (CRT-1)
(--) Aug 15 16:26:02 NVIDIA(0): Samsung SyncMaster (CRT-1): 400.0 MHz maximum pixel clock
(II) Aug 15 16:26:02 NVIDIA(0): Assigned Display Device: CRT-1
(==) Aug 15 16:26:02 NVIDIA(0): 
(==) Aug 15 16:26:02 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Aug 15 16:26:02 NVIDIA(0):     will be used as the requested mode.
(==) Aug 15 16:26:02 NVIDIA(0): 
(II) Aug 15 16:26:02 NVIDIA(0): Validated modes:
(II) Aug 15 16:26:02 NVIDIA(0):     "nvidia-auto-select"
(II) Aug 15 16:26:02 NVIDIA(0): Virtual screen size determined to be 1920 x 1200
(--) Aug 15 16:26:02 NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
(--) Aug 15 16:26:02 NVIDIA(0):     option
(==) Aug 15 16:26:02 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Aug 15 16:26:02 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Aug 15 16:26:02 NVIDIA(0): Initialized GPU GART.
(II) Aug 15 16:26:02 NVIDIA(0): ACPI: failed to connect to the ACPI event daemon; the daemon
(II) Aug 15 16:26:02 NVIDIA(0):     may not be running or the "AcpidSocketPath" X
(II) Aug 15 16:26:02 NVIDIA(0):     configuration option may not be set correctly.  When the
(II) Aug 15 16:26:02 NVIDIA(0):     ACPI event daemon is available, the NVIDIA X driver will
(II) Aug 15 16:26:02 NVIDIA(0):     try to use it to receive ACPI event notifications.  For
(II) Aug 15 16:26:02 NVIDIA(0):     details, please see the "ConnectToAcpid" and
(II) Aug 15 16:26:02 NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
(II) Aug 15 16:26:02 NVIDIA(0):     Config Options in the README.
(II) Aug 15 16:26:02 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) Aug 15 16:26:02 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Aug 15 16:26:02 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initiali

---

### Post by itsjustarumour on 2010-08-15
.. and the other bit that the forum truncated:

> (II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device USB Optical Mouse USB Optical Mouse (/dev/input/event4)
(**) USB Optical Mouse USB Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) USB Optical Mouse USB Optical Mouse: always reports core events
(**) USB Optical Mouse USB Optical Mouse: Device: "/dev/input/event4"
(II) USB Optical Mouse USB Optical Mouse: Found 10 mouse buttons
(II) USB Optical Mouse USB Optical Mouse: Found scroll wheel(s)
(II) USB Optical Mouse USB Optical Mouse: Found relative axes
(II) USB Optical Mouse USB Optical Mouse: Found x and y relative axes
(II) USB Optical Mouse USB Optical Mouse: Configuring as mouse
(**) USB Optical Mouse USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) USB Optical Mouse USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "USB Optical Mouse USB Optical Mouse" (type: MOUSE)
(II) USB Optical Mouse USB Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device USB Optical Mouse USB Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
ian@COOLERMASTER:~$

---

### Post by davidmohammed on 2010-08-15
here is a [thread]("http://ubuntuforums.org/showthread.php?t=1423210") how to revert from the nvidia driver to the nouveau driver.  Hope this helps.

---

### Post by lidex on 2010-08-15
Looks like the driver is loading correctly however there are acpi issues reported in your log file. I suspect this is at least part of your problem. If the update you mention included a new kernel, try rebooting into an older one.

---

### Post by voidmage on 2010-08-18
I have a GT240 and had the same hard lock problems in 256.44 and fixed it by manually reverting to the 256.35 drivers. There may be a copy of the 256.35 package in /var/cache/apt/archives. I use the ubuntu-x-swat ppa so my package names might be a little different than yours.

```

nvidia-current_256.35-0ubuntu2~xup2_amd64.deb
nvidia-current-modaliases_256.35-0ubuntu2~xup2_amd64.deb

```

I reinstalled those with sudo dpkg -i <packagename>.deb then rebooted. The important thing is that they're version 256.35. If you don't have those files I can look for a link to download them manually.

Nvidia knows about this bug, see [http://www.nvnews.net/vbulletin/showthread.php?t=153875](http://www.nvnews.net/vbulletin/showthread.php?t=153875) for more information.

Edit: After doing this make sure not to update your nvidia packages until a version newer than 256.44 comes out that should fix it.

Another edit: Links to 256.35 packages from ubuntu-x-swat ppa
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+files/nvidia-current_256.35-0ubuntu2%7Exup2_amd64.deb](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+files/nvidia-current_256.35-0ubuntu2%7Exup2_amd64.deb)
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+files/nvidia-current-modaliases_256.35-0ubuntu2%7Exup2_amd64.deb](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+files/nvidia-current-modaliases_256.35-0ubuntu2%7Exup2_amd64.deb)

---

### Post by itsjustarumour on 2010-08-22
> **lidex said:**
> Looks like the driver is loading correctly however there are acpi issues reported in your log file. I suspect this is at least part of your problem. If the update you mention included a new kernel, try rebooting into an older one.

Thanks for the post, same problem with any kernel though.

---

### Post by itsjustarumour on 2010-08-22
> **davidmohammed said:**
> here is a [thread]("http://ubuntuforums.org/showthread.php?t=1423210") how to revert from the nvidia driver to the nouveau driver.  Hope this helps.

Alas, those suggestions didn't help... and Driver Manager (aka Jockey) seems to have lost all touch with reality due to, well, bugs in Jockey...

Actually, Jockey just produced what I think must be the second most stoopid error message I have ever experienced on an operating system:

"The NVidia driver is activated, but is not in use".

Eh???  :shock:

Although to be fair, that still doesn't beat what must be THE most stoopid error message I have ever experienced on an operating system, which will stay with me forever:

"There was a problem with Windows Vista.  This problem was caused by - Windows Vista. Click "OK" for help troubleshooting this problem." (and then on clicking "OK") "There is no solution to your problem." :lolflag:

OK, I'm digressing!  More to follow shortly...

---

### Post by itsjustarumour on 2010-08-22
> **voidmage said:**
> I have a GT240 and had the same hard lock problems in 256.44 and fixed it by manually reverting to the 256.35 drivers. There may be a copy of the 256.35 package in /var/cache/apt/archives. I use the ubuntu-x-swat ppa so my package names might be a little different than yours.

```

nvidia-current_256.35-0ubuntu2~xup2_amd64.deb
nvidia-current-modaliases_256.35-0ubuntu2~xup2_amd64.deb

```

I reinstalled those with sudo dpkg -i <packagename>.deb then rebooted. The important thing is that they're version 256.35. If you don't have those files I can look for a link to download them manually.

Nvidia knows about this bug, see [http://www.nvnews.net/vbulletin/showthread.php?t=153875](http://www.nvnews.net/vbulletin/showthread.php?t=153875) for more information.

Edit: After doing this make sure not to update your nvidia packages until a version newer than 256.44 comes out that should fix it.

Another edit: Links to 256.35 packages from ubuntu-x-swat ppa
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+files/nvidia-current_256.35-0ubuntu2%7Exup2_amd64.deb](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+files/nvidia-current_256.35-0ubuntu2%7Exup2_amd64.deb)
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+files/nvidia-current-modaliases_256.35-0ubuntu2%7Exup2_amd64.deb](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+files/nvidia-current-modaliases_256.35-0ubuntu2%7Exup2_amd64.deb)

Voidimage - thanks for the post - after several days of head scratching (and some similar problems with the latest driver on my Fedora 13 box) I'd just discovered the very same post you mention! Logged onto the forum to update this post, and read your comment.  Yes, looks like this is down to a bug in the 256.44  NVidia driver, affecting GT240 cards (and some others).  The good news on the post you refered to is that the NVidia guy said on on 20/08/10 that there will be a fix out in a week or two, so hopefully we won't have to wait long for the solution.  So that explains my original problem anyway, although it doesn't explain all the mess when trying to revert to the Nouveau driver.... think I'll just have to wait for the NVidia fix.  

Cheers to all who replied to this thread anyway.

Best,

itsjustarumour

---


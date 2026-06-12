---
title: "no login menu after xubuntu starts"
date: 2012-09-26
forum: General Help
---

### Post by supernater on 2012-09-26
I'm running Xubuntu 12.04 64 bit edition.  When I start up my computer the xubuntu splash screen shows up and then it goes into command line mode.  I can still login by typing my username and password but I have to type startx to start up xfce.  This does not happen all the time.  How do I fix this?

---

### Post by Rexilion on 2012-09-27
Seems like a race condition, do you use rc.local to start your session?

---

### Post by supernater on 2012-09-27
> **Rexilion said:**
> Seems like a race condition, do you use rc.local to start your session?

I'm not sure.  I did not modify anything in rc.local.  I simply installed Xubuntu and it randomly stopped displaying the graphical login manager.  Sometimes I get it, other times I get the command line login and I have to type startx to start xfce.  Is there a log file I can check to see what is going on?

---

### Post by spjackson on 2012-09-27
Next time it fails, have a look for clues in /var/log/Xorg.0.log and /var/log/lightdm/* .

---

### Post by supernater on 2012-09-29
My lightdm log says...

[I][+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.1, UID=0 PID=1107
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for greeter
[+0.00s] DEBUG: Starting local X display
[+0.00s] DEBUG: X server :0 will replace Plymouth
[+0.02s] DEBUG: Using VT 7
[+0.02s] DEBUG: Activating VT 7
[+0.02s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.03s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.03s] DEBUG: Launching X Server
[+0.03s] DEBUG: Launching process 1141: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.03s] DEBUG: Waiting for ready signal from X server :0
[+0.03s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.03s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.15s] DEBUG: Process 1141 exited with return value 1
[+0.15s] DEBUG: X server stopped
[+0.15s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+0.15s] DEBUG: Releasing VT 7
[+0.15s] DEBUG: Stopping Plymouth, X server failed to start
[+0.16s] DEBUG: Display server stopped
[+0.16s] DEBUG: Stopping display
[+0.16s] DEBUG: Display stopped
[+0.16s] DEBUG: Stopping X local seat, failed to start a display
[+0.16s] DEBUG: Stopping seat
[+0.16s] DEBUG: Seat stopped
[+0.16s] DEBUG: Required seat has stopped
[+0.16s] DEBUG: Stopping display manager
[+0.16s] DEBUG: Display manager stopped
[+0.16s] DEBUG: Stopping daemon
[+0.16s] DEBUG: Exiting with return value 1[/I]

So the X server appears to fail to start on occasion.  I went to the x server log and found....

[I][     9.432] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[     9.432] X Protocol Version 11, Revision 0
[     9.432] Build Operating System: Linux 2.6.42-26-generic x86_64 Ubuntu
[     9.432] Current Operating System: Linux LinPC 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 x86_64
[     9.432] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic root=UUID=dede1101-4990-4c98-81af-631483c882ed ro quiet splash vt.handoff=7
[     9.432] Build Date: 16 July 2012  08:06:31PM
[     9.432] xorg-server 2:1.11.4-0ubuntu10.6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     9.432] Current version of pixman: 0.24.4
[     9.432] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[     9.432] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     9.432] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep 29 08:23:08 2012
[     9.432] (==) Using config file: "/etc/X11/xorg.conf"
[     9.432] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     9.432] (==) No Layout section.  Using the first Screen section.
[     9.432] (==) No screen section available. Using defaults.
[     9.432] (**) |-->Screen "Default Screen Section" (0)
[     9.432] (**) |   |-->Monitor "<default monitor>"
[     9.433] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[     9.433] (**) |   |-->Device "Default Device"
[     9.433] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[     9.433] (==) Automatically adding devices
[     9.433] (==) Automatically enabling devices
[     9.442] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     9.442] 	Entry deleted from font path.
[     9.442] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     9.442] 	Entry deleted from font path.
[     9.442] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     9.442] 	Entry deleted from font path.
[     9.444] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     9.444] 	Entry deleted from font path.
[     9.444] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     9.444] 	Entry deleted from font path.
[     9.444] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     9.444] 	Entry deleted from font path.
[     9.444] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     9.444] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     9.444] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     9.444] (II) Loader magic: 0x7f458a3adb00
[     9.444] (II) Module ABI versions:
[     9.444] 	X.Org ANSI C Emulation: 0.4
[     9.444] 	X.Org Video Driver: 11.0
[     9.444] 	X.Org XInput driver : 16.0
[     9.444] 	X.Org Server Extension : 6.0
[     9.444] (--) PCI:*(0:1:0:0) 10de:1244:1458:3536 rev 161, Mem @ 0xf4000000/33554432, 0xe0000000/134217728, 0xe8000000/67108864, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     9.445] (II) Open ACPI successful (/var/run/acpid.socket)
[     9.445] (II) LoadModule: "extmod"
[     9.446] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     9.447] (II) Module extmod: vendor="X.Org Foundation"
[     9.447] 	compiled for 1.11.3, module version = 1.0.0
[     9.447] 	Module class: X.Org Server Extension
[     9.447] 	ABI class: X.Org Server Extension, version 6.0
[     9.447] (II) Loading extension MIT-SCREEN-SAVER
[     9.447] (II) Loading extension XFree86-VidModeExtension
[     9.447] (II) Loading extension XFree86-DGA
[     9.447] (II) Loading extension DPMS
[     9.447] (II) Loading extension XVideo
[     9.447] (II) Loading extension XVideo-MotionCompensation
[     9.447] (II) Loading extension X-Resource
[     9.447] (II) LoadModule: "dbe"
[     9.447] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     9.447] (II) Module dbe: vendor="X.Org Foundation"
[     9.447] 	compiled for 1.11.3, module version = 1.0.0
[     9.447] 	Module class: X.Org Server Extension
[     9.447] 	ABI class: X.Org Server Extension, version 6.0
[     9.447] (II) Loading extension DOUBLE-BUFFER
[     9.447] (II) LoadModule: "glx"
[     9.447] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     9.485] (II) Module glx: vendor="NVIDIA Corporation"
[     9.485] 	compiled for 4.0.2, module version = 1.0.0
[     9.485] 	Module class: X.Org Server Extension
[     9.485] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[     9.485] (II) Loading extension GLX
[     9.485] (II) LoadModule: "record"
[     9.485] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     9.485] (II) Module record: vendor="X.Org Foundation"
[     9.485] 	compiled for 1.11.3, module version = 1.13.0
[     9.485] 	Module class: X.Org Server Extension
[     9.485] 	ABI class: X.Org Server Extension, version 6.0
[     9.485] (II) Loading extension RECORD
[     9.485] (II) LoadModule: "dri"
[     9.485] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     9.485] (II) Module dri: vendor="X.Org Foundation"
[     9.485] 	compiled for 1.11.3, module version = 1.0.0
[     9.485] 	ABI class: X.Org Server Extension, version 6.0
[     9.485] (II) Loading extension XFree86-DRI
[     9.485] (II) LoadModule: "dri2"
[     9.485] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     9.485] (II) Module dri2: vendor="X.Org Foundation"
[     9.485] 	compiled for 1.11.3, module version = 1.2.0
[     9.485] 	ABI class: X.Org Server Extension, version 6.0
[     9.485] (II) Loading extension DRI2
[     9.485] (==) Matched nvidia as autoconfigured driver 0
[     9.485] (==) Matched nouveau as autoconfigured driver 1
[     9.485] (==) Matched nv as autoconfigured driver 2
[     9.485] (==) Matched vesa as autoconfigured driver 3
[     9.485] (==) Matched fbdev as autoconfigured driver 4
[     9.485] (==) Assigned the driver to the xf86ConfigLayout
[     9.485] (II) LoadModule: "nvidia"
[     9.485] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     9.486] (II) Module nvidia: vendor="NVIDIA Corporation"
[     9.486] 	compiled for 4.0.2, module version = 1.0.0
[     9.486] 	Module class: X.Org Video Driver
[     9.486] (II) LoadModule: "nouveau"
[     9.486] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     9.486] (II) Module nouveau: vendor="X.Org Foundation"
[     9.486] 	compiled for 1.11.3, module version = 0.0.16
[     9.486] 	Module class: X.Org Video Driver
[     9.486] 	ABI class: X.Org Video Driver, version 11.0
[     9.486] (II) LoadModule: "nv"
[     9.486] (WW) Warning, couldn't open module nv
[     9.486] (II) UnloadModule: "nv"
[     9.486] (II) Unloading nv
[     9.486] (EE) Failed to load module "nv" (module does not exist, 0)
[     9.486] (II) LoadModule: "vesa"
[     9.486] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     9.486] (II) Module vesa: vendor="X.Org Foundation"
[     9.486] 	compiled for 1.11.3, module version = 2.3.0
[     9.486] 	Module class: X.Org Video Driver
[     9.486] 	ABI class: X.Org Video Driver, version 11.0
[     9.486] (II) LoadModule: "fbdev"
[     9.486] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     9.486] (II) Module fbdev: vendor="X.Org Foundation"
[     9.486] 	compiled for 1.11.3, module version = 0.4.2
[     9.486] 	ABI class: X.Org Video Driver, version 11.0
[     9.486] (==) Matched nvidia as autoconfigured driver 0
[     9.486] (==) Matched nouveau as autoconfigured driver 1
[     9.486] (==) Matched nv as autoconfigured driver 2
[     9.486] (==) Matched vesa as autoconfigured driver 3
[     9.486] (==) Matched fbdev as autoconfigured driver 4
[     9.486] (==) Assigned the driver to the xf86ConfigLayout
[     9.486] (II) LoadModule: "nvidia"
[     9.486] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     9.486] (II) Module nvidia: vendor="NVIDIA Corporation"
[     9.486] 	compiled for 4.0.2, module version = 1.0.0
[     9.486] 	Module class: X.Org Video Driver
[B][     9.486] (II) UnloadModule: "nvidia"
[     9.486] (II) Unloading nvidia
[     9.486] (II) Failed to load module "nvidia" (already loaded, 32581)[/B]
[     9.486] (II) LoadModule: "nouveau"
[     9.487] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     9.487] (II) Module nouveau: vendor="X.Org Foundation"
[     9.487] 	compiled for 1.11.3, module version = 0.0.16
[     9.487] 	Module class: X.Org Video Driver
[     9.487] 	ABI class: X.Org Video Driver, version 11.0
[     9.487] (II) UnloadModule: "nouveau"
[     9.487] (II) Unloading nouveau
[     9.487] (II) Failed to load module "nouveau" (already loaded, 32581)
[     9.487] (II) LoadModule: "nv"
[     9.487] (WW) Warning, couldn't open module nv
[     9.487] (II) UnloadModule: "nv"
[     9.487] (II) Unloading nv
[     9.487] (EE) Failed to load module "nv" (module does not exist, 0)
[     9.487] (II) LoadModule: "vesa"
[     9.487] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     9.487] (II) Module vesa: vendor="X.Org Foundation"
[     9.487] 	compiled for 1.11.3, module version = 2.3.0
[     9.487] 	Module class: X.Org Video Driver
[     9.487] 	ABI class: X.Org Video Driver, version 11.0
[     9.487] (II) UnloadModule: "vesa"
[     9.487] (II) Unloading vesa
[     9.487] (II) Failed to load module "vesa" (already loaded, 0)
[     9.487] (II) LoadModule: "fbdev"
[     9.487] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     9.487] (II) Module fbdev: vendor="X.Org Foundation"
[     9.487] 	compiled for 1.11.3, module version = 0.4.2
[     9.487] 	ABI class: X.Org Video Driver, version 11.0
[     9.487] (II) UnloadModule: "fbdev"
[     9.487] (II) Unloading fbdev
[     9.487] (II) Failed to load module "fbdev" (already loaded, 0)
[     9.487] (II) NVIDIA dlloader X Driver  295.40  Thu Apr  5 21:38:35 PDT 2012
[     9.487] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     9.487] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[     9.487] (II) NOUVEAU driver for NVIDIA chipset families :
[     9.487] 	RIVA TNT        (NV04)
[     9.487] 	RIVA TNT2       (NV05)
[     9.487] 	GeForce 256     (NV10)
[     9.487] 	GeForce 2       (NV11, NV15)
[     9.487] 	GeForce 4MX     (NV17, NV18)
[     9.487] 	GeForce 3       (NV20)
[     9.487] 	GeForce 4Ti     (NV25, NV28)
[     9.487] 	GeForce FX      (NV3x)
[     9.487] 	GeForce 6       (NV4x)
[     9.487] 	GeForce 7       (G7x)
[     9.487] 	GeForce 8       (G8x)
[     9.487] 	GeForce GTX 200 (NVA0)
[     9.487] 	GeForce GTX 400 (NVC0)
[     9.487] (II) VESA: driver for VESA chipsets: vesa
[     9.487] (II) FBDEV: driver for framebuffer: fbdev
[     9.487] (++) using VT number 7

[     9.487] (II) Loading sub module "fb"
[     9.487] (II) LoadModule: "fb"
[     9.487] (II) Loading /usr/lib/xorg/modules/libfb.so
[     9.487] (II) Module fb: vendor="X.Org Foundation"
[     9.487] 	compiled for 1.11.3, module version = 1.0.0
[     9.487] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     9.487] (II) Loading sub module "wfb"
[     9.487] (II) LoadModule: "wfb"
[     9.487] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     9.487] (II) Module wfb: vendor="X.Org Foundation"
[     9.487] 	compiled for 1.11.3, module version = 1.0.0
[     9.487] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     9.488] (II) Loading sub module "ramdac"
[     9.488] (II) LoadModule: "ramdac"
[     9.488] (II) Module "ramdac" already built-in
[     9.488] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     9.488] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     9.488] (II) Loading /usr/lib/xorg/modules/libfb.so
[     9.488] (WW) Falling back to old probe method for vesa
[     9.488] (WW) Falling back to old probe method for fbdev
[     9.488] (II) Loading sub module "fbdevhw"
[     9.488] (II) LoadModule: "fbdevhw"
[     9.488] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     9.488] (II) Module fbdevhw: vendor="X.Org Foundation"
[     9.488] 	compiled for 1.11.3, module version = 0.0.2
[     9.488] 	ABI class: X.Org Video Driver, version 11.0
[B][     9.488] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[     9.488] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     9.488] (==) NVIDIA(0): RGB weight 888
[     9.488] (==) NVIDIA(0): Default visual is TrueColor
[     9.488] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     9.488] (**) NVIDIA(0): Option "NoLogo" "True"
[     9.488] (**) NVIDIA(0): Enabling 2D acceleration
[     9.540] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[     9.540] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[     9.540] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[     9.540] (EE) NVIDIA(0):  *** Aborting ***[/B]
[     9.540] (II) UnloadModule: "nvidia"
[     9.540] (II) Unloading nvidia
[     9.540] (II) UnloadModule: "wfb"
[     9.540] (II) Unloading wfb
[     9.540] (II) UnloadModule: "fb"
[     9.540] (II) Unloading fb
[     9.540] (EE) Screen(s) found, but none have a usable configuration.
[     9.540] 
Fatal server error:
[     9.540] no screens found
[     9.540] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[     9.540] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[     9.540] 
[     9.550]  ddxSigGiveUp: Closing log
[     9.550] Server terminated with error (1). Closing log file.[/I]



So it looks like the Nvidia kernel module failed to intialize.  I went to the kernel log and looked for entries relevant to NVIDIA and found....

[I]Sep 29 08:23:08 LinPC kernel: [    9.420442] cfg80211: Calling CRDA to update world regulatory domain
Sep 29 08:23:08 LinPC kernel: [    9.422262] type=1400 audit(1348921388.170:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=646 comm="apparmor_parser"
Sep 29 08:23:08 LinPC kernel: [    9.422482] type=1400 audit(1348921388.170:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=646 comm="apparmor_parser"
Sep 29 08:23:08 LinPC kernel: [    9.422611] type=1400 audit(1348921388.170:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=646 comm="apparmor_parser"
Sep 29 08:23:08 LinPC kernel: [    9.429293] snd_ca0106 0000:05:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Sep 29 08:23:08 LinPC kernel: [    9.429325] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
Sep 29 08:23:08 LinPC kernel: [    9.430546] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Sep 29 08:23:08 LinPC kernel: [    9.430633] snd_hda_intel 0000:00:1b.0: irq 54 for MSI/MSI-X
Sep 29 08:23:08 LinPC kernel: [    9.430671] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
Sep 29 08:23:08 LinPC kernel: [    9.454482] cfg80211: World regulatory domain updated:
Sep 29 08:23:08 LinPC kernel: [    9.454484] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
**Sep 29 08:23:08 LinPC kernel: [    9.454486] nvidia: module license 'NVIDIA' taints kernel.**
Sep 29 08:23:08 LinPC kernel: [    9.454487] Disabling lock debugging due to kernel taint
Sep 29 08:23:08 LinPC kernel: [    9.454489] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 29 08:23:08 LinPC kernel: [    9.454491] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 29 08:23:08 LinPC kernel: [    9.454492] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep 29 08:23:08 LinPC kernel: [    9.454494] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 29 08:23:08 LinPC kernel: [    9.454496] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 29 08:23:08 LinPC kernel: [    9.458078] asus_wmi: ASUS WMI generic driver loaded
Sep 29 08:23:08 LinPC kernel: [    9.458565] asus_wmi: Initialization: 0x0
Sep 29 08:23:08 LinPC kernel: [    9.458586] asus_wmi: BIOS WMI version: 0.9
Sep 29 08:23:08 LinPC kernel: [    9.458620] asus_wmi: SFUN value: 0x0
Sep 29 08:23:08 LinPC kernel: [    9.458857] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input4
Sep 29 08:23:08 LinPC kernel: [    9.481401] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input5
Sep 29 08:23:08 LinPC kernel: [    9.481446] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input6
Sep 29 08:23:08 LinPC kernel: [    9.481478] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input7
Sep 29 08:23:08 LinPC kernel: [    9.481520] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input8
Sep 29 08:23:08 LinPC kernel: [    9.481550] input: HDA Intel PCH Line-Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card1/input9
Sep 29 08:23:08 LinPC kernel: [    9.481580] input: HDA Intel PCH Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card1/input10
Sep 29 08:23:08 LinPC kernel: [    9.481609] input: HDA Intel PCH Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card1/input11
Sep 29 08:23:08 LinPC kernel: [    9.481640] input: HDA Intel PCH Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
Sep 29 08:23:08 LinPC kernel: [    9.481803] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17[/I]

[I]Sep 29 08:23:09 LinPC kernel: [   10.363505] input: zc3xx as /devices/pci0000:00/0000:00:14.0/usb3/3-2/input/input13
Sep 29 08:23:09 LinPC kernel: [   10.363673] usbcore: registered new interface driver zc3xx
Sep 29 08:23:09 LinPC kernel: [   10.375105] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
Sep 29 08:23:09 LinPC kernel: [   10.375182] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input14
Sep 29 08:23:09 LinPC kernel: [   10.375226] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input15
Sep 29 08:23:09 LinPC kernel: [   10.375263] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input16
Sep 29 08:23:09 LinPC kernel: [   10.375298] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input17
Sep 29 08:23:09 LinPC kernel: [   10.375589] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 29 08:23:09 LinPC kernel: [   10.375597] nvidia 0000:01:00.0: setting latency timer to 64
Sep 29 08:23:09 LinPC kernel: [   10.375600] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Sep 29 08:23:09 LinPC kernel: [   10.375681] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.40  Thu Apr  5 21:37:00 PDT 2012
Sep 29 08:23:09 LinPC kernel: [   10.425831] init: plymouth-stop pre-start process (1318) terminated with status 1
Sep 29 08:23:09 LinPC kernel: [   10.441732] usbcore: registered new interface driver snd-usb-audio[/I]

Now I'm not sure where to go from here.  I could try updating my nvidia driver.  I'm not sure what "nvidia: module license 'NVIDIA' taints kernel." means.  Also, why is the xserver unloading the nvidia module and then failing to reload it? Any ideas?

---

### Post by Rexilion on 2012-09-29
The module in Xorg is referring to the 'driver module' (i.e. xf86-video-nvidia). Don't know why it unloads and then loads it.

Kernel 'taint' means that the kernel has been tampered with. Causes include proprietary (non-open source) modules, kernel bugs and some experimental drivers. This means that if you post this dmesg to kernel.org you will not get much help if you have any issue's. This is because you are using the OS in an unsupported way. The technical reason for this is that kernel developers cannot look what happens inside the proprietary module and don't know what kind of (dirty) tricks it does on the kernel (as Torvalds says (not my words): '**** you nvidia'). But it is no indication of an error or a bad situation, just a 'tag' that says: You use stuff we don't support, if you get trouble: good luck finding it!.

I still believe this is a race condition: The nvidia kernel module is not ready in time to respond to the request X is making to it. Sometimes it works, and sometimes it does not.

However, one other thing stands out. The fact that you have the nouveau xorg driver. Long shot, but try purging that one.

```
dpkg --purge xserver-xorg-video-nouveau
```

---

### Post by supernater on 2012-10-01
I think you are correct.  This never happened on my old system.  I just upgraded to a new SSD drive with boots up lightning fast and I occasionally get this error.  I wish there was a way to stop xserver from starting until the NVIDIA driver was loaded.

---

### Post by Rexilion on 2012-10-02
You can use rc.local for this. Let it handle the Xserver management, so you can put a sleep 10s in advance.

---


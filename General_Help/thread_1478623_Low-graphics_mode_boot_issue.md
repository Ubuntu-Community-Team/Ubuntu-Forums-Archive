---
title: "Low-graphics mode boot issue"
date: 2010-05-09
forum: General Help
---

### Post by Ubunthree on 2010-05-09
I have added the kubuntu-desktop package to the regular Ubuntu installation. It worked long enough for me to develop a liking for KDE, but now I am having this problem at boot:

[IMG]http://ubuntuforums.org/picture.php?albumid=1465&pictureid=6077[/IMG]

I can boot into low-graphics mode, but that's it. Reinstalling the Nvidia driver doesn't seem to help. I did [COLOR="DarkSlateGray"]sudo dpkg-reconfigure xserver-xorg[/COLOR] as suggested elsewhere, to no effect. I have searched a bit for a solution to this, but nothing I've found so far seems to work. Here is the paste of my entire /var/log/Xorg.0.log file, as I gather it seems to be involved somehow; apologies for the length of this post, but I don't know which parts of this are relevant:

----------------------------------------
[COLOR="DarkSlateGray"]X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux jpl-desktop-psb701 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=bcf52069-03e0-4ae0-b568-9c0013f951a2 ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May  9 20:49:57 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
	Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
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
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 8

(--) PCI: (0:0:3:3) 10de:07da:1462:7366 nVidia Corporation MCP73 Co-processor rev 162, Mem @ 0xfeb80000/524288
(--) PCI:*(0:0:16:0) 10de:07e1:1462:7366 nVidia Corporation C73 [GeForce 7100 / nForce 630i] rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
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
(II) NVIDIA GLX Module  195.36.15  Thu Mar 11 23:39:48 PST 2010
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
(II) NVIDIA dlloader X Driver  195.36.15  Thu Mar 11 22:01:49 PST 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:10:0
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
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) May 09 20:49:57 NVIDIA(0): Enabling RENDER acceleration
(II) May 09 20:49:57 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) May 09 20:49:57 NVIDIA(0):     enabled.
(EE) May 09 20:49:58 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) May 09 20:49:58 NVIDIA(0):     system's kernel log for additional error messages and
(EE) May 09 20:49:58 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log[/COLOR]
---------------------------------------


Here are what I believe to be the applicable portions of my system information as generated by sysinfo (my username replaced with "foo"):

---------------------------------------
[COLOR="DarkSlateGray"]SYSTEM INFORMATION
	Running Ubuntu Linux, the Ubuntu 10.04 (lucid) release.
	GNOME: 2.30.0 (Ubuntu 2010-03-31)
	Kernel version: 2.6.32-22-generic (#33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010)
	GCC: 4.4.3 (i486-linux-gnu)
	Xorg: unknown (23 April 2010  05:11:50PM)
	Hostname: foo-desktop-psb701
	Uptime: 0 days 0 h 35 min

GRAPHIC CARD
	VGA controller
		nVidia Corporation C73 [GeForce 7100 / nForce 630i] (rev a2)
		Subsystem: Micro-Star International Co., Ltd. Device 7366

NVIDIA GRAPHIC CARD INFORMATION
	Model name: GeForce 7100 / nForce 630i[/COLOR]
---------------------------------------

I have one earlier kernel in GRUB, but booting into it doesn't help.

Thanks in advance for any help that anyone can give me with this.

---

### Post by James78 on 2010-05-09
The kernel module is failing. It might be that it didn't fully install correctly. If the package install/configuring was interrupted in anyway, it might have an effect like this. You could boot into the recovery to use the command line, and use aptitude to reinstall the nvidia drivers.

What does /var/log/Xorg.0.log say?

---

### Post by Ubunthree on 2010-05-10
> **James78 said:**
> The kernel module is failing. It might be that it didn't fully install correctly. If the package install/configuring was interrupted in anyway, it might have an effect like this. You could boot into the recovery to use the command line, and use aptitude to reinstall the nvidia drivers.

I could try that I suppose. I'll need a bit of guidance as to what package to tell it to install, though. I assume it would be "[COLOR="DarkSlateGray"]sudo aptitude install xxx[/COLOR]" but I don't know what "xxx" should be. I've tried removing and reloading the driver through System/Administration/Hardware Drivers (in GNOME), but that doesn't appear to have done anything.

> **James78 said:**
> What does /var/log/Xorg.0.log say?

Beyond what I pasted into my original post, I don't know. I assume the (EE) lines describe the errors. I'm not knowledgeable enough to know where to find the log and readme files referenced, though, or probably to know how to use them if I found them.

---

### Post by tipiglen on 2010-05-10
The only way I can get a usable computer is to boot into recovery and opt for failsafe graphics.  Then I get a perfect screen hi-res as ever, and no longer a freeze-up on first keypress.

I suspect the problem is with x, but no solution so far.
have tried copying etc/X11/xorg.conf.failsafe
to the usr/... directory as 04-xorg.conf but no joy
xorg log:
```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux ed-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=25bb8e74-8c02-476b-8052-8168eb9bd560 ro splash quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May 10 16:47:03 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
```
.......

Any ideas?

---

### Post by Ubunthree on 2010-05-10
> **tipiglen said:**
> The only way I can get a usable computer is to boot into recovery and opt for failsafe graphics.  Then I get a perfect screen hi-res as ever, and no longer a freeze-up on first keypress.

Doesn't work for me; Failsafe just brings up the low-graphics dialog again.

I am probably going to have to reinstall, as my system is not usable like this in any practical sense. So that I can avoid this happening again, does anyone at least know whether this is an issue with:

A) Lucid specifically
B) KDE or the kubuntu-desktop package
C) the current Nvidia driver (if so, how to downgrade?)
D) GDM or KDM (I have tried combinations of each with both GNOME and KDE)
or
E) Something else?

Thanks.

---

### Post by tipiglen on 2010-05-10
> Doesn't work for me; Failsafe just brings up the low-graphics dialog again.

I get the dialog and click through it, and am then greeted with a working system, and if it's low-res, there's something wrong with my eyes.

Can't work out what's wrong, but may just adapt grub to use recovery option automatically...all else seems ok.

???????

---

### Post by Zorael on 2010-05-10
I'd try **purging** and reinstalling the driver. Something like;
```
$ sudo aptitude **purge** nvidia-current    # or whatever the package is called nowadays
$ sudo aptitude install nvidia-current
```

---

### Post by tipiglen on 2010-05-10
> I'd try purging and reinstalling the driver. Something like;

Thanks.  Tried it and it appeared to work, but firefox couldn't connect, and typing revealed the same infinitely repeating key preoblem.

Back to the drawing board...

---

### Post by Ubunthree on 2010-05-10
Just in case it would be at all helpful, here is a shot of my startup errors:

[IMG]http://ubuntuforums.org/picture.php?albumid=1465&pictureid=6080[/IMG]

Nothing I've tried here has worked - recovery mode, purging/reinstalling etc. I'm going to have to reinstall everything tonight in order to have a working system. I just wish I knew whether I should use KDE again, whether I have to go back to Karmic, or what, to avoid this happening again...

---

### Post by Ubunthree on 2010-05-10
I notice that the /tmp folder has *both* an .X0-lock and an .X1-lock in it. When I delete these and restart, I get the low-graphics thing as usual, and both of these files are back in /tmp again. My backup machine, which is also running Lucid, has only the one .X0-lock file in its .tmp folder.

Could this be related in some way to the "already active" error that the system complains about at startup? I of course have no idea what .X0-lock actually does. I'm just grasping at straws here.

---

### Post by slammer on 2010-05-13
hi, i am having the same problem on my machine, since upgrading to 10.04, have tried re-installing nvidia etc with no change. i think it may have to do with gdm. if i log into the console and run 'startx' everything runs fine, full 3d acceleration etc.

---


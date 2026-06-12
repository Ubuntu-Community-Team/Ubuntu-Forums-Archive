---
title: "ATI Radeon Mobility X1400....help (10.04)"
date: 2010-05-01
forum: General Help
---

### Post by Kaneda187 on 2010-05-01
Just installed the new ubuntu 10.04 and I'm loving everything...... except I cant seem to get my graphics card to work!

```
~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400

```

I tried the drivers from the repos and then I downloaded the one from the ATI site this is what i got
```
kaneda@kaneda-laptop:~$ cd /home/kaneda/Desktop
kaneda@kaneda-laptop:~/Desktop$ chmod +x ati.run
kaneda@kaneda-laptop:~/Desktop$ sudo ./ati.run
[sudo] password for kaneda: 
Created directory fglrx-install.WkvwaW
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.32-21-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.WkvwaW
kaneda@kaneda-laptop:~/Desktop$ 

```

Any ideas guys?

---

### Post by Kaneda187 on 2010-05-01
Anybody?

---

### Post by Mark Phelps on 2010-05-01
You can't use any of the fglrx drivers -- no matter where you get them from.  ATI dropped fglrx support for this card over a year ago.

The only drivers that will work with this card and recent Ubuntu versions are the open source drivers -- and those are installed by default.

---

### Post by SirMariusz on 2010-05-01
You can try to download 

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.9&lang=us&rev=9.3&ostype=Linux%20x86](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.9&lang=us&rev=9.3&ostype=Linux%20x86)

and then install the drivers for package Ubuntu
check --help when installing ...

---

### Post by Kaneda187 on 2010-05-02
So will my card ever have support?

---

### Post by SirMariusz on 2010-05-02
Try this driver! I also have this card and it works fine :)

---

### Post by gaalaaant on 2010-05-02
Tell us if this works because I have this weird wiggling screen problem which i think this may fix BUT just 20 minutes, my wireless in ubu stopped working FSM.

---

### Post by clhsharky on 2010-05-02
HI Kaneda187

> So will my card ever have support?

Your card is supported by ATI in the radeon open source driver.

You will need to purge all fglrx from your system for OSS "open source stack" drivers to work correctly.

The cat 9.3 mentioned will only work on 8.04LTS.

There are fresher OSS drivers available, including new G3D.

Sharky

---

### Post by gaalaaant on 2010-05-02
Sharky can you please link to what you are referring to?

---

### Post by clhsharky on 2010-05-02
HI gaalaaant

> harky can you please link to what you are referring to?
Sure, but I would like to know a little more about your problem.
The OSS in the last 6 months has chanced very rapidly,and is not as restricted as fglrx. 

Sharky

If your asking about G3D 'Gallium'here
[http://ubuntuforums.org/showthread.php?t=1451727](http://ubuntuforums.org/showthread.php?t=1451727)

---

### Post by gaalaaant on 2010-05-02
Umm I have a thread open on the matter but basically the problem is: Everytime I boot with the monitor connected the scrren wiggles horizontally faster and slower depending on the refresh rate I choose.  It also does not allow me to use my monitor at it's full resolution if i want the highest refresh that the monitor is made for.  Also, my wireless dropped in it like 10 minutes ago, after having worked great, but that may have been temporary.

---

### Post by clhsharky on 2010-05-02
gaalaaant

I been on Lucid since A2 and tested all kernel and OSS driver up grades and like where the stack is going. 

Let me read your other post an see where your at, and Id like to know what you have changed or done from default Lucid.
Are you still on KMS or UMS for one and what wifi card do you have.

Read my previous post I added Gallium link but we need to get system right first.

Sharky

---

### Post by gaalaaant on 2010-05-02
Umm that's the thing, half way through the OTA upgrade, back when it said "23 hours to go" I cancelled and burned a disk.  When I popped it in it got stuck at 30 minutes left for about 2.5 hours so I just reinstalled Wubi.  I have a realtek card, thoguh I am not quite sure which.  I have ATI Radeon x1300 in a Toshiba Satellite A215 S7422.  I am not sure what KMS and UMS are.

---

### Post by clhsharky on 2010-05-02
gaalaaant

Install ' mesa-utils '

In terminal

```
lspci
glxinfo | grep OpenGL
```

Past back in 'wrap code'

So you should have fresh install with wubi, in W7 right?
32bit or 64bit?
Are you using two monitors?

Sharky

---

### Post by gaalaaant on 2010-05-02
umm I have W7 and it installed 64 bit.  It didnt give me the choice to install 32 which was annoying cause I hear 64 has more issues.  i'll try to.  Lemme just reboot into Ubu real quick.  I am using an external monitor for my laptop with the laptop closed.  if it's disconnected from everything including power when booting i don't have these problems.  

edit: wow this is strange, my wireless , after a few reboots, just started working again.  will post code asap.

---

### Post by gaalaaant on 2010-05-02
Okay here is the response for lspci

```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

And for glxinfo | OpenGl

```
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils
OpenGL: command not found

```

I then tried installing mesa utils (I just got what you meant as I was typing, sorry for the process)

and glxinfo | OpenGL yielded:

```
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RS690 791F) 20090101  NO-TCL DRI2
OpenGL version string: 1.5 Mesa 7.7.1
OpenGL extensions:

```

Hope that helps.  As to the wireless problem I think I understnad what it is.  I had some troubles in Jaunty that when I had too many peripherals plugged in at boot (camera, HDD, mouse/keyboard) my wireless wouldn't start and my HDD would mount.  Right before what I previously thought was a miraculous fixing of my wireless just a minute ago, I remember I unplugged my camera and HDD.  My monitor issues are still ailing me.  Of course it would be nice to fix the peripherals thing, but I am more concerned with the monitor ATM.

---

### Post by clhsharky on 2010-05-02
gaalaaant

Do you have a powered USB hub?
For laptop you have a lot of things hanging don't ya.
Do you prefer latest stable drivers and kernel or do you not mind newer stuff?
Theres no reason to use 32bit OS any more AFAIC but i32-libs should be installed for compatibility.Id have to look to see where they are at ATM.

See if glxgears is working,and list back the other 2 .

In terminal
> glxgears
lsusb
xrandr -q 


Sharky

What is defalt resolution? How is monitor conected?

---

### Post by gaalaaant on 2010-05-02
> **clhsharky said:**
> gaalaaant

Do you have a powered USB hub?
For laptop you have a lot of things hanging don't ya.
Do you prefer latest stable drivers and kernel or do you not mind newer stuff?
Theres no reason to use 32bit OS any more AFAIC but i32-libs should be installed for compatibility.Id have to look to see where they are at ATM.

See if glxgears is working,and list back the other 2 .

In terminal


Sharky

What is defalt resolution? How is monitor conected?

Umm I am down with whatever works as far as kernels go.  Monitor is connected through VGA default resolution is 1440x900 and max refresh rate is 75 Hz.

glxgears returns a set of blue, red, and green gears, with just a little occasional flicker.

lsusb returns:

> 

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 05ac:1291 Apple, Inc. iPod Touch 1.Gen
Bus 001 Device 004: ID 0bc2:2100 Seagate RSS LLC 
Bus 001 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


and xrandr -q returns:
> 
VGA-0 connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+   75.0  
   1280x1024      75.0     60.0  
   1152x864       75.0     67.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3     56.2  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS connected (normal left inverted right x axis y axis)
   1280x800       59.9 +
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)

---

### Post by clhsharky on 2010-05-02
gaalaaant


Can you post back the commands so I can see whats available and the set up.

Sharky

Sorry you did it already.

Did you not have fps in terminal when glxgears was running?

---

### Post by gaalaaant on 2010-05-02
my bad here it is 

[QUOTE}

1629 frames in 5.0 seconds
1640 frames in 5.0 seconds
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 10038 requests (10035 known processed) with 0 events remaining.
[/QUOTE]

---

### Post by clhsharky on 2010-05-02
gaalaaant


Did you not have fps in terminal when glxgears was running?
Its good to see if open gl is working and to check drivers, Its for 3D.
Install 'GtkPerf' simple but good video tester.

Do you have Ubuntu tweak? Real handy never had a problem with it.
It will also install PPAs you'll be testing,compositing & so on.
[http://launchpad.net/ubuntu-tweak/0.5.x/0.5.4/+download/ubuntu-tweak_0.5.4-1_all.deb](http://launchpad.net/ubuntu-tweak/0.5.x/0.5.4/+download/ubuntu-tweak_0.5.4-1_all.deb)

Your xrandr looks correct, How were you setting 75hz on resolution
60 is normal for LCD but shows 75?

Sharky

OK seen your fps in glxgears

---

### Post by gaalaaant on 2010-05-02
Umm I can set 75 in W7, but here the monitor itself in this blue menu pane gives an error message.  Do you think it's my graphics drivers that are causing the wiggle?  Also, I was setting it to 75 in W7 because I had been having eye pains and had heard it might help.

---

### Post by jelofson on 2010-05-02
I can't help any, but I have an X1300 pro and my frame rates have really decreased since moving to Lucid. Glxgears reports about 1/2 as many fps as it was in 9.10. Bummer!

Not sure how to fix that. Revert back to 9.10 maybe

---

### Post by clhsharky on 2010-05-02
gaalaaant

Heres a read, you thought yours was bad, some devs gave some suggestion .Yes we will try some driver and kernel.

[http://www.phoronix.com/forums/showthread.php?t=18773](http://www.phoronix.com/forums/showthread.php?t=18773)

Sharky

Have you installed the apps yet?

---

### Post by gaalaaant on 2010-05-02
Yes I have my good man.  Man I used to say that my next PC would have an nvidia card but I hear they're even worse off in some cases than us ATI users.

---

### Post by clhsharky on 2010-05-02
jelofson

Half the fps would be correct in glxgears because of UMS and KMS.
Glxgears is not a benchmark and doest mean much because of the way glxgears works. Unless it drops down into 100s or less then something is broke.
Use GtkPerf to test, would be more meaningful.

Sharky

---

### Post by gaalaaant on 2010-05-02
Yea at least I can still you know, see things.  But I mean, if that only happened when gaming, I would be down with that, cos I never game.    Yea I installed the programs.

---

### Post by clhsharky on 2010-05-02
gaalaaant

Give me 10 for a pit stop and grab me a drink and we will get at it.

Sharky

---

### Post by gaalaaant on 2010-05-02
totally cool man.  I have to go cook my mom a quick dinner anyway.

---

### Post by clhsharky on 2010-05-03
gaalaaant

Can you past me one more thing before you start?
System/Administration/Log file viewer/Xorg.0.log

Install  ia32-libs  in repos for better compatibility.
This has nothing to do with kernel, its for 32bit apps in a 64 OS.

Were installing kernel 2.6.34.rc6, its what was recommended for the xrandr fixes and its more laptop friendly "dynamic PM, better wifi drivers".

you will need these 3 deb downloaded
installed 1 at a time
in this order
linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb
linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_amd64.deb
linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_amd64.deb

from here
[http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc6-lucid/](http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc6-lucid/)

then restart

You may need radeon.dynpm=1 in the boot string to enable dynamic PM with a 2.6.34 kernel.

While installing debs if it asks you about config choose the one you have.
Has drop down box. We don't want to mess up your duel boot.
We will start with kernel before moving on to drivers.

---

### Post by gaalaaant on 2010-05-03
System/Administration/Log file viewer/Xorg.0.log:
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May  2 21:08:32 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
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
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:5:0) 1002:791f:1179:ff1a ATI Technologies Inc RS690M [Radeon X1200 Series] rev 0, Mem @ 0xf0000000/134217728, 0xf8100000/65536, 0xf8000000/1048576, I/O @ 0x00009000/256
(II) Open ACPI successful (/var/run/acpid.socket)
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
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
(==) Matched ati as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 6.13.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 6.13.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
	CEDAR
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:05:0
(II) [KMS] Kernel modesetting enabled.
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon X1200" (ChipID = 0x791f)
(II) RADEON(0): PCI card detected
(II) RADEON(0): KMS Color Tiling: disabled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) RADEON(0): Output VGA-0 has no monitor section
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: GSM  Model: 4b77  Serial#: 20246
(II) RADEON(0): Year: 2008  Week: 8
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.637 redY: 0.343   greenX: 0.297 greenY: 0.615
(II) RADEON(0): blueX: 0.145 blueY: 0.069   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x864@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 67  vid: 18289
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: W1952
(II) RADEON(0): Monitor name: 
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d774b164f0000
(II) RADEON(0): 	081201036a291a78ea3231a3574c9d25
(II) RADEON(0): 	115054a76f80950f9500818071470101
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384b1e
(II) RADEON(0): 	530e000a202020202020000000fc0057
(II) RADEON(0): 	313935320a20202020202020000000fc
(II) RADEON(0): 	000a20202020202020202020202000df
(II) RADEON(0): EDID vendor "GSM", prod id 19319
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1152x864"x67.0   92.41  1152 1224 1344 1536  864 865 868 898 -hsync +vsync (60.2 kHz)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x67.0   92.44  1152 1224 1344 1536  864 865 868 898 -hsync +vsync (60.2 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SHP  Model: 13ce  Serial#: 0
(II) RADEON(0): Year: 1990  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) RADEON(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004d10ce1300000000
(II) RADEON(0): 	0000010380211578ca00000000000000
(II) RADEON(0): 	00000000000001010101010101010101
(II) RADEON(0): 	010101010101bc1b00a0502017303020
(II) RADEON(0): 	36004bcf100000190000001000000000
(II) RADEON(0): 	00000000000000000a20000000100000
(II) RADEON(0): 	000000000000000000000a2000000010
(II) RADEON(0): 	004c513135344b314c423143200a0062
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
(II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Using fuzzy aspect match for initial modes
(II) RADEON(0): Output VGA-0 using initial mode 1024x768
(II) RADEON(0): Output LVDS using initial mode 1024x768
(II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:8000000 visible:7ab2000
(II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
(**) RADEON(0): Display dimensions: (410, 260) mm
(**) RADEON(0): DPI set to (63, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules/libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.5.0
	ABI class: X.Org Video Driver, version 6.0
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) RADEON(0): [DRI2] Setup complete
(II) RADEON(0): Front buffer size: 3072K
(II) RADEON(0): VRAM usage limit set to 110311K
(==) RADEON(0): Backing store disabled
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
(II) RADEON(0): Setting EXA maxPitchBytes
(II) EXA(0): Driver allocated offscreen pixmaps
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(II) RADEON(0): Acceleration enabled
(==) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Set up textured video
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 270 x 203
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Video Bus (/dev/input/event7)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event7"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event6"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) Logitech USB Receiver: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event8)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event9"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
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
(II) RADEON(0): EDID vendor "SHP", prod id 5070
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) RADEON(0): EDID vendor "SHP", prod id 5070
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) RADEON(0): EDID vendor "SHP", prod id 5070
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) RADEON(0): EDID vendor "SHP", prod id 5070
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) RADEON(0): EDID vendor "SHP", prod id 5070
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) RADEON(0): EDID vendor "SHP", prod id 5070
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) RADEON(0): Allocate new frame buffer 1440x912 stride 1472
(II) RADEON(0): VRAM usage limit set to 108356K
(II) RADEON(0): EDID vendor "SHP", prod id 5070
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) RADEON(0): EDID vendor "GSM", prod id 19319
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1152x864"x67.0   92.41  1152 1224 1344 1536  864 865 868 898 -hsync +vsync (60.2 kHz)
(II) RADEON(0): EDID vendor "GSM", prod id 19319
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1152x864"x67.0   92.41  1152 1224 1344 1536  864 865 868 898 -hsync +vsync (60.2 kHz)
(II) RADEON(0): EDID vendor "GSM", prod id 19319
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1152x864"x67.0   92.41  1152 1224 1344 1536  864 865 868 898 -hsync +vsync (60.2 kHz)
(II) RADEON(0): EDID vendor "GSM", prod id 19319
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1152x864"x67.0   92.41  1152 1224 1344 1536  864 865 868 898 -hsync +vsync (60.2 kHz)

```

  Okay I just installed, about to restart.  I will post back the result but after that I have to go to bed; AP exams in the morning.  Thanks for all the help tonight Sharky.

---

### Post by gaalaaant on 2010-05-03
Hallelujah!  When it restarted, instead of listing after I selected the normal three options (Ubuntu 2.6.32, "   " safe mode, and Win7) it also listed two extras!  That being 2.6.34 and its safe mode.  When I completed boot, wireless worked perfectly and the screen wasn't wiggling anymore! Also, 75 Hz works now!  Big thanks Sharky.  I have to retire, but if you have any more tips, or anymore advice, I would be thankful to get them.

---

### Post by clhsharky on 2010-05-03
gaalaaant

Your welcome, PM me if you need me.

Sharky

Your xorg log looked good.

---

### Post by midnightLuke on 2010-05-03
Hallelujah! 

I have been pulling my hair out the last couple of days because my Radeon Mobility x1400 would not properly output to my external monitor.  Installing the new Linux kernel cleared everything up, thank you Sharky, you rule,

midnightLuke

---

### Post by iluvzinta on 2010-05-21
Hi I have an ATI radeon x1300 graphics card on my Toshiba Satellite A100 P542 laptop. I am new to ubuntu. On installation, I was pleased with the mac feel as I use mac at my home. 
However, I have a big problem. I just cant get the card to work. In the hardware options, my card isn't displayed in proprietary thingy.

 I later realised that my graphic driver is no longer supported by ATI and there are no official drivers. So I tried all the alternatives available in Ubuntu software centre. I currently have everything related to ATI, fglrx, xorg etc installed. But seems like all these things are of no use, as my graphics driver still isn't recognized and I cant use Compiz fusion. Leave alone compiz fusion I cannot run good quality videos. The screen gets sluggish when I do that.

I will be really grateful if someone can help me get my graphics card (ATI radeon x1300) working. I dont want to use windows but this graphics prob on ubuntu is giving me a big headache. Pls pls pls help.

P.S @Sharky I have seen that you have been very helpful here. Could you please explain me the steps to get my graphics card working. Thanks.

---

### Post by gillza on 2010-05-24
Hi,

I'm having a similar issue on my Fujitsu e8210 laptop. It has ATI x1400 Mobility radeon. I have installed 10.04 (32bit) today and noticing the following: every few seconds screen starts to become filled with white noise-like interference and becomes completely unreadable for a second and then snaps back to clarity. While the interference occurs system also becomes frozen. External monitor when connected is showing a distorted grainy picture. I would be very thankful if someone can help me fix it. 

**lspci**
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:03.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
08:03.1 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
08:03.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
08:03.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
08:03.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)

```


**glxinfo | grep OpenGL**
```

OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RV515 7145) 20090101 x86/MMX/SSE2 TCL DRI2
OpenGL version string: 1.5 Mesa 7.7.1
OpenGL extensions:

```


**glxgears**
```

6110 frames in 5.0 seconds
6009 frames in 5.0 seconds
5983 frames in 5.0 seconds
6044 frames in 5.0 seconds
6063 frames in 5.0 seconds
6019 frames in 5.0 seconds

```


**lsusb**
```

Bus 005 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

**xrandr -q**
```

Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1680x1050+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1680x1050      60.2*+   60.0  
   1600x1024      60.2  
   1400x1050      60.0     60.0  
   1280x1024      59.9     60.0  
   1440x900       59.9     59.9  
   1280x960       60.0     59.9  
   1280x854       59.9  
   1360x768       59.8  
   1280x800       59.8  
   1152x864       60.0  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right x axis y axis)
DVI-0 disconnected (normal left inverted right x axis y axis)
  1680x1050 (0x55)  119.0MHz
        h: width  1680 start 1728 end 1760 total 1840 skew    0 clock   64.7KHz
        v: height 1050 start 1053 end 1059 total 1080           clock   59.9Hz

```

**(NOTE: after I ran this command the screen cleared up and the system did not freeze again) **

I have followed clhsharky's instructions and installed new kernels from :

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/)

This did not solve the problem unfortunately.

Thank you!

---

### Post by insert_name_here on 2010-05-26
I have the same problem with the flickering screen. 

I don't understand the kernal change solution. Could someone re-explain it? (I'm not totally clueless, I've been running ubuntu since Dapper and used to play around with fglrx and all that, though -- thankfully -- I haven't had to deal with that in a while.)

Specs:

Thinkpad T60
ATI Radeon Mobility X1400
radeon OSS driver

Thanks...

---

### Post by gillza on 2010-05-26
Well I don't really know what driver exactly in the new Kernel might be responsible for fixing the issue (mine was not resolved) but if you want you can try installing the new kernel and see if it will fix your problem. Here is how I did it:
From 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/)

install in the order below:

1) linux-headers-2.6.34-020634rc7_2.6.34-020634rc7_all.deb
2) linux-headers-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb
3) linux-image-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb

restart. 

Boot with the new kernel and see if it improved your situation.

Good luck!

---

### Post by insert_name_here on 2010-05-26
Is the new kernel liable to break anything? I'm loathe to end up breaking anything else... if it's likely to make anything unstable, I'll probably just downgrade to 9.10.

(So much for LTS???)

Thanks!

---

### Post by gillza on 2010-05-26
I did not notice any problems after updating the kernel.

If you are considering downgrading to 9.10 you might as well try the kernel update first. If it works - perfect. If it doesn't - back to 9.10 it is :) I'm also considering this, but want to try to purge gallium 3d first and install updated ATI open source drivers to see if it helps.

P.S. I curse the day I bought a laptop with ATI video card... Never again...

---

### Post by gillza on 2010-05-26
ok so I reinstalled 10.04 (was easier than removing all the drivers and libs and etc that I piled into it while trying to fix the issue).

then **sudo gedit /etc/default/grub**
pasted **radeon.modeset=0** into **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**

so it will look like this: **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0"**

saved it and **sudo update-grub**

reboot and it looks like the issue has been solved, no need to install anything else.

Note: if the grub is updated later you will have to go in and add radeon.modeset=0 again.

P.S. When i had gallium 3D installed this fix screwed up the video driver completely and thus I decided to reinstall the system instead of trying to remove it

---

### Post by datum on 2010-05-31
> **clhsharky said:**
> gaalaaant

Can you past me one more thing before you start?
System/Administration/Log file viewer/Xorg.0.log

Install  ia32-libs  in repos for better compatibility.
This has nothing to do with kernel, its for 32bit apps in a 64 OS.

Were installing kernel 2.6.34.rc6, its what was recommended for the xrandr fixes and its more laptop friendly "dynamic PM, better wifi drivers".

you will need these 3 deb downloaded
installed 1 at a time
in this order
linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb
linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_amd64.deb
linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_amd64.deb

from here
[http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc6-lucid/](http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc6-lucid/)

then restart

You may need radeon.dynpm=1 in the boot string to enable dynamic PM with a 2.6.34 kernel.

While installing debs if it asks you about config choose the one you have.
Has drop down box. We don't want to mess up your duel boot.
We will start with kernel before moving on to drivers.

It worked perfect for me regarding dual monitors but then I completely lost my wireless. The problem is in the bcmwl-kernel-source. It can not make configuration. I found a solution suggesting to remove both bcmwl-kernel-source and dkms and then make a new install of bcmwl but the problem is that the bcmwl wants the dksm to be installed. 

I've found a post for this specific problem but there is no solution so far. 

I found also other suggested solutions but none is working

Anyone out there who know the solution?

---

### Post by matros_ua on 2010-06-02
I got the same issue,
after kernel update I lost all my network connection :(
Somebody knows How to fix It?

[COLOR="Red"]P.S.[/COLOR] I found the solution for my network issue [http://ubuntuforums.org/showpost.php?p=9292726&postcount=11](http://ubuntuforums.org/showpost.php?p=9292726&postcount=11)

---

### Post by datum on 2010-06-04
> **matros_ua said:**
> I got the same issue,
after kernel update I lost all my network connection :(
Somebody knows How to fix It?

[COLOR=Red]P.S.[/COLOR] I found the solution for my network issue [http://ubuntuforums.org/showpost.php?p=9292726&postcount=11](http://ubuntuforums.org/showpost.php?p=9292726&postcount=11)

I didn't try this solution but I made a made a new installation of 10.04 and then I corrected the problem with the monitor on the basis of the following post:
[http://www.niccolofavari.com/ubuntu-10.04-lucid-issues-with-external-monitor-and-ati-radeon-card](http://www.niccolofavari.com/ubuntu-10.04-lucid-issues-with-external-monitor-and-ati-radeon-card)

Monitor works fine now and I have wireless. The problem is though that the 2.6.34-020364rc7 kernel is much faster than the 2.6.32-22. But with the 2.6.34 I had the problem with the wireless.

So now my problem is that the boot and login time is very slow

---

### Post by artursm on 2010-06-18
This thread helped me a little, so I thought I'd contribute with my system info, in case someone else stumbles by this thread.

I'm using an ATI Radeon Mobility X1200 (or x1250). I had the same problem as the OP, the external monitor had a very wavy and wiggly image. And this wavyness varied depending on the resolution and frequency I set for it. Installing the new kernels fixed it almost completely, the wavyness was almost completely gone. I then clicked the Autoset button on the side of my monitor, and now the wavyness is gone completely.

The kernels screwed up my wireless unfortunately. I had to manually install a broadcom STA wireless driver back when I first installed 10.04. After installing these new kernels, the broadcom STA driver is no longer activated, and trying to activate it results in error messages. I'll try to download and install it again, if I don't post back it means it didn't work.

---

### Post by artursm on 2010-06-18
Reporting back. Trying to recompile the makefile for the driver failed miserably. Fortunately, the modules I was using previously were still in the system. I got everything working with the following modprobes:
```

sudo modprobe -i ssb
sudo modprobe -i lib80211
sudo modprobe -i b43

```

Obviously this are specific to my wireless card (broadcom BCM4312).

---

### Post by matthazley on 2010-06-20
Guys - been experiencing some problems with this display adapter also also... I installed 10.04 a few days back and have planned to migrate completely from windows. 

But yesterday, and today, while using my laptop, the display has gone really funny colours, like almost static-y in some places, as over time it just degrades away to almost nothing, like when you take a full colour JPEG and reduce it to a 4 colour gif (if that makes any sense) 

One thing to note (although I havent tested for 100% certainty) is that this is maybe happening after I have used some piece of flash on the web, like youtube or a flash chat box. 

Kind of a pain - I was wondering if any of you had solved your X1400 problems?

---

### Post by insert_name_here on 2010-06-22
I had this same problem (Radeon X1400 Mobility -> flickering and lack of usability). 

I fixed it by upgrading to the 2.6.34-020634rc7-generic Kernel. Of course, this then broke my wireless (ath5k module for Atheros 5212). I fixed the wireless by switching to the Madwifi driver. If you need help doing any of this yourself (or figuring out if it applies to you), feel free to PM me.

(Another way to fix the wireless was to choose a different kernel at startup via GRUB: that is, to use 2.6.22 when I need wireless, and 2.6.34rc7 when I only need wired internet. However, this was also a problem, because Skype crashed on 2.6.22.)

---

### Post by gillza on 2010-06-22
> **matthazley said:**
> Guys - been experiencing some problems with this display adapter also also... I installed 10.04 a few days back and have planned to migrate completely from windows. 

But yesterday, and today, while using my laptop, the display has gone really funny colours, like almost static-y in some places, as over time it just degrades away to almost nothing, like when you take a full colour JPEG and reduce it to a 4 colour gif (if that makes any sense) 

One thing to note (although I havent tested for 100% certainty) is that this is maybe happening after I have used some piece of flash on the web, like youtube or a flash chat box. 

Kind of a pain - I was wondering if any of you had solved your X1400 problems?

I am not sure if our problems are similar but I did have issues with my card and my screen going all staticish on me and freezing. I solved it by modifying boot parameters:

[http://ubuntuforums.org/showpost.php?p=9361539&postcount=41](http://ubuntuforums.org/showpost.php?p=9361539&postcount=41)

---

### Post by jimmyUT on 2010-06-24
I have this same graphics card and I installed the .34 kernel.  The flickering seems to have stopped.  However.  I still cannot change any settings when I go into monitor preferences and when I try to use a dual screen (external monitor) the monitor flickers.  I only see one monitor and it shows unknown, so its not recognizing my laptop (t60) monitor or the external.  I can only use 5:4 and my entire laptop monitor space is not being used.  Everything worked fine in Karmic, but now that I have Lucid I am having this issue.  Can anyone tell me how to fix it.. I am a noob and don't really understand yet.


Update- the flickering has stopped on my second monitor, but when I go into monitor setting i still only see one monitor that shows unknown.  The second monitor is only a clone if first and I can't set up the extended desktop like i did in karmic

---

### Post by artursm on 2010-06-24
> **jimmyUT said:**
> I have this same graphics card and I installed the .34 kernel.  The flickering seems to have stopped.  However.  I still cannot change any settings when I go into monitor preferences and when I try to use a dual screen (external monitor) the monitor flickers.  I only see one monitor and it shows unknown, so its not recognizing my laptop (t60) monitor or the external.  I can only use 5:4 and my entire laptop monitor space is not being used.  Everything worked fine in Karmic, but now that I have Lucid I am having this issue.  Can anyone tell me how to fix it.. I am a noob and don't really understand yet.

I am no expert but I can try to help. One possible reason for your problem, is that you might have a badly configured xorg.conf file. This file is unnecessary, but (if present) it is used to configure your display settings. 

Read all the way before trying it.

This file is located in /etc/X11/xorg.conf
To hide it from the system, without deleting it, do the following:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
You'll have to type in your password.

If the terminal complains "No such file or directory", than you're not using any xorg.conf file (that's ok) and so it is not the source of your problems.

If the terminal doesn't say anything, than the operation succeeded. Reboot and see what happens.

Now here's the disclaimer: This operation shouldn't give you any problems, but if you reboot and the screen is completely unusable for some reason, here's how you can revert the change we made:

Reboot again, this time pick "Recovery" on the grub menu. Login with your username and password. You'll be given a command line, type the following:
```
sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

This will get you the file you had before. Just reboot again.

---


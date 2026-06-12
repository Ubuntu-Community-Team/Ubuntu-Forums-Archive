---
title: "Working ATI/Intel MultiSeat Configuration Ubuntu 11.04 / Mint / PinGuy - One Question"
date: 2011-05-18
forum: General Help
---

### Post by Vietman on 2011-05-18
I am running PinGuy, a modification/mix of Debian, Ubuntu and Mint.

I managed to collate all the necessary info and got my multiseat system up. The only problem is, how do I get sound output working on my second output? I can get both of them to use the first output simultaneously, but there is no sound when using the second (HDMI) output which normally works in Windows.

Attached is my kdmrc and xorg.conf.

You may also find this useful as a reference in case you wish to use multiseat on a similar configuration. Mine is ATI Radeon 5850 and Sandy Bridge Onboard Graphics (2600K) for the TV via HDMI. Both are using the open-source drivers, everything updated to the newest version.

Keep in mind you need to be using kdm to do this. I references these to get started:
[B]
[https://wiki.archlinux.org/index.php/Xorg_multiseat#.2Fetc.2FX11.2Fxorg.conf](https://wiki.archlinux.org/index.php/Xorg_multiseat#.2Fetc.2FX11.2Fxorg.conf)[/B]

**[https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)**

The pulse audio fix in the second link didn't get the HDMI going, but it did allow them to both use the audio on my main speakers.

---

### Post by Vietman on 2011-05-18
Also, for the config you may opt to clone a user to make things more streamlined, as logging in to the same account is not good practice.

[http://ubuntuforums.org/showthread.php?t=365440](http://ubuntuforums.org/showthread.php?t=365440)

---

### Post by grekpg on 2011-06-07
hy i have this devices : 

```
grek@dom-server:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:02.0 Display controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400 GS] (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:01.0 Multimedia controller: Twinhan Technology Co. Ltd Mantis DTV PCI Bridge Controller [Ver 1.0] (rev 01)

```

this is my graphics cards ?

00:02.0 Display controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

and 


01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400 GS] (rev a1)


im ask beacose i cant run multiseat and in many tutorials to find grapgics card i must look at : 


grek@dom-server:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400 GS] (rev a1)


so i have once beacose 00:02.0 Display controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10) dont have VGA in name its ok ?


here is xorg error : 
```

[  3936.365] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[  3936.368] X Protocol Version 11, Revision 0
[  3936.369] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[  3936.371] Current Operating System: Linux dom-server 2.6.38-10-generic #44-Ubuntu SMP Thu Jun 2 21:32:22 UTC 2011 x86_64
[  3936.372] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=51f6cefe-5adc-4453-8e9b-9a9c02ea335f ro quiet splash vt.handoff=7
[  3936.373] Build Date: 21 May 2011  11:48:41AM
[  3936.375] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[  3936.376] Current version of pixman: 0.20.2
[  3936.377] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  3936.380] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  3936.384] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun  7 22:24:57 2011
[  3936.385] (==) Using config file: "/etc/X11/xorg.conf"
[  3936.387] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  3936.388] (==) ServerLayout "Layout0"
[  3936.388] (**) |-->Screen "Screen0" (0)
[  3936.388] (**) |   |-->Monitor "Monitor0"
[  3936.388] (**) |   |-->Device "Device0"
[  3936.388] (**) |-->Input Device "kbd_0"
[  3936.388] (**) |-->Input Device "Mouse0"
[  3936.388] (**) Option "Xinerama" "0"
[  3936.388] (**) Option "AutoAddDevices" "false"
[  3936.389] (**) Option "AutoEnableDevices" "false"
[  3936.389] (**) Not automatically adding devices
[  3936.389] (**) Not automatically enabling devices
[  3936.389] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  3936.389] 	Entry deleted from font path.
[  3936.389] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  3936.389] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  3936.389] (==) |-->Input Device "Mouse0"
[  3936.389] (==) |-->Input Device "<default keyboard>"
[  3936.389] (==) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
[  3936.389] (==) The core keyboard device wasn't specified explicitly in the layout.
	Using the default keyboard configuration.
[  3936.389] (II) Loader magic: 0x7e0280
[  3936.389] (II) Module ABI versions:
[  3936.389] 	X.Org ANSI C Emulation: 0.4
[  3936.389] 	X.Org Video Driver: 10.0
[  3936.389] 	X.Org XInput driver : 12.3
[  3936.389] 	X.Org Server Extension : 5.0
[  3936.389] (--) PCI: (0:0:2:0) 8086:29c2:1458:d000 rev 16, Mem @ 0xe5300000/524288, 0xd0000000/268435456, 0xe5000000/1048576, I/O @ 0x0000e000/8
[  3936.389] (--) PCI:*(0:1:0:0) 10de:0422:1458:3454 rev 161, Mem @ 0xe2000000/16777216, 0xc0000000/268435456, 0xe0000000/33554432, I/O @ 0x0000c000/128, BIOS @ 0x????????/131072
[  3936.390] (II) Open ACPI successful (/var/run/acpid.socket)
[  3936.390] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[  3936.390] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[  3936.390] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[  3936.390] (II) "record" will be loaded by default.
[  3936.390] (II) "dri" will be loaded by default.
[  3936.390] (II) "dri2" will be loaded by default.
[  3936.390] (II) LoadModule: "dbe"
[  3936.390] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  3936.390] (II) Module dbe: vendor="X.Org Foundation"
[  3936.390] 	compiled for 1.10.1, module version = 1.0.0
[  3936.390] 	Module class: X.Org Server Extension
[  3936.390] 	ABI class: X.Org Server Extension, version 5.0
[  3936.390] (II) Loading extension DOUBLE-BUFFER
[  3936.390] (II) LoadModule: "extmod"
[  3936.390] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  3936.390] (II) Module extmod: vendor="X.Org Foundation"
[  3936.391] 	compiled for 1.10.1, module version = 1.0.0
[  3936.391] 	Module class: X.Org Server Extension
[  3936.391] 	ABI class: X.Org Server Extension, version 5.0
[  3936.391] (II) Loading extension MIT-SCREEN-SAVER
[  3936.391] (II) Loading extension XFree86-VidModeExtension
[  3936.391] (II) Loading extension XFree86-DGA
[  3936.391] (II) Loading extension DPMS
[  3936.391] (II) Loading extension XVideo
[  3936.391] (II) Loading extension XVideo-MotionCompensation
[  3936.391] (II) Loading extension X-Resource
[  3936.391] (II) LoadModule: "glx"
[  3936.391] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[  3936.400] (II) Module glx: vendor="NVIDIA Corporation"
[  3936.400] 	compiled for 4.0.2, module version = 1.0.0
[  3936.400] 	Module class: X.Org Server Extension
[  3936.400] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[  3936.400] (II) Loading extension GLX
[  3936.400] (II) LoadModule: "record"
[  3936.400] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  3936.400] (II) Module record: vendor="X.Org Foundation"
[  3936.400] 	compiled for 1.10.1, module version = 1.13.0
[  3936.400] 	Module class: X.Org Server Extension
[  3936.400] 	ABI class: X.Org Server Extension, version 5.0
[  3936.400] (II) Loading extension RECORD
[  3936.400] (II) LoadModule: "dri"
[  3936.401] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  3936.401] (II) Module dri: vendor="X.Org Foundation"
[  3936.401] 	compiled for 1.10.1, module version = 1.0.0
[  3936.401] 	ABI class: X.Org Server Extension, version 5.0
[  3936.401] (II) Loading extension XFree86-DRI
[  3936.401] (II) LoadModule: "dri2"
[  3936.401] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  3936.401] (II) Module dri2: vendor="X.Org Foundation"
[  3936.401] 	compiled for 1.10.1, module version = 1.2.0
[  3936.401] 	ABI class: X.Org Server Extension, version 5.0
[  3936.401] (II) Loading extension DRI2
[  3936.401] (II) LoadModule: "nvidia"
[  3936.401] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[  3936.402] (II) Module nvidia: vendor="NVIDIA Corporation"
[  3936.402] 	compiled for 4.0.2, module version = 1.0.0
[  3936.402] 	Module class: X.Org Video Driver
[  3936.402] (II) LoadModule: "evdev"
[  3936.402] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  3936.402] (II) Module evdev: vendor="X.Org Foundation"
[  3936.402] 	compiled for 1.10.0.902, module version = 2.6.0
[  3936.402] 	Module class: X.Org XInput Driver
[  3936.402] 	ABI class: X.Org XInput driver, version 12.3
[  3936.402] (II) LoadModule: "mouse"
[  3936.403] (II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
[  3936.403] (II) Module mouse: vendor="X.Org Foundation"
[  3936.403] 	compiled for 1.9.99.902, module version = 1.6.99
[  3936.403] 	Module class: X.Org XInput Driver
[  3936.403] 	ABI class: X.Org XInput driver, version 12.3
[  3936.403] (II) LoadModule: "kbd"
[  3936.403] (WW) Warning, couldn't open module kbd
[  3936.403] (II) UnloadModule: "kbd"
[  3936.403] (II) Unloading kbd
[  3936.403] (EE) Failed to load module "kbd" (module does not exist, 0)
[  3936.405] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:25 PDT 2011
[  3936.405] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  3936.405] (--) using VT number 8

[  3936.409] (EE) No devices detected.
[  3936.409] 
Fatal server error:
[  3936.409] no screens found
[  3936.409] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[  3936.409] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  3936.409] 

```

---

### Post by grekpg on 2011-06-07
and here is  xorg

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-08.nvidia.com)  Mon Apr 18 15:14:00 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "kbd_0" 
    InputDevice    "Mouse0" 
 Option      "AutoEnableDevices"     "false"
    Option      "AutoAddDevices"        "false"
    Option      "AllowEmptyInput"       "true"

EndSection


Section "ServerLayout"

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#	InputDevice    "Keyboard0" "CoreKeyboard"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#	InputDevice    "Mouse0" "CorePointer"
    Identifier     "Layout1"
    Screen      0  "Screen1" 0 0
#    Screen      1  "Screen1" RightOf "Screen0"
#    InputDevice    "Keyboard0" "CoreKeyboard"
#    InputDevice    "Mouse0" "CorePointer"
#    Option         "Xinerama" "0"
##   InputDevice    "Keyboard0" "CoreKeyboard"
 InputDevice "kbd_1"
    Option      "AutoEnableDevices"     "false"
    Option      "AutoAddDevices"        "false"
    Option      "AllowEmptyInput"       "true"

EndSection


Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection


Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection


Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "kbd_0"
    Driver "evdev"
    Option      "Device"        "/dev/input/by-path/pci-0000:00:1d.7-usb-0:8.3:1.0-event-kbd"
    Option "XkbRules" "xorg"
    Option "XkbModel" "105"
#    Option "XkbLayout" "us"

EndSection


Section "InputDevice"
    # generated from default
    Identifier     "kbd_1"
    Driver "evdev"
    Option      "Device"        "/dev/input/by-path/pci-0000:00:1d.7-usb-0:8.3:1.1-event-kbd"
    Option "XkbRules" "xorg"
    Option "XkbModel" "105"
    Option "XkbLayout" "us"
#    Option "XkbVariant" "nodeadkeys"
    Option  "Protocol"      "Standard"
#    Option  "XkbOptions"    "compose:rctrl"

EndSection


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection


Section "Monitor"
	Identifier   "Monitor1"
	Option	    "VendorName" "Unknown"
	Option	    "ModelName" "Generic Autodetecting Monitor"
##    HorizSync       31.0 - 84.0
##    VertRefresh     56.0 - 75.0
        Option      "DPMS"
#	Option	    "DPMS" "true"
#	Option	    "PreferredMode" "1920x1080"
#	Option	    "TargetRefresh" "60"
#	Option	    "Position" "0 0"
#	Option	    "Rotate" "normal"
#	Option	    "Disable" "false"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
      BusID          "PCI:01:00.0"
Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "intel"
    VendorName     ""
    BoardName      ""
    BusID          "PCI:00:02.0"
    Screen          0
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```


and kdmrc /etc/kde4/kdmrc - >correct file ?


```
[General]
ConfigVersion=2.4
ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6
GreeterUID=kdm
PidFile=/var/run/kdm.pid
ReserveServers=:1,:2,:3
ServerVTs=-7
StaticServers=:0

[Shutdown]
BootManager=None
HaltCmd=/sbin/shutdown -h -P now
RebootCmd=/sbin/shutdown -r now

[X-*-Core]
AntiAliasing=false
AllowNullPasswd=false
AllowRootLogin=false
AllowShutdown=Root
AutoReLogin=false
ClientLogFile=.xsession-errors-%d
Reset=/etc/kde4/kdm/Xreset
Session=/etc/kde4/kdm/Xsession
Setup=/etc/kde4/kdm/Xsetup
Startup=/etc/kde4/kdm/Xstartup

[X-*-Greeter]
AntiAliasing=true
ColorScheme=
FaceSource=AdminOnly
FailFont=Sans Serif,10,-1,5,75,0,0,0,0,0
GUIStyle=
GreetFont=Serif,20,-1,5,50,0,0,0,0,0
GreetString=Witamy na komputerze %s w %n
GreeterPos=50,50
HiddenUsers=
Language=pl
LogoArea=Logo
LogoPixmap=/usr/share/kde4/apps/kdm/pics/kdelogo.png
MaxShowUID=29999
MinShowUID=1000
Preloader=/usr/bin/preloadkde
SelectedUsers=
ShowUsers=NotHidden
SortUsers=true
StdFont=Sans Serif,10,-1,5,50,0,0,0,0,0
Theme=/usr/share/kde4/apps/kdm/themes/oxygen
UseBackground=true
UseTheme=true
UserCompletion=false
UserList=true

[X-:*-Core]
AllowNullPasswd=true
AllowShutdown=All
NoPassEnable=false
NoPassUsers=
ServerArgsLocal=-nr -nolisten tcp
#ServerCmd=/usr/bin/X

[X-:*-Greeter]
AllowClose=true
DefaultUser=basia
FocusPasswd=true
LoginMode=DefaultLocal
PreselectUser=Previous

[X-:0-Greeter]
DefaultUser=

[X-:1-Greeter]
DefaultUser=

[X-:0-Core]
AutoLoginEnable=false
AutoLoginLocked=false
AutoLoginUser=
ClientLogFile=.xsession-errors
ServerCmd=/usr/bin/X -sharevts -layout layout0 -isolateDevice PCI:01:00.0 -keeptty
ServerVT=7

[X-:1-Core]
AutoLoginEnable=false
AutoLoginLocked=false
AutoLoginUser=
ClientLogFile=.xsession-errors
ServerCmd=/usr/bin/X -sharevts -novtswitch -layout layout1 -isolateDevice PCI:00:02.0 -keeptty
ServerVT=9


[Xdmcp]
Enable=false
Willing=/etc/kde4/kdm/Xwilling
```


any can help ? :) i realy need multiseat


i find this solutions 
[http://userful.com/](http://userful.com/)
now i waitng for they response but looking great - they have some human understand configurator software for linux (not nessesery usb multiples but its easy and can give next users)

---


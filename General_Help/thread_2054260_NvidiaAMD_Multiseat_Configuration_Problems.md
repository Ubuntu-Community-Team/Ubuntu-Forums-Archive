---
title: "Nvidia/AMD Multiseat Configuration Problems"
date: 2012-09-06
forum: General Help
---

### Post by kamiloxnumetal on 2012-09-06
First of all, hello! 
i hope you can help me to solve a problem and sorry for my english hehe...

I have problems with a multiseat configuration with 2 seats under kubuntu 12.04 x64 using evdev, and 2 gpus

gpu1 is : Amd Radeon HD 6450 using fglrx driver (pci busid 2:0.0)
gpu2 is: Nvidia GeForce 6100 using nvidia driver (pci busid 0:5.0)

as you may know kubuntu and other ubuntus won't let you to automatically install fglrx and nvidia-current packages drivers at the same time
yes you can install both packages, but only one is "active"

to solve this i found a solution:

install the nvidia driver with the .run installer (i'm using 295.53 version)
and then install the .deb package of fglrx

the multiseat configuration works, the two displays starts and everything seems to be ok

the problem is the nvidia seat, can't use openGL and hardware acceleration, also it can't use the nvidia-settings utility (the amd seat can use catalyst-cc , opengl and all without problems)
, that's not good because i can't configure color, brightness, gamma and all that (i managed to configure gamma with xgamma)

i tried the 295.53 nvidia driver alone before buying the Amd gpu, and it's works ok, so the openGL and hardware acceleration problems are not the same of the 295.40 drivers bug

this is the output for glxgears on the nvidia seat:

```
seat2@kamiloxnumetal-desktop:~$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
seat2@kamiloxnumetal-desktop:~$

```

and this is the output for nvidia-settings:

```

seat2@kamiloxnumetal-desktop:~$ nvidia-settings
The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 158 error_code 1 request_code 136 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
seat2@kamiloxnumetal-desktop:~$

```

one interesing thing is, if i put a preconfigured .nvidia-setting-rc file on the home folder with preconfigured brightness and other things values, and i try to run nvidia-settings, the settings saved in the .nvidia-settings-rc file are applied, next the application crash with the bug above and close

using nvidia-xconfig breaks the xorg.conf multiseat config
let the .run nvidia installer to configure xorg.conf breaks the multiseat too , so i can't do that

here is mi kdmrc and xorg.conf

```

[General]
ConfigVersion=2.4
ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6
GreeterUID=kdm
PidFile=/var/run/kdm.pid
ReserveServers=:2,:3
ServerVTs=7,9
StaticServers=:0,:1

[Shutdown]
BootManager=None
HaltCmd=/sbin/shutdown -h -P now
RebootCmd=/sbin/shutdown -r now

[X-*-Core]
AllowNullPasswd=false
AllowRootLogin=false
AllowShutdown=Root
AutoReLogin=false
ClientLogFile=.xsession-errors-%d
Reset=/etc/kde4/kdm/Xreset
Session=/etc/kde4/kdm/Xsession
SessionsDirs=/usr/share/xsessions,/var/lib/menu-xdg/xsessions,/etc/kde4/kdm/sessions,/usr/share/kde4/apps/kdm/sessions
Setup=/etc/kde4/kdm/Xsetup
Startup=/etc/kde4/kdm/Xstartup

[X-*-Greeter]
AntiAliasing=false
ColorScheme=
FaceSource=AdminOnly
FailFont=Sans Serif,10,-1,5,75,0,0,0,0,0
GUIStyle=
GreetFont=Serif,20,-1,5,50,0,0,0,0,0
GreetString=Bienvenido a %s en %n
GreeterPos=50,50
HiddenUsers=
Language=en_GB
LogoArea=Logo
LogoPixmap=/usr/share/kde4/apps/kdm/pics/kdelogo.png
MaxShowUID=29999
MinShowUID=1000
Preloader=/usr/bin/preloadkde
SelectedUsers=
ShowUsers=NotHidden
SortUsers=true
StdFont=Sans Serif,10,-1,5,50,0,0,0,0,0
Theme=/usr/share/kde4/apps/kdm/themes/black_diamond
UseBackground=true
UseTheme=true
UserCompletion=false
UserList=true

[X-:*-Core]
AllowNullPasswd=true
AllowShutdown=All
NoPassEnable=false
NoPassUsers=
ServerArgsLocal=-br -nolisten tcp
ServerCmd=/usr/bin/X

[X-:*-Greeter]
AllowClose=true
DefaultUser=kamiloxnumetal
FocusPasswd=true
LoginMode=DefaultLocal
PreselectUser=Previous

[X-:0-Core]
AutoLoginEnable=true
AutoLoginLocked=false
AutoLoginUser=kamiloxnumetal
ClientLogFile=.xsession-errors
ServerCmd=/usr/bin/X -sharevts -layout layout0 -isolateDevice PCI:1:0:0 -keeptty
ServerVT=7

[X-:0-Greeter]
DefaultUser=

[X-:1-Core]
AutoLoginEnable=false
AutoLoginLocked=false
AutoLoginUser=
ClientLogFile=.xsession-errors
ServerCmd=/usr/bin/X -sharevts -novtswitch -layout layout1 -isolateDevice PCI:0:2:0 -keeptty
ServerVT=9

[X-:1-Greeter]
DefaultUser=

[Xdmcp]
Enable=false
Willing=/etc/kde4/kdm/Xwilling

```

xorg.conf

```

##################### NVIDIA GEFORCE 6100 SEAT ####################

Section "ServerLayout"
	Identifier     "Layout1"
	Screen      0  "Screen1" 0 0
	InputDevice    "Keyboard1" "CoreKeyboard"
	InputDevice    "Mouse1" "CorePointer"
	Option	    "AutoEnableDevices" "false"
	Option	    "AutoAddDevices" "false"
	Option	    "AllowEmptyInput" "true"
EndSection

Section "InputDevice"
	#Option	    "Protocol" "auto"
	#Option	    "Emulate3Buttons" "no"
	#Option	    "ZAxisMapping" "4 5"
	Identifier  "Mouse1"
	Driver      "evdev"
	Option	    "Device" "/dev/input/by-path/platform-i8042-serio-1-event-mouse"
	#Option	    "Device" "/dev/input/mouse1"
	Option	    "GrabDevice" "on"
EndSection

Section "InputDevice"
	Identifier  "Keyboard1"
	Driver      "evdev"
	Option	    "Device" "/dev/input/by-path/platform-i8042-serio-0-event-kbd"
	Option	    "XkbRules" "xorg"
	#Option	    "XkbModel" "105"
	Option	    "XkbLayout" "es"
	Option	    "Protocol" "Standard"
EndSection

Section "Monitor"
	Identifier   "Compaq MV520 CRT"
	VendorName   "Unknown"
	ModelName    "COMPAQ MV520"
	HorizSync    30.0 - 54.0
	VertRefresh  50.0 - 100.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Device1"
	Driver      "nvidia"
	VendorName  "NVIDIA Corporation"
	BoardName   "GeForce 6100"
	Option         "RenderAccel" "true"
	#Option         "TripleBuffer" "true"
	Option         "NoLogo" "1"
	BusID       "PCI:0:5:0"
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Device1"
	Monitor    "Compaq MV520 CRT"
	DefaultDepth     24
	Option	    "TwinView" "0"
	Option	    "metamodes" "1024x768 +0+0; nvidia-auto-select +0+0"
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

##################### NVIDIA GEFORCE 6100 SEAT ####################
##################### AMD RADEON HD 6450 SEAT #####################

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
	Option	    "AutoEnableDevices" "false"
	Option	    "AutoAddDevices" "false"
	Option	    "AllowEmptyInput" "true"
EndSection

Section "InputDevice"
	#Option	    "Protocol" "auto"
	#Option	    "Emulate3Buttons" "no"
	#Option	    "ZAxisMapping" "4 5"
	Identifier  "Mouse0"
	Driver      "evdev"
	Option	    "Device" "/dev/input/by-path/pci-0000:00:0b.0-usb-0:2:1.0-event-mouse"
	Option	    "GrabDevice" "on"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "evdev"
	Option	    "Device" "/dev/input/by-path/pci-0000:00:0b.0-usb-0:4:1.0-event-kbd"
	Option	    "XkbRules" "xorg"
	#Option	    "XkbModel" "105"
	Option	    "XkbLayout" "es"
	Option	    "Protocol" "Standard"
EndSection

Section "Monitor"
	Identifier  "AOC FT720g CRT"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Device0"
	Driver      "fglrx"
	Option	    "Monitor-CRT1" "AOC FT720g CRT"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Device0"
	DefaultDepth     24
	Option         "Monitor-CRT1" "AOC FT720g CRT"
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

##################### AMD RADEON HD 6450 SEAT #####################
######################### OTHER CONFIG ############################

Section "Module"
	Load  "dbe"
	Load  "extmod"
	Load  "type1"
	Load  "freetype"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option         "AutoAddDevices" "false"
	Option         "AutoEnableDevices" "false"
	Option         "AllowMouseOpenFail" "on"
	Option         "AllowEmptyInput" "on"
	Option         "ZapWarning" "on"
	Option         "DontZap" "false"
	Option         "HandleSepcialKeys" "off"
	Option         "DRI2" "on"
	Option         "Xinerama" "off"
EndSection

######################### OTHER CONFIG ############################

```

i really want to use opengl , hardware accel and nvidia-settings with the nvidia-seat is there a way to do that?

also i have another problem hehe....

that's the user in the nvidia-seat can't mount usb drives
only the primary amd-seat can do it, and it mount it with permissions 700 (rwx------), so the other user can't access the usb drive

do you know how to let the other user have rights to mount usb drives
or at least something for the amd seat user to mount the usb drives with 777 (rwxrwxrwx) permissions

both users are in the same groups and the same privileges...

that's all thanks!

---

### Post by Epodx64 on 2012-09-07
Not sure if this will help but try adding the x-swat/x-org repo and updating your driver to 304 the 29x on my old Geforce 6150se refused to work what so ever.

---

### Post by mmorgan27 on 2012-12-21
Just wanted to link to a site that has suggestions that have fixed my multiseat stability issues: [Fixing Reliability Problems with Multiseat Linux]("http://blog.startupanywhere.org/fixing-reliability-problems-with-multiseat-linux/")

---


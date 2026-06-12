---
title: "nvidia proprietary driver"
date: 2009-07-07
forum: General Help
---

### Post by jim_ryan on 2009-07-07
SOLVED
needed to add BUSID under devices.

I'm having some difficulty getting the nvidia proprietary drivers to stick, was hoping you guys could help.  Whenever I install the nvidia proprietary drivers and reboot, i get something like

kinit: no resume image...

I've tried installing via system/admin/hardware drivers and by using envy.  Both times I get the same error.  I'm running 64 bit and would appreciate the help.  Is there any other information that I can provide that will help diagnose?

---

### Post by jbrown96 on 2009-07-07
Does it freeze at that point? What model card do you have; you can check with ```
lspci | grep VGA
``` in a terminal? Did you choose the 173.xx or 180.xx version?


If you have access to a wired internet connection, it should be fairly easy to install the driver manually. If you do, I'll post the instructions, but I don't want to type them for no reason.

---

### Post by jim_ryan on 2009-07-08
No, it doesn't freeze, it just boots without a GUI.  I think i chose the 180, im not sure though.  I've since uninstalled nvidia...

I have a pair of gtx 260's.

02:00.0 VGA compatible controller: nVidia Corporation GT200 [GTX260-216] (rev a1)
03:00.0 VGA compatible controller: nVidia Corporation GT200 [GTX260-216] (rev a1)

I do have a wired connection.

---

### Post by kpkeerthi on 2009-07-08
> **jim_ryan said:**
> 
kinit: no resume image...

That is not an error nor is related to your graphics driver. The kernel logs that message when it attempts to find a resume image that would have been created if you have hibernated your last session. You can ignore that message.

If the drivers from Ubuntu Repository doesn't work or support your card, try manually installing the latest driver. 

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by jbrown96 on 2009-07-08
You will need to install the following packages first

```
sudo apt-get install build-essential kernel-headers
``` there may be more, but the nvidia installer should tell you. Then download the proper driver from nvidia.com. You will then need to quit X. Close all your applications and logout. Then press Alt+F1 to switch to a virtual terminal. Login, then stop X with ```
sudo /etc/init.d/gdm stop
``` Now run the installer ```
sudo sh path/to/driver/
``` It will probably download to your desktop. You should type sudo sh Desktop/ then press tab a couple of times to list the files in the directory. Type the first few letters then press tab again to automatically complete the filename. Follow the instructions. I've never known what the implications of the 32-bit opengl files are, but I always install them. You should be able to reboot with ```
sudo reboot
``` hopefully this works. You may also want to install nvidia-settings to configure everything (I imagine that you will need to do something about SLI, but I don't have a sweet setup like that).

---

### Post by jim_ryan on 2009-07-08
when I enter the first command...

jim_ryan@jim_ryan-desktop:~$ sudo apt-get install build-essential kernel-headers
[sudo] password for jim_ryan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kernel-headers is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kernel-headers has no installation candidate

---

### Post by jim_ryan on 2009-07-08
I skipped the first step, followed the rest and... same problem.

kinit: no resume image, doing normal boot

no gui.

---

### Post by jim_ryan on 2009-07-08
> **kpkeerthi said:**
> That is not an error nor is related to your graphics driver. The kernel logs that message when it attempts to find a resume image that would have been created if you have hibernated your last session. You can ignore that message.

If the drivers from Ubuntu Repository doesn't work or support your card, try manually installing the latest driver. 

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

sorry im such a newb, I understand its not an error, and that it doesn't have anything to do with my card.  Its just whenever I install the nvidia drivers and reboot, I get that message and no gui.  I appreciate your help though.

---

### Post by Trophy on 2009-07-08
I am having the exact same problem with my 

1:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1)
0a:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1)

I got:
Linux Kernel 2.6.28-13-generic
X.Org 7.4 (i don't have XFree86)
Kernel modutils 3.7-pre9
binutils 2.19.1
GNU make 3.81
gcc 4.33

i have run :
sudo apt-get install build-essential linux-headers-2.6.28-13-generic

I have the file NVIDIA-Linux-x86-185.18.14-pkg1.run on my desktop

i hit Ctr-Alt-F1
 at this point my xorg.conf file looked like this:

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

i ran 
 sudo /etc/init.d/gdm stop

then 
sudo sh NVIDIA-Linux-x86-185.18.14-pkg1.run

ran through the installation, only thing that didn't work was when it tried to check the NVidia site for some file but then it made it's own.

The xorg.conf now looks like this

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Wed May 27 03:15:36 PDT 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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
    Driver         "nvidia"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

But on reboot the screen has a "_" which flashes and nothing else happens.

I hit Ctr-Alt-F1 and uninstall and replace the Xorg.conf to get back the beginning.

---

### Post by CatKiller on 2009-07-08
> **jim_ryan said:**
> sorry im such a newb, I understand its not an error, and that it doesn't have anything to do with my card.  Its just whenever I install the nvidia drivers and reboot, I get that message and no gui.  I appreciate your help though.

Even without the drivers, or when you've got your drivers installed properly, when you reboot you'll get that message. You might think it's significant because it's the last message that gets put on screen, but it isn't.

It's probably worth checking to see if you can log into a virtual console (Ctrl-Alt-F1 to Ctrl-Alt-F6) to check X's log at /var/log/Xorg.0.log to see if that sheds any light on why you aren't getting a graphical environment.

---

### Post by jim_ryan on 2009-07-08
> **CatKiller said:**
> Even without the drivers, or when you've got your drivers installed properly, when you reboot you'll get that message. You might think it's significant because it's the last message that gets put on screen, but it isn't.

It's probably worth checking to see if you can log into a virtual console (Ctrl-Alt-F1 to Ctrl-Alt-F6) to check X's log at /var/log/Xorg.0.log to see if that sheds any light on why you aren't getting a graphical environment.

Gotcha, thanks for the clarification.  

Since i'm working out of command line only, how do i copy the contents of /var/log/Xorg.0.log to the forum?

---

### Post by CatKiller on 2009-07-08
> **jim_ryan said:**
> Since i'm working out of command line only, how do i copy the contents of /var/log/Xorg.0.log to the forum?

How are you accessing the forum now?

You could use ```
cat /var/log/Xorg.0.log > /some/path/here/filename
``` to spit the contents into another file somewhere - a thumb drive or what-have-you - to transfer to whichever computer you're using now. Or you could SSH from another machine. Or if you're dual-booting, you could use the command I gave you above to put that text on a partition that Windows can read.

---

### Post by jim_ryan on 2009-07-08
here is the contents of Xorg.0.log


X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux es0-desktop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul  8 17:56:07 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(!!) More than one possible primary device found
(--) PCI: (0@2:0:0) nVidia Corporation GT200 [GTX260-216] rev 161, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000af00/128, BIOS @ 0x????????/524288
(--) PCI: (0@3:0:0) nVidia Corporation GT200 [GTX260-216] rev 161, Mem @ 0xda000000/16777216, 0xb0000000/268435456, 0xd8000000/33554432, I/O @ 0x00008f00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.14  Wed May 27 01:53:56 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
Primary device is not PCI
(==) Matched vesa for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: 
(WW) Falling back to old probe method for vesa
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by jim_ryan on 2009-07-08
I've reinstalled the OS.  I'm going to repeat the steps thus far and then try this solution



If you have a problem where after installation and reboot you end up at a console prompt, it is possible that you have multiple display cards and X is not able to pick the primary card.

    * /var/log/Xorg.0.log contains entries like the following:

         (EE) No devices detected.

      The following command provides information on hardware installed on your system:
          o

                sudo lshw -businfo | grep -i display

      If you see multiple display cards listed, you need to explicitly add the PCI bus ID to your /etc/X11/xorg.conf file:
          o

            Use your text editor to open /etc/X11/xorg.conf. (try sudo vi /etc/X11/xorg.conf)
          o

            Find the line that says Section "Device"
          o

            Insert a new line that says BusID    "PCI:x:x:x", where x:x:x is the PCI address displayed by lshw command.
          o

            Save the file. If you had to restart into recovery mode, type reboot, otherwise restart your display using sudo /etc/init.d/gdm restart.

---

### Post by Trophy on 2009-07-10
ok that was my problem. It couldn't determin which was my primary device. Using the PCI# from 

sudo lshw -businfo | grep -i display

I inserted the following lines in the xorg.conf file under the device section

Busid "PCI:1:0:0"
option "sli" "auto"

and rebooted ... everything works fine now ... thanks

---


---
title: "Ubuntu is running low-graphics mode - HP Pavilion dv2000"
date: 2010-04-09
forum: General Help
---

### Post by soultaker0x on 2010-04-09
Today I installed Ubuntu on my HP Pavilion dv2000.
I installed the OS using the 9.04 Version Disc, and after I updated to 9.10 I started getting the Ubuntu is runnin low-graphics mode message.

After that the window displays the following message:
The following error was encountered. You may need to update your configuration to solve this.

(EE) intel(0): No modes.
(EE) Screen(s) found, but none have usable configuration.

I'm a total Linux/Ubuntu noob, I'd appreciate your help.

---

### Post by -humanaut- on 2010-04-09
Are you using any proprietary video cards Such a nVidia or ATI?

---

### Post by soultaker0x on 2010-04-09
No, it's not a proprietary video card. I believe it's an Intel video card.

---

### Post by lidex on 2010-04-09
What is the output of this command:
```
lspci -nn | grep VGA
```
In a terminal="Applications>Accessories>Terminal"

Post the output of these as well:
```
cat /var/log/Xorg.0.log
cat /etc/X11/xorg.conf
```

---

### Post by quadproc on 2010-04-09
> **soultaker0x said:**
> Today I installed Ubuntu on my HP Pavilion dv2000.
I installed the OS using the 9.04 Version Disc, and after I updated to 9.10 I started getting the Ubuntu is runnin low-graphics mode message.

After that the window displays the following message:
The following error was encountered. You may need to update your configuration to solve this.

(EE) intel(0): No modes.
(EE) Screen(s) found, but none have usable configuration.

I'm a total Linux/Ubuntu noob, I'd appreciate your help.
I had a very similar problem.  The resolution for me was to uninstall and reinstall the driver for the graphics card(s).  I do not know why that should have been necessary but it fixed my problem.

quadproc

---

### Post by lidex on 2010-04-10
> **quadproc said:**
> I had a very similar problem.  The resolution for me was to uninstall and reinstall the driver for the graphics card(s).  I do not know why that should have been necessary but it fixed my problem.

quadproc
That's sound advice. OP just upgraded and that means new kernel so a likely scenario.

soultaker0x: Make sure you're using the correct kernel. In a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

Reboot.

---

### Post by soultaker0x on 2010-04-10
> **lidex said:**
> What is the output of this command:
```
lspci -nn | grep VGA
```In a terminal="Applications>Accessories>Terminal"

Post the output of these as well:
```
cat /var/log/Xorg.0.log
cat /etc/X11/xorg.conf
```

Thank you, these are the outputs:


~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03


cat /var/log/Xorg.0.log

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux hplaptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686
Kernel command line: root=UUID=8102d3d5-2159-4fde-aa60-7a52c645e47d ro quiet splash 
Build Date: 04 March 2010  09:56:47AM
xorg-server 2:1.6.4-2ubuntu4.2 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr  9 22:01:20 2010
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
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:27a2:103c:30b2 Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xd4200000/524288, 0xc0000000/268435456, 0xd4300000/262144, I/O @ 0x00001800/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
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
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.9.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
(--) intel(0): Chipset: "945GM"
(II) intel(0): Output VGA1 using monitor section Configured Monitor
(II) intel(0): Output TV1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output TV1
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output TV1 disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output TV1 disconnected
(WW) intel(0): Unable to find initial modes
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(EE) intel(0): No modes.
(II) UnloadModule: "intel"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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

---

### Post by soultaker0x on 2010-04-10
> **lidex said:**
> That's sound advice. OP just upgraded and that means new kernel so a likely scenario.

soultaker0x: Make sure you're using the correct kernel. In a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```Reboot.

I updated or corrected the kernel.

How can I delete the old drivers for the graphics card? And where can I find the new drivers?

---

### Post by quadproc on 2010-04-10
> **soultaker0x said:**
> I updated or corrected the kernel.

How can I delete the old drivers for the graphics card? And where can I find the new drivers?
Normally, the drivers and instructions for installing/removing them are available either from the manufacturer of the graphics hardware (in this case, Intel) or from the manufacturer of the system in which the hardware is installed.  Usually, the process is pretty straightforward because the manufacturer has provided scripts to do all of the tedious things.

You might be able to use Synaptic to do the removal and installation.  For this, you will need to know the name of the driver package.

There is a chance that you might get your system into a state where you don't have a functioning manufacturer's driver.  If that occurs then you will probably have to do at least a little work using command lines so it would be advisable to be prepared for that.  In the worst cae you can probably fall back to a vesa driver and use that to get things squared away, then replace it with the full capability driver afterwards.

quadproc

---

### Post by soultaker0x on 2010-04-11
> **quadproc said:**
> Normally, the drivers and instructions for installing/removing them are available either from the manufacturer of the graphics hardware (in this case, Intel) or from the manufacturer of the system in which the hardware is installed.  Usually, the process is pretty straightforward because the manufacturer has provided scripts to do all of the tedious things.

You might be able to use Synaptic to do the removal and installation.  For this, you will need to know the name of the driver package.

There is a chance that you might get your system into a state where you don't have a functioning manufacturer's driver.  If that occurs then you will probably have to do at least a little work using command lines so it would be advisable to be prepared for that.  In the worst cae you can probably fall back to a vesa driver and use that to get things squared away, then replace it with the full capability driver afterwards.

quadproc

Thank you very much for you help. I'm going to try to do the removal and installation of the new drivers with the instructions you gave me.

---

### Post by Praetor77 on 2010-05-13
Did you have any success?

I had the exact same problem with the exact same graphics card (INTEL 945GM). 
After trying to disable KMS completely using "i915.modeset=0", I found forcing KMS by using "i915.modeset=1", I no longer recieved the errors posted here, but I still get low graphics mode.

This all started happening after my 3rd boot of Lucid (upgraded from Karmic). I have an Asus 1005HA.

I tried everything listed here:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

So now I am using 2.6.33-3 kernel, 2.11 xserver-xorg-intel driver, and UXA rendering, but still running in low graphics mode.

The error when I get the low graphics mode message says my hardware could not be detected, but judging from my xorg.conf file (put together by myself using the wiki and also from *dpkg*-*reconfigure* xserver-xorg) everything should be working okay?!

Here is my xorg.conf file (Tried commenting all the options and VideoRam with no avail):

```
Section "Device"
        Identifier           "Configured Video Device"
        Driver "intel"
    Option     "FramebufferCompression" "on"
    Option     "AccelMethod" "EXA"
    Option     "Tiling" "on"
    Option "MigrationHeuristic" "greedy"
    Option "XvMC" "true"
    VideoRam 261376
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    # Uncomment if your screen resolution is 1024x600
    DisplaySize 195 113
EndSection


Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Virtual    1024 600
    EndSubSection    
EndSection
```

Here is my xorg log:

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux rodrigo-laptop 2.6.33-02063303-generic #02063303 SMP Tue Apr 27 12:14:21 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.33-02063303-generic root=UUID=75a7c909-751f-4712-bb7a-32096e7997bc ro crashkernel=384M-2G:64M,2G-:128M i915.modeset=1 quiet splash acpi_osi=Linux
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May 13 01:55:05 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:27ae:1043:8340 Intel Corporation Mobile 945GME Express Integrated Graphics Controller rev 3, Mem @ 0xf7e00000/524288, 0xd0000000/268435456, 0xf7dc0000/262144, I/O @ 0x0000dc00/8
(--) PCI: (0:0:2:1) 8086:27a6:1043:8340 Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xf7e80000/524288
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
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.11.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) Primary Device is: PCI 00@00:02:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(**) intel(0): Option "Tiling" "on"
(**) intel(0): Option "XvMC" "true"
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GME
(--) intel(0): Chipset: "945GME"
(==) intel(0): video overlay key set to 0x101fe

```

Only error I can find in my logs is in my boot.log:

```
fsck from util-linux-ng 2.17.2 
/dev/sda6: clean, 349614/1044480 files, 3024287/4170867 blocks (check in 2 mounts) 
init: ureadahead-other main process (808) terminated with status 4  
 * Setting sensors limits       [128G  [122G[ OK ] 
 * Loading cpufreq kernel modules...       [128G  [122G[ OK ] 
 * CPUFreq Utilities: Setting ondemand CPUFreq governor...       [128G  * CPU0...       [128G  * CPU1...       [128G  [122G[ OK ] 
```

Going crazy here, looking for help other than "Enable VESA". Thanks in advance to anyone who can help me!

---


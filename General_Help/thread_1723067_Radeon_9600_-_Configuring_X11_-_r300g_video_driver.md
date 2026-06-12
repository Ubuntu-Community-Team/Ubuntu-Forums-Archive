---
title: "Radeon 9600 - Configuring X11 - r300g video driver - Ubuntu 10.10 powerpc"
date: 2011-04-06
forum: General Help
---

### Post by 1984dc on 2011-04-06
Hello every one here on the forums!

I am trying to set ubuntu up on my powermac g5 and I am having some  trouble configuring X. When i boot Yaboot is fine and then i get a bit  of splash then black :confused:

I tried just putting the following example of xorg.conf in the /etc/X11  but I still get a blank screen on boot. I think that is because the  radeon-kms driver isn´t installed.
[http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx](http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx)

So i did a bit of googling and i found this documentation from Ubuntu.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

It suggested the r300g driver  would work.

So  I tried to purge the old driver by 

```
sudo apt-get remove --purge fglrx
```but i don´t think the  fglrx is the right driver on Ubuntu powerpc as it wouldn't purge! How  can i find out what driver I am currently using or purge the driver  without being specific?



Is it also possible to install the r300g through apt-get? I think that  would be better for me as I am in a "bare bones" system. So would the  code would be ;

```
sudo apt-get install libgl1- mesa-dri/lucid  libgl1-mesa-dri-dbg/lucid libgl1-mesa-glx/lucid  libgl1-mesa-glx-dbg/lucid libglu1-mesa/lucid  mesa-utils/lucid
```Which was taken from;

[https://launchpad.net/~xorg-edgers/+archive/radeon]("https://launchpad.net/%7Exorg-edgers/+archive/radeon")

Is there any other configuration i need to do after that like   reconfigure the xorg.conf file? What would be my best options for the  xorg.conf? Any help on this would be hugely appreciated I've never  configured X before, still a bit of a noob two years down the line!

Here´s some details of my set-up;

ATI Radeon 9600:

  Chipset Model:    ATY,RV351
  Type:    Display
  Bus:    AGP
  Slot:    SLOT-1
  VRAM (Total):    128 MB
  Vendor:    ATI (0x1002)
  Device ID:    0x4150
  Revision ID:    0x0000
  ROM Revision:    113-A58504-113
  
Displays: Pennon PVHK-H0781A
1780:
  Resolution:    1024 x 768 @ 60 Hz
  Depth:    32-Bit Color
  Core Image:    Hardware Accelerated
  Main Display:    Yes
  Mirror:    Off
  Online:    Yes
  Quartz Extreme:    Supported
  Rotation:    Supported
Display Connector:
  Status:    No Display Connected

Many, many, many thanks

dc

---

### Post by 1984dc on 2011-04-07
I think I might have actually installed the wrong version ne way. Doh! ](*,)
 
I think i just installed the 32mb version and i have a 64mb G5.
 
I Will re-install and re-post.
 
All the best.
 
dc.

---

### Post by 1984dc on 2011-04-07
Realised that i may have pcked the wrong option whilst installing, gonna install the powerpc64 version again (just in case) and post back.

---

### Post by 1984dc on 2011-04-07
So... I re-installed and I still get the black screen of death  :cry:

Any sugestions would be great.

Many thanks.

dc

---

### Post by Krytarik on 2011-04-07
Generally, it's this way:

To upgrade to the packages provided by Xorg-Edgers' PPA, including the "radeon" driver, run these commands:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

If you need/want to downgrade again, run those:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```Reboot/relogin after each of those operations.

But since you are supposedly running a PPC architecture, and the PPA only provides builds for i386 and AMD64, I'm not sure if you are able to install those packages at all.

However, since there seems to be no "powerpc64 version" of Ubuntu, you might be running the AMD64 version, and you might be able to install those packages.

Greetings.

---

### Post by 1984dc on 2011-04-08
Thanks Krytarik
 
I will certainly try that out once i have got my system back up.
 
I was mucking about with yaboot.conf to try and get macosx as my default option to boot and i might have corrupted my whole linux system!! Lots of error messages aboyut root dirs not existing and i get chucked in to initramfs shell. I reckon i might have to re install for the 3rd time! 
 
Gonna make a new post for that topic as it is seperate i'll post a link here to it.
 
Once i get that fixed I''ll come back to this post to configure X.
 
Many thanks.
 
DC.

---

### Post by 1984dc on 2011-04-11
Back up and running!

```
sudo add-apt-repository ppa:org-edgers/ppa
sudo apt-get update
sudo apt-get upgrade 
```Now all i get is a blank screen and i can't jump into command line by pressing ctrl+alt+f1!! I suppose i will have to purge and update using my live cd and start again.

Any other suggestions on how i can get X11 up and working would be greatly appreciated.

Many thanks.

dc

---

### Post by Krytarik on 2011-04-11
- Make sure that there is no xorg.conf.

- Check "/var/log/Xorg.0.log" for related error messages, either by using a liveCD or the "recovery mode" boot option.

- If you want to downgrade the packages again, run the previously stated commands from "recovery mode -> root shell prompt with networking".

- Why do you want to upgrade the driver in the first place? Does the default driver not work?

---

### Post by 1984dc on 2011-04-11
Okay so I purged the org-edgers ppa as it didn't seem to be workin. I didn't have a xorg.conf file when i installed btw (as i removed it before install).

> Why do you want to upgrade the driver in the first place? Does the default driver not work?

That's correct the video default driver does not work and I can't get X to configure correctly. I just get a black screen after splash. I ran YDL on my G5 and everything worked straight out of the box, but i didn't really dig the distro that much (I have had Linux mint and ubuntu on another box for just over a year now and i found YDL a lot clunkier).

Don't really know where to go from here, any suggestions are more than welcome.

dc

---

### Post by Krytarik on 2011-04-11
Then there was actually no difference between the default driver and those of Xorg-Edgers? Why did you feel the need to downgrade them then?

How about this?:
> **Krytarik said:**
> 
- Check "/var/log/Xorg.0.log" for related error messages.


---

### Post by 1984dc on 2011-04-11
I purged the Xorg-edgers because i couldn't drop into command line when i got a black screen (normally i just ctrl alt f1) so I was stuck without a working terminal. I´m now back in tty1 and all is running as normal again (minus X of course). 


Here is the output off Xorg.0.log.old (which i think was the original when i Installed) there are quite a few Xorg.#.logs so i wil just attach a couple.

[U]Xorg.0.log.old
[/U]
[COLOR=Indigo][    14.846] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    14.846] X Protocol Version 11, Revision 0
[    14.846] Build Operating System: Linux 2.6.35-24-powerpc64-smp ppc Ubuntu
[    14.846] Current Operating System: Linux G5-ubuntu-10 2.6.35-22-powerpc64-smp #35-Ubuntu SMP Sat Oct 16 22:40:47 UTC 2010 ppc64
[    14.846] Kernel command line: root=/dev/sda4 ro quiet splash 
[    14.846] Build Date: 09 January 2011  12:20:41PM
[    14.846] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    14.846] Current version of pixman: 0.18.4
[    14.846]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    14.846] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.846] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 11 21:50:25 2011
[    14.847] (==) Using config file: "/etc/X11/xorg.conf"
[    14.847] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.856] (==) ServerLayout "Default Layout"
[    14.856] (**) |-->Screen "Default Screen" (0)
[    14.856] (**) |   |-->Monitor "Configured Monitor"
[    14.857] (**) |   |-->Device "Radeon 9600"
[    14.857] (==) Automatically adding devices
[    14.857] (==) Automatically enabling devices
[    14.857] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.857]     Entry deleted from font path.
[    14.857] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    14.857] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.857] (**) Extension "Composite" is enabled
[    14.857] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.857] (II) Loader magic: 0x101f0c08
[    14.857] (II) Module ABI versions:
[    14.857]     X.Org ANSI C Emulation: 0.4
[    14.857]     X.Org Video Driver: 8.0
[    14.857]     X.Org XInput driver : 11.0
[    14.857]     X.Org Server Extension : 4.0
[    14.859] (--) PCI:*(0:240:16:0) 1002:4150:1002:4150 rev 0, Mem @ 0x98000000/134217728, 0x90000000/65536, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
[    14.859] (II) LoadModule: "extmod"
[    14.863] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.863] (II) Module extmod: vendor="X.Org Foundation"
[    14.863]     compiled for 1.9.0, module version = 1.0.0
[    14.863]     Module class: X.Org Server Extension
[    14.863]     ABI class: X.Org Server Extension, version 4.0
[    14.863] (II) Loading extension MIT-SCREEN-SAVER
[    14.863] (II) Loading extension XFree86-VidModeExtension
[    14.863] (II) Loading extension XFree86-DGA
[    14.863] (II) Loading extension DPMS
[    14.863] (II) Loading extension XVideo
[    14.863] (II) Loading extension XVideo-MotionCompensation
[    14.863] (II) Loading extension X-Resource
[    14.863] (II) LoadModule: "dbe"
[    14.864] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.864] (II) Module dbe: vendor="X.Org Foundation"
[    14.864]     compiled for 1.9.0, module version = 1.0.0
[    14.864]     Module class: X.Org Server Extension
[    14.864]     ABI class: X.Org Server Extension, version 4.0
[    14.864] (II) Loading extension DOUBLE-BUFFER
[    14.864] (II) LoadModule: "glx"
[    14.865] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.865] (II) Module glx: vendor="X.Org Foundation"
[    14.865]     compiled for 1.9.0, module version = 1.0.0
[    14.865]     ABI class: X.Org Server Extension, version 4.0
[    14.865] (==) AIGLX enabled
[    14.865] (II) Loading extension GLX
[    14.865] (II) LoadModule: "record"
[    14.866] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.866] (II) Module record: vendor="X.Org Foundation"
[    14.866]     compiled for 1.9.0, module version = 1.13.0
[    14.866]     Module class: X.Org Server Extension
[    14.866]     ABI class: X.Org Server Extension, version 4.0
[    14.866] (II) Loading extension RECORD
[    14.866] (II) LoadModule: "dri"
[    14.867] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.867] (II) Module dri: vendor="X.Org Foundation"
[    14.867]     compiled for 1.9.0, module version = 1.0.0
[    14.867]     ABI class: X.Org Server Extension, version 4.0
[    14.867] (II) Loading extension XFree86-DRI
[    14.867] (II) LoadModule: "dri2"
[    14.868] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.868] (II) Module dri2: vendor="X.Org Foundation"
[    14.868]     compiled for 1.9.0, module version = 1.2.0
[    14.868]     ABI class: X.Org Server Extension, version 4.0
[    14.868] (II) Loading extension DRI2
[    14.868] (II) LoadModule: "nouveau"
[    14.868] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    14.877] (II) Module nouveau: vendor="X.Org Foundation"
[    14.877]     compiled for 1.8.99.905, module version = 0.0.16
[    14.877]     Module class: X.Org Video Driver
[    14.877]     ABI class: X.Org Video Driver, version 8.0
[    14.877] (II) NOUVEAU driver Date:   Thu Aug 5 00:40:40 2010 +0200
[    14.877] (II) NOUVEAU driver for NVIDIA chipset families :
[    14.877]     RIVA TNT    (NV04)
[    14.877]     RIVA TNT2   (NV05)
[    14.877]     GeForce 256 (NV10)
[    14.877]     GeForce 2   (NV11, NV15)
[    14.878]     GeForce 4MX (NV17, NV18)
[    14.878]     GeForce 3   (NV20)
[    14.878]     GeForce 4Ti (NV25, NV28)
[    14.878]     GeForce FX  (NV3x)
[    14.878]     GeForce 6   (NV4x)
[    14.878]     GeForce 7   (G7x)
[    14.878]     GeForce 8   (G8x)
[    14.878] (++) using VT number 7

[    14.914] (EE) No devices detected.
[    14.914] 
Fatal server error:
[    14.914] no screens found
[    14.914] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    14.914] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    14.914] [COLOR=Black]

[/COLOR][COLOR=Black]And here is the more recent [/COLOR][/COLOR][COLOR=Black]/var/log/Xorg.0.log[/COLOR][COLOR=Indigo][COLOR=Black] (i was tring to make it run the nouveau driver here, which also didn´t work).[/COLOR]

[    14.527] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    14.528] X Protocol Version 11, Revision 0
[    14.528] Build Operating System: Linux 2.6.35-24-powerpc64-smp ppc Ubuntu
[    14.528] Current Operating System: Linux G5-ubuntu-10 2.6.35-22-powerpc64-smp #35-Ubuntu SMP Sat Oct 16 22:40:47 UTC 2010 ppc64
[    14.528] Kernel command line: root=/dev/sda4 ro quiet splash 
[    14.528] Build Date: 09 January 2011  12:20:41PM
[    14.528] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    14.528] Current version of pixman: 0.18.4
[    14.528]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    14.528] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.528] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 11 22:25:16 2011
[    14.528] (==) Using config file: "/etc/X11/xorg.conf"
[    14.528] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.540] (==) ServerLayout "Default Layout"
[    14.540] (**) |-->Screen "Default Screen" (0)
[    14.540] (**) |   |-->Monitor "Configured Monitor"
[    14.540] (**) |   |-->Device "Radeon 9600"
[    14.541] (==) Automatically adding devices
[    14.541] (==) Automatically enabling devices
[    14.541] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.541]     Entry deleted from font path.
[    14.541] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    14.541] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.541] (**) Extension "Composite" is enabled
[    14.541] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.541] (II) Loader magic: 0x101f0c08
[    14.541] (II) Module ABI versions:
[    14.541]     X.Org ANSI C Emulation: 0.4
[    14.541]     X.Org Video Driver: 8.0
[    14.541]     X.Org XInput driver : 11.0
[    14.541]     X.Org Server Extension : 4.0
[    14.543] (--) PCI:*(0:240:16:0) 1002:4150:1002:4150 rev 0, Mem @ 0x98000000/134217728, 0x90000000/65536, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
[    14.543] (II) LoadModule: "extmod"
[    14.547] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.547] (II) Module extmod: vendor="X.Org Foundation"
[    14.547]     compiled for 1.9.0, module version = 1.0.0
[    14.547]     Module class: X.Org Server Extension
[    14.547]     ABI class: X.Org Server Extension, version 4.0
[    14.547] (II) Loading extension MIT-SCREEN-SAVER
[    14.547] (II) Loading extension XFree86-VidModeExtension
[    14.547] (II) Loading extension XFree86-DGA
[    14.547] (II) Loading extension DPMS
[    14.547] (II) Loading extension XVideo
[    14.547] (II) Loading extension XVideo-MotionCompensation
[    14.547] (II) Loading extension X-Resource
[    14.547] (II) LoadModule: "dbe"
[    14.548] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.548] (II) Module dbe: vendor="X.Org Foundation"
[    14.548]     compiled for 1.9.0, module version = 1.0.0
[    14.548]     Module class: X.Org Server Extension
[    14.548]     ABI class: X.Org Server Extension, version 4.0
[    14.548] (II) Loading extension DOUBLE-BUFFER
[    14.548] (II) LoadModule: "glx"
[    14.548] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.549] (II) Module glx: vendor="X.Org Foundation"
[    14.549]     compiled for 1.9.0, module version = 1.0.0
[    14.549]     ABI class: X.Org Server Extension, version 4.0
[    14.549] (==) AIGLX enabled
[    14.549] (II) Loading extension GLX
[    14.549] (II) LoadModule: "record"
[    14.550] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.550] (II) Module record: vendor="X.Org Foundation"
[    14.550]     compiled for 1.9.0, module version = 1.13.0
[    14.550]     Module class: X.Org Server Extension
[    14.550]     ABI class: X.Org Server Extension, version 4.0
[    14.550] (II) Loading extension RECORD
[    14.550] (II) LoadModule: "dri"
[    14.550] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.551] (II) Module dri: vendor="X.Org Foundation"
[    14.551]     compiled for 1.9.0, module version = 1.0.0
[    14.551]     ABI class: X.Org Server Extension, version 4.0
[    14.551] (II) Loading extension XFree86-DRI
[    14.551] (II) LoadModule: "dri2"
[    14.551] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.552] (II) Module dri2: vendor="X.Org Foundation"
[    14.552]     compiled for 1.9.0, module version = 1.2.0
[    14.552]     ABI class: X.Org Server Extension, version 4.0
[    14.552] (II) Loading extension DRI2
[    14.552] (II) LoadModule: "nouveau"
[    14.552] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    14.560] (II) Module nouveau: vendor="X.Org Foundation"
[    14.560]     compiled for 1.8.99.905, module version = 0.0.16
[    14.560]     Module class: X.Org Video Driver
[    14.560]     ABI class: X.Org Video Driver, version 8.0
[    14.561] (II) NOUVEAU driver Date:   Thu Aug 5 00:40:40 2010 +0200
[    14.561] (II) NOUVEAU driver for NVIDIA chipset families :
[    14.561]     RIVA TNT    (NV04)
[    14.561]     RIVA TNT2   (NV05)
[    14.561]     GeForce 256 (NV10)
[    14.561]     GeForce 2   (NV11, NV15)
[    14.561]     GeForce 4MX (NV17, NV18)
[    14.561]     GeForce 3   (NV20)
[    14.561]     GeForce 4Ti (NV25, NV28)
[    14.561]     GeForce FX  (NV3x)
[    14.561]     GeForce 6   (NV4x)
[    14.562]     GeForce 7   (G7x)
[    14.562]     GeForce 8   (G8x)
[    14.562] (++) using VT number 7

[    14.599] (EE) No devices detected.
[    14.599] 
Fatal server error:
[    14.599] no screens found
[    14.599] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    14.599] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    14.599] 


[COLOR=Black]I think that this is the key probably (but i´m not sure how to fix it);
 [/COLOR][/COLOR][COLOR=Indigo][    14.599] (EE) No devices detected.
[    14.599] 
Fatal server error:
[    14.599] no screens found
[    14.599] [/COLOR][COLOR=Indigo]

[COLOR=Black]Once again many thanks for all your help.

dc
[/COLOR][/COLOR]

---

### Post by Krytarik on 2011-04-11
The "nouveau" driver is for Nvidia cards/chips. And it is still being tried to load, which is apparently the cause of the issue.

I don't know exactly why, but you can either try to disable it, and choose the "radeon" driver (commands below the "OR", I really don't know if this works):
[http://ubuntuforums.org/showthread.php?t=1423210]("http://ubuntuforums.org/showthread.php?p=9120571#post9120571")

Or you can simply purge it:
```
sudo apt-get purge xserver-xorg-video-nouveau
```Another way is to to set up an xorg.conf and specify "radeon" there, I presume you already know how to set up one, since you've done it before.

---

### Post by 1984dc on 2011-04-12
Writing from inside a fully functional ubuntu terminal with X   :biggrin: I had to use  a fresh xorg.conf and then added in a few lines (marked in red):


[COLOR=DarkSlateBlue]Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "record"
    Load  "glx"
    Load  "dbe"
    Load  "dri2"
    Load  "extmod"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        Driver      [COLOR=Red]"radeon"[/COLOR]
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "CustomEDID"             # [<str>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "MacModel"               # <str>
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
        #Option     "DefaultTVDACAdj"        # [<bool>]
        #Option     "Int10"                  # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "ATOMTVOut"              # [<bool>]
        #Option     "R4xxATOM"               # [<bool>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "DynamicPM"              # [<bool>]
        #Option     "NewPLL"                 # [<bool>]
        #Option     "ZaphodHeads"            # <str>
   [COLOR=Red] Option      "Reverse DDC"               "on"  [/COLOR]
        Identifier  "Card0"
    Driver     [COLOR=Red] "radeon"[/COLOR]
    BusID       "PCI:240:16:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
[/COLOR][COLOR=Black]
I&#7743; not sure if the [/COLOR][COLOR=DarkSlateBlue][COLOR=Red]Option      "Reverse DDC"               "on"   [COLOR=Black]option s actually doing anything, but i will leave it in for the time being.

Many thanks for all your help on this [/COLOR][/COLOR][/COLOR]Krytarik.

Peace Out,

Dc

---

### Post by Krytarik on 2011-04-12
Great that it finally works! However, you have specified the 'Driver' twice, and I would remove at least the outcommented lines to slim down the file. Also, the option "Reverse DDC" seems not to be necessary, like you suspect it too. At least I didn't find many matches on Google. ;-)

---


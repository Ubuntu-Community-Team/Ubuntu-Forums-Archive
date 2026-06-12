---
title: "screen resolution"
date: 2011-12-03
forum: General Help
---

### Post by Tonywin on 2011-12-03
Hi, Can anyone help please?

I have just added a new system I5 with Ubuntu 10.04, screen is viewsonic 22”.

My older system 32 bi didn't recognise the screen but allowed me to change the res easily.

Shows res up to 1320 * 768 where I use 1024 * 768.

The 64 bit I5 system shows also monitor unknown, but max res is 800 * 600 and mhz is 61, 
I cannot change values to higher res.

I presume the working code may well be in a file on the older 32bit system. 

Is there any easy way for a non programmer to alter the res before I have to jettison the screen. I tested the system on a DELL screen and that allows max res to be gained, even showing 0 mhz.

Any help and advice please?

---

### Post by BC59 on 2011-12-03
To show what resolutions are currently supported for your display run:

```
xrandr
```

And you can change resolution running:

```
xrandr --output VGA --mode 1024×768 --rate 75
```

Change the mode from 1024x768 according to your needs.

---

### Post by Tonywin on 2011-12-03
p { margin-bottom: 0.21cm; }  

 

 Hi,
 Thank you for this,
 I tried that but it returned  
 warning: output VGA not found; ignoring 
 

 I then tried xrandr
 and got
 

 Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600 
 default connected 800x600+0+0 0mm x 0mm 
    800x600        61.0*  
    640x480        60.0   
 Any further suggestion please? I am a novice in this, also will xrandr need to be set each time?

---

### Post by Tonywin on 2011-12-03
PS
I switched systems and if it helps,
the 32 bit system shows

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
VGA2 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9

---

### Post by BC59 on 2011-12-03
I don't know if you installed the proprietary drivers for your Graphics card.

---

### Post by Tonywin on 2011-12-03
Thank you,
I did for windows xp pro they came with the motherboard disk.
But for ubuntu, I don't appear to have any, I looked at viewsonic websites for downloads, and there were none.
I approached Viewsonic, and got a generic reply eg: it is plug and play, etc, but as usual these sellers commit to support in words but not deeds.
I want to throw the screen out, but clearly it CAN work, and does under ubunto 32bit.
Regards
Tony

---

### Post by BC59 on 2011-12-03
Then search in your Applications....I don't remember exactly how it was in 10.04. Find the application Additional Drivers. Open it put password and wait until to finish searching for recommended drivers. If any, activate (you need internet connection of course) and reboot.

---

### Post by Tonywin on 2011-12-03
Thank you,

I looked at all the Applications, most relevant being Graphics, Sound & video, and Ubuntu software but find no application 'additional drivers'. 
The nearest looked like ALSA, but that is for sound.
Regards
Tony

---

### Post by BC59 on 2011-12-03
Ok I found the command to execute it from a terminal. Open a terminal with CTRL+ALT+T and run the command:

```
 /usr/bin/jockey-gtk
```

Then look if there is a driver to activate

---

### Post by Tonywin on 2011-12-03
Thank tried that,
It said no proprietary drivers are in use on this system...

I am now wondering about a new re-installation.
I am unsure of the previous history...
When I installed the dual boot system Win xp pro, then I think ubuntu 10.4 I did so on another PC, not mine, with a DELL 23" screen. It worked there.
Then moved the PC to my system, which has a KVM switch to toggle one screen for several systems. Hence the system setup IF I RECALL correctly, may have been done on another screen.
Is that any help?

---

### Post by BC59 on 2011-12-03
So you mean there is nothing on the screen there is no driver shawn like in mine which is attached?

---

### Post by Tonywin on 2011-12-03
I tried another idea.
I loaded up the CD I used for the installation, in trial mode, not install.
It came up with the same results as the first post to this thread. 
Only two screen res's from which to choose.

---

### Post by Tonywin on 2011-12-03
I tried another idea.
I loaded up the CD I used for the installation, in trial mode, not install.
It came up with the same results as the first post to this thread. 
Only two screen res's from which to choose.

Just saw your reply.
Nothing like that, all blank under the message.
Regards
Tony

---

### Post by oldtimer7777 on 2011-12-03
Usually I can configure TV output from with Nvidia server resolution settings. It is really the only way to get the kind of resolution you need for that TV.  You may need to use a previous version of Ubuntu to get this just right.

> **Tonywin said:**
> Thank tried that,
It said no proprietary drivers are in use on this system...

I am now wondering about a new re-installation.
I am unsure of the previous history...
When I installed the dual boot system Win xp pro, then I think ubuntu 10.4 I did so on another PC, not mine, with a DELL 23" screen. It worked there.
Then moved the PC to my system, which has a KVM switch to toggle one screen for several systems. Hence the system setup IF I RECALL correctly, may have been done on another screen.
Is that any help?

---

### Post by Tonywin on 2011-12-03
Thanks, BTW it is a PC monitor, not tv.

Do you mean something like ubuntu 9.04?

I am puzzled, since this [COLOR="Blue"]works[/COLOR] on another screen - Dell, and [COLOR="blue"]works[/COLOR] on this viewsonic under 10.04 lts 32 bit, an older pc.

Is there a file set up in etc/x11 that I could take off the 32 bit system and copy to the 64bit system perhaps?

Tony

---

### Post by matt_symes on 2011-12-03
Hi

> Then moved the PC to my system, which has a KVM switch to toggle one  screen for several systems. Hence the system setup IF I RECALL  correctly, may have been done on another screen.It's possible the KVM switch may be causing you problems as KMS may not be able to read the EDID information from your monitor and set it to the correct native resolution. It would then fall back to fail safe graphics mode of 800x600 and 640x480.

Try connecting directly to your monitor and rebooting the PC. Do you get more screen resolutions ?

Anyway, more information might be useful.

Open a terminal and type

```
sudo lshw -c display
```Enter your password. It will not be echoed to the screen. Post the results back here.

Kind regards

---

### Post by Tonywin on 2011-12-03
Thanks her it is...

tony@tony-desktop2:~$ sudo lshw -c display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
       resources: memory:fe000000-fe3fffff memory:c0000000-cfffffff(prefetchable) ioport:f000(size=64)

---

### Post by matt_symes on 2011-12-03
Hi

> **Tonywin said:**
> Thanks her it is...

tony@tony-desktop2:~$ sudo lshw -c display
  ***-display UNCLAIMED     **
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
       resources: memory:fe000000-fe3fffff memory:c0000000-cfffffff(prefetchable) ioport:f000(size=64)

You have no graphics driver installed for your display. Not quite sure what card you have.

What's the output of 

```
lspci -nn | grep -i vga
```

Are you directly connected to the monitor ?

Kind regards

---

### Post by Tonywin on 2011-12-03
p { margin-bottom: 0.21cm; }  

 Thanks again
 re:
 

 It's possible the KVM switch may be causing you problems as KMS may not be able to read the EDID information from your monitor and set it to the correct native resolution. It would then fall back to fail safe graphics mode of 800x600 and 640x480.

Try connecting directly to your monitor and rebooting the PC. Do you get more screen resolutions ?


 

 Just tried this also,no changes...
 Tony

---

### Post by Tonywin on 2011-12-03
directly connected to pc

mboard is asus p8z68 - v
self build

p { margin-bottom: 0.21cm; }  

 Thanks again
 re:
 

 It's possible the KVM switch may be causing you problems as KMS may not be able to read the EDID information from your monitor and set it to the correct native resolution. It would then fall back to fail safe graphics mode of 800x600 and 640x480.

Try connecting directly to your monitor and rebooting the PC. Do you get more screen resolutions ?


 

 Just tried this also,no changes...
 Tony

---

### Post by Tonywin on 2011-12-03
lspci -nn | grep -i vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0112] (rev 09)

ps asus mb p8z68-V LE has Intel z68 chipset support on disk

---

### Post by matt_symes on 2011-12-03
Hi

As far as i can make out you should just need the standard i915 driver. Let's try to fnd out what's going on.

Can you post the output of (you may not have this file)

```
cat /etc/X11/xorg.conf
```and also

```
cat /var/log/Xorg.0.log
```Please use code tag as it will make the results much easier to read. 

To use code tags press the #key above where you type your post or wrap the text like this

[noparse]```
text
```[/noparse] 

to produce output like this ```
text
```Kind regards

---

### Post by Tonywin on 2011-12-03
> **matt_symes said:**
> Hi

As far as i can make out you should just need the standard i915 driver. Let's try to fnd out what's going on.

Can you post the output of (you may not have this file)

```
cat /etc/X11/xorg.conf
```and also

```
cat /var/log/Xorg.0.log
```Please use code tag as it will make the results much easier to read. 

To use code tags press the #key above where you type your post or wrap the text like this

[noparse]```
text
```[/noparse] 

to produce output like this ```
text
```Kind regards


The first result is 

  	 	 	 	p { margin-bottom: 0.21cm; }  Here is the result for a list … ls of X11
 


 tony@tony-desktop2:/etc/X11$ ls 
 app-defaults             fonts    xinit   Xreset.d    Xsession.d 
 cursors                  rgb.txt  xkb     Xresources  Xsession.options 
 default-display-manager  X        Xreset  Xsession    Xwrapper.config 
 I don't see any xorg.conf, but I do see a similar one on the older 32 bt sys..
 It is xorg.conf.failsafe, and contains merely text for filling in code.


The second produces a massive text of some 6 pages. How do I save that to a file, it is to large to cat | more and segment, or is there a piece you want please.
Tony

---

### Post by matt_symes on 2011-12-03
Hi

No problem about the first file. I was not sure if it would be there.

For the second file do this.

Press Alt + F2 together and type

```
gedit /var/log/Xorg.0.log
```Copy and paste all the text from that file into your next post between code tags.

Kind regards

---

### Post by Tonywin on 2011-12-03
here it is, a bit large..

```
text


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux tony-desktop2 2.6.32-36-generic #79-Ubuntu SMP Tue Nov 8 22:29:53 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-36-generic root=UUID=56f893e7-8ea1-45e1-88a8-545784f822cb ro quiet splash
Build Date: 20 October 2011  03:03:02PM
xorg-server 2:1.7.6-2ubuntu7.10 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec  3 21:40:37 2011
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
(II) Loader magic: 0x7cb840
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0112:1043:844d Intel Corporation rev 9, Mem @ 0xfe000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
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
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.9.1
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65472 kB
(II) VESA(0): VESA VBE OEM: Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R) Sandybridge/Ivybridge Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): VESA VBE PanelID invalid
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 161 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 162 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 163 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 164 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 165 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 166 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 167 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 168 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 169 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16a (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16b (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16c (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16d (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16e (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16f (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 170 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 171 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 13c (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 1920
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 22
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1920
    BnkNumberOfImagePages: 22
    LinNumberOfImagePages: 22
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 14d (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 3840
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3840
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 15c (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 7680
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 5
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 7680
    BnkNumberOfImagePages: 5
    LinNumberOfImagePages: 5
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 13a (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 1600
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 33
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 33
    LinNumberOfImagePages: 33
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 14b (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 3200
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 16
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 16
    LinNumberOfImagePages: 16
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 15a (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 6400
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 7
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 6400
    BnkNumberOfImagePages: 7
    LinNumberOfImagePages: 7
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 107 (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 1280
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 50
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 50
    LinNumberOfImagePages: 50
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 11a (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 2560
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 24
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 24
    LinNumberOfImagePages: 24
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 11b (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 5120
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 5120
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 105 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 1024
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 84
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1024
    BnkNumberOfImagePages: 84
    LinNumberOfImagePages: 84
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 117 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 2048
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 41
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2048
    BnkNumberOfImagePages: 41
    LinNumberOfImagePages: 41
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 118 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 4096
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 20
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 4096
    BnkNumberOfImagePages: 20
    LinNumberOfImagePages: 20
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
*Mode: 112 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 2560
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 52
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 52
    LinNumberOfImagePages: 52
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 114 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 1600
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 67
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 67
    LinNumberOfImagePages: 67
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 115 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 3200
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 33
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 33
    LinNumberOfImagePages: 33
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 101 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 203
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 203
    LinNumberOfImagePages: 203
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 103 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 832
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 126
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 832
    BnkNumberOfImagePages: 126
    LinNumberOfImagePages: 126
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 111 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 101
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 101
    LinNumberOfImagePages: 101
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 17d (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 1024
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 84
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1024
    BnkNumberOfImagePages: 84
    LinNumberOfImagePages: 84
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 17e (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 2048
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 41
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2048
    BnkNumberOfImagePages: 41
    LinNumberOfImagePages: 41
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 17f (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007ebb
    BytesPerScanline: 4096
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 20
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 4096
    BnkNumberOfImagePages: 20
    LinNumberOfImagePages: 20
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 1023 64KB banks (65472kB)
(II) VESA(0): <default monitor>: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1920x1440" (no mode of this name)
(II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter...
(II) VESA(0): <default monitor>: Using hsync range of 31.50-37.90 kHz
(II) VESA(0): <default monitor>: Using vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1920x1440" (hsync out of range)
(II) VESA(0): Not using built-in mode "1600x1200" (hsync out of range)
(II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "intel"
(II) Unloading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65472 kB
(II) VESA(0): VESA VBE OEM: Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R) Sandybridge/Ivybridge Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): virtual address = 0x7fbb3d9c0000,
    physical address = 0xc0000000, size = 67043328
(II) VESA(0): Setting up VESA Mode 0x115 (800x600)
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(==) VESA(0): DPMS enabled
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
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
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
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device HOLTEK Wireless USB Device (/dev/input/event3)
(**) HOLTEK Wireless USB Device: Applying InputClass "evdev keyboard catchall"
(**) HOLTEK Wireless USB Device: always reports core events
(**) HOLTEK Wireless USB Device: Device: "/dev/input/event3"
(II) HOLTEK Wireless USB Device: Found keys
(II) HOLTEK Wireless USB Device: Configuring as keyboard
(II) XINPUT: Adding extended input device "HOLTEK Wireless USB Device" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device HOLTEK Wireless USB Device (/dev/input/event4)
(**) HOLTEK Wireless USB Device: Applying InputClass "evdev pointer catchall"
(**) HOLTEK Wireless USB Device: Applying InputClass "evdev keyboard catchall"
(**) HOLTEK Wireless USB Device: always reports core events
(**) HOLTEK Wireless USB Device: Device: "/dev/input/event4"
(II) HOLTEK Wireless USB Device: Found 9 mouse buttons
(II) HOLTEK Wireless USB Device: Found scroll wheel(s)
(II) HOLTEK Wireless USB Device: Found relative axes
(II) HOLTEK Wireless USB Device: Found x and y relative axes
(II) HOLTEK Wireless USB Device: Found keys
(II) HOLTEK Wireless USB Device: Configuring as mouse
(II) HOLTEK Wireless USB Device: Configuring as keyboard
(**) HOLTEK Wireless USB Device: YAxisMapping: buttons 4 and 5
(**) HOLTEK Wireless USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HOLTEK Wireless USB Device" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) HOLTEK Wireless USB Device: initialized for relative axes.
(II) config/udev: Adding input device HOLTEK Wireless USB Device (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
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
(II) XKB: reuse xkmfile /var/lib/xkb/server-CD78C244518B4EB50E0BCCC8CF875AD1B52C1720.xkm
(II) config/udev: Adding input device Cypress Cypress PS/2 Keyboard - PS/2 Mouse (/dev/input/event6)
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Applying InputClass "evdev pointer catchall"
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: always reports core events
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Device: "/dev/input/event6"
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Found 3 mouse buttons
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Found scroll wheel(s)
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Found relative axes
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Found x and y relative axes
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Configuring as mouse
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Cypress Cypress PS/2 Keyboard - PS/2 Mouse" (type: MOUSE)
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: initialized for relative axes.
(II) config/udev: Adding input device Cypress Cypress PS/2 Keyboard - PS/2 Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Cypress Cypress PS/2 Keyboard - PS/2 Mouse (/dev/input/event5)
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Applying InputClass "evdev keyboard catchall"
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: always reports core events
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Device: "/dev/input/event5"
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Found keys
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Configuring as keyboard
(II) XINPUT: Adding extended input device "Cypress Cypress PS/2 Keyboard - PS/2 Mouse" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) XKB: reuse xkmfile /var/lib/xkb/server-CD78C244518B4EB50E0BCCC8CF875AD1B52C1720.xkm
(II) config/udev: removing device Cypress Cypress PS/2 Keyboard - PS/2 Mouse
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Close
(II) UnloadModule: "evdev"
(II) config/udev: removing device Cypress Cypress PS/2 Keyboard - PS/2 Mouse
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Close
(II) UnloadModule: "evdev"
(II) XKB: reuse xkmfile /var/lib/xkb/server-CD78C244518B4EB50E0BCCC8CF875AD1B52C1720.xkm
(II) config/udev: Adding input device Cypress Cypress PS/2 Keyboard - PS/2 Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Cypress Cypress PS/2 Keyboard - PS/2 Mouse (/dev/input/event6)
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Applying InputClass "evdev pointer catchall"
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: always reports core events
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Device: "/dev/input/event6"
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Found 3 mouse buttons
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Found scroll wheel(s)
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Found relative axes
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Found x and y relative axes
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Configuring as mouse
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Cypress Cypress PS/2 Keyboard - PS/2 Mouse" (type: MOUSE)
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: initialized for relative axes.
(II) config/udev: Adding input device Cypress Cypress PS/2 Keyboard - PS/2 Mouse (/dev/input/event5)
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Applying InputClass "evdev keyboard catchall"
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: always reports core events
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Device: "/dev/input/event5"
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Found keys
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Configuring as keyboard
(II) XINPUT: Adding extended input device "Cypress Cypress PS/2 Keyboard - PS/2 Mouse" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) XKB: reuse xkmfile /var/lib/xkb/server-CD78C244518B4EB50E0BCCC8CF875AD1B52C1720.xkm
(II) config/udev: removing device Cypress Cypress PS/2 Keyboard - PS/2 Mouse
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Close
(II) UnloadModule: "evdev"
(II) config/udev: removing device Cypress Cypress PS/2 Keyboard - PS/2 Mouse
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Close
(II) UnloadModule: "evdev"
(II) config/udev: Adding input device Cypress Cypress PS/2 Keyboard - PS/2 Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Cypress Cypress PS/2 Keyboard - PS/2 Mouse (/dev/input/event6)
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Applying InputClass "evdev pointer catchall"
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: always reports core events
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Device: "/dev/input/event6"
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Found 3 mouse buttons
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Found scroll wheel(s)
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Found relative axes
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Found x and y relative axes
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Configuring as mouse
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Cypress Cypress PS/2 Keyboard - PS/2 Mouse" (type: MOUSE)
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: initialized for relative axes.
(II) config/udev: Adding input device Cypress Cypress PS/2 Keyboard - PS/2 Mouse (/dev/input/event5)
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Applying InputClass "evdev keyboard catchall"
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: always reports core events
(**) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Device: "/dev/input/event5"
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Found keys
(II) Cypress Cypress PS/2 Keyboard - PS/2 Mouse: Configuring as keyboard
(II) XINPUT: Adding extended input device "Cypress Cypress PS/2 Keyboard - PS/2 Mouse" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) XKB: reuse xkmfile /var/lib/xkb/server-CD78C244518B4EB50E0BCCC8CF875AD1B52C1720.xkm


``` 
I hope I got it right.
Tony

---

### Post by Tonywin on 2011-12-03
Hi to all,
I am unsure where you are but in the UK it is now closing on 11.30 pm. so I am turning in.
I can't thank you enough for the enormous efforts and contributions put in to help resolve this. It is a real marker for pro bono help among the community. Thank you, Thank you, I shall return midday tomorrow.
Thank you again and goodnight.
Tony

---

### Post by BicyclerBoy on 2011-12-03
Your kernel is to old to recognize the sandybridge iCPU/GPU SNA.
You then end up with the vesa driver & this maxes out at 1280..

You need a kernel from natty or later to get the best from SNA..

If you want to stay at 10.04.3 Lucid you can use a natty backports kernel package & also use the xorg-edgers ppa for the intel driver..

The only other solution is to use 11.04 or 11.10..

---

### Post by matt_symes on 2011-12-03
Hi

> **BicyclerBoy said:**
> Your kernel is to old to recognize the sandybridge iCPU/GPU SNA.
You then end up with the vesa driver & this maxes out at 1280..

You need a kernel from natty or later to get the best from SNA..

If you want to stay at 10.04.3 Lucid you can use a natty backports kernel package & also use the xorg-edgers ppa for the intel driver..

The only other solution is to use 11.04 or 11.10..

Yes. This is looking bang on the money.

Kind regards

---

### Post by Tonywin on 2011-12-04
Gentlemen, 
Thank you for your advice, I shall take it, since this is a new installation.
This may take a while, but I shall return and confirm your advice worked as expected, and saves me channelling down a somewhat dead end with 10.04 on 64bit, I am happy to remain with 10.04 on the 32 bit.

One question please.
On the download site, there is a comment that 11.04 is in beta, but also 11.10 on another link is the same beta stage.
What would be the preferred choice for LTS on either please?
Regards.
Tony

---

### Post by Tonywin on 2011-12-04
Hi,
I downloaded 11.10 and tested it as a CD, it showed 1024, and I then installed in side by side with Windows.
On rebooting, I got no dual boot option, just a windows boot. I can see the partitions from Windows. Any help please, can I fix this with the cd, or perhaps try 11.04?
Regards.
Tony

---

### Post by matt_symes on 2011-12-04
Hi

> **Tonywin said:**
> Hi,
I downloaded 11.10 and tested it as a CD, it showed 1024, and I then installed in side by side with Windows.

Not quite sure what you mean by 1024 (resolution ?).

> 
On rebooting, I got no dual boot option, just a windows boot. I can see the partitions from Windows. Any help please, can I fix this with the cd, or perhaps try 11.04?
Regards.
TonyIf you look in my signature you will see a link to the boot info script. Please run this script from a liveCD and post the results back here.

The instructions are on the website.

It will give us an idea of what has happened to your system after you installed 11.10.

Kind regards

---

### Post by Tonywin on 2011-12-04
p { margin-bottom: 0.21cm; }  Hi, Matt,
 Thank you,  
 I decided to revert to 11.04 ans see if that works..
 **It does! And I have now a dual boot, plus 4 screen resolutions, up to 1024. I was going to post this as [COLOR=Red]superb[/COLOR], as soon as I mastered the new feel which I find awkward and a learning curve**.
 For example I downloaded vbox to set up XP, and ran set up, but cannot for the life of me find how to launch it, it appears I must do so from a terminal. All new to me.
 I wanted my old desktop if I can get it, and wonder if that is what the difference between some other desktop and GNOME?
 I like the top and bottom panels, to load programs to, and launch from there. This is hampering my learning since it is not my preferred option. Do I have the wrong login windows? If that is what it is called/.
 

 Regards, Tony, and well on the way to success now, I think.

---

### Post by Tonywin on 2011-12-04
I managed it,
Set back to classic, now using my familiar territory GNOME.
When launching vbox, it goes to a terminal then shows the normal screen. I guess that is because I was using a different trm, so will uninstall and reinsall vbox.

Gentleman, I cannot thank you enough....
Save my life with the anxieties.

THANK YOU, THANK YOU, THANK YOU, THANK YOU,

---

### Post by Tonywin on 2011-12-05
Small question please to conclude another matter mentioned.
When I loaded the 11.04, and installed vbox under the standard login screen, not gnome classic, it stated vbox must be run** from a terminal.**
I switched to classic gnome mode, re-installed vbox, and it loads, but shows a terminal screen first before loading itself, its minor, and will be messy.
Is there any quick fix for this please. or the long way is to re-install the lot, now I am happy with the screen resolved?
Kind regards, and thanks once again.
Tony

---

### Post by matt_symes on 2011-12-06
Hi

I have not used virtual box under 11.04 so i may not be much help. I am migrating to qemu-kvm on my server.

What happens if you run virtual box from the terminal ? Do you get an extra pop up terminal ?

Have a look at what the laucher is calling. That may give you some clues as to why it is displaying a terminal first (maybe it's setting some environmental variables or something).

Kind regards

---

### Post by Tonywin on 2011-12-06
Hi, MATT,

I tried several ways for a **get around..**
I upgraded to 11.10, but again found I was **locked out** of GNOME, which I could not believe, unable to find a 'login screen option'.
Then I simply re-installed 11.04, and all worked out fine... I have 1024 and 800 res only, but that is all I want.
I dread upgrading to 11.10, it is very unclear as to how one can revert to GNOME.

AGAIN, I thank you so much. The system is making good progress now, and the boot disk, an ssd drive is nice and fast, due to be backed up soonest.
**DELIGHTED.**
Regards.
PS..
I see you are in the uk...
**IF it helps you **in any way, I have an OLD but free web site, on how power corrupts and the powerful have been confronted with *hi caught* : court cases, by me, and backed down. ALL free, and due to be upgraded... if it helps.
Either google **logic law **, usually nr one in 200 mill. 
or url    	 	 	 	p { margin-bottom: 0.21cm; }a:link {*   [www.logiclaw.co.uk]("http://www.logiclaw.co.uk/")
 

[COLOR=Blue]**Tony**[/COLOR]

---

### Post by matt_symes on 2011-12-06
Hi

Thanks for the link. I will check it out :)

Kind regards

---

### Post by BicyclerBoy on 2011-12-06
To get gnome/classic desktop login back on 11.10 etc install:
gnome-session-fallback

This thread started as 11.10 but turned into 12.04..
[http://ubuntuforums.org/showthread.php?t=1873765](http://ubuntuforums.org/showthread.php?t=1873765)

---

### Post by Tonywin on 2011-12-06
> **BicyclerBoy said:**
> To get gnome/classic desktop login back on 11.10 etc install:
gnome-session-fallback

This thread started as 11.10 but turned into 12.04..
[http://ubuntuforums.org/showthread.php?t=1873765](http://ubuntuforums.org/showthread.php?t=1873765)


AH......... that's very useful, since I was confounded. Thanks, I will save that info along with the four pages, for when the time comes, now with more confidence..

**SOLVED........**

Thanks, with kind regards.
Tony

---


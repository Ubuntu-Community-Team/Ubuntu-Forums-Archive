---
title: "Trying to configure xorg.conf file in Lucid..."
date: 2010-06-08
forum: General Help
---

### Post by rainbowagent7 on 2010-06-08
Hi kids. All I need to do is get my screen resolution to 1024x768, I can  currently only get 800x600 and that's unacceptable for school. I  created an xorg.conf file in Lucid and it does in fact refer to and use  it. I'm not a noob but am still fairly new to Ubuntu/Linux and have once  again come to the point where I need help, what led me to believe that  is when I looked in the mirror and noticed smoke slowly rolling out of  my ears! After replacing some of that smoke with a cigarette I decided  to make this thread. As I said, I created the xorg.conf.new file with:
```
sudo  Xorg -configure
``` from recovery mode.
And then moved it to its  proper place with:```
cp /home/william/xorg.conf.new  /etc/X11/xorg.conf
```And that nested it right where it needs to be. X  does in fact use it as confirmed by my Xorg.0.log.
Now I have an  xorg.conf file, but am quickly becoming overwhelmed with information as  to what to do. I've tried to create mode lines with xrandr, which gave  me new settings, but I was unable to use them. Obviously the EDID info.  is not being read because there is no mention of clock speed, Vsync or  Hsync in my Xorg.0.log either. Please help as I have tried many things  and really don't have time to spend all day at my computer, at least not  with this issue. I'm in school and have to focus primarily on that  right now. Any help would be tremendously appreciated, I will give what  info I know is relevant starting with my monitor specs:

Dynex  DX-LCDTV19
vertical resolution: 720 p
aspect ratio: 16:10
screen  refresh rate: 60hz
comb filter: 3D/YC digital
max  resolution:1440x900
screen size: 19"
contrast ratio: 800:1
horizontal  scan rate: ? (I have searched everywhere for this to no avail)
vertical  synchronizaton rate: ? (same as above)

/var/log/Xorg.0.log:

[HTML]X.Org  X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11,  Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current  Operating System: Linux RAINBOWDATASTORAGE 2.6.32-22-generic #36-Ubuntu  SMP Thu Jun 3 22:02:19 UTC 2010 i686
Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic  root=UUID=7e58eae4-58c4-4f51-86a6-6d217d5efbbb ro quiet splash
Build  Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce  Harrington <bryce@ubuntu.com>) 
Current version of pixman:  0.16.4
    Before reporting problems, check http://wiki.x.org
     to make sure that you have the latest version.
Markers: (--) probed,  (**) from config file, (==) default setting,
    (++) from command  line, (!!) notice, (II) informational,
    (WW) warning, (EE) error,  (NI) not implemented, (??) unknown.
(==) Log file:  "/var/log/Xorg.0.log", Time: Tue Jun  8 15:21:36 2010
(==) Using  config file: "/etc/X11/xorg.conf"
(==) Using config directory:  "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "X.org Configured"
(**)  |-->Screen "Screen0" (0)
(**) |   |-->Monitor "<default  monitor>"
(**) |   |-->Device "Card0"
(==) No monitor  specified for screen "Screen0".
    Using a default monitor  configuration.
(**) |-->Input Device "Mouse0"
(**) |-->Input  Device "Keyboard0"
(==) Automatically adding devices
(==)  Automatically enabling devices
(WW) The directory  "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted  from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic"  does not exist.
    Entry deleted from font path.
(**) FontPath  set to:
    /usr/share/fonts/X11/misc,
     /usr/share/fonts/X11/100dpi/:unscaled,
     /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
     /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
     /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins,
     /usr/share/fonts/X11/misc,
     /usr/share/fonts/X11/100dpi/:unscaled,
     /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
     /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
     /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(**)  ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is  on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW)  Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic:  0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation:  0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
     X.Org Server Extension : 2.0
(++) using VT number 7

(--)  PCI:*(0:1:0:0) 1002:5046:1002:0014 ATI Technologies Inc Rage 128 PF/PRO  AGP 4x TMDS rev 0, Mem @ 0xc8000000/67108864, 0xcfefc000/16384, I/O @  0x0000b800/256, BIOS @ 0x????????/131072
(II) Open ACPI successful  (/var/run/acpid.socket)
(II) "extmod" will be loaded. This was  enabled by default and also specified in the config file.
(II) "dbe"  will be loaded. This was enabled by default and also specified in the  config file.
(II) "glx" will be loaded. This was enabled by default  and also specified in the config file.
(II) "record" will be loaded.  This was enabled by default and also specified in the config file.
(II)  "dri" will be loaded. This was enabled by default and also specified in  the config file.
(II) "dri2" will be loaded. This was enabled by  default and also specified in the config file.
(II) LoadModule:  "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II)  Module record: vendor="X.Org Foundation"
    compiled for 1.7.6,  module version = 1.13.0
    Module class: X.Org Server Extension
     ABI class: X.Org Server Extension, version 2.0
(II) Loading  extension RECORD
(II) LoadModule: "dri"
(II) Loading  /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri:  vendor="X.Org Foundation"
    compiled for 1.7.6, module version =  1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II)  Loading extension XFree86-DRI
(II) LoadModule: "glx"
(II) Loading  /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx:  vendor="X.Org Foundation"
    compiled for 1.7.6, module version =  1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==)  AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dbe"
(II)  Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe:  vendor="X.Org Foundation"
    compiled for 1.7.6, module version =  1.0.0
    Module class: X.Org Server Extension
    ABI class:  X.Org Server Extension, version 2.0
(II) Loading extension  DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading  /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod:  vendor="X.Org Foundation"
    compiled for 1.7.6, module version =  1.0.0
    Module class: X.Org Server Extension
    ABI class:  X.Org Server Extension, version 2.0
(II) Loading extension  MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II)  Loading extension XFree86-DGA
(II) Loading extension DPMS
(II)  Loading extension XVideo
(II) Loading extension  XVideo-MotionCompensation
(II) Loading extension X-Resource
(II)  LoadModule: "dri2"
(II) Loading  /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2:  vendor="X.Org Foundation"
    compiled for 1.7.6, module version =  1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II)  Loading extension DRI2
(II) LoadModule: "r128"
(II) Loading  /usr/lib/xorg/modules/drivers/r128_drv.so
(II) Module r128:  vendor="X.Org Foundation"
    compiled for 1.7.6, module version =  6.8.1
    Module class: X.Org Video Driver
    ABI class: X.Org  Video Driver, version 6.0
(II) R128: Driver for ATI Rage 128  chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128  Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage  128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (PCI/AGP), ATI  Rage 128 Pro GL PB (PCI/AGP),
    ATI Rage 128 Pro GL PC (PCI/AGP),  ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (PCI/AGP),  ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (PCI/AGP),  ATI Rage 128 Pro VR PH (PCI/AGP),
    ATI Rage 128 Pro VR PI  (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
    ATI Rage 128 Pro VR  PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
    ATI Rage 128 Pro  VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
    ATI Rage 128  Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128  Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128  Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
    ATI Rage  128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
    ATI  Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
     ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128  RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI  Rage 128 4X SE (PCI/AGP),
    ATI Rage 128 4X SF (PCI/AGP), ATI Rage  128 4X SG (PCI/AGP),
    ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128  4X SK (PCI/AGP),
    ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM  (AGP),
    ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF  (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR  (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA  TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
(II) Primary  Device is: PCI 01@00:00:0
(II) R128(0): PCI bus 1 card 0 func 0
(==)  R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth  = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default  visual is TrueColor
(II) Loading sub module "vgahw"
(II)  LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II)  Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.6,  module version = 0.1.0
    ABI class: X.Org Video Driver, version 6.0
(II)  R128(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is  0x0000
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits  per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II)  LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II)  Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6,  module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II)  R128(0): initializing int10
(II) R128(0): Primary V_BIOS segment is:  0xc000
(--) R128(0): Chipset: "ATI Rage 128 Pro GL PF (AGP)" (ChipID  = 0x5046)
(--) R128(0): Linear framebuffer at 0xc8000000
(--)  R128(0): MMIO registers at 0xcfefc000
(--) R128(0): VideoRAM: 32768  kByte (64-bit SDR SGRAM 1:1)
(**) R128(0): Using external CRT for  display
(II) R128(0): Primary Display == Type 3
(WW) R128(0):  Can't determine panel dimensions, and none specified.
    Disabling  programming of FP registers.
(II) R128(0): PLL parameters: rf=2700  rd=60 min=12500 max=40000; xclk=14000
(II) Loading sub module "ddc"
(II)  LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading  sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading  /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org  Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI  class: X.Org Video Driver, version 6.0
(II) R128(0): VESA BIOS  detected
(II) R128(0): VESA VBE Version 2.0
(II) R128(0): VESA VBE  Total Mem: 32768 kB
(II) R128(0): VESA VBE OEM: ATI RAGE128
(II)  R128(0): VESA VBE OEM Software Rev: 1.0
(II) R128(0): VESA VBE OEM  Vendor: ATI Technologies Inc.
(II) R128(0): VESA VBE OEM Product:  R128
(II) R128(0): VESA VBE OEM Product Rev: 01.00
(II) Loading  sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already  built-in
(II) R128(0): VESA VBE DDC supported
(II) R128(0): VESA  VBE DDC Level none
(II) R128(0): VESA VBE DDC transfer in appr. 2  sec.
(II) R128(0): VESA VBE DDC read failed
(==) R128(0): Using  gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "i2c"
(II)  LoadModule: "i2c"
(II) Module "i2c" already built-in
(II)  R128(0): I2C bus "DDC" initialized.
(II) R128(0): I2C device  "DDC:ddc2" registered at address 0xA0.
(EE) R128(0): No DFP detected
(II)  R128(0): <default monitor>: Using default hsync range of  31.50-37.90 kHz
(II) R128(0): <default monitor>: Using default  vrefresh range of 50.00-70.00 Hz
(WW) R128(0): Unable to estimate  virtual size
(II) R128(0): Clock range:  12.50 to 400.00 MHz
(II)  R128(0): Not using default mode "640x350" (vrefresh out of range)
(II)  R128(0): Not using default mode "320x175" (vrefresh out of range)
(II)  R128(0): Not using default mode "640x400" (vrefresh out of range)
(II)  R128(0): Not using default mode "320x200" (vrefresh out of range)
(II)  R128(0): Not using default mode "720x400" (vrefresh out of range)
(II)  R128(0): Not using default mode "360x200" (vrefresh out of range)
(II)  R128(0): Not using default mode "640x480" (vrefresh out of range)
(II)  R128(0): Not using default mode "320x240" (vrefresh out of range)
(II)  R128(0): Not using default mode "640x480" (vrefresh out of range)
(II)  R128(0): Not using default mode "320x240" (vrefresh out of range)
(II)  R128(0): Not using default mode "640x480" (hsync out of range)
(II)  R128(0): Not using default mode "320x240" (hsync out of range)
(II)  R128(0): Not using default mode "800x600" (hsync out of range)
(II)  R128(0): Not using default mode "400x300" (hsync out of range)
(II)  R128(0): Not using default mode "800x600" (hsync out of range)
(II)  R128(0): Not using default mode "400x300" (hsync out of range)
(II)  R128(0): Not using default mode "800x600" (hsync out of range)
(II)  R128(0): Not using default mode "400x300" (hsync out of range)
(II)  R128(0): Not using default mode "1024x768" (vrefresh out of range)
(II)  R128(0): Not using default mode "512x384" (vrefresh out of range)
(II)  R128(0): Not using default mode "1024x768" (hsync out of range)
(II)  R128(0): Not using default mode "512x384" (hsync out of range)
(II)  R128(0): Not using default mode "1024x768" (hsync out of range)
(II)  R128(0): Not using default mode "512x384" (hsync out of range)
(II)  R128(0): Not using default mode "1024x768" (hsync out of range)
(II)  R128(0): Not using default mode "512x384" (hsync out of range)
(II)  R128(0): Not using default mode "1024x768" (hsync out of range)
(II)  R128(0): Not using default mode "512x384" (hsync out of range)
(II)  R128(0): Not using default mode "1152x864" (hsync out of range)
(II)  R128(0): Not using default mode "576x432" (hsync out of range)
(II)  R128(0): Not using default mode "1280x960" (hsync out of range)
(II)  R128(0): Not using default mode "640x480" (hsync out of range)
(II)  R128(0): Not using default mode "1280x960" (hsync out of range)
(II)  R128(0): Not using default mode "640x480" (hsync out of range)
(II)  R128(0): Not using default mode "1280x1024" (hsync out of range)
(II)  R128(0): Not using default mode "640x512" (hsync out of range)
(II)  R128(0): Not using default mode "1280x1024" (hsync out of range)
(II)  R128(0): Not using default mode "640x512" (hsync out of range)
(II)  R128(0): Not using default mode "1280x1024" (hsync out of range)
(II)  R128(0): Not using default mode "640x512" (hsync out of range)
(II)  R128(0): Not using default mode "1600x1200" (hsync out of range)
(II)  R128(0): Not using default mode "800x600" (hsync out of range)
(II)  R128(0): Not using default mode "1600x1200" (hsync out of range)
(II)  R128(0): Not using default mode "800x600" (hsync out of range)
(II)  R128(0): Not using default mode "1600x1200" (hsync out of range)
(II)  R128(0): Not using default mode "800x600" (hsync out of range)
(II)  R128(0): Not using default mode "1600x1200" (hsync out of range)
(II)  R128(0): Not using default mode "800x600" (hsync out of range)
(II)  R128(0): Not using default mode "1600x1200" (hsync out of range)
(II)  R128(0): Not using default mode "800x600" (hsync out of range)
(II)  R128(0): Not using default mode "1792x1344" (hsync out of range)
(II)  R128(0): Not using default mode "896x672" (hsync out of range)
(II)  R128(0): Not using default mode "1792x1344" (hsync out of range)
(II)  R128(0): Not using default mode "896x672" (hsync out of range)
(II)  R128(0): Not using default mode "1856x1392" (hsync out of range)
(II)  R128(0): Not using default mode "928x696" (hsync out of range)
(II)  R128(0): Not using default mode "1856x1392" (hsync out of range)
(II)  R128(0): Not using default mode "928x696" (hsync out of range)
(II)  R128(0): Not using default mode "1920x1440" (hsync out of range)
(II)  R128(0): Not using default mode "960x720" (hsync out of range)
(II)  R128(0): Not using default mode "1920x1440" (hsync out of range)
(II)  R128(0): Not using default mode "960x720" (hsync out of range)
(II)  R128(0): Not using default mode "832x624" (hsync out of range)
(II)  R128(0): Not using default mode "416x312" (hsync out of range)
(II)  R128(0): Not using default mode "1152x864" (hsync out of range)
(II)  R128(0): Not using default mode "576x432" (hsync out of range)
(II)  R128(0): Not using default mode "1152x864" (hsync out of range)
(II)  R128(0): Not using default mode "576x432" (hsync out of range)
(II)  R128(0): Not using default mode "1152x864" (hsync out of range)
(II)  R128(0): Not using default mode "576x432" (hsync out of range)
(II)  R128(0): Not using default mode "1152x864" (hsync out of range)
(II)  R128(0): Not using default mode "576x432" (hsync out of range)
(II)  R128(0): Not using default mode "1152x864" (hsync out of range)
(II)  R128(0): Not using default mode "576x432" (hsync out of range)
(II)  R128(0): Not using default mode "1152x864" (hsync out of range)
(II)  R128(0): Not using default mode "576x432" (hsync out of range)
(II)  R128(0): Not using default mode "1360x768" (hsync out of range)
(II)  R128(0): Not using default mode "680x384" (hsync out of range)
(II)  R128(0): Not using default mode "1360x768" (hsync out of range)
(II)  R128(0): Not using default mode "680x384" (hsync out of range)
(II)  R128(0): Not using default mode "1400x1050" (hsync out of range)
(II)  R128(0): Not using default mode "700x525" (hsync out of range)
(II)  R128(0): Not using default mode "1400x1050" (hsync out of range)
(II)  R128(0): Not using default mode "700x525" (hsync out of range)
(II)  R128(0): Not using default mode "1400x1050" (hsync out of range)
(II)  R128(0): Not using default mode "700x525" (hsync out of range)
(II)  R128(0): Not using default mode "1400x1050" (hsync out of range)
(II)  R128(0): Not using default mode "700x525" (hsync out of range)
(II)  R128(0): Not using default mode "1440x900" (hsync out of range)
(II)  R128(0): Not using default mode "720x450" (hsync out of range)
(II)  R128(0): Not using default mode "1600x1024" (hsync out of range)
(II)  R128(0): Not using default mode "800x512" (hsync out of range)
(II)  R128(0): Not using default mode "1680x1050" (hsync out of range)
(II)  R128(0): Not using default mode "840x525" (hsync out of range)
(II)  R128(0): Not using default mode "1680x1050" (hsync out of range)
(II)  R128(0): Not using default mode "840x525" (hsync out of range)
(II)  R128(0): Not using default mode "1680x1050" (hsync out of range)
(II)  R128(0): Not using default mode "840x525" (hsync out of range)
(II)  R128(0): Not using default mode "1680x1050" (hsync out of range)
(II)  R128(0): Not using default mode "840x525" (hsync out of range)
(II)  R128(0): Not using default mode "1680x1050" (hsync out of range)
(II)  R128(0): Not using default mode "840x525" (hsync out of range)
(II)  R128(0): Not using default mode "1920x1080" (hsync out of range)
(II)  R128(0): Not using default mode "960x540" (hsync out of range)
(II)  R128(0): Not using default mode "1920x1200" (hsync out of range)
(II)  R128(0): Not using default mode "960x600" (hsync out of range)
(II)  R128(0): Not using default mode "1920x1440" (hsync out of range)
(II)  R128(0): Not using default mode "960x720" (hsync out of range)
(II)  R128(0): Not using default mode "2048x1536" (hsync out of range)
(II)  R128(0): Not using default mode "1024x768" (hsync out of range)
(II)  R128(0): Not using default mode "2048x1536" (hsync out of range)
(II)  R128(0): Not using default mode "1024x768" (hsync out of range)
(II)  R128(0): Not using default mode "2048x1536" (hsync out of range)
(II)  R128(0): Not using default mode "1024x768" (hsync out of range)
(--)  R128(0): Virtual size is 800x600 (pitch 800)
(**) R128(0): *Default  mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) R128(0): Modeline  "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync  (37.9 kHz)
(**) R128(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz,  56.2 Hz
(II) R128(0): Modeline "800x600"x56.2   36.00  800 824 896  1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) R128(0): *Default  mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) R128(0): Modeline  "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync  (31.5 kHz)
(**) R128(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz,  60.3 Hz (D)
(II) R128(0): Modeline "400x300"x60.3   20.00  400 420  484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**)  R128(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II)  R128(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301  312 doublescan +hsync +vsync (35.2 kHz)
(**) R128(0): *Default mode  "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) R128(0): Modeline  "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan  -hsync -vsync (31.5 kHz)
(==) R128(0): DPI set to (96, 96)
(II)  Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading  /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org  Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI  class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module  "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already  built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II)  Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa:  vendor="X.Org Foundation"
    compiled for 1.7.6, module version =  1.2.1
    ABI class: X.Org Video Driver, version 6.0
(II) Loading  sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading  /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb:  vendor="X.Org Foundation"
    compiled for 1.7.6, module version =  1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II)  R128(0): Page flipping disabled
(!!) R128(0): For information on  using the multimedia capabilities
    of this adapter, please see  http://gatos.sf.net.
(--) Depth 24 pixmap format is 32 bpp
drmOpenDevice:  node name is /dev/dri/card0
drmOpenDevice: node name is  /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice:  node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid:  drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports  pci:0000:01:00.0
(II) [drm] loaded kernel module for "r128" driver.
(II)  [drm] DRM interface version 1.3
(II) [drm] DRM open master  succeeded.
(II) R128(0): [drm] Using the DRM lock SAREA also for  drawables.
(II) R128(0): [drm] framebuffer handle = 0xc8000000
(II)  R128(0): [drm] added 1 reserved context for kernel
(II) R128(0): X  context handle = 0x1
(II) R128(0): [drm] installed DRM signal handler
(II)  R128(0): [agp] Mode 0x1f000201 [AGP 0x1039/0x0735; Card 0x1002/0x5046]
(II)  R128(0): [agp] 8192 kB allocated with handle 0x00000001
(II)  R128(0): [agp] ring handle = 0xd0000000
(II) R128(0): [agp] Ring  mapped at 0xb54fb000
(II) R128(0): [agp] ring read ptr handle =  0xd0101000
(II) R128(0): [agp] Ring read ptr mapped at 0xb775c000
(II)  R128(0): [agp] vertex/indirect buffers handle = 0xd0102000
(II)  R128(0): [agp] Vertex/indirect buffers mapped at 0xb52fb000
(II)  R128(0): [agp] AGP texture map handle = 0xd0302000
(II) R128(0):  [agp] AGP Texture map mapped at 0xb4e1b000
(II) R128(0): [drm]  register handle = 0xcfefc000
(II) R128(0): [dri] Visual configs  initialized
(II) R128(0): CCE in BM mode
(II) R128(0): Using 8 MB  AGP aperture
(II) R128(0): Using 1 MB for the ring buffer
(II)  R128(0): Using 2 MB for vertex/indirect buffers
(II) R128(0): Using 5  MB for AGP textures
(II) R128(0): Memory manager initialized to  (0,0) (800,3112)
(II) R128(0): Reserved area from (0,600) to  (800,602)
(II) R128(0): Largest offscreen area available: 800 x 2510
(II)  R128(0): Reserved back buffer from (0,602) to (800,1202)
(II)  R128(0): Reserved depth buffer from (0,1202) to (800,1803)
(II)  R128(0): Reserved depth span from (0,1802) offset 0x57fd00
(II)  R128(0): Reserved 23040 kb for textures at offset 0x97f400
(II)  R128(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to  screen bit blits
    Solid filled rectangles
    8x8 mono pattern  filled rectangles
    Indirect CPU to Screen color expansion
     Solid Lines
    Dashed Lines
    Setting up tile and stipple  cache:
        32 128x128 slots
        7 256x256 slots
(II)  R128(0): Acceleration enabled
(==) R128(0): Backing store disabled
(==)  R128(0): Silken mouse enabled
(II) R128(0): Using hardware cursor  (scanline 7212)
(II) R128(0): Largest offscreen area available: 800 x  1306
(==) R128(0): DPMS enabled
(II) R128(0): [DRI] installation  complete
(II) R128(0): [drm] Added 128 16384 byte vertex/indirect  buffers
(II) R128(0): [drm] Mapped 128 vertex/indirect buffers
(II)  R128(0): [drm] dma control initialized, using IRQ 11
(II) R128(0):  Direct rendering enabled
(==) RandR enabled
(II) Initializing  built-in extension Generic Event Extension
(II) Initializing built-in  extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II)  Initializing built-in extension XInputExtension
(II) Initializing  built-in extension XTEST
(II) Initializing built-in extension  BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II)  Initializing built-in extension XKEYBOARD
(II) Initializing built-in  extension XC-MISC
(II) Initializing built-in extension SECURITY
(II)  Initializing built-in extension XINERAMA
(II) Initializing built-in  extension XFIXES
(II) Initializing built-in extension RENDER
(II)  Initializing built-in extension RANDR
(II) Initializing built-in  extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II)  AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is  /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid:  Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is  /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid:  drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports  pci:0000:01:00.0
(II) AIGLX: enabled GLX_SGI_swap_control and  GLX_MESA_swap_control
(II) AIGLX: Loaded and initialized  /usr/lib/dri/r128_dri.so
(II) GLX: Initialized DRI GL provider for  screen 0
(II) XKB: reuse xkmfile  /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II)  config/udev: Adding input device Power Button (/dev/input/event1)
(**)  Power Button: Applying InputClass "evdev keyboard catchall"
(II)  LoadModule: "evdev"
(II) Loading  /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev:  vendor="X.Org Foundation"
    compiled for 1.7.6, module version =  2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org  XInput driver, version 7.0
(**) Power Button: always reports core  events
(**) Power Button: Device: "/dev/input/event1"
(II) Power  Button: Found keys
(II) Power Button: Configuring as keyboard
(II)  XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**)  Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**)  Option "xkb_layout" "us"
(II) config/udev: Adding input device Sleep  Button (/dev/input/event0)
(**) Sleep Button: Applying InputClass  "evdev keyboard catchall"
(**) Sleep Button: always reports core  events
(**) Sleep Button: Device: "/dev/input/event0"
(II) Sleep  Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II)  XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**)  Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**)  Option "xkb_layout" "us"
(II) config/udev: Adding input device  Microsoft Microsoft 3-Button Mouse with IntelliEye™ (/dev/input/event4)
(**)  Microsoft Microsoft 3-Button Mouse with IntelliEye™: Applying  InputClass "evdev pointer catchall"
(**) Microsoft Microsoft 3-Button  Mouse with IntelliEye™: always reports core events
(**) Microsoft  Microsoft 3-Button Mouse with IntelliEye™: Device: "/dev/input/event4"
(II)  Microsoft Microsoft 3-Button Mouse with IntelliEye™: Found 3 mouse  buttons
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye™:  Found scroll wheel(s)
(II) Microsoft Microsoft 3-Button Mouse with  IntelliEye™: Found relative axes
(II) Microsoft Microsoft 3-Button  Mouse with IntelliEye™: Found x and y relative axes
(II) Microsoft  Microsoft 3-Button Mouse with IntelliEye™: Configuring as mouse
(**)  Microsoft Microsoft 3-Button Mouse with IntelliEye™: YAxisMapping:  buttons 4 and 5
(**) Microsoft Microsoft 3-Button Mouse with  IntelliEye™: EmulateWheelButton: 4, EmulateWheelInertia: 10,  EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device  "Microsoft Microsoft 3-Button Mouse with IntelliEye™" (type: MOUSE)
(II)  Microsoft Microsoft 3-Button Mouse with IntelliEye™: initialized for  relative axes.
(II) config/udev: Adding input device Microsoft  Microsoft 3-Button Mouse with IntelliEye™ (/dev/input/mouse1)
(II) No  input driver/identifier specified (ignoring)
(II) config/udev:  Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**)  AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard  catchall"
(**) AT Translated Set 2 keyboard: always reports core  events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II)  AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2  keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input  device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option  "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option  "xkb_layout" "us"
(II) config/udev: Adding input device Macintosh  mouse button emulation (/dev/input/event2)
(**) Macintosh mouse  button emulation: Applying InputClass "evdev pointer catchall"
(**)  Macintosh mouse button emulation: always reports core events
(**)  Macintosh mouse button emulation: Device: "/dev/input/event2"
(II)  Macintosh mouse button emulation: Found 3 mouse buttons
(II)  Macintosh mouse button emulation: Found relative axes
(II) Macintosh  mouse button emulation: Found x and y relative axes
(II) Macintosh  mouse button emulation: Configuring as mouse
(**) Macintosh mouse  button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse  button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10,  EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device  "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse  button emulation: initialized for relative axes.
(II) config/udev:  Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II)  No input driver/identifier specified (ignoring)[/HTML]/etc/X11/xorg.conf:
[HTML]Section  "ServerLayout"
    Identifier     "X.org Configured"
     Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0"  "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section  "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath      "/usr/share/fonts/X11/misc"
    FontPath      "/usr/share/fonts/X11/cyrillic"
    FontPath      "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath      "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath      "/usr/share/fonts/X11/Type1"
    FontPath      "/usr/share/fonts/X11/100dpi"
    FontPath      "/usr/share/fonts/X11/75dpi"
    FontPath      "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath      "built-ins"
EndSection

Section "Module"
    Load  "record"
     Load  "dri"
    Load  "glx"
    Load  "dbe"
    Load  "extmod"
     Load  "dri2"
EndSection

Section "InputDevice"
     Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section  "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
     Option        "Protocol" "auto"
    Option        "Device"  "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section  "Monitor"
    Identifier   "Generic Monitor"
    VendorName    "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section  "Device"
        ### Available Driver options are:-
        ###  Values: <i>: integer, <f>: float, <bool>:  "True"/"False",
        ### <string>: "String", <freq>:  "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
         #Option     "NoAccel"                # [<bool>]
         #Option     "SWcursor"               # [<bool>]
         #Option     "Dac6Bit"                # [<bool>]
         #Option     "Dac8Bit"                # [<bool>]
         #Option     "DMAForXv"               # [<bool>]
         #Option     "ForcePCIMode"           # [<bool>]
         #Option     "CCEPIOMode"             # [<bool>]
         #Option     "CCENoSecurity"          # [<bool>]
         #Option     "CCEusecTimeout"         # <i>
        #Option      "AGPMode"                # <i>
        #Option      "AGPSize"                # <i>
        #Option      "RingSize"               # <i>
        #Option      "BufferSize"             # <i>
        #Option      "EnablePageFlip"         # [<bool>]
        #Option      "Display"                # <str>
        #Option      "PanelWidth"             # <i>
        #Option      "PanelHeight"            # <i>
        #Option      "ProgramFPRegs"          # [<bool>]
        #Option      "UseFBDev"               # [<bool>]
        #Option      "VideoKey"               # <i>
        #Option      "ShowCache"              # [<bool>]
        #Option      "VGAAccess"              # [<bool>]
    Identifier  "Card0"
     Driver      "r128"
    VendorName  "ATI Technologies Inc"
     BoardName   "Rage 128 PF/PRO AGP 4x TMDS"
    BusID       "PCI:1:0:0"
EndSection

Section  "Screen"
    Identifier "Screen0"
    Device     "Card0"
     Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0  0
        Depth     1
    EndSubSection
    SubSection  "Display"
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
EndSection[/HTML]lspci  | grep VGA :
[HTML]william@RAINBOWDATASTORAGE:~$ lspci | grep VGA
01:00.0  VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x  TMDS[/HTML]lshw:
[HTML]william@RAINBOWDATASTORAGE:~$  sudo lshw
[sudo] password for william: 
rainbowdatastorage        
     description: Desktop Computer
    product: K7S5A
    vendor: ECS
     version: 1.0
    serial: 00000000
    width: 32 bits
     capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop
   *-core
       description: Motherboard
       product: K7S5A
        vendor: ECS
       physical id: 0
       version: 1.0
        serial: 00000000
     *-firmware
          description: BIOS
           vendor: American Megatrends Inc.
          physical id: 0
           version: 07.00T (04/02/01)
          size: 64KiB
           capacity: 192KiB
          capabilities: isa pci pnp apm upgrade  shadowing escd cdboot bootselect socketedrom edd int13floppy360  int13floppy1200 int13floppy720 int13floppy2880 int5printscreen  int9keyboard int17printer int10video acpi usb agp ls120boot zipboot  biosbootspecification
     *-cpu
          description: CPU
           product: AMD Athlon(tm) Processor
          vendor: Advanced Micro  Devices [AMD]
          physical id: 4
          bus info: cpu@0
           version: 6.6.2
          slot: Socket-A
          size: 1150MHz
           capacity: 1200MHz
          width: 32 bits
          clock: 66MHz
           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr  pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up
         *-cache:0
             description: L1 cache
              physical id: 5
             slot: Internal Cache
              size: 128KiB
             capacity: 1MiB
              capabilities: synchronous internal write-back unified
         *-cache:1
             description: L2 cache
             physical  id: 6
             slot: Internal Cache
             size: 256KiB
              capacity: 1MiB
             capabilities: synchronous internal  write-back unified
     *-memory
          description: System  memory
          physical id: 1
          size: 1015MiB
      *-pci
          description: Host bridge
          product: 735  Host
          vendor: Silicon Integrated Systems [SiS]
           physical id: 100
          bus info: pci@0000:00:00.0
           version: 01
          width: 32 bits
          clock: 33MHz
           configuration: driver=agpgart-sis latency=32
          resources:  irq:0 memory:d0000000-d3ffffff
        *-pci
              description: PCI bridge
             product: Virtual PCI-to-PCI  bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
              physical id: 1
             bus info: pci@0000:00:01.0
              version: 00
             width: 32 bits
             clock: 33MHz
              capabilities: pci bus_master
             resources:  ioport:b000(size=4096) memory:cfe00000-cfefffff  memory:c7c00000-cfcfffff(prefetchable)
           *-display UNCLAIMED
                 description: VGA compatible controller
                product: Rage  128 PF/PRO AGP 4x TMDS
                vendor: ATI Technologies Inc
                 physical id: 0
                bus info: pci@0000:01:00.0
                 version: 00
                width: 32 bits
                clock:  66MHz
                capabilities: agp agp-2.0 pm bus_master  cap_list
                configuration: latency=64 mingnt=8
                 resources: memory:c8000000-cbffffff(prefetchable) ioport:b800(size=256)  memory:cfefc000-cfefffff memory:cfec0000-cfedffff(prefetchable)
         *-isa
             description: ISA bridge
             product:  SiS85C503/5513 (LPC Bridge)
             vendor: Silicon Integrated  Systems [SiS]
             physical id: 2
             bus info:  pci@0000:00:02.0
             version: 00
             width: 32  bits
             clock: 33MHz
             capabilities: isa  bus_master
             configuration: latency=0
        *-serial  UNCLAIMED
             description: SMBus
             product:  SiS961/2 SMBus Controller
             vendor: Silicon Integrated  Systems [SiS]
             physical id: 2.1
             bus info:  pci@0000:00:02.1
             version: 00
             width: 32  bits
             clock: 33MHz
             configuration:  latency=0
             resources: ioport:c00(size=32)
         *-usb:0
             description: USB Controller
              product: USB 1.1 Controller
             vendor: Silicon Integrated  Systems [SiS]
             physical id: 2.2
             bus info:  pci@0000:00:02.2
             version: 07
             width: 32  bits
             clock: 33MHz
             capabilities:  bus_master
             configuration: driver=ohci_hcd latency=64  maxlatency=80
             resources: irq:12 memory:cfffe000-cfffefff
         *-usb:1
             description: USB Controller
              product: USB 1.1 Controller
             vendor: Silicon Integrated  Systems [SiS]
             physical id: 2.3
             bus info:  pci@0000:00:02.3
             version: 07
             width: 32  bits
             clock: 33MHz
             capabilities:  bus_master
             configuration: driver=ohci_hcd latency=64  maxlatency=80
             resources: irq:5 memory:cffff000-cfffffff
         *-ide
             description: IDE interface
              product: 5513 [IDE]
             vendor: Silicon Integrated Systems  [SiS]
             physical id: 2.5
             bus info:  pci@0000:00:02.5
             logical name: scsi0
              logical name: scsi1
             version: d0
             width:  32 bits
             clock: 33MHz
             capabilities: ide  bus_master emulated
             configuration: driver=pata_sis  latency=128
             resources: irq:0 ioport:1f0(size=8)  ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
            *-disk
                description: ATA Disk
                 product: ST340016A
                vendor: Seagate
                 physical id: 0
                bus info: scsi@0:0.0.0
                 logical name: /dev/sda
                version: 3.19
                 serial: 3HS6DCBL
                size: 37GiB (40GB)
                 capabilities: partitioned partitioned:dos
                 configuration: ansiversion=5 signature=0004818d
               *-volume:0
                   description: EXT4 volume
                    vendor: Linux
                   physical id: 1
                    bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                    logical name: /
                   version: 1.0
                    serial: 7e58eae4-58c4-4f51-86a6-6d217d5efbbb
                    size: 35GiB
                   capacity: 35GiB
                    capabilities: primary bootable journaled extended_attributes large_files  huge_files dir_nlink recover extents ext4 ext2 initialized
                    configuration: created=2010-06-06 20:24:32 filesystem=ext4  lastmountpoint=/&#65533;gB&#65533;&#65533;&#65533;(&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;u^ &#65533;U/&#65533;d&#65533;&#65533;&#65533;~!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#830;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;a  modified=2010-06-06 20:56:05 mount.fstype=ext4  mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered  mounted=2010-06-08 15:21:31 state=mounted
              *-volume:1
                    description: Extended partition
                   physical id: 2
                    bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                    size: 1610MiB
                   capacity: 1610MiB
                    capabilities: primary extended partitioned partitioned:extended
                  *-logicalvolume
                      description: Linux swap /  Solaris partition
                      physical id: 5
                       logical name: /dev/sda5
                      capacity: 1610MiB
                       capabilities: nofs
           *-cdrom:0
                 description: CD-R/CD-RW writer
                physical id: 1
                 bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                 logical name: /dev/cdrw1
                logical name: /dev/scd0
                 logical name: /dev/sr0
                capabilities: audio cd-r  cd-rw
                configuration: status=nodisc
            *-cdrom:1
                description: DVD reader
                 product: DVD-ROM SR-8584A
                vendor: MATSHITA
                 physical id: 0.1.0
                bus info: scsi@1:0.1.0
                 logical name: /dev/cdrom
                logical name: /dev/dvd
                 logical name: /dev/scd1
                logical name: /dev/sr1
                 version: f15C
                serial: [MATSHITADVD-ROM  SR-8584Af15C6XPM07/21/99
                capabilities: removable  audio dvd
                configuration: ansiversion=5 status=nodisc
         *-multimedia
             description: Multimedia audio controller
              product: AC'97 Sound Controller
             vendor: Silicon  Integrated Systems [SiS]
             physical id: 2.7
              bus info: pci@0000:00:02.7
             version: a0
              width: 32 bits
             clock: 33MHz
              capabilities: pm bus_master cap_list
             configuration:  driver=Intel ICH latency=64 maxlatency=11 mingnt=52
              resources: irq:11 ioport:dc00(size=256) ioport:d800(size=64)
         *-network:0
             description: Ethernet interface
              product: NC100 Network Everywhere Fast Ethernet 10/100
              vendor: ADMtek
             physical id: b
             bus info:  pci@0000:00:0b.0
             logical name: eth0
              version: 11
             serial: 00:0c:41:e9:7f:d0
              width: 32 bits
             clock: 33MHz
              capabilities: pm bus_master cap_list rom ethernet physical
              configuration: broadcast=yes driver=tulip driverversion=1.1.15  ip=192.168.0.5 latency=64 maxlatency=128 mingnt=64 multicast=yes
              resources: irq:11 ioport:d400(size=256) memory:cfffcc00-cfffcfff  memory:cffa0000-cffbffff(prefetchable)
        *-network:1
              description: Wireless interface
             product: RT2500 802.11g  Cardbus/mini-PCI
             vendor: RaLink
              physical id: f
             bus info: pci@0000:00:0f.0
              logical name: wlan0
             version: 01
             serial:  00:0f:66:f3:dc:ae
             width: 32 bits
             clock:  33MHz
             capabilities: pm bus_master cap_list ethernet  physical wireless
             configuration: broadcast=yes  driver=rt2500pci latency=64 multicast=yes wireless=IEEE 802.11bg
              resources: irq:12 memory:cfffa000-cfffbfff
william@RAINBOWDATASTORAGE:~$  [/HTML]Hopefully this info will help, even if someone  could just point me in the right direction it would be greatly  appreciated. This is a fresh install of Lucid and there isn't anything  tampered with. Thanks in advance to all who help, I'll be in school  (online classes) the rest of the day on my wifes computer, but I will  check the forums regularly. I've worked my **** off to figure this  problem out and won't settle until it's resolved!
One more thing, I  know my graphics card is probably not supported, but rendering **is**  enabled and it **will **use 1024x768 and I **have** had Compiz  woking on older versions. Thanks again.


:guitar::guitar::guitar:

---

### Post by rainbowagent7 on 2010-06-08
Anyone?...Anyone?

---

### Post by Yellow Pasque on 2010-06-08
You're going to have to manually specify the hsync in the monitor section because the default one being used is probably too small. To see what you need, generate a modeline, e.g.
```
cvt 1024 768 60.0Hz
```

My system returns this:
```
# 1024x768 59.92 Hz (CVT 0.79M3) **hsync: 47.82 kHz**; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
```

Then, in my Monitor section, I would put a HorizSync that includes the hsync returned (just don't set it to some insanely high value), so open xorg.conf for editing:
```
gksu gedit /etc/X11/xorg.conf
```
And make your Monitor section look like (e.g.):
```
Section  "Monitor"
    Identifier   "Generic Monitor"
    VendorName    "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync    31-50
EndSection
```
Save, quit gedit, and log out to restart X.

---

### Post by rainbowagent7 on 2010-06-08
Thanks Temujin. I already used cvt to generate a mode line and and inserted it with xrandr, it gave me the resolution in the list but my machine wouldn't recognize it. I'll just try putting the hsync value in my xorg.conf like you recommended and keep you posted. I'm crunching in school right now, so it might be a couple of hours before I can get back with you. Thanks again for your time.

---

### Post by tkoco on 2010-06-23
No matter how much I know, there is always something new to learn. Thank you for the new info!

> **Temüjin said:**
> You're going to have to manually specify the hsync in the monitor section because the default one being used is probably too small. To see what you need, generate a modeline, e.g.
```
cvt 1024 768 60.0Hz
```

My system returns this:
```
# 1024x768 59.92 Hz (CVT 0.79M3) **hsync: 47.82 kHz**; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
```

Then, in my Monitor section, I would put a HorizSync that includes the hsync returned (just don't set it to some insanely high value), so open xorg.conf for editing:
```
gksu gedit /etc/X11/xorg.conf
```
And make your Monitor section look like (e.g.):
```
Section  "Monitor"
    Identifier   "Generic Monitor"
    VendorName    "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync    31-50
EndSection
```
Save, quit gedit, and log out to restart X.

---

### Post by Thelasko on 2010-06-23
You're issue is probably related to an incorrect video driver.  What kind of card do you have?

Once you have the correct driver installed, Ubuntu should detect the correct resolutions for your monitor automatically.

Xorg.conf is a "[big hammer]("http://attheridge.files.wordpress.com/2008/12/square-peg-round-hole.jpg")" you can use if nothing else will fix the problem.

---

### Post by Thelasko on 2010-06-23
Looking through your xorg.conf file, it looks like you have an ATI graphics card.  [Here are some instructions on that.]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

If it is indeed a Rage 128 card, I don't believe the binary driver will help(it might make it worse).  In which case you will need to configure xorg.conf as you are doing right now.

---

### Post by Praetor77 on 2010-06-23
You can check here for detailed instructions to add new resolution modes:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Nevertheless, this only works if your videocard/monitor support said resolution, obviously.

---


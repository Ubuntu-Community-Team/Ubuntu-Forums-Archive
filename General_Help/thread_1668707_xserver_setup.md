---
title: "xserver setup"
date: 2011-01-16
forum: General Help
---

### Post by necco on 2011-01-16
greetings.

i am evaluating the use of ubuntu 10.10 on a dell "hybrid studio". the video card has a 256Mb VRAM and (i think) is an integrated i810.

gnome panel proposes a max 4/3 resolution of 1024*768@60Hz, my good old trinitron screen goes up to 2048 and is otimized for a 1600*1200@85Hz resolution.

i have tried to run as root dpkg-reconfigure xserver-xorg on tty1 but nothing happens and i have my "#" back. ctrl-alt backspace does not work to kill gnome and when stopping Xorg through /etc/init.s/stop gdm the procedure freezes trying to check the battery level.

does anybody has a clue on how i can get a decent workspace?

thanks in advance.

necco

---

### Post by lithopsian on 2011-01-16
Could you confirm the graph8ics card.  Use lspci.  Grep for VGA if there is too much output for you.

The contents of your xorg.conf are also helpful, shouldn't be too big.

The output from /var/log/xorg.0.log is also helpful but pretty big.  You might want to just browse for now and pick out bits you think are interesting.

Your card should be fairly well supported from 10.10.  Which drivers do you have (the log file will say)?  Which kernel modules is it loading (lsmod)?

---

### Post by necco on 2011-01-17
greetings, and thanks for your interest.

as of the specifications from dell support links the chipset is a Mobile Intel GM965 Express.  i have tried to install the i965-va-driver package but with no 'intuitive' result.

lspci provides the following: 

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

xorg.0.log provides the following:

[    19.778] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)

here is the complete outcome of lsmod:

root@linux:/home/necco# lsmod
Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
usblp                  10651  0 
snd_hda_codec_realtek   218227  1 
i915                  294989  4 
snd_hda_intel          22107  4 
drm_kms_helper         30200  1 i915
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
drm                   168092  4 i915,drm_kms_helper
snd_hwdep               5040  1 snd_hda_codec
i2c_algo_bit            5168  1 i915
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec
video                  18712  1 i915
psmouse                59033  0 
snd_seq_midi            4588  0 
output                  1883  1 video
intel_agp              26694  2 i915
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
agpgart                32011  2 drm,intel_agp
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
wacom                  27752  0 
serio_raw               4022  0 
dell_wmi_aio            1733  0 
lp                      7342  0 
dcdbas                  5402  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8767  0 
snd                    49038  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport                31492  3 parport_pc,ppdev,lp
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
usbhid                 36882  0 
hid                    67742  1 usbhid
usb_storage            40172  1 
r8169                  36489  0 
firewire_ohci          21042  0 
ahci                   19198  2 
mii                     4425  1 r8169
libahci                21664  1 ahci
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
root@linux:/home/necco# clear

root@linux:/home/necco# lsmod
Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
usblp                  10651  0 
snd_hda_codec_realtek   218227  1 
i915                  294989  4 
snd_hda_intel          22107  4 
drm_kms_helper         30200  1 i915
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
drm                   168092  4 i915,drm_kms_helper
snd_hwdep               5040  1 snd_hda_codec
i2c_algo_bit            5168  1 i915
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec
video                  18712  1 i915
psmouse                59033  0 
snd_seq_midi            4588  0 
output                  1883  1 video
intel_agp              26694  2 i915
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
agpgart                32011  2 drm,intel_agp
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
wacom                  27752  0 
serio_raw               4022  0 
dell_wmi_aio            1733  0 
lp                      7342  0 
dcdbas                  5402  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8767  0 
snd                    49038  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport                31492  3 parport_pc,ppdev,lp
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
usbhid                 36882  0 
hid                    67742  1 usbhid
usb_storage            40172  1 
r8169                  36489  0 
firewire_ohci          21042  0 
ahci                   19198  2 
mii                     4425  1 r8169
libahci                21664  1 ahci
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core



hope this is of help :)

many thanks again for your assistance.

---

### Post by lithopsian on 2011-01-17
OK, 965 is what I expected.  The correct kernel modules are being loaded, i915, intel_agp, and agpgart.

i965-va-driver is not the graphics driver for your card, it is just a bit that provides acceleration specific to video.  The driver you need is xserver-xorg-video-intel (v2.9?), but even that needs other things as well.  You probably have them, but perhaps not configured properly.  I don't think dpkg-reconfigure is going to do it for you.

From /var/log/Xorg.0.log, useful lines are:
the one starting "(--) PCI:*(0@0:2:0) Intel Corporation ..."
The few lines starting with "(II) Module intel: vendor="X.Org Foundation"
Anything with Intel or VGA in it

The one line you posted suggests a configuration issue, but doesn't necessarily mean it is fatal.  It indicates that the default mode for your card (1600x1200 pixels) cannot be displayed by your monitor, at least not at the configured refresh rate, or at least X doesn't think it is.

Post your /etc/X11/xorg.conf file, or at least the video-related bits.  It may not be correctly indicating what your card and monitor can do.  You can also use xrandr to reset the resolution, refresh rate, DPI, etc, on the fly but it won't stick unless you include it somewhere like your autostart script.

ctrl-alt-backspace is now disabled by default.  You can re-enable it, but I forget how.

---

### Post by necco on 2011-01-18
here are the lines from Xorg.0.log concerning xserver, though i wonder what have some xfree86 mentions to do.

[    20.758] (--) PCI:*(0:0:2:0) 8086:2a02:1028:0279 rev 3, Mem @ 0xfe700000/1048576, 0xd0000000/268435456, I/O @ 0x0000c400/8
[    20.758] (--) PCI: (0:0:2:1) 8086:2a03:1028:0279 rev 3, Mem @ 0xfe800000/1048576
[    20.758] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    20.759] (II) LoadModule: "extmod"
[    20.803] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.813] (II) Module extmod: vendor="X.Org Foundation"
[    20.813] 	compiled for 1.9.0, module version = 1.0.0
[    20.813] 	Module class: X.Org Server Extension
[    20.813] 	ABI class: X.Org Server Extension, version 4.0
[    20.813] (II) Loading extension MIT-SCREEN-SAVER
[    20.813] (II) Loading extension XFree86-VidModeExtension
[    20.813] (II) Loading extension XFree86-DGA
[    20.813] (II) Loading extension DPMS
[    20.813] (II) Loading extension XVideo
[    20.813] (II) Loading extension XVideo-MotionCompensation
[    20.813] (II) Loading extension X-Resource
[    20.813] (II) LoadModule: "dbe"
[    20.813] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.819] (II) Module dbe: vendor="X.Org Foundation"
[    20.819] 	compiled for 1.9.0, module version = 1.0.0
[    20.819] 	Module class: X.Org Server Extension
[    20.819] 	ABI class: X.Org Server Extension, version 4.0
[    20.819] (II) Loading extension DOUBLE-BUFFER
[    20.819] (II) LoadModule: "glx"
[    20.820] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.839] (II) Module glx: vendor="X.Org Foundation"
[    20.839] 	compiled for 1.9.0, module version = 1.0.0
[    20.839] 	ABI class: X.Org Server Extension, version 4.0
[    20.841] (==) AIGLX enabled
[    20.841] (II) Loading extension GLX
[    20.841] (II) LoadModule: "record"
[    20.841] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.842] (II) Module record: vendor="X.Org Foundation"
[    20.842] 	compiled for 1.9.0, module version = 1.13.0
[    20.842] 	Module class: X.Org Server Extension
[    20.842] 	ABI class: X.Org Server Extension, version 4.0
[    20.842] (II) Loading extension RECORD
[    20.842] (II) LoadModule: "dri"
[    20.842] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.856] (II) Module dri: vendor="X.Org Foundation"
[    20.856] 	compiled for 1.9.0, module version = 1.0.0
[    20.856] 	ABI class: X.Org Server Extension, version 4.0
[    20.856] (II) Loading extension XFree86-DRI
[    20.856] (II) LoadModule: "dri2"
[    20.856] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.856] (II) Module dri2: vendor="X.Org Foundation"
[    20.856] 	compiled for 1.9.0, module version = 1.2.0
[    20.857] 	ABI class: X.Org Server Extension, version 4.0
[    20.857] (II) Loading extension DRI2
[    20.857] (==) Matched intel as autoconfigured driver 0
[    20.857] (==) Matched vesa as autoconfigured driver 1
[    20.857] (==) Matched fbdev as autoconfigured driver 2
[    20.857] (==) Assigned the driver to the xf86ConfigLayout
[    20.857] (II) LoadModule: "intel"
[    20.863] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    20.881] (II) Module intel: vendor="X.Org Foundation"
[    20.881] 	compiled for 1.9.0, module version = 2.12.0
[    20.881] 	Module class: X.Org Video Driver
[    20.881] 	ABI class: X.Org Video Driver, version 8.0
[    20.881] (II) LoadModule: "vesa"
[    20.881] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.897] (II) Module vesa: vendor="X.Org Foundation"
[    20.897] 	compiled for 1.8.99.905, module version = 2.3.0
[    20.897] 	Module class: X.Org Video Driver
[    20.897] 	ABI class: X.Org Video Driver, version 8.0
[    20.897] (II) LoadModule: "fbdev"
[    20.897] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.909] (II) Module fbdev: vendor="X.Org Foundation"
[    20.909] 	compiled for 1.8.99.905, module version = 0.4.2
[    20.909] 	ABI class: X.Org Video Driver, version 8.0
[    20.909] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    20.910] (II) VESA: driver for VESA chipsets: vesa
[    20.910] (II) FBDEV: driver for framebuffer: fbdev
[    20.910] (++) using VT number 7

[    20.910] (WW) Falling back to old probe method for vesa
[    20.910] (WW) Falling back to old probe method for fbdev
[    20.910] (II) Loading sub module "fbdevhw"
[    20.910] (II) LoadModule: "fbdevhw"
[    20.911] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.917] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.917] 	compiled for 1.9.0, module version = 0.0.2
[    20.918] 	ABI class: X.Org Video Driver, version 8.0
[    20.919] drmOpenDevice: node name is /dev/dri/card0
[    20.919] drmOpenDevice: open result is 8, (OK)
[    20.932] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    20.932] drmOpenDevice: node name is /dev/dri/card0
[    20.932] drmOpenDevice: open result is 8, (OK)
[    20.932] drmOpenByBusid: drmOpenMinor returns 8
[    20.932] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    20.932] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    20.932] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    20.932] (==) intel(0): RGB weight 888
[    20.932] (==) intel(0): Default visual is TrueColor
[    20.932] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    20.932] (--) intel(0): Chipset: "965GM"
[    20.932] (==) intel(0): video overlay key set to 0x101fe
[    21.012] (II) intel(0): Output VGA1 has no monitor section
[    21.040] (II) intel(0): Output DVI1 has no monitor section
[    21.376] (II) intel(0): Output TV1 has no monitor section
[    21.448] (II) intel(0): EDID for output VGA1

i have tried to see what might happen using xrandr but this honestly goes beyond my knowledge :/

best regards and thanks again for your interest.

---

### Post by lithopsian on 2011-01-18
Everything looks more or less OK, although I'm not entirely happy to see VESA and FB drivers getting loaded.  So it just seems to be a matter of configuring correctly using xrandr or xorg.conf.  You can play with the xrandr --mode and --rate settings if you like, but they have a habit of rebooting X with this card which sort of defeats the purpose.  There is also a permanent xrandr configuration file now, but I don;'t use it.

Here is a basic xorg.conf that should help you.  Notice the screen size is hard-coded because this driver doesn't seem to have an option for accepting a DPI setting.  You should be able to use it more or less intact, but you can also play with the resolution and DPI as needed.   I've left a bunch of options commented out, some of which are obsolete, but you might want to try some of them:
```

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
    Driver        “intel”
#    Option        "UseFBDev"            "true"
#    Option        "AccelMethod"            "uxa"
#    Option        "EXAOptimizeMigration"        "true"
#    Option        "MigrationHeuristic"        "greedy"
    Option        "Tiling"            "true"
#    Option        "Legacy3D"            "false"
    Option        "XvMC"                "false" # not on 865G
#    Option        "Shadow"            "true" # last resort for stability
#    Option        "SwapbuffersWait"        "true" # fix tearing
#    Option        "HotPlug"            "true" monitor hotplugging
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    DisplaySize    396    317    # 82x82dpi
    Option        "PreferredMode" "1280x1024"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection



```

---

### Post by lithopsian on 2011-01-18
Everything looks more or less OK, although I'm not entirely happy to see VESA and FB drivers getting loaded.  So it just seems to be a matter of configuring correctly using xrandr or xorg.conf.  You can play with the xrandr --mode and --rate settings if you like, but they have a habit of rebooting X with this card which sort of defeats the purpose.  There is also a permanent xrandr configuration file now, but I don;'t use it.

Here is a basic xorg.conf that should help you.  Notice the screen size is hard-coded because this driver doesn't seem to have an option for accepting a DPI setting.  You should be able to use it more or less intact, but you can also play with the resolution and DPI as needed.   I've left a bunch of options commented out, some of which are obsolete, but you might want to try some of them:
```

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
    Driver        “intel”
#    Option        "UseFBDev"            "true"
#    Option        "AccelMethod"            "uxa"
#    Option        "EXAOptimizeMigration"        "true"
#    Option        "MigrationHeuristic"        "greedy"
    Option        "Tiling"            "true"
#    Option        "Legacy3D"            "false"
    Option        "XvMC"                "false" # not on 865G
#    Option        "Shadow"            "true" # last resort for stability
#    Option        "SwapbuffersWait"        "true" # fix tearing
#    Option        "HotPlug"            "true" monitor hotplugging
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    DisplaySize    396    317    # 82x82dpi
    Option        "PreferredMode" "1280x1024"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection



```

---

### Post by necco on 2011-01-19
thanks a lot for your interest,  i have solved it by forcing monitor recognition !

---


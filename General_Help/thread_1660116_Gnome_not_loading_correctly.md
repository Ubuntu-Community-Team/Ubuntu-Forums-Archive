---
title: "Gnome not loading correctly"
date: 2011-01-04
forum: General Help
---

### Post by GreatKeyHunter on 2011-01-04
Hi, i recently typed in the terminal sudo apt-get upgrade, and it upgraded certain features. Now, after rebooting gnome doesn't boot correctly at all.  Its missing several features/ the panels are not working properly, its not loading emerald or gtk.  the only way it boots up correctly is in safe mode.  Any ideas on how i should go about fixing this?

What was upgraded are the following files:
libevolution 
libgudev-1.0-0
evolution-plugins 
clamav
evolution
nvidia-current
nvidia-current-modaliases
clamav-base
evolution-common
libclamav6
udev
gnome-system-tools
playonlinux
ubuntu-sso
libdecoration
libudev0
clamav-freshclam
linux-libc-dev
acroread
libsqlite3-0

I'm currently running Ubuntu 10.10

---

### Post by GreatKeyHunter on 2011-01-05
I think i have gotten control of this, it seems to be a problem with compiz.  This is what i tried to do, re-installing nvidia drivers, that didn't work.  However after clicking on the compiz-fusion icon and setting the window manager to metacity things started to behave correctly again.  When i try changing it back to compiz, thats when all hell breaks loose.  I have no idea what could possibly be causing this.

---

### Post by amsterdamharu on 2011-01-05
Some files and commands you might check out/post here are:

```
lsmod
``` see what drivers are loaded (my guess it's nouveau instead of nvidia).

What's in /etc/X11/xorg.conf

And what's in /var/log/Xorg.0.log

I think you could try to uninstall nvidia so it'll use nouveau, when you're in your desktop (3d and compiz disabled) it can detect nvidia and install it again. (the program that does that is jockey-gtk or jocky-text for terminal)

---

### Post by GreatKeyHunter on 2011-01-05
```
Module                  Size  Used by
parport_pc             30086  0 
ppdev                   6804  0 
binfmt_misc             7984  1 
snd_hda_codec_nvhdmi    15451  8 
xt_limit                2204  8 
xt_tcpudp               2627  7 
ipt_LOG                 5394  8 
ipt_MASQUERADE          1919  0 
xt_DSCP                 2269  0 
ipt_REJECT              2440  1 
nf_conntrack_irc        4501  0 
nf_conntrack_ftp        7158  0 
xt_state                1386  6 
snd_hda_codec_via      62447  1 
vboxnetadp              5267  0 
vboxnetflt             14966  0 
vboxdrv              1792472  2 vboxnetadp,vboxnetflt
snd_hda_intel          26019  2 
snd_hda_codec         100919  3 snd_hda_codec_nvhdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
iptable_nat             4593  0 
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
nvidia              10274473  57 
nf_nat                 20067  2 ipt_MASQUERADE,iptable_nat
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
nf_conntrack_ipv4      13143  9 iptable_nat,nf_nat
snd_seq_midi_event      7291  1 snd_seq_midi
nf_conntrack           75238  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
nf_defrag_ipv4          1569  1 nf_conntrack_ipv4
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
iptable_mangle          1823  0 
snd                    64181  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter          1778  1 
ip_tables              19139  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               24423  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
hwmon_vid               3154  0 
i2c_nforce2             6155  0 
soundcore               1240  1 snd
video                  22176  0 
output                  2527  1 video
lp                     10201  0 
edac_core              46822  0 
k10temp                 3535  0 
parport                37032  3 parport_pc,ppdev,lp
edac_mce_amd            9387  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
asus_atk0110           12987  0 
usbhid                 42062  0 
hid                    84710  1 usbhid
firewire_ohci          24615  0 
ahci                   22210  6 
firewire_core          54327  1 firewire_ohci
libahci                26052  1 ahci
forcedeth              55649  0 
crc_itu_t               1739  1 firewire_core
pata_amd               12050  0 
greatwhite@greatwhite-desktop:~$ lsmod
Module                  Size  Used by
parport_pc             30086  0 
ppdev                   6804  0 
binfmt_misc             7984  1 
snd_hda_codec_nvhdmi    15451  8 
xt_limit                2204  8 
xt_tcpudp               2627  7 
ipt_LOG                 5394  8 
ipt_MASQUERADE          1919  0 
xt_DSCP                 2269  0 
ipt_REJECT              2440  1 
nf_conntrack_irc        4501  0 
nf_conntrack_ftp        7158  0 
xt_state                1386  6 
snd_hda_codec_via      62447  1 
vboxnetadp              5267  0 
vboxnetflt             14966  0 
vboxdrv              1792472  2 vboxnetadp,vboxnetflt
snd_hda_intel          26019  2 
snd_hda_codec         100919  3 snd_hda_codec_nvhdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
iptable_nat             4593  0 
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
nvidia              10274473  57 
nf_nat                 20067  2 ipt_MASQUERADE,iptable_nat
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
nf_conntrack_ipv4      13143  9 iptable_nat,nf_nat
snd_seq_midi_event      7291  1 snd_seq_midi
nf_conntrack           75238  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
nf_defrag_ipv4          1569  1 nf_conntrack_ipv4
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
iptable_mangle          1823  0 
snd                    64181  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter          1778  1 
ip_tables              19139  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               24423  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
hwmon_vid               3154  0 
i2c_nforce2             6155  0 
soundcore               1240  1 snd
video                  22176  0 
output                  2527  1 video
lp                     10201  0 
edac_core              46822  0 
k10temp                 3535  0 
parport                37032  3 parport_pc,ppdev,lp
edac_mce_amd            9387  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
asus_atk0110           12987  0 
usbhid                 42062  0 
hid                    84710  1 usbhid
firewire_ohci          24615  0 
ahci                   22210  6 
firewire_core          54327  1 firewire_ohci
libahci                26052  1 ahci
forcedeth              55649  0 
crc_itu_t               1739  1 firewire_core
pata_amd               12050  0 
``` thats what i have running

For ect/X11/xorg.conf this is what i have running:
```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```and for /var/log/Xorg.0.log
```
[    17.293] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    17.293] X Protocol Version 11, Revision 0
[    17.293] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    17.293] Current Operating System: Linux greatwhite-desktop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64
[    17.293] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=0600122e-e9db-4440-8115-3e64a53ecb1d ro quiet splash
[    17.293] Build Date: 16 September 2010  06:18:41PM
[    17.293] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    17.293] Current version of pixman: 0.18.4
[    17.293]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    17.293] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.294] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan  5 05:33:03 2011
[    17.294] (==) Using config file: "/etc/X11/xorg.conf"
[    17.294] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.294] (==) No Layout section.  Using the first Screen section.
[    17.294] (**) |-->Screen "Default Screen" (0)
[    17.294] (**) |   |-->Monitor "<default monitor>"
[    17.295] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    17.295] (**) |   |-->Device "Default Device"
[    17.295] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    17.295] (==) Automatically adding devices
[    17.295] (==) Automatically enabling devices
[    17.295] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.295]     Entry deleted from font path.
[    17.295] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    17.295] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.295] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.295] (II) Loader magic: 0x7d0200
[    17.295] (II) Module ABI versions:
[    17.296]     X.Org ANSI C Emulation: 0.4
[    17.296]     X.Org Video Driver: 8.0
[    17.296]     X.Org XInput driver : 11.0
[    17.296]     X.Org Server Extension : 4.0
[    17.298] (--) PCI: (0:2:0:0) 10de:0dc4:3842:1450 rev 161, Mem @ 0xf4000000/33554432, 0xc8000000/134217728, 0xd0000000/67108864, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[    17.298] (--) PCI:*(0:3:0:0) 10de:0dc4:3842:1450 rev 161, Mem @ 0xf8000000/16777216, 0xd8000000/134217728, 0xd4000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/524288
[    17.298] (II) Open ACPI successful (/var/run/acpid.socket)
[    17.298] (II) "extmod" will be loaded by default.
[    17.298] (II) "dbe" will be loaded by default.
[    17.298] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    17.298] (II) "record" will be loaded by default.
[    17.298] (II) "dri" will be loaded by default.
[    17.298] (II) "dri2" will be loaded by default.
[    17.298] (II) LoadModule: "glx"
[    17.299] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    17.309] (II) Module glx: vendor="NVIDIA Corporation"
[    17.309]     compiled for 4.0.2, module version = 1.0.0
[    17.309]     Module class: X.Org Server Extension
[    17.309] (II) NVIDIA GLX Module  260.19.29  Wed Dec  8 12:24:30 PST 2010
[    17.309] (II) Loading extension GLX
[    17.309] (II) LoadModule: "extmod"
[    17.336] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.336] (II) Module extmod: vendor="X.Org Foundation"
[    17.336]     compiled for 1.9.0, module version = 1.0.0
[    17.336]     Module class: X.Org Server Extension
[    17.336]     ABI class: X.Org Server Extension, version 4.0
[    17.336] (II) Loading extension MIT-SCREEN-SAVER
[    17.336] (II) Loading extension XFree86-VidModeExtension
[    17.336] (II) Loading extension XFree86-DGA
[    17.336] (II) Loading extension DPMS
[    17.336] (II) Loading extension XVideo
[    17.336] (II) Loading extension XVideo-MotionCompensation
[    17.336] (II) Loading extension X-Resource
[    17.336] (II) LoadModule: "dbe"
[    17.337] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.337] (II) Module dbe: vendor="X.Org Foundation"
[    17.337]     compiled for 1.9.0, module version = 1.0.0
[    17.337]     Module class: X.Org Server Extension
[    17.337]     ABI class: X.Org Server Extension, version 4.0
[    17.337] (II) Loading extension DOUBLE-BUFFER
[    17.337] (II) LoadModule: "record"
[    17.338] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.338] (II) Module record: vendor="X.Org Foundation"
[    17.338]     compiled for 1.9.0, module version = 1.13.0
[    17.338]     Module class: X.Org Server Extension
[    17.338]     ABI class: X.Org Server Extension, version 4.0
[    17.338] (II) Loading extension RECORD
[    17.338] (II) LoadModule: "dri"
[    17.338] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.339] (II) Module dri: vendor="X.Org Foundation"
[    17.339]     compiled for 1.9.0, module version = 1.0.0
[    17.339]     ABI class: X.Org Server Extension, version 4.0
[    17.339] (II) Loading extension XFree86-DRI
[    17.339] (II) LoadModule: "dri2"
[    17.339] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.339] (II) Module dri2: vendor="X.Org Foundation"
[    17.339]     compiled for 1.9.0, module version = 1.2.0
[    17.339]     ABI class: X.Org Server Extension, version 4.0
[    17.340] (II) Loading extension DRI2
[    17.340] (II) LoadModule: "nvidia"
[    17.340] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    17.340] (II) Module nvidia: vendor="NVIDIA Corporation"
[    17.341]     compiled for 4.0.2, module version = 1.0.0
[    17.341]     Module class: X.Org Video Driver
[    17.341] (II) NVIDIA dlloader X Driver  260.19.29  Wed Dec  8 12:10:14 PST 2010
[    17.341] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    17.341] (++) using VT number 7

[    17.353] (II) Loading sub module "fb"
[    17.353] (II) LoadModule: "fb"
[    17.354] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.355] (II) Module fb: vendor="X.Org Foundation"
[    17.355]     compiled for 1.9.0, module version = 1.0.0
[    17.355]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.355] (II) Loading sub module "wfb"
[    17.355] (II) LoadModule: "wfb"
[    17.356] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    17.356] (II) Module wfb: vendor="X.Org Foundation"
[    17.356]     compiled for 1.9.0, module version = 1.0.0
[    17.356]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.356] (II) Loading sub module "ramdac"
[    17.356] (II) LoadModule: "ramdac"
[    17.356] (II) Module "ramdac" already built-in
[    17.356] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    17.356] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    17.356] (==) NVIDIA(0): RGB weight 888
[    17.356] (==) NVIDIA(0): Default visual is TrueColor
[    17.356] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    17.356] (**) NVIDIA(0): Option "NoLogo" "True"
[    17.357] (**) NVIDIA(0): Enabling RENDER acceleration
[    17.357] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    17.357] (II) NVIDIA(0):     enabled.
[    17.995] (II) NVIDIA(0): NVIDIA GPU GeForce GTS 450 (GF106) at PCI:3:0:0 (GPU-0)
[    17.995] (--) NVIDIA(0): Memory: 1048576 kBytes
[    17.995] (--) NVIDIA(0): VideoBIOS: 70.06.13.00.52
[    17.995] (II) NVIDIA(0): Detected PCI Express Link width: 8X
[    17.995] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    17.995] (--) NVIDIA(0): Connected display device(s) on GeForce GTS 450 at PCI:3:0:0
[    17.995] (--) NVIDIA(0):     HP S2031 (CRT-0)
[    17.995] (--) NVIDIA(0): HP S2031 (CRT-0): 400.0 MHz maximum pixel clock
[    18.038] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    18.038] (==) NVIDIA(0): 
[    18.038] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    18.038] (==) NVIDIA(0):     will be used as the requested mode.
[    18.038] (==) NVIDIA(0): 
[    18.038] (II) NVIDIA(0): Validated modes:
[    18.038] (II) NVIDIA(0):     "nvidia-auto-select"
[    18.038] (II) NVIDIA(0): Virtual screen size determined to be 1600 x 900
[    18.062] (--) NVIDIA(0): DPI set to (92, 91); computed from "UseEdidDpi" X config
[    18.062] (--) NVIDIA(0):     option
[    18.062] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    18.062] (--) Depth 24 pixmap format is 32 bpp
[    18.062] (II) NVIDIA: Using 3069.00 MB of virtual memory for indirect memory
[    18.062] (II) NVIDIA:     access.
[    19.091] (II) NVIDIA(GPU-1): NVIDIA GPU GeForce GTS 450 (GF106) at PCI:2:0:0 (GPU-1)
[    19.091] (--) NVIDIA(GPU-1): Memory: 1048576 kBytes
[    19.091] (--) NVIDIA(GPU-1): VideoBIOS: 70.06.13.00.52
[    19.091] (II) NVIDIA(GPU-1): Detected PCI Express Link width: 8X
[    19.091] (--) NVIDIA(GPU-1): Interlaced video modes are supported on this GPU
[    19.091] (--) NVIDIA(GPU-1): Connected display device(s) on GeForce GTS 450 at PCI:2:0:0
[    19.091] (--) NVIDIA(GPU-1):     none
[    19.094] (II) NVIDIA(0): Initialized GPU GART.
[    19.104] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    19.124] (II) Loading extension NV-GLX
[    19.185] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    19.189] (==) NVIDIA(0): Disabling shared memory pixmaps
[    19.189] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    19.189] (==) NVIDIA(0): Backing store disabled
[    19.189] (==) NVIDIA(0): Silken mouse enabled
[    19.205] (==) NVIDIA(0): DPMS enabled
[    19.205] (II) Loading extension NV-CONTROL
[    19.205] (II) Loading extension XINERAMA
[    19.205] (II) Loading sub module "dri2"
[    19.205] (II) LoadModule: "dri2"
[    19.206] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.206] (II) NVIDIA(0): [DRI2] Setup complete
[    19.206] (==) RandR enabled
[    19.206] (II) Initializing built-in extension Generic Event Extension
[    19.206] (II) Initializing built-in extension SHAPE
[    19.206] (II) Initializing built-in extension MIT-SHM
[    19.206] (II) Initializing built-in extension XInputExtension
[    19.206] (II) Initializing built-in extension XTEST
[    19.206] (II) Initializing built-in extension BIG-REQUESTS
[    19.206] (II) Initializing built-in extension SYNC
[    19.206] (II) Initializing built-in extension XKEYBOARD
[    19.206] (II) Initializing built-in extension XC-MISC
[    19.206] (II) Initializing built-in extension SECURITY
[    19.206] (II) Initializing built-in extension XINERAMA
[    19.206] (II) Initializing built-in extension XFIXES
[    19.206] (II) Initializing built-in extension RENDER
[    19.206] (II) Initializing built-in extension RANDR
[    19.206] (II) Initializing built-in extension COMPOSITE
[    19.206] (II) Initializing built-in extension DAMAGE
[    19.206] (II) Initializing built-in extension GESTURE
[    19.206] (II) Initializing extension GLX
[    19.231] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.236] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    19.237] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.237] (II) LoadModule: "evdev"
[    19.237] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.237] (II) Module evdev: vendor="X.Org Foundation"
[    19.237]     compiled for 1.9.0, module version = 2.3.2
[    19.237]     Module class: X.Org XInput Driver
[    19.237]     ABI class: X.Org XInput driver, version 11.0
[    19.237] (**) Power Button: always reports core events
[    19.237] (**) Power Button: Device: "/dev/input/event1"
[    19.314] (II) Power Button: Found keys
[    19.314] (II) Power Button: Configuring as keyboard
[    19.314] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.314] (**) Option "xkb_rules" "evdev"
[    19.314] (**) Option "xkb_model" "pc105"
[    19.314] (**) Option "xkb_layout" "us"
[    19.318] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.318] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.318] (**) Power Button: always reports core events
[    19.318] (**) Power Button: Device: "/dev/input/event0"
[    19.390] (II) Power Button: Found keys
[    19.390] (II) Power Button: Configuring as keyboard
[    19.390] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.390] (**) Option "xkb_rules" "evdev"
[    19.390] (**) Option "xkb_model" "pc105"
[    19.390] (**) Option "xkb_layout" "us"
[    19.394] (II) config/udev: Adding input device Logitech USB Gaming Mouse (/dev/input/event3)
[    19.394] (**) Logitech USB Gaming Mouse: Applying InputClass "evdev pointer catchall"
[    19.394] (**) Logitech USB Gaming Mouse: always reports core events
[    19.394] (**) Logitech USB Gaming Mouse: Device: "/dev/input/event3"
[    19.470] (II) Logitech USB Gaming Mouse: Found 20 mouse buttons
[    19.470] (II) Logitech USB Gaming Mouse: Found scroll wheel(s)
[    19.470] (II) Logitech USB Gaming Mouse: Found relative axes
[    19.470] (II) Logitech USB Gaming Mouse: Found x and y relative axes
[    19.470] (II) Logitech USB Gaming Mouse: Configuring as mouse
[    19.470] (**) Logitech USB Gaming Mouse: YAxisMapping: buttons 4 and 5
[    19.470] (**) Logitech USB Gaming Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.470] (II) XINPUT: Adding extended input device "Logitech USB Gaming Mouse" (type: MOUSE)
[    19.470] (II) Logitech USB Gaming Mouse: initialized for relative axes.
[    19.471] (II) config/udev: Adding input device Logitech USB Gaming Mouse (/dev/input/mouse0)
[    19.471] (II) No input driver/identifier specified (ignoring)
[    19.481] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    19.481] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    19.481] (**) AT Translated Set 2 keyboard: always reports core events
[    19.481] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    19.550] (II) AT Translated Set 2 keyboard: Found keys
[    19.550] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    19.550] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    19.550] (**) Option "xkb_rules" "evdev"
[    19.550] (**) Option "xkb_model" "pc105"
[    19.550] (**) Option "xkb_layout" "us"
[  1781.673] (II) Open ACPI successful (/var/run/acpid.socket)
[  1781.722] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[  1781.990] (II) Power Button: Device reopened after 1 attempts.
[  1782.030] (II) Power Button: Device reopened after 1 attempts.
[  1782.080] (II) Logitech USB Gaming Mouse: Device reopened after 1 attempts.
[  1782.160] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
```

---

### Post by GreatKeyHunter on 2011-01-05
maybe its a problem with the nvidia driver 260.19.29

I tried running in the terminal compiz --replace and it said the following
compiz: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_property_to_quads

---

### Post by GreatKeyHunter on 2011-01-05
Fixed it. I reinstalled everything related to compiz following this thread [http://ubuntuforums.org/showthread.php?t=1593523](http://ubuntuforums.org/showthread.php?t=1593523)

---


---
title: "CPU Overheat in 11.04 xubuntu"
date: 2011-05-04
forum: General Help
---

### Post by rtk217 on 2011-05-04
I'll try to give out as much details as possible but this issue is very troubling.
I used to work with maverick until the final natty xubuntu went online the other day.

So I'm now working with Xubuntu 11.04 amd64
Since i started working with it im experiencing on my PC a serious overheat causing the computer to shut itself down and to my LED screen on the mother board to report more then 100C degrees of the cpu...
this never happened before, and after some testing i found out that i only happens in full screen opengl game (Enemy territory- shuts itself after 6 minutes) and full screen flash movie playing (such as mega video- shuts itselfs after 10-15 minutes).
I don't use stock cooling im using a arctic freezer 64 pro. and i clean my computer and put new thermal grease every couple of months (i also did it again after the problem started).

now for the specs:
I'll just add that the only other thing changed is the fglrx drivers which i now use the 11.4 catalyst.
```
Summary Computer Processor2x AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ Memory4057MB (1662MB used) Operating SystemUbuntu 11.04 User Nameroy (roy) Date/TimeThu 05 May 2011 12:19:00 AM IDT Display Resolution1680x1050 pixels OpenGL RendererATI Radeon HD 3850 X11 VendorThe X.Org Foundation Multimedia Audio AdapterHDA-Intel - HDA ATI SB Audio AdapterHDA-Intel - HDA ATI HDMI 


 Power Button
 AT Translated Set 2 keyboard
 Logitech USB Optical Mouse
 HDA ATI SB Headphone
Printers (CUPS) Officejet-5600-series*Default* Officejet-5600-series-Fax
SCSI Disks ATA WDC WD1600JB-00R
ATA Maxtor 6Y080M0
ATA ST3500320AS
TSSTcorp CDDVDW SH-S223C
Operating System Version KernelLinux 2.6.38-9-generic (x86_64) Compiled#43-Ubuntu SMP Thu Apr 28 15:23:06 UTC 2011 C LibraryUnknown Default C CompilerGNU C Compiler version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4)  DistributionUbuntu 11.04 Current Session Computer Nameroy-server User Nameroy (roy) Home Directory/home/roy Desktop EnvironmentXFCE 4 Misc Uptime11 hours, 8 minutes Load Average0.22, 0.24, 0.15 Kernel Modules Loaded Modules nls_utf8
isofs
vesafb
vboxnetadpOracle VM VirtualBox Network Adapter Driver vboxnetfltOracle VM VirtualBox Network Filter Driver vboxdrvOracle VM VirtualBox Support Driver nfsd
lockdNFS file locking service version 0.5. nfs_acl
auth_rpcgss
sunrpc
exportfs
snd_hda_codec_hdmiHDMI HD-audio codec snd_hda_codec_realtekRealtek HD-audio codec snd_hda_intelIntel HDA driver snd_hda_codecHDA codec core snd_hwdepHardware dependent layer snd_pcmMidlevel PCM code for ALSA. usblpUSB Printer Device Class driver snd_seq_midiAdvanced Linux Sound Architecture sequencer MIDI synth. snd_rawmidiMidlevel RawMidi code for ALSA. snd_seq_midi_eventMIDI byte <-> sequencer event coder snd_seqAdvanced Linux Sound Architecture sequencer. edac_coreCore library routines for EDAC reporting snd_timerALSA timer interface fglrxATI Fire GL snd_seq_deviceALSA sequencer device management k8tempAMD K8 core temperature monitor edac_mce_amdAMD MCE decoder sp5100_tcoTCO timer driver for SP5100 chipset sndAdvanced Linux Sound Architecture driver for soundcards. i2c_piix4PIIX4 SMBus driver soundcoreCore sound module snd_page_allocMemory allocator for ALSA system. usbhidUSB HID core driver hid
ahciAHCI SATA low-level driver floppy
libahciCommon AHCI SATA low-level routines sky2Marvell Yukon 2 Gigabit Ethernet driver pata_atiixplow-level driver for ATI IXP200/300/400 
Filesystems Mounted File Systems   /dev/sdb1/41.95 % (24.7 GiB of 42.5 GiB)   none/dev0.04 % (1.9 GiB of 1.9 GiB)   none/dev/shm0.25 % (1.9 GiB of 1.9 GiB)   none/var/run0.03 % (1.9 GiB of 1.9 GiB)   none/var/lock0.00 % (1.9 GiB of 1.9 GiB)   /dev/sdb5/media/Backups92.63 % (2.2 GiB of 29.5 GiB)   /dev/sdc1/media/Downloads72.66 % (127.4 GiB of 465.8 GiB)   /dev/sda1/media/WDC83.76 % (24.2 GiB of 149.0 GiB) Display Display Resolution1680x1050 pixels VendorThe X.Org Foundation Version1.10.1 Monitors Monitor 01680x1050 pixels Extensions AMDXVBA
AMDXVOPL
ATIFGLEXTENSION
ATIFGLRXDRI
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
GestureExtension
MIT-SCREEN-SAVER
MIT-SHM
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
XVideo-MotionCompensation
glesx
OpenGL VendorATI Technologies Inc. RendererATI Radeon HD 3850 Version3.3.10665 Compatibility Profile Context Direct RenderingYes Environment Variables Environment Variables GDM_KEYBOARD_LAYOUTus USERroy LANGUAGEen_US:en SSH_AGENT_PID1630 HOME/home/roy GTK_PATH:/usr/lib/gtk-2.0 XDG_SESSION_COOKIE04ac37bfa7c73b930f08c50b00000009-1304503862.878819-418952508 DESKTOP_SESSIONxubuntu GTK_MODULEScanberra-gtk-module DBUS_SESSION_BUS_ADDRESSunix:abstract=/tmp/dbus-hA6G4R71LL,guid=7c8fde36299f5497494632010000003d GLADE_MODULE_PATH: MANDATORY_PATH/usr/share/gconf/xubuntu.mandatory.path LOGNAMEroy DEFAULTS_PATH/usr/share/gconf/xubuntu.default.path USERNAMEroy WINDOWPATH7 GLADE_PIXMAP_PATH: GDM_LANGen_US.UTF-8 PATH/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/games XDG_MENU_PREFIXxfce- LANGen_US.UTF-8 XAUTHORITY/var/run/gdm/auth-for-roy-xB2om2/database GLADE_CATALOG_PATH: SSH_AUTH_SOCK/tmp/ssh-fEWZQWaq1580/agent.1580 SHELL/bin/bash GDMSESSIONxubuntu PWD/home/roy LIBGLADE_MODULE_PATH: XDG_CONFIG_DIRS/etc/xdg/xdg-xubuntu:/etc/xdg:/etc/xdg XDG_DATA_DIRS/usr/share/xubuntu:/usr/share/xubuntu:/usr/local/share/:/usr/share/:/usr/share LIBGL_DRIVERS_PATH/usr/lib/fglrx/dri:/usr/lib32/fglrx/dri SESSION_MANAGERlocal/roy-server:@/tmp/.ICE-unix/1667,unix/roy-server:/tmp/.ICE-unix/1667 DISPLAY:0.0
```

---

### Post by rtk217 on 2011-05-04
I should also add that i tested some stuff out.
regressing to kernel 2.6.35/2.6.37 or tryin the 2.6.39 did not help at all.
in ET game there is an option to diable opengl extensions. when i did that the CPU did not overheat, but the game was unplayable with an average of 25 FPS rate.
Things i did not try is : replacing fglrx with mesa driver.
replacing catalyst 11.4 with older versions.
and i should also probably post my xorg.conf:

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

---

### Post by 4Orbs on 2011-05-04
I suggest turning off compositing in Settings Manager->Window Manager Tweaks, then reboot and try it again.

---

### Post by rtk217 on 2011-05-04
I'm not a fan of Eye candy stuff, looking for functionalty, the compositor was turned off since the beginning of my use. any other suggestion, also the tear free is disabled.
and while im talking about opengl overheat you should take notice its the CPU thats overheating and not the GPU.

---

### Post by 4Orbs on 2011-05-04
The problems I have encountered with Xubuntu seem to be related to two things; either the ati proprietary driver, or pulseaudio. Hope you get it sorted out.

---

### Post by cokicd on 2011-05-04
Try 2.6.32 kernel. I have similar problems with newer kernels.

---

### Post by rtk217 on 2011-05-04
As I was saying I had no issues what so ever under maverick with 2.6.35/36
but those kernels under natty still extremely overheats my CPU.
However I will take your advice and give it a try 2.6.32 kernel.

I'm going to try the latest  v2.6.32.38.17 -lucid amd64 2/5/11
hope it will work

> DEPmode while insallign the kernel didnt succeed in importing the fglrx module.
so ill need to manually install it later, ill postpone the testing until tommorow.

---

### Post by rtk217 on 2011-05-05
As Expected the system did not boot up with the 2.6.32.38.17 Kernel.
So I'm probably going to regress to 10.10 until this issue will have any kind of solution

---

### Post by salingpusa on 2011-11-07
i think this is a problem with the tear free from ati catalyst. using it both in windows and ubuntu 11. just by watching movies - computer (netbook !!! - wind u230 ), undervolted, will overheat and shutdown. powernow enabled - still same results. upon checking whats new with the latest catalyst, i found that tear free is enabled. i disabled it and so far system is stable.

---

### Post by youWho on 2012-01-16
This might not be relevant to your specific situation, but then it might be... I'm using ubuntu studio natty (64 bit) and when I first installed it there were often moments when for no apparent reason something would start consuming 100% of CPU, the fan would start running at full speed and that's what would tip me off that it had happened. Anyway the solution in my case was to use the nvidia driver, as I described here:

[http://ubuntuforums.org/showthread.php?t=1797981](http://ubuntuforums.org/showthread.php?t=1797981)

Hopefully it helps you.

---


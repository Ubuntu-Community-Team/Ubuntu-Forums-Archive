---
title: "Ubuntu hangs before loading the login screen"
date: 2011-05-16
forum: General Help
---

### Post by leviathan8 on 2011-05-16
Hello.
This problem started like one week ago, and I thought it might work itself out over time, but it didn't, and now the rate of the problem is increasing.

So, here's the deal. I boot my Dell N5010 laptop, and right before the Plymouth screen appears (the purple screen with logo), the display will just go black and hang for 30 seconds, then after that the cooler will go up to maximum and the laptop will simply shutdown. Anyway, after booting it again, works just fine, but I don't really feel like booting everyday twice my laptop just to get it working. 
I've had other issues in the past with my Intel HD Graphics IGP, more accurately crashes, but those were fixed. And now this, and I can't really think why this happens and how to solve this. 
Just as a note, I have the package "uswsusp" installed, so when booting Ubuntu actually, only a text containing "resume libgcrypt version 1.4.x" appears, and only after that, normally, the Plymouth screen appears, then I'm directly into the desktop ready to go. 

I don't really know what logs should I post. I've checked several of them, even the boots, and it doesn't show it. Basically, Ubuntu is unaware of that faulty boot, therefore doesn't log it.

Anyway, here are some specs that might help:

lshw

```
mono@mono-laptop:~$ sudo lshw -short
H/W path           Device      Class          Description
=========================================================
                               system         Inspiron N5010
/0                             bus            0WXY9J
/0/4                           processor      Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
/0/4/5                         memory         64KiB L1 cache
/0/4/6                         memory         512KiB L2 cache
/0/4/7                         memory         3MiB L3 cache
/0/4/0.1                       processor      Logical CPU
/0/4/0.2                       processor      Logical CPU
/0/4/0.3                       processor      Logical CPU
/0/4/0.4                       processor      Logical CPU
/0/4/0.5                       processor      Logical CPU
/0/4/0.6                       processor      Logical CPU
/0/4/0.7                       processor      Logical CPU
/0/4/0.8                       processor      Logical CPU
/0/4/0.9                       processor      Logical CPU
/0/4/0.a                       processor      Logical CPU
/0/4/0.b                       processor      Logical CPU
/0/4/0.c                       processor      Logical CPU
/0/4/0.d                       processor      Logical CPU
/0/4/0.e                       processor      Logical CPU
/0/4/0.f                       processor      Logical CPU
/0/4/0.10                      processor      Logical CPU
/0/1d                          memory         2GiB System Memory
/0/1d/0                        memory         2GiB DIMM Synchronous 1333 MHz (0.8 ns)
/0/1d/1                        memory         DIMM [empty]
/0/0                           memory         64KiB BIOS
/0/1                           processor      
/0/1/0.1                       processor      Logical CPU
/0/1/0.2                       processor      Logical CPU
/0/1/0.3                       processor      Logical CPU
/0/1/0.4                       processor      Logical CPU
/0/1/0.5                       processor      Logical CPU
/0/1/0.6                       processor      Logical CPU
/0/1/0.7                       processor      Logical CPU
/0/1/0.8                       processor      Logical CPU
/0/1/0.9                       processor      Logical CPU
/0/1/0.a                       processor      Logical CPU
/0/1/0.b                       processor      Logical CPU
/0/1/0.c                       processor      Logical CPU
/0/1/0.d                       processor      Logical CPU
/0/1/0.e                       processor      Logical CPU
/0/1/0.f                       processor      Logical CPU
/0/1/0.10                      processor      Logical CPU
/0/100                         bridge         Core Processor DRAM Controller
/0/100/2                       display        Core Processor Integrated Graphics Controller
/0/100/16                      communication  5 Series/3400 Series Chipset HECI Controller
/0/100/1a                      bus            5 Series/3400 Series Chipset USB2 Enhanced Host Controller
/0/100/1b                      multimedia     5 Series/3400 Series Chipset High Definition Audio
/0/100/1c                      bridge         5 Series/3400 Series Chipset PCI Express Root Port 1
/0/100/1c.1                    bridge         5 Series/3400 Series Chipset PCI Express Root Port 2
/0/100/1c.1/0      eth1        network        Broadcom Corporation
/0/100/1c.2                    bridge         5 Series/3400 Series Chipset PCI Express Root Port 3
/0/100/1c.2/0      eth0        network        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
/0/100/1c.4                    bridge         5 Series/3400 Series Chipset PCI Express Root Port 5
/0/100/1d                      bus            5 Series/3400 Series Chipset USB2 Enhanced Host Controller
/0/100/1e                      bridge         82801 Mobile PCI Bridge
/0/100/1f                      bridge         Mobile 5 Series Chipset LPC Interface Controller
/0/100/1f.2        scsi0       storage        5 Series/3400 Series Chipset 6 port SATA AHCI Controller
/0/100/1f.2/0      /dev/sda    disk           500GB WDC WD5000BEVT-7
/0/100/1f.2/0/1    /dev/sda1   volume         258GiB EXT3 volume
/0/100/1f.2/0/3    /dev/sda3   volume         206GiB Extended partition
/0/100/1f.2/0/3/5  /dev/sda5   volume         1907MiB Linux swap / Solaris partition
/0/100/1f.2/0/3/6  /dev/sda6   volume         205GiB Linux filesystem partition
/0/100/1f.2/1      /dev/cdrom  disk           DVD+-RW TS-L633C
/0/100/1f.3                    bus            5 Series/3400 Series Chipset SMBus Controller
/0/100/1f.6                    generic        5 Series/3400 Series Chipset Thermal Subsystem
/1                             power          DELL 8NH550A

```

lsmod

```
mono@mono-laptop:~$ lsmod
Module                  Size  Used by
michael_mic             1732  4 
arc4                    1153  2 
binfmt_misc             6587  1 
joydev                  8740  0 
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_idt      52010  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
btusb                  10957  0 
bluetooth              49892  1 btusb
snd_hda_intel          22069  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
dell_wmi                1793  0 
i915                  287810  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               57310  0 
drm_kms_helper         29329  1 i915
snd                    54180  17 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211_crypt_tkip     7596  0 
dell_laptop             6888  0 
usbhid                 36110  0 
hid                    67096  1 usbhid
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
drm                   162345  3 i915,drm_kms_helper
soundcore               6620  1 snd
psmouse                63245  0 
serio_raw               3978  0 
wl                   1959598  0 
dcdbas                  5422  1 dell_laptop
lib80211                5046  2 lib80211_crypt_tkip,wl
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  1 lp
ahci                   32200  2 
r8169                  34108  0 
mii                     4381  1 r8169

```

lspci

```
mono@mono-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
12:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

lsusb

```
mono@mono-laptop:~$ lsusb
Bus 002 Device 006: ID 413c:8160 Dell Computer Corp. 
Bus 002 Device 005: ID 413c:8162 Dell Computer Corp. 
Bus 002 Device 004: ID 413c:8161 Dell Computer Corp. 
Bus 002 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:641d Microdia 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Here are some images, I have no idea if it helps:

[IMG]http://i.imgur.com/3BiZg.png[/IMG]

[IMG]http://i.imgur.com/sUT3v.png[/IMG]

[IMG]http://i.imgur.com/wB99m.png[/IMG]

---

### Post by jerrrys on 2011-05-17
some simple things to try:

check for [broken packages]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=fix+broken+packages&as_qdr=all&sa=Google+Search&lang=en#881")

maybe drop back one kernel and see if it helps

notice that your running a usb hub.  if this has been working right in the past, its probably ok.  but hubs can cause problems.

---

### Post by leviathan8 on 2011-05-18
> **jerrrys said:**
> some simple things to try:

check for [broken packages]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=fix+broken+packages&as_qdr=all&sa=Google+Search&lang=en#881")

maybe drop back one kernel and see if it helps

notice that your running a usb hub.  if this has been working right in the past, its probably ok.  but hubs can cause problems.

No, I never connect any usb's before booting. I know that these cause problems. 
Apparently, the hang was caused by a SD card that was inserted into the card adapter slot. But this has been dong while the system was running, and it was unmounted correctly. However, after a cold boot, it seems to hang. To confirm this assumption, I have done a testing right on this, and it seems to be correct. Well, I guess there is nothing to be done.
Maybe a new kernel, or a newer version in the future will fix this (I have no intention to upgrade now).

Thanks for help. I'll keep the thread bumped if anything else appears.

---


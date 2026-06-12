---
title: "Which one is my webcam driver ?"
date: 2011-09-18
forum: General Help
---

### Post by cap10Ibraim on 2011-09-18
):P
Which one is my webcam driver ?
```

ibrahim@ibrahim-U405:~$ lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
binfmt_misc            13213  1 
joydev                 17322  0 
snd_hda_codec_conexant    43782  1 
nfsd                  252397  11 
lockd                  74292  1 nfsd
nfs_acl                12771  1 nfsd
auth_rpcgss            39173  1 nfsd
sunrpc                199096  12 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs               12870  1 nfsd
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
arc4                   12473  2 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
iwlagn                284745  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
iwlcore               148964  1 iwlagn
mac80211              257001  2 iwlagn,iwlcore
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  451033  3 
videodev               75143  1 uvcvideo
soundcore              12600  1 snd
drm_kms_helper         40745  1 i915
cfg80211              156212  3 iwlagn,iwlcore,mac80211
drm                   184164  4 i915,drm_kms_helper
sparse_keymap          13666  0 
i2c_algo_bit           13184  1 i915
psmouse                73312  0 
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
ahci                   21591  2 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
sky2                   49172  0 
libahci                25548  1 ahci

```
if it's not here how to find it ?

---

### Post by TeoBigusGeekus on 2011-09-18
If it's built in, try with
```
lspci
```
If it's a usb one, try with
```
lsusb
```

---

### Post by cap10Ibraim on 2011-09-18
It's a built-in webcam (cheese is working , so it's there some where!)
```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
08:00.0 Network controller: Intel Corporation WiFi Link 5100
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```

---

### Post by TeoBigusGeekus on 2011-09-18
Can't see it...
What's the output of lsusb?

---

### Post by cap10Ibraim on 2011-09-18
oh I figured because it's built in there is no need to check lsusb anyway here it is 
```

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
maybe it's Bus 002 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd  ?

---

### Post by TeoBigusGeekus on 2011-09-18
Could be...
What do you have plugged in your usb slots?

---

### Post by cap10Ibraim on 2011-09-18
Yes it's I just checked google , thanks man 
do you know how can I edit the driver file or where is the actual driver file ?

---

### Post by TeoBigusGeekus on 2011-09-18
Why? Where does your webcam fail you?

---

### Post by no2498 on 2011-09-18
in a terminal type dmesg click enter
that will tell you the driver

---

### Post by cap10Ibraim on 2011-09-18
I want it to work , but with the blue light thing off 
maybe there is a simple bool(int) variable that I can switch

---

### Post by TeoBigusGeekus on 2011-09-18
> **cap10Ibraim said:**
> I want it to work , but with the blue light thing off 
maybe there is a simple bool(int) variable that I can switch

With what specific software?

---

### Post by cap10Ibraim on 2011-09-18
Cheese , should I check cheese code or the driver it self ?

---

### Post by TeoBigusGeekus on 2011-09-18
Sorry, misunderstanding...
I thought you meant that it works in cheese.

---

### Post by cap10Ibraim on 2011-09-18
this was the output of lsusb for the camera 
us 002 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
so I typed 
```

ibrahim@ibrahim-U405:~$ dmesg | grep '04f2:b070'
[   22.714353] uvcvideo: Found UVC 1.00 device CNF7051 (04f2:b070)
ibrahim@ibrahim-U405:~$ lsmod uvcvideo
Usage: lsmod
ibrahim@ibrahim-U405:~$ modinfo uvcvideo
filename:       /lib/modules/2.6.38-11-generic/kernel/drivers/media/video/uvc/uvcvideo.ko
version:        v1.0.0
license:        GPL
description:    USB Video Class driver
author:         Laurent Pinchart <laurent.pinchart@ideasonboard.com>
srcversion:     4A2FAF04A524B0EDCD414F9
alias:          usb:v*p*d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v1C4Fp3000d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v1B3Bp2951d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v19ABp1000d00*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v19ABp1000d01[0-1]*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v19ABp1000d012[0-6]dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v18ECp3290d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v18ECp3288d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v18ECp3188d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v18CDpCAFEd*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v1871p0306d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v17EFp480Bd*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v17DCp0202d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v174Fp8A34d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v174Fp8A33d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v174Fp8A31d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v174Fp8A12d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v174Fp5931d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v174Fp5212d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v13D3p5103d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v0E8Dp0004d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v0AC8p3420d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v0AC8p3410d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v0AC8p332Dd*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v05E3p0505d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v05ACp8501d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v058Fp3820d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v04F2pB071d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v046Dp08C7d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C6d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C5d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C3d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C2d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C1d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v045Ep0723d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v045Ep00F8d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v0458p706Ed*dc*dsc*dp*ic0Eisc01ip00*
depends:        videodev
vermagic:       2.6.38-11-generic SMP mod_unload modversions 686 
parm:           clock:Video buffers timestamp clock
parm:           nodrop:Don't drop incomplete frames (uint)
parm:           quirks:Forced device quirks (uint)
parm:           trace:Trace level bitmask (uint)
parm:           timeout:Streaming control requests timeout (uint)

```
is this the driver file ?

---

### Post by TeoBigusGeekus on 2011-09-18
Yes. 
From a quick google search, I've found that this is the proper driver for your webcam.

---

### Post by cap10Ibraim on 2011-09-18
is git.kernel.org also down ?

---

### Post by no2498 on 2011-09-18
for the blue light a piece of black tape
as for cheese it uses gstreamer and ubuntu/linux is not loading all of it
for gstreamer you need the good set,bad set,ugly set and the 0.10 from the bad set for the package's you use
and for cheese
in a terminal type copy/paste
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
click enter

---

### Post by cap10Ibraim on 2011-09-18
because kernel.org is down 
I need help to get the source code for this specific driver can I use Ubuntu repositories or .. ?

---


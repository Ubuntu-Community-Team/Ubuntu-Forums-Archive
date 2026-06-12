---
title: "no wireless after new 10.04/installed ndiswraper, cant find inf.file"
date: 2011-10-15
forum: General Help
---

### Post by mejbr2003 on 2011-10-15
Hi, thanks for reading!
this is a new dual boot 10.04 install with xp. the belkin N150 wireless usb adapter functions perfectly, connecting to netgear router, in windows...but not in ubuntu.

it took me forever to get ndiswrapper to install, got it finally. but now I just can't seem to get a inf file off the belkin disc.

I've tried other suggested methods to connect, I can't tell you exactly what they were, but none worked...obviously.
If you haven't guessed I have little experience speaking about and conducting ubuntu operations.

please help...I hate using windowss.

thank you very much

---

### Post by gandaran on 2011-10-16
> **mejbr2003 said:**
> Hi, thanks for reading!
this is a new dual boot 10.04 install with xp. the belkin N150 wireless usb adapter functions perfectly, connecting to netgear router, in windows...but not in ubuntu.

it took me forever to get ndiswrapper to install, got it finally. but now I just can't seem to get a inf file off the belkin disc.

I've tried other suggested methods to connect, I can't tell you exactly what they were, but none worked...obviously.
If you haven't guessed I have little experience speaking about and conducting ubuntu operations.

please help...I hate using windowss.

thank you very much
why do you go the windows driver with ndiswrapper way when your adapter if I'm not mistaken is supposed to work on Ubuntu?
if the adapter uses the ralink chipset it will be very easy to set up, no need to install drivers.
please post the output of
```
lsusb
```
and
```
lsmod
```

---

### Post by mejbr2003 on 2011-10-16
thanks for helping

j@mydamncomputer:~$ lsusb
Bus 005 Device 003: ID 04f3:01a4 Elan Microelectronics Corp.
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c506 Logitech, Inc. MX-700 Cordless Mouse Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:945a Belkin Components
Bus 001 Device 002: ID 1307:0163 Transcend Information, Inc. 512MB/1GB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
j@mydamncomputer:~$ lsmod
Module Size Used by
nls_iso8859_1 3249 1
nls_cp437 4919 1
vfat 8933 1
fat 47767 1 vfat
nls_utf8 1069 1
isofs 29250 1
binfmt_misc 6587 1
ppdev 5259 0
snd_hda_codec_realtek 203376 1
fbcon 35102 71
tileblit 1999 1 fbcon
font 7557 1 fbcon
bitblit 4707 1 fbcon
softcursor 1189 1 bitblit
vga16fb 11385 0
vgastate 8961 1 vga16fb
snd_hda_intel 22069 2
snd_hda_codec 74201 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 5412 1 snd_hda_codec
snd_pcm_oss 35308 0
snd_mixer_oss 13746 1 snd_pcm_oss
snd_pcm 70694 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4 1153 2
snd_seq_dummy 1338 0
snd_seq_oss 26722 0
snd_seq_midi 4557 0
snd_rawmidi 19056 1 snd_seq_midi
snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi
snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 19098 2 snd_pcm,snd_seq
snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
b43 163556 0
mac80211 205402 1 b43
i915 288611 3
snd 54244 16
snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pc
m,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211 126144 2 b43,mac80211
drm_kms_helper 29329 1 i915
ndiswrapper 184677 0
led_class 2864 1 b43
joydev 8740 0
intel_agp 24375 2 i915
soundcore 6620 1 snd
drm 162377 4 i915,drm_kms_helper
i2c_algo_bit 5028 1 i915
lp 7028 0
psmouse 63677 0
serio_raw 3978 0
snd_page_alloc 7076 2 snd_hda_intel,snd_pcm
agpgart 31724 2 intel_agp,drm
video 17375 1 i915
output 1871 1 video
parport 32635 2 ppdev,lp
usbhid 36110 0
ohci1394 26950 0
e100 28211 0
hid 67288 1 usbhid
ssb 38934 1 b43
mii 4381 1 e100
ieee1394 81181 1 ohci1394
usb_storage 39841 1

---

### Post by gandaran on 2011-10-16
> ndiswrapper 184677 0
can you remove ndiswrapper then reboot and post again the output of
```
lsmod
```
I have encountered a small problem while searching, some articles say the belkin N150 (Device 003: ID 050d:945a) has a realtek chipset (RTL8192SU) while others mention  ralink chipset, can you somehow confirm from the windows drivers if it really is realtek RTL8192SU?
in case it's the RTL8192SU chip you will have to install the driver on ubuntu 10.04, 10.10 requires a minor fix with firmware and only on 11.04 and 11.10 it works out of the box.
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU)

---

### Post by mejbr2003 on 2011-10-16
j@mydamncomputer:~$ lsmod
Module Size Used by
nls_iso8859_1 3249 1
nls_cp437 4919 1
vfat 8933 1
nls_utf8 1069 1
fat 47767 1 vfat
isofs 29250 1
binfmt_misc 6587 1
ppdev 5259 0
snd_hda_codec_realtek 203376 1
fbcon 35102 71
tileblit 1999 1 fbcon
font 7557 1 fbcon
bitblit 4707 1 fbcon
softcursor 1189 1 bitblit
vga16fb 11385 0
vgastate 8961 1 vga16fb
snd_hda_intel 22069 2
snd_hda_codec 74201 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 5412 1 snd_hda_codec
snd_pcm_oss 35308 0
snd_mixer_oss 13746 1 snd_pcm_oss
snd_pcm 70694 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4 1153 2
snd_seq_dummy 1338 0
snd_seq_oss 26722 0
snd_seq_midi 4557 0
snd_rawmidi 19056 1 snd_seq_midi
snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi
snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
b43 163556 0
snd_timer 19098 2 snd_pcm,snd_seq
i915 288611 3
snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211 205402 1 b43
drm_kms_helper 29329 1 i915
ndiswrapper 184677 0
cfg80211 126144 2 b43,mac80211
psmouse 63677 0
drm 162377 4 i915,drm_kms_helper
snd 54244 16
snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pc
m,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class 2864 1 b43
serio_raw 3978 0
intel_agp 24375 2 i915
joydev 8740 0
i2c_algo_bit 5028 1 i915
soundcore 6620 1 snd
lp 7028 0
agpgart 31724 2 drm,intel_agp
video 17375 1 i915
output 1871 1 video
snd_page_alloc 7076 2 snd_hda_intel,snd_pcm
parport 32635 2 ppdev,lp
usbhid 36110 0
ohci1394 26950 0
e100 28211 0
hid 67288 1 usbhid
ieee1394 81181 1 ohci1394
ssb 38934 1 b43
mii 4381 1 e100
usb_storage 39841 2
j@mydamncomputer:~$

---


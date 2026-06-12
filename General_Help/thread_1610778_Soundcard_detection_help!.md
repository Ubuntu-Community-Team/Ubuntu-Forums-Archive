---
title: "Soundcard detection help!"
date: 2010-11-01
forum: General Help
---

### Post by Aarohi on 2010-11-01
This is my auto-generated alsa configuration information file:

```
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Mon Nov  1 09:09:53 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Dell Inc.
Product Name:      Inspiron N5010


!!Kernel Information
!!------------------

Kernel release:    2.6.35-22-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:3b56 (rev 06)
	Subsystem: 1028:0447


!!Modprobe options (Sound related)
!!--------------------------------

snd-hda-intel: model=dell-m6
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 3 Nov  1 09:59 /dev/snd/seq
crw-rw----  1 root audio 116, 2 Nov  1 09:59 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:235: no soundcards found...

ARECORD

arecord: device_list:235: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
parport_pc
dm_crypt
ppdev
cryptd
aes_x86_64
aes_generic
binfmt_misc
rfcomm
sco
bnep
l2cap
snd_hda_intel
snd_hda_codec
joydev
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
btusb
bluetooth
snd_seq
snd_timer
snd_seq_device
snd
lib80211_crypt_tkip
psmouse
wl
uvcvideo
videodev
v4l1_compat
dell_wmi
dell_laptop
v4l2_compat_ioctl32
soundcore
dcdbas
serio_raw
intel_ips
snd_page_alloc
lib80211
lp
parport
usbhid
hid
i915
drm_kms_helper
drm
ahci
libahci
i2c_algo_bit
r8169
video
mii
intel_agp
output


!!ALSA/HDA dmesg
!!------------------




```

There is no soundcard being detected. Among all the other modules in modprobe.d/alsa-base.conf, I added "options snd-hda-intel model=dell-m6". When I force alsa to restart using alsa force-reload, the process seems to get stuck at "unloading alsa sound driver: snd-hda-intel".

Thank you for your help.

---

### Post by seventyeights on 2010-11-03
> When I force alsa to restart using alsa force-reload, the process seems to get stuck at "unloading alsa sound driver: snd-hda-intel".


Same here, on an Acer 7741Z with intel 5/3400 series audio and realtek alc272 codec.

Here are some alsa info pages for comparison:

10.10 (no sound device found)
[http://www.alsa-project.org/db/?f=bb249813a67ea60eedc03c513993db065542e176]("http://www.alsa-project.org/db/?f=bb249813a67ea60eedc03c513993db065542e176")

10.04 live cd (sound works)
[http://www.alsa-project.org/db/?f=30f25d44085c92428a2c4f86c4f6ab332797cb0c]("http://www.alsa-project.org/db/?f=30f25d44085c92428a2c4f86c4f6ab332797cb0c")

fedora 14 live cd (sound works)
[ http://www.alsa-project.org/db/?f=d8d364138309a98a3062b9084a711317e136497c]("http://www.alsa-project.org/db/?f=d8d364138309a98a3062b9084a711317e136497c")

(please note that the live cd loaded driver uses underscores, not hyphens , e.g. snd_hda_intel)

---

### Post by seventyeights on 2010-11-07
Adding Alsa info page for 10.04 full install. (sound works)

[http://www.alsa-project.org/db/?f=3fc1edc2753c69484ebb85fa46baee49c577ec86]("http://www.alsa-project.org/db/?f=3fc1edc2753c69484ebb85fa46baee49c577ec86")


I am going to reinstall 10.10 soon, but this time the 64 bit version.

---


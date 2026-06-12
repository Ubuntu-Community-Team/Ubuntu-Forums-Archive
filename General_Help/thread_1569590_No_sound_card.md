---
title: "No sound card?"
date: 2010-09-06
forum: General Help
---

### Post by enigmaingr on 2010-09-06
Hello,

I've made several attempts to solve my sound issues to no avail.  Here is the file for the Alsa script:

[http://www.alsa-project.org/db/?f=2db4fc70f7d5a2868c06de70f2756e45b0a2313b](http://www.alsa-project.org/db/?f=2db4fc70f7d5a2868c06de70f2756e45b0a2313b)

Any advice would be greatly appreciated!

!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Tue Sep  7 03:45:24 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      BIOSTAR Group
Product Name:      945GC-M4


!!Kernel Information
!!------------------

Kernel release:    2.6.32-24-generic
Operating System:  GNU/Linux
Architecture:      i686
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

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 01)
	Subsystem: 1565:821f


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: probe_mask=1


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  1 Sep  6 23:31 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Sep  6 23:31 /dev/snd/timer


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
binfmt_misc
fbcon
tileblit
font
bitblit
softcursor
vga16fb
vgastate
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
arc4
snd_seq
i915
rt2500pci
snd_timer
rt2x00pci
snd_seq_device
drm_kms_helper
rt2x00lib
led_class
usbhid
ppdev
drm
i2c_algo_bit
mac80211
snd
hid
intel_agp
video
parport_pc
cfg80211
eeprom_93cx6
lp
soundcore
output
agpgart
snd_page_alloc
parport
floppy
usb_storage
r8169
mii


!!ALSA/HDA dmesg
!!------------------

[   15.103708] vga16fb: not registering due to another framebuffer present
[   15.111418] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.111484]   alloc irq_desc for 27 on node -1
[   15.111487]   alloc kstat_irqs on node -1
[   15.111501] HDA Intel 0000:00:1b.0: irq 27 for MSI/MSI-X
[   15.111532] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.146629] ALSA hda_intel.c:1447: no codecs initialized
[   15.146776] HDA Intel 0000:00:1b.0: PCI INT A disabled
[   15.257880] Console: switching to colour frame buffer device 240x67

---

### Post by enigmaingr on 2010-09-07
Any leads?  I've tried a number of solutions already posted to no avail.

---


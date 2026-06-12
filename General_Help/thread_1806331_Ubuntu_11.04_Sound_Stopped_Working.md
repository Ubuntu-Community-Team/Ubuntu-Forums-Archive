---
title: "Ubuntu 11.04 Sound Stopped Working ???"
date: 2011-07-17
forum: General Help
---

### Post by chris301up on 2011-07-17
I have recently installed Ubuntu 11.04 on my IBM T30 laptop and, until yesterday, it was working fine.

Now, when I try to play music, there is no longer any sound.

The sound isn't muted and I get the following readout:

!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sun Jul 17 19:41:25 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.04"


!!DMI Information
!!---------------

Manufacturer:      IBM
Product Name:      236683G
Product Version:   Not Available


!!Kernel Information
!!------------------

Kernel release:    2.6.38-10-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------

thinkpad_acpi


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

29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw 1IHT20WW-1.07


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1f.5 0401: 8086:2485 (rev 02)
	Subsystem: 1014:0508


!!Modprobe options (Sound related)
!!--------------------------------

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

!!Module: thinkpad_acpi
	brightness_enable : 2
	brightness_mode : 2
	dbg_bluetoothemul : 0
	dbg_uwbemul : 0
	dbg_wlswemul : 0
	dbg_wwanemul : 0
	enable : Y
	experimental : 0
	fan_control : N
	force_load : N
	hotkey_report_mode : 0
	id : ThinkPadEC
	index : -536870912
	volume_capabilities : 0
	volume_control : N
	volume_mode : 3


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  2 Jul 17 11:52 /dev/snd/controlC29
crw-rw----  1 root audio 116,  1 Jul 17 11:52 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Jul 17 11:52 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jul 17 11:52 .
drwxr-xr-x 3 root root 120 Jul 17 11:52 ..
lrwxrwxrwx 1 root root  13 Jul 17 11:52 platform-thinkpad_acpi -> ../controlC29


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:261: snd_ctl_pcm_next_device
**** List of PLAYBACK Hardware Devices ****

ARECORD

arecord: device_list:261: snd_ctl_pcm_next_device
**** List of CAPTURE Hardware Devices ****

!!Amixer output
!!-------------

!!-------Mixer controls for card 29 [ThinkPadEC]

Card hw:29 'ThinkPadEC'/'ThinkPad Console Audio Control at EC reg 0x30, fw 1IHT20WW-1.07'
  Mixer name	: 'ThinkPad EC 1IHT20WW-1.07'
  Components	: ''
  Controls      : 2
  Simple ctrls  : 1
Simple mixer control 'Console',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 14
  Mono: Playback 11 [79%] [off]


!!Alsactl output
!!-------------

--startcollapse--
state.ThinkPadEC {
	control.1 {
		iface MIXER
		name 'Console Playback Volume'
		value 11
		comment {
			access read
			type INTEGER
			count 1
			range '0 - 14'
		}
	}
	control.2 {
		iface MIXER
		name 'Console Playback Switch'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_seq_dummy
thinkpad_acpi
radeon
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
binfmt_misc
ttm
joydev
ppdev
snd_timer
pcmcia
snd_seq_device
drm_kms_helper
nsc_ircc
hostap_pci
drm
snd
psmouse
irda
hostap
yenta_socket
parport_pc
pcmcia_rsrc
video
soundcore
lp
pcmcia_core
serio_raw
nvram
i2c_algo_bit
lib80211
crc_ccitt
parport
shpchp
ndiswrapper
e100
floppy


!!ALSA/HDA dmesg
!!--------------
[B][COLOR="Red"]
ANY SUGGESTIONS WOULD BE GREATLY APPRECIATED !![/COLOR][/B]

---


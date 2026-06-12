---
title: "Sound disapeared in 11.04"
date: 2011-06-16
forum: General Help
---

### Post by Draknof on 2011-06-16
Hello everyone, I have a Creative audigy soundcard (ca0106), and my motherboard chipset (disabled in the BIOS).
Everything was working well until today. I start my computer and no sound.

I've checked that nothing is mute, I've tried to run

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils 
then reinstall pulse audio & alsa, but it didn't work

here are more details

[http://www.alsa-project.org/db/?f=8c1b17b3593d59f19fdf6d00dcfbe434d06f190c](http://www.alsa-project.org/db/?f=8c1b17b3593d59f19fdf6d00dcfbe434d06f190c)


```
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Thu Jun 16 20:49:14 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.04"


!!DMI Information
!!---------------

Manufacturer:      System Manufact
Product Name:      System Product
Product Version:   1.0


!!Kernel Information
!!------------------

Kernel release:    2.6.38-8-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_ca0106


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfd8fc000 irq 47
 1 [CA0106         ]: CA0106 - CA0106
                      Audigy SE OEM [SB0570a] at 0x9f00 irq 22


!!PCI Soundcards installed in the system
!!--------------------------------------

01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
06:01.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

01:00.1 0403: 1002:aa30
	Subsystem: 1462:aa30
--
06:01.0 0401: 1102:0007
	Subsystem: 1102:1011


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

!!Module: snd_hda_intel
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N

!!Module: snd_ca0106
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	subsystem : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=1, channel=0
  Digital:
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=03, enabled=1
  Connection: 1
     0x02
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  4 Jun 16 22:07 /dev/snd/controlC0
crw-rw----  1 root audio 116, 14 Jun 16 22:07 /dev/snd/controlC1
crw-rw----  1 root audio 116,  3 Jun 16 22:07 /dev/snd/hwC0D0
crw-rw----  1 root audio 116,  5 Jun 16 22:07 /dev/snd/midiC1D0
crw-rw----  1 root audio 116,  2 Jun 16 22:08 /dev/snd/pcmC0D3p
crw-rw----  1 root audio 116, 13 Jun 16 22:14 /dev/snd/pcmC1D0c
crw-rw----  1 root audio 116, 12 Jun 16 22:41 /dev/snd/pcmC1D0p
crw-rw----  1 root audio 116, 11 Jun 16 22:07 /dev/snd/pcmC1D1c
crw-rw----  1 root audio 116, 10 Jun 16 22:08 /dev/snd/pcmC1D1p
crw-rw----  1 root audio 116,  9 Jun 16 22:07 /dev/snd/pcmC1D2c
crw-rw----  1 root audio 116,  8 Jun 16 22:08 /dev/snd/pcmC1D2p
crw-rw----  1 root audio 116,  7 Jun 16 22:07 /dev/snd/pcmC1D3c
crw-rw----  1 root audio 116,  6 Jun 16 22:08 /dev/snd/pcmC1D3p
crw-rw----  1 root audio 116,  1 Jun 16 22:07 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Jun 16 22:07 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Jun 16 22:07 .
drwxr-xr-x 3 root root 360 Jun 16 22:07 ..
lrwxrwxrwx 1 root root  12 Jun 16 22:07 pci-0000:01:00.1 -> ../controlC0
lrwxrwxrwx 1 root root  12 Jun 16 22:07 pci-0000:06:01.0 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [HDMI]

Card hw:0 'HDMI'/'HDA ATI HDMI at 0xfd8fc000 irq 47'
  Mixer name	: 'ATI R6xx HDMI'
  Components	: 'HDA:1002aa01,00aa0100,00100100'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]

!!-------Mixer controls for card 1 [CA0106]

Card hw:1 'CA0106'/'Audigy SE OEM [SB0570a] at 0x9f00 irq 22'
  Mixer name	: 'CA0106'
  Components	: ''
  Controls      : 35
  Simple ctrls  : 18
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 255
  Mono: Playback 204 [80%] [-12.75dB] [on]
Simple mixer control 'Line in',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 180 [71%] [-13.50dB]
  Front Right: Capture 180 [71%] [-13.50dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 42 [16%] [-82.50dB]
  Front Right: Capture 42 [16%] [-82.50dB]
Simple mixer control 'Phone',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 207 [81%] [0.00dB]
  Front Right: Capture 207 [81%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Center/LFE',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'IEC958 Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'IEC958 Rear',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'IEC958 Unknown',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'Aux',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 207 [81%] [0.00dB]
  Front Right: Capture 207 [81%] [0.00dB]
Simple mixer control 'Analog Center/LFE',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB] [on]
  Front Right: Playback 207 [81%] [0.00dB] [on]
Simple mixer control 'Analog Front',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB] [on]
  Front Right: Playback 207 [81%] [0.00dB] [on]
Simple mixer control 'Analog Rear',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB] [on]
  Front Right: Playback 207 [81%] [0.00dB] [on]
Simple mixer control 'Analog Side',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB] [on]
  Front Right: Playback 207 [81%] [0.00dB] [on]
Simple mixer control 'Analog Source',0
  Capabilities: cenum
  Items: 'Phone' 'Mic' 'Line in' 'Aux'
  Item0: 'Mic'
Simple mixer control 'CAPTURE feedback',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 55 [22%] [-38.00dB]
  Front Right: Playback 55 [22%] [-38.00dB]
Simple mixer control 'Digital Source',0
  Capabilities: cenum
  Items: 'IEC958 out' 'i2s mixer out' 'IEC958 in' 'i2s in' 'AC97 in' 'SRC out'
  Item0: 'i2s in'
Simple mixer control 'Shared Mic/Line in',0
  Capabilities: cenum
  Items: 'Line in' 'Mic in'
  Item0: 'Mic in'


!!Alsactl output
!!-------------

--startcollapse--
state.HDMI {
	control.1 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.2 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.3 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
}
state.CA0106 {
	control.1 {
		iface MIXER
		name 'Analog Front Playback Volume'
		value.0 207
		value.1 207
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 255'
			dbmin -9999999
			dbmax 1200
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.2 {
		iface MIXER
		name 'Analog Rear Playback Volume'
		value.0 207
		value.1 207
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 255'
			dbmin -9999999
			dbmax 1200
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.3 {
		iface MIXER
		name 'Analog Center/LFE Playback Volume'
		value.0 207
		value.1 207
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 255'
			dbmin -9999999
			dbmax 1200
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.4 {
		iface MIXER
		name 'Analog Side Playback Volume'
		value.0 207
		value.1 207
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 255'
			dbmin -9999999
			dbmax 1200
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.5 {
		iface MIXER
		name 'IEC958 Front Playback Volume'
		value.0 207
		value.1 207
		comment {
			access 'read write locked'
			type INTEGER
			count 2
			range '0 - 255'
			dbmin -9999999
			dbmax 1200
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.6 {
		iface MIXER
		name 'IEC958 Rear Playback Volume'
		value.0 207
		value.1 207
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 255'
			dbmin -9999999
			dbmax 1200
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.7 {
		iface MIXER
		name 'IEC958 Center/LFE Playback Volume'
		value.0 207
		value.1 207
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 255'
			dbmin -9999999
			dbmax 1200
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.8 {
		iface MIXER
		name 'IEC958 Unknown Playback Volume'
		value.0 207
		value.1 207
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 255'
			dbmin -9999999
			dbmax 1200
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.9 {
		iface MIXER
		name 'CAPTURE feedback Playback Volume'
		value.0 55
		value.1 55
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 255'
			dbmin -9999999
			dbmax 1200
			dbvalue.0 -3800
			dbvalue.1 -3800
		}
	}
	control.10 {
		iface PCM
		name 'IEC958 Playback Mask'
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.11 {
		iface PCM
		name 'IEC958 Playback Mask'
		index 1
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.12 {
		iface PCM
		name 'IEC958 Playback Mask'
		index 2
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.13 {
		iface PCM
		name 'IEC958 Playback Mask'
		index 3
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.14 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write locked'
			type BOOLEAN
			count 1
		}
	}
	control.15 {
		iface MIXER
		name 'Digital Source Capture Enum'
		value 'i2s in'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'IEC958 out'
			item.1 'i2s mixer out'
			item.2 'IEC958 in'
			item.3 'i2s in'
			item.4 'AC97 in'
			item.5 'SRC out'
		}
	}
	control.16 {
		iface MIXER
		name 'Analog Source Capture Enum'
		value Mic
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Phone
			item.1 Mic
			item.2 'Line in'
			item.3 Aux
		}
	}
	control.17 {
		iface PCM
		name 'IEC958 Playback Default'
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.18 {
		iface PCM
		name 'IEC958 Playback Default'
		index 1
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write locked'
			type IEC958
			count 1
		}
	}
	control.19 {
		iface PCM
		name 'IEC958 Playback Default'
		index 2
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.20 {
		iface PCM
		name 'IEC958 Playback Default'
		index 3
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.21 {
		iface PCM
		name 'IEC958 Playback PCM Stream'
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.22 {
		iface PCM
		name 'IEC958 Playback PCM Stream'
		index 1
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.23 {
		iface PCM
		name 'IEC958 Playback PCM Stream'
		index 2
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.24 {
		iface PCM
		name 'IEC958 Playback PCM Stream'
		index 3
		value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.25 {
		iface MIXER
		name 'Phone Capture Volume'
		value.0 207
		value.1 207
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 255'
			dbmin -9999999
			dbmax 2400
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.26 {
		iface MIXER
		name 'Mic Capture Volume'
		value.0 42
		value.1 42
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 255'
			dbmin -9999999
			dbmax 2400
			dbvalue.0 -8250
			dbvalue.1 -8250
		}
	}
	control.27 {
		iface MIXER
		name 'Line in Capture Volume'
		value.0 180
		value.1 180
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 255'
			dbmin -9999999
			dbmax 2400
			dbvalue.0 -1350
			dbvalue.1 -1350
		}
	}
	control.28 {
		iface MIXER
		name 'Aux Capture Volume'
		value.0 207
		value.1 207
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 255'
			dbmin -9999999
			dbmax 2400
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.29 {
		iface MIXER
		name 'Shared Mic/Line in Capture Switch'
		value 'Mic in'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'Line in'
			item.1 'Mic in'
		}
	}
	control.30 {
		iface MIXER
		name 'Analog Front Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.31 {
		iface MIXER
		name 'Analog Rear Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.32 {
		iface MIXER
		name 'Analog Center/LFE Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.33 {
		iface MIXER
		name 'Analog Side Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.34 {
		iface MIXER
		name 'Master Playback Volume'
		value 204
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 255'
			dbmin -9999999
			dbmax 0
			dbvalue.0 -1275
		}
	}
	control.35 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
parport_pc
ppdev
vesafb
snd_ca0106
snd_ac97_codec
ac97_bus
snd_hda_codec_hdmi
snd_seq_midi
fglrx
snd_rawmidi
snd_hda_intel
snd_seq_midi_event
snd_seq
snd_hda_codec
snd_hwdep
snd_pcm
snd_timer
snd_seq_device
snd
soundcore
snd_page_alloc
psmouse
serio_raw
lp
parport
usbhid
floppy
8139too
ahci
hid
pata_jmicron
8139cp
libahci
sky2


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[    5.310364] <30>udev[372]: renamed network interface eth1-eth2 to eth2
[    5.511916] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.511974] HDA Intel 0000:01:00.1: irq 47 for MSI/MSI-X
[    5.511992] HDA Intel 0000:01:00.1: setting latency timer to 64
[    5.782542] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
--
[   18.297038] EXT4-fs (sda9): re-mounted. Opts: commit=0
[   19.701326] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   20.230003] eth1: no IPv6 routers present



```


Any help is welcome

---

### Post by mihalybaci on 2011-06-16
+1. I don't have any help to offer, but this also happened to me starting about 3-5 days ago. Usually a reboot would bring the sound back, until today when 4 restarts in a row did nothing. I've reported this as a bug [here]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/798394") so hopefully it (assuming it is a bug) will be fixed soon.

---

### Post by mihalybaci on 2011-06-16
also, try sound troubleshooting.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

for me it did nothing, which is why i sent the bug. hopefully you'll have better luck with it.

---

### Post by Draknof on 2011-06-17
Unfortunately, it didn't help. My sound card id perfectly recognized by Ubuntu.

---

### Post by mihalybaci on 2011-06-17
Same for me. Unless somebody else posts a solution we might be stuck. I got a first reply from my bug post, unfortunately it didn't help, but hopefully some will get to me with a fix that I can post here. I might keep searching for a solution for a little while depending on how the bug report goes. Until then, the sound will be off for me I suppose.

---

### Post by mihalybaci on 2011-06-21
The "solution" I'm about to post could be end up being a complete waste of time, but it did something for my computer.  Yesterday I got fed up with no sound so I used gparted to shrink my 11.04 partition, and create a 12 GB partition on which I installed Ubuntu 10.04 with the intention of eventually removing 11.04. After install, I tested the sound on the 10.04 partition and it worked fine so it wasn't the computer or the speakers. After updating 10.04 and doing the reboot back to 10.04. I restarted and booted into 11.04, and now my sound now works. I don't know why since the separate partitions should have kept the different installs separate, but depending on your situation it might work. IF you wanted to try this way, definitely make sure you back up everything you don't want to lose including stuff you might not think about (computer settings, bookmarks, etc.) because the gparted gives a few warnings about changing partitions causing data loss. Also, you need to have a few spare GB of space to test this (10-12 if you think would you switch back to 10.04.2). Just be extremely careful when doing this, I tested the procedure on my laptop to ensure I knew how to do it since I didn't care if I lost info on that computer.

---


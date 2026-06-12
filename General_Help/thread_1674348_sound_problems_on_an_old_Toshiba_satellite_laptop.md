---
title: "sound problems on an old Toshiba satellite laptop"
date: 2011-01-23
forum: General Help
---

### Post by dazndom on 2011-01-23
[LIST]
[*]urgent help needed on Grandpa's computer.
[*]
[*]im out on there farm 150 km from anywhere and going home today and i really need to get this working. silly old bugger had a fall and has a broken hip
[*]
[*]please help !!!!!!!!
[/LIST]

just installed xubuntu 10.04 on this old laptop and i have no sound from the laptop
i have been thru multimedia howto and installed sound and vid codecs etc.

i do havesound thru the head phones jack but not from laptops speakers

cheers Daz

---

### Post by DanneStrat on 2011-01-23
Hi!

I will see if I can help you!

First start a source of sound.

Open a terminal and type:

```
alsamixer
```

If there happens to be a channel that you need that is muted, you 

can unmute it with your "m" key and then adjust it with the "up" 

and "down" arrows.

Good luck!

---

### Post by dazndom on 2011-01-23
hi there thanks for the quick reply

i did as you said but i cannot adjust master, headphone or front columns only pcm and beep columns.
i can mute with m button any suggestions

cheers
Daz

---

### Post by dazndom on 2011-01-23
here is print out from alsa.org

!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Mon Jan 24 12:48:22 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      Satellite L30                    
Product Version:   PSL30A-00100E


!!Kernel Information
!!------------------

Kernel release:    2.6.32-27-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


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

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd0000000 irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:437b (rev 01)
	Subsystem: 1179:ff31


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


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : 0
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC861
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0861
Subsystem Id: 0x1179820d
Revision Id: 0x100300
No Modem Function Group found
Default PCM:
    rates [0x140]: 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x03 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
Node 0x07 [Audio Output] wcaps 0x605: Stereo Digital Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  Power: setting=D0, actual=D0
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x02, nsteps=0x0d, stepsize=0x0b, mute=1
  Amp-In vals:  [0x0d 0x0d] [0x0d 0x0d] [0x0d 0x0d] [0x0d 0x0d] [0x0d 0x0d] [0x0d 0x0d]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x140]: 48000 96000
    bits [0x2]: 16
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 6
     0x0d* 0x0c 0x0f 0x10 0x11 0x15
Node 0x09 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001f: OUT HP Detect Trigger ImpSense
  Pin Default 0x99030110: [Fixed] Line Out at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x16
Node 0x0c [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000037: IN OUT Detect Trigger ImpSense
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x19
Node 0x0d [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000337: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50
  Pin Default 0x01a11820: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x18
Node 0x0e [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000017: OUT Detect Trigger ImpSense
  Pin Default 0x0121101f: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x19
Node 0x0f [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000033f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x1a
Node 0x10 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000033f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x1b
Node 0x11 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000063: IN Balanced Trigger ImpSense
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x12 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x07
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x0d 0x10
Node 0x15 [Audio Mixer] wcaps 0x20050f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x0c, nsteps=0x17, stepsize=0x0b, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x0c, nsteps=0x0c, stepsize=0x0b, mute=1
  Amp-Out vals:  [0x0c 0x0c]
  Power: setting=D0, actual=D0
  Connection: 3
     0x11 0x14 0x1c
Node 0x16 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x15
Node 0x17 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x04 0x15
Node 0x18 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x05 0x15
Node 0x19 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x06 0x15
Node 0x1a [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 4
     0x04 0x06 0x15 0x03
Node 0x1b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 4
     0x04 0x06 0x15 0x03
Node 0x1c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x0c 0x0f
Node 0x1d [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1e [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1f [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000017: OUT Detect Trigger ImpSense
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x18
Node 0x20 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000017: OUT Detect Trigger ImpSense
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x17
  Processing Coefficient: 0x00
  Coefficient Index: 0x00
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x23 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x0f, nsteps=0x0f, stepsize=0x0b, mute=1
  Amp-Out vals:  [0x0f]
Codec: LSI ID 1040
Address: 1
Function Id: 0x2
Vendor Id: 0x11c11040
Subsystem Id: 0x11790001
Revision Id: 0x100200
Modem Function Group: 0x1
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 8 Jan 24 20:20 /dev/snd/controlC0
crw-rw----  1 root audio 116, 7 Jan 24 20:20 /dev/snd/hwC0D0
crw-rw----  1 root audio 116, 6 Jan 24 20:20 /dev/snd/hwC0D1
crw-rw----  1 root audio 116, 5 Jan 24 20:21 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 4 Jan 24 23:09 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 3 Jan 24 20:20 /dev/snd/seq
crw-rw----  1 root audio 116, 2 Jan 24 20:20 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jan 24 20:20 .
drwxr-xr-x 3 root root 200 Jan 24 20:20 ..
lrwxrwxrwx 1 root root  12 Jan 24 20:20 pci-0000:00:14.2 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

Card hw:0 'SB'/'HDA ATI SB at 0xd0000000 irq 16'
  Mixer name	: 'Realtek ALC861'
  Components	: 'HDA:10ec0861,1179820d,00100300 HDA:11c11040,11790001,00100200'
  Controls      : 8
  Simple ctrls  : 6
Simple mixer control 'Master',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 15
  Mono:
  Front Left: Playback 15 [100%] [0.00dB] [on]
  Front Right: Playback 15 [100%] [0.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 13
  Front Left: Capture 13 [100%] [33.00dB] [on]
  Front Right: Capture 13 [100%] [33.00dB] [on]


!!Alsactl output
!!-------------

--startcollapse--
state.SB {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 13'
		comment.dbmin -600
		comment.dbmax 3300
		iface MIXER
		name 'Capture Volume'
		value.0 13
		value.1 13
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin -4500
		comment.dbmax 0
		iface MIXER
		name 'Beep Playback Volume'
		value.0 15
		value.1 15
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Beep Playback Switch'
		value.0 true
		value.1 true
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.8 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
udf
ppdev
snd_hda_codec_realtek
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
fbcon
tileblit
font
snd_seq_oss
bitblit
softcursor
snd_seq_midi
vga16fb
vgastate
snd_rawmidi
snd_seq_midi_event
snd_seq
arc4
snd_timer
joydev
snd_seq_device
radeon
snd
ttm
rt73usb
soundcore
ati_agp
drm_kms_helper
crc_itu_t
rt2x00usb
drm
lp
snd_page_alloc
rt2x00lib
agpgart
i2c_algo_bit
led_class
psmouse
shpchp
i2c_piix4
mac80211
parport
cfg80211
serio_raw
usbhid
8139too
hid
8139cp
mii
pata_atiixp
sata_sil


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x0b 0x99030110
0x0c 0x411111f0
0x0d 0x01a11820
0x0e 0x0121101f
0x0f 0x411111f0
0x10 0x411111f0
0x11 0x411111f0
0x12 0x411111f0
0x1f 0x411111f0
0x20 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   14.470723] Console: switching to colour frame buffer device 160x50
[   15.138319] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.191443] type=1505 audit(1295860855.477:5):  operation="profile_replace" pid=666 name="/sbin/dhclient3"
--
[   15.192997] type=1505 audit(1295860855.481:7):  operation="profile_replace" pid=666 name="/usr/lib/connman/scripts/dhclient-script"
[   15.490506] hda_codec: ALC861: BIOS auto-probing.
[   15.491349] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input7
[   15.702677] type=1505 audit(1295860855.989:8):  operation="profile_load" pid=667 name="/usr/bin/evince"
--
[10125.907261] UDF-fs INFO UDF: Mounting volume 'DORA_THE_EXPLORER', timestamp 2008/08/16 20:33 (1294)
[12460.984035] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x001f000a
[12461.988020] hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x001f000a


cheers for your help
Daz

---

### Post by Trublue on 2011-01-24
I have a Toshiba L30 satellite laptop and it has the same sound as yours. To get sound I edit /etc/modprobe.d/alsa-base.conf by adding "options snd-hda-intel model=uniwill-m31" (without quotes) Reboot

---

### Post by DanneStrat on 2011-01-24
> **Trublue said:**
> I have a Toshiba L30 satellite laptop and it has the same sound as yours. To get sound I edit /etc/modprobe.d/alsa-base.conf by adding "options snd-hda-intel model=uniwill-m31" (without quotes) Reboot


You can try that.

To open alsa-base.conf open a terminal and do a

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

You can then add the line "options snd-hda-intel model=uniwill-m31" without quotes,

to the end of the file, then save the file with "file > save". Reboot and check if you have

sound. If not you can open alsamixer again to make sure you have "master" and

"pcm" unmuted.

---

### Post by DanneStrat on 2011-01-24
If the above doesn't work for you then open alsa-base.conf

again and look for the line you created:

"options snd-hda-intel model=uniwill-m31"

Replace "uniwill-m31" with "dallas"

Save the file and reboot.

---

### Post by Trublue on 2011-01-24
The code should be 
gksudo gedit /etc/modprobe.d/alsa-base.conf

---

### Post by DanneStrat on 2011-01-24
> **Trublue said:**
> The code should be 
gksudo gedit /etc/modprobe.d/alsa-base.conf

Thanks for pointing it out, I changed it!:D

---

### Post by dazndom on 2011-01-24
Heh Trueblu and DanneStrat,  thank you very much for your help, it works great,
but here is the rub

your gksudo command puts sound to laptop speakers    but

it no longer comes thru the headphone jack

i tried changing to "dallas"  but it changed things back to the way they were, headphones - yes
laptop - no

would be great for both to work , but for next few weeks headphones is all he requires coz he is in hospital with broken hip

if there is a solution it would be great

cheers
daz

---

### Post by dazndom on 2011-01-24
Also volume control - there is no master volume slider only PCM and Front

yes PCM controls the volume, but gee the volume is soft.
how do i get louder volume settings

cheers
Daz

---

### Post by DanneStrat on 2011-01-25
Can you post the output of

In a terminal:

```
sudo aplay -l
```Can you also give me some detailed info on the following:

Different sound inputs(headphone jack, speaker jack, spdif etc.) and where on the 

computer they are located(left side, right side etc.)

If you give me this info I can help you further.

---

### Post by dazndom on 2011-01-26
Thanks for your help, it is greatly appreciated.

it will be a week or so before i can get that info for you, the laptop is now with my grandfather in hospital and he has no internet access there. i have returned home, but i am going back to visit sometime next week

the headphone and microphone jack are in the centre / centre right of the front edge of the laptop.

the volume thru headphones when set to max is so low i can only just hear it. when i set it up i was using an external speaker that plug into my mp3 player, it is a small ball shaped speaker with a volume control on it

cheers,
be in touch early next week

daz

---

### Post by dazndom on 2011-02-22
HI GUYS , MY APOLOGIES FOR Not getting back to you
silly old bugger took a bad turn, so lappy was the least of our worries.
i will be back in touch when i can but it not a priority (and its 500km away)

thanks for your help

will be in touch

Daz

---

### Post by DanneStrat on 2011-02-22
> **dazndom said:**
> HI GUYS , MY APOLOGIES FOR Not getting back to you
silly old bugger took a bad turn, so lappy was the least of our worries.
i will be back in touch when i can but it not a priority (and its 500km away)

thanks for your help

will be in touch

Daz

Hi!

I have a subscription on this thread

so just post when you can,

and I will try to help you.

---

### Post by M0riarty on 2011-02-25
I have the same laptop as your grandpa and I managed to work out the problem brutally. Though this solution seems quite weird, but it really worked. Both speaker and microphone will work. Here's the steps:

sudo nano /etc/modprobe.d/alsa-base.conf

At the end of file, insert this line:

options snd-hda-intel model=asus
(I said it's weird, ain't I?)

Then:

sudo alsa force-reload

Now, try playing a sound file. If it don't work, increase pcm volume in alsamixer. 
You can also replace module=asus with others: uniwill-m31, 3stack, 3stack-dig, 6stack-dig, 3stack-660, toshiba, asus-laptop, auto. (just repeat these steps) That's how I did it.
Hope it's helpful.

---

### Post by M0riarty on 2011-02-25
I've just found out that module=asus-laptop worked as well.
Enjoy music!!

---


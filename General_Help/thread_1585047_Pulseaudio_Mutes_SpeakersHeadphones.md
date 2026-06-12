---
title: "Pulseaudio Mutes Speakers/Headphones"
date: 2010-09-30
forum: General Help
---

### Post by NightwishFan on 2010-09-30
Can someone help me out with this, as this problem is kind of confusing. Though I am using Maverick I had this problem on Lucid as well. With an old version of alsa my headphones mute my laptops speakers when I plug them in. This seems to be the correct behavior.

With a newer alsa, plugging in headphones enables sound in both laptop speakers and headphones. Sometimes plugging in the headphones mutes everything, when I unmute it has the same behavior of playing sound out of both outputs. Changing to Analog Headphones enables playback with only the speaker but is always muted by default, requiring me to go into alsamixer. Removing pulse gets the correct behavior with just alsa, so pulse seems to be the culprit.

Here is my result of the alsa info script. I tried an option suggested in an alsa wikipage to do "snd-hda-intel: enable_msi=1". It did not help.
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Thu Sep 30 04:05:45 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu maverick (development branch) \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu maverick (development branch)"


!!DMI Information
!!---------------

Manufacturer:      ASUSTeK Computer Inc.        
Product Name:      K50IJ               


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

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9f4000 irq 44


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
    Subsystem: 1111:1043


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
snd-hda-intel: enable_msi=1


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : 1
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


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: VIA VT1708S
Address: 0
Function Id: 0x1
Vendor Id: 0x11060397
Subsystem Id: 0x10431111
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=1, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x10 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="VT1708S Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x2a 0x2a]
  Converter: stream=5, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x2a 0x2a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
Node 0x12 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x13 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="VT1708S Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x17
Node 0x14 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x1e
Node 0x15 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x16 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Control: name="Master Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Master Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x17 0x17] [0x00 0x00] [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x97 0x97] [0x97 0x97]
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 7
     0x10 0x1f 0x1a 0x1b 0x1e 0x1d 0x25
Node 0x17 [Audio Selector] wcaps 0x300501: Stereo
  Control: name="Input Source", index=0, device=0
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 6
     0x1f 0x1a* 0x1b 0x1e 0x1d 0x16
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x11
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x410110f2: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x2
  Pin-ctls: 0x00:
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x18
Node 0x1a [Pin Complex] wcaps 0x400581: Stereo
  Control: name="Mic Boost Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Smart 5.1", index=0, device=0
  Pincap 0x00002334: IN OUT Detect
    Vref caps: HIZ 50 100
  Pin Default 0x01a19038: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x8
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x26
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Control: name="Independent HP", index=0, device=0
  Pincap 0x00002334: IN OUT Detect
    Vref caps: HIZ 50 100
  Pin Default 0x418130f9: [N/A] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0xf, Sequence = 0x9
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x18
Node 0x1c [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x90070110: [Fixed] Line Out at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x16
Node 0x1d [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Independent HP", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000233c: IN OUT HP Detect
    Vref caps: HIZ 50 100
  Pin Default 0x0121401f: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=05, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x16* 0x25
Node 0x1e [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Front Mic Boost Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Smart 5.1", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000233c: IN OUT HP Detect
    Vref caps: HIZ 50 100
  Pin Default 0x90a7013e: [Fixed] Mic at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x3, Sequence = 0xe
    Misc = NO_PRESENCE
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x16 0x25*
Node 0x1f [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x593701f7: [N/A] CD at Int ATAPI
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x7
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x20 [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x474411f0: [N/A] SPDIF Out at Ext Rear Panel
    Conn = RCA, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x474411f0: [N/A] SPDIF Out at Ext Rear Panel
    Conn = RCA, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x15
Node 0x22 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x410160f1: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0xf, Sequence = 0x1
  Pin-ctls: 0x00:
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x26
Node 0x23 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x410120f4: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0xf, Sequence = 0x4
  Pin-ctls: 0x00:
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x27
Node 0x24 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x2a 0x2a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
Node 0x25 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x2a 0x2a]
  Converter: stream=5, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
Node 0x26 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1
     0x24
Node 0x27 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x25
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 7 Sep 30 00:01 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 6 Sep 30 00:01 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 5 Sep 30 00:01 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 4 Sep 30 00:02 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 3 Sep 30 00:01 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Sep 30 00:01 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Sep 30 00:01 .
drwxr-xr-x 3 root root 180 Sep 30 00:01 ..
lrwxrwxrwx 1 root root  12 Sep 30 00:01 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xfe9f4000 irq 44'
  Mixer name    : 'VIA VT1708S'
  Components    : 'HDA:11060397,10431111,00100000'
  Controls      : 21
  Simple ctrls  : 14
Simple mixer control 'Master Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 42
  Mono:
  Front Left: Playback 42 [100%] [0.00dB] [off]
  Front Right: Playback 42 [100%] [0.00dB] [off]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]
Simple mixer control 'Independent HP',0
  Capabilities: enum
  Items: 'OFF' 'ON'
  Item0: 'OFF'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Stereo Mixer' 'Mic' 'Front Mic'
  Item0: 'Mic'
Simple mixer control 'Smart 5.1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Master Front Playback Volume'
        value.0 23
        value.1 23
    }
    control.2 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Master Front Playback Switch'
        value.0 true
        value.1 true
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 42'
        comment.dbmin -6300
        comment.dbmax 0
        iface MIXER
        name 'Front Playback Volume'
        value.0 42
        value.1 42
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Front Playback Switch'
        value.0 false
        value.1 false
    }
    control.7 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Mic Playback Volume'
        value.0 0
        value.1 0
    }
    control.8 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Mic Playback Switch'
        value.0 false
        value.1 false
    }
    control.9 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Front Mic Playback Volume'
        value.0 0
        value.1 0
    }
    control.10 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Front Mic Playback Switch'
        value.0 false
        value.1 false
    }
    control.11 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 OFF
        comment.item.1 ON
        iface MIXER
        name 'Independent HP'
        value OFF
    }
    control.12 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Smart 5.1'
        value false
    }
    control.13 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -1650
        comment.dbmax 3000
        iface MIXER
        name 'Capture Volume'
        value.0 0
        value.1 0
    }
    control.14 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
    }
    control.15 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -1650
        comment.dbmax 3000
        iface MIXER
        name 'Capture Volume'
        index 1
        value.0 0
        value.1 0
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        index 1
        value.0 true
        value.1 true
    }
    control.17 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 3'
        comment.dbmin 0
        comment.dbmax 3075
        iface MIXER
        name 'Mic Boost Capture Volume'
        value.0 0
        value.1 0
    }
    control.18 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 3'
        comment.dbmin 0
        comment.dbmax 3075
        iface MIXER
        name 'Front Mic Boost Capture Volume'
        value.0 0
        value.1 0
    }
    control.19 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'Stereo Mixer'
        comment.item.1 Mic
        comment.item.2 'Front Mic'
        iface MIXER
        name 'Input Source'
        value Mic
    }
    control.20 {
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
    control.21 {
        comment.access 'read write user'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 120'
        comment.tlv '0000000100000008fffff44800000032'
        comment.dbmin -3000
        comment.dbmax 3000
        iface MIXER
        name 'Digital Capture Volume'
        value.0 120
        value.1 120
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
cryptd
aes_x86_64
aes_generic
parport_pc
ppdev
binfmt_misc
vboxnetadp
vboxnetflt
vboxdrv
joydev
snd_hda_codec_via
i915
arc4
drm_kms_helper
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
ath9k
snd_rawmidi
drm
snd_seq_midi_event
ath9k_common
ath9k_hw
snd_seq
ath
uvcvideo
videodev
v4l1_compat
mac80211
snd_timer
v4l2_compat_ioctl32
snd_seq_device
psmouse
serio_raw
i2c_algo_bit
snd
cfg80211
asus_laptop
sparse_keymap
video
soundcore
intel_agp
output
snd_page_alloc
led_class
lp
parport
usbhid
hid
atl1e
ahci
libahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x19 0x410110f2
0x1a 0x01a19038
0x1b 0x418130f9
0x1c 0x90070110
0x1d 0x0121401f
0x1e 0x90a7013e
0x1f 0x593701f7
0x20 0x474411f0
0x21 0x474411f0
0x22 0x410160f1
0x23 0x410120f4

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   15.518780]   alloc kstat_irqs on node -1
[   15.518789] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.518848]   alloc irq_desc for 44 on node -1
[   15.518850]   alloc kstat_irqs on node -1
[   15.518861] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   15.518906] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.534702] ath: EEPROM regdomain: 0x60


```

---

### Post by lidex on 2010-09-30
Hmm. Try removing your ~/.pulse folder and the msi entry from alsa-base.conf. Replace that with:
```
options snd-hda-intel model=auto
```
Reboot and check your profile and connector in sound preferences. It may help to use gnome-alsamixer to ensure any jack-sense options are enabled as well.

---

### Post by NightwishFan on 2010-09-30
Same behavior. Is there a way I can erase my alsa configuration and start over, just in case I tinkered something wrong? :(

Thanks for helping by the way. I know this is solvable because without pulse it works great.

---

### Post by lidex on 2010-09-30
> **NightwishFan said:**
> Same behavior. Is there a way I can erase my alsa configuration and start over, just in case I tinkered something wrong? :(

Thanks for helping by the way. I know this is solvable because without pulse it works great.

That would be done via this command:
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```

I note there is a mixer entry for "Independent HP" which I'm not familiar with, set to Off:
```
Simple mixer control 'Independent HP',0
  Capabilities: enum
  Items: 'OFF' 'ON'
  Item0: 'OFF'

```
```
control.11 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 OFF
        comment.item.1 ON
        iface MIXER
        name 'Independent HP'
        value OFF
    }

```
The codec info:
```
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Control: name="Independent HP", index=0, device=0
  Pincap 0x00002334: IN OUT Detect
    Vref caps: HIZ 50 100
  Pin Default 0x418130f9: [N/A] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0xf, Sequence = 0x9
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D3, actual=D3
  Connection: 1

Node 0x1d [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Independent HP", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000233c: IN OUT HP Detect
    Vref caps: HIZ 50 100
  Pin Default 0x0121401f: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=05, enabled=1
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
  Connection: 2

```
Probably has something to do with that, pulse not switching for some reason. You could try duplicating the issue while outputting this:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```
If that doesn't work then maybe dmesg or syslog may tell us why pulse is choking.

---

### Post by NightwishFan on 2010-09-30
Some other things I noticed:
[LIST]
[*]Without module-udev-detect tsched=0, audio begins to stutter badly after a while.
[*]There is a lot of crackling and popping as the daemon spawns, and the login screen sound does not play.
[*]Removing pulseaudio and using only alsa the speakers work as intended.
[/LIST]



Output of first command:
```
virgil@coffee-laptop:~$ pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux x86_64 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 371f50c946cda61961dfcf384c99ae6e.
I: main.c: Session ID is 371f50c946cda61961dfcf384c99ae6e-1285830371.223620-1881322225.
I: main.c: Using runtime directory /home/virgil/.pulse/371f50c946cda61961dfcf384c99ae6e-runtime.
I: main.c: Using state directory /home/virgil/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
```

Interesting stuff in the system log:
```
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 96.
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c: snd_pcm_dump():
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c: Soft volume PCM
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c: Control: PCM Playback Volume
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c: min_dB: -51
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c: max_dB: 0
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c: resolution: 256
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c: Its setup is:
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   stream       : CAPTURE
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   access       : MMAP_INTERLEAVED
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   format       : S16_LE
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   subformat    : STD
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   channels     : 2
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   rate         : 44100
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   exact rate   : 44100 (44100/1)
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   msbits       : 16
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   buffer_size  : 88192
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   period_size  : 44096
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   period_time  : 999909
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   tstamp_mode  : ENABLE
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   period_step  : 1
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   avail_min    : 87310
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   period_event : 0
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   start_threshold  : -1
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   stop_threshold   : 6205960286516543488
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   silence_threshold: 0
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   silence_size : 0
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   boundary     : 6205960286516543488
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c: Its setup is:
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   stream       : CAPTURE
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   access       : MMAP_INTERLEAVED
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   format       : S16_LE
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   subformat    : STD
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   channels     : 2
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   rate         : 44100
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   exact rate   : 44100 (44100/1)
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   msbits       : 16
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   buffer_size  : 88192
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   period_size  : 44096
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   period_time  : 999909
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   tstamp_mode  : ENABLE
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   period_step  : 1
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   avail_min    : 87310
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   period_event : 0
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   start_threshold  : -1
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   stop_threshold   : 6205960286516543488
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   silence_threshold: 0
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   silence_size : 0
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   boundary     : 6205960286516543488
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   appl_ptr     : 87368
Sep 30 03:07:57 coffee-laptop pulseaudio[1952]: alsa-util.c:   hw_ptr       : 87368
Sep 30 03:08:01 coffee-laptop pulseaudio[1952]: ratelimit.c: 11 events suppressed
```

---

### Post by lidex on 2010-09-30
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---


---
title: "Issue with Sound blaster no longer working"
date: 2012-06-17
forum: General Help
---

### Post by HugoStiglitz on 2012-06-17
Once working my soundblaster CA0106 no longer works.  I have checked the speakers/setup and when booting a live CD it works fine.  I followed the guides on here (libasound reinstall, switching default card and checking additional drivers) and nothing seems to work.  The only think I can think of that there seems to be too many device instances of my sound card:

> :~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
could this be the issue?

I have the output of alsa-info.sh too:

> upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.61
!!################################

!!Script ran on: Sun Jun 17 09:52:33 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu


!!DMI Information
!!---------------

Manufacturer:      MICRO-STAR INTERNATIONAL CO., LTD
Product Name:      MS-7253
Product Version:   1.00
Firmware Version:  6.00 PG


!!Kernel Information
!!------------------

Kernel release:    2.6.38-13-generic
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

snd_ca0106
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

 0 [CA0106         ]: CA0106 - CA0106
                      Sound Blaster 5.1vx [SB1070] at 0xaf00 irq 18
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xdfefc000 irq 25


!!PCI Soundcards installed in the system
!!--------------------------------------

02:00.1 Audio device: ATI Technologies Inc RV710/730
05:05.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

02:00.1 0403: 1002:aa38
    Subsystem: 1545:aa38
--
05:05.0 0401: 1102:0007
    Subsystem: 1102:1004


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
!!---------------------------

!!Module: snd_ca0106
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    subsystem : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0

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
  Digital: Enabled GenLevel
  Digital category: 0x2
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

crw-rw----+ 1 root audio 116, 11 Jun 17 08:52 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 14 Jun 17 08:52 /dev/snd/controlC1
crw-rw----+ 1 root audio 116, 13 Jun 17 08:52 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116,  2 Jun 17 08:52 /dev/snd/midiC0D0
crw-rw----+ 1 root audio 116, 10 Jun 17 09:36 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  9 Jun 17 10:50 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  8 Jun 17 08:52 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116,  7 Jun 17 09:36 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  6 Jun 17 08:52 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116,  5 Jun 17 09:36 /dev/snd/pcmC0D2p
crw-rw----+ 1 root audio 116,  4 Jun 17 08:52 /dev/snd/pcmC0D3c
crw-rw----+ 1 root audio 116,  3 Jun 17 09:36 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116, 12 Jun 17 09:36 /dev/snd/pcmC1D3p
crw-rw----+ 1 root audio 116,  1 Jun 17 08:52 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jun 17 08:52 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Jun 17 08:52 .
drwxr-xr-x 3 root root 360 Jun 17 08:52 ..
lrwxrwxrwx 1 root root  12 Jun 17 08:52 pci-0000:02:00.1 -> ../controlC1
lrwxrwxrwx 1 root root  12 Jun 17 08:52 pci-0000:05:05.0 -> ../controlC0


!!ALSA configuration files
!!------------------------

!!System wide config file (/etc/asound.conf)

pcm.!default {
type plug slave.pcm {
type hw card 1 device 0
}
}



!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [CA0106]

Card hw:0 'CA0106'/'Sound Blaster 5.1vx [SB1070] at 0xaf00 irq 18'
  Mixer name    : 'CA0106'
  Components    : ''
  Controls      : 30
  Simple ctrls  : 13
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 255
  Mono: Playback 255 [100%] [0.00dB] [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Center/LFE',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'IEC958 Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'IEC958 Rear',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'IEC958 Unknown',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
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
  Item0: 'Phone'
Simple mixer control 'CAPTURE feedback',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Digital Source',0
  Capabilities: cenum
  Items: 'IEC958 out' 'i2s mixer out' 'IEC958 in' 'i2s in' 'AC97 in' 'SRC out'
  Item0: 'i2s in'

!!-------Mixer controls for card 1 [HDMI]

Card hw:1 'HDMI'/'HDA ATI HDMI at 0xdfefc000 irq 25'
  Mixer name    : 'ATI R6xx HDMI'
  Components    : 'HDA:1002aa01,00aa0100,00100100'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!--------------

--startcollapse--
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
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 255'
            dbmin -9999999
            dbmax 1200
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.6 {
        iface MIXER
        name 'IEC958 Rear Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 255'
            dbmin -9999999
            dbmax 1200
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.7 {
        iface MIXER
        name 'IEC958 Center/LFE Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 255'
            dbmin -9999999
            dbmax 1200
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.8 {
        iface MIXER
        name 'IEC958 Unknown Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 255'
            dbmin -9999999
            dbmax 1200
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.9 {
        iface MIXER
        name 'CAPTURE feedback Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 255'
            dbmin -9999999
            dbmax 1200
            dbvalue.0 -9999999
            dbvalue.1 -9999999
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
            access 'read write'
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
        value Phone
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
        value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
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
        value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
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
        name 'Analog Front Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.26 {
        iface MIXER
        name 'Analog Rear Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.27 {
        iface MIXER
        name 'Analog Center/LFE Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.28 {
        iface MIXER
        name 'Analog Side Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.29 {
        iface MIXER
        name 'Master Playback Volume'
        value 255
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 255'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
        }
    }
    control.30 {
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
        value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.4 {
        iface MIXER
        name 'IEC958 Playback Switch'
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
dm_crypt
vesafb
snd_hda_codec_hdmi
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_ca0106
snd_ac97_codec
ac97_bus
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
binfmt_misc
snd_seq
snd_timer
ir_lirc_codec
lirc_dev
rc_imon_pad
ir_sony_decoder
snd_seq_device
ir_jvc_decoder
ir_rc6_decoder
ir_rc5_decoder
vboxnetadp
ir_nec_decoder
vboxnetflt
ppdev
imon
usblp
vboxdrv
joydev
fglrx
zram
rc_core
snd
edac_core
soundcore
k8temp
snd_page_alloc
edac_mce_amd
i2c_viapro
parport_pc
shpchp
lp
parport
dm_raid45
xor
btrfs
zlib_deflate
libcrc32c
usbhid
hid
floppy
via_rhine
pata_via
sata_via
ramzswap
xvmalloc


!!Sysfs Files
!!-----------

/sys/class/sound/hwC1D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:


!!ALSA/HDA dmesg
!!--------------

[   15.479376] snd-ca0106: Model 1004 Rev 00000000 Serial 10041102
[   15.535128] HDA Intel 0000:02:00.1: PCI INT B -> GSI 25 (level, low) -> IRQ 25
[   15.535176] HDA Intel 0000:02:00.1: setting latency timer to 64
[   15.535185] HDA Intel 0000:02:00.1: PCI: Disallowing DAC for device
[   15.572853] hda-intel: Enable sync_write for AMD chipset
[   15.728560] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90012600000, using 5120k, total 5120k
--
[   25.725962] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   25.792278] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[ 2615.444292] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_r6xx.c at line: 75I am stumped and frustrated.  Any assistance would be appreciated

---

### Post by whatthefunk on 2012-06-18
Im having similar issues.  Did this happen after a recent update?

---

### Post by HugoStiglitz on 2012-07-08
Not sure I'm away a lot but the wife uses the computer while I am away.

---


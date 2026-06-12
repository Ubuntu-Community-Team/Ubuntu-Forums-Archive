---
title: "Creative X-FI Microphone Doesn't Work (no sound)"
date: 2011-07-05
forum: General Help
---

### Post by Xruptor on 2011-07-05
I can't for the life of me get my microphone on my Creative X-FI Titanium Fatality PCI-Express card to work.  I've search the web for countless hours and tried every combination of on/off switching in alsamixer and it just still doesn't work.  No matter what mic I use (i've tried 3) none of them seem to be working with the card.  The level meter always stays at 0 as if it's not receiving anything.  NOTE:  The sound on the system works perfectly fine.  The surround sound works just fine and everything else including the games work perfectly.  It's just the microphone that is not getting ANY input whatsoever.  It's enabled and selected in the sound preferences but just doesn't get any input from any of the mics I plugin.

I've tested the mics on windows so it can't possibly be the mics.  I have a 4.1 speaker set (4 speakers and subwoffer ;) ).  I set the hardware profile to 4.1 surround + analog mono input.  That's the only way I can see the microphone listed under the input devices.  I've muted Line-in like everyone has suggested.  I've enabled/disabled countless times the Mic and PCM setting.  Nothing I do seems to get the mic to get any audio.  I've tried plugging the mic on the front panel, on the back of the computer, in other jacks... nothing.  Is there something I'm doing wrong?  Other people seem to have gotten this to work.

Any help with this problem would greatly be appreciated!! :P



[[IMG]http://img713.imageshack.us/img713/2588/screenshot1np.png[/IMG]]("http://img713.imageshack.us/i/screenshot1np.png/")

[[IMG]http://img842.imageshack.us/img842/420/screenshot2nm.png[/IMG]]("http://img842.imageshack.us/i/screenshot2nm.png/")

[[IMG]http://img189.imageshack.us/img189/2011/screenshot3tz.png[/IMG]]("http://img189.imageshack.us/i/screenshot3tz.png/")

[[IMG]http://img97.imageshack.us/img97/8468/screenshot4rq.png[/IMG]]("http://img97.imageshack.us/i/screenshot4rq.png/")

[SIZE=2]
[/SIZE][SIZE=3][U][B][SIZE=2]I've even gone out of the way to do an alsa-info.sh output for you.[/SIZE]
[/B][/U][/SIZE]
```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Wed Jul  6 01:39:17 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.04"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name
Product Version:   System Version


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

snd_ctxfi


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

 0 [XFi            ]: SB-XFi - Creative X-Fi
                      Creative X-Fi 20K2 SB0880


!!PCI Soundcards installed in the system
!!--------------------------------------

02:00.0 Audio device: Creative Labs X-Fi Titanium series [EMU20k2] (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

02:00.0 0403: 1102:000b (rev 03)
    Subsystem: 1102:0043


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

!!Module: snd_ctxfi
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    multiple : 2
    reference_rate : 48000
    subsystem : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    use_system_timer : N


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  8 Jul  5 21:08 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  7 Jul  5 21:26 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  6 Jul  5 21:26 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  5 Jul  5 21:08 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  4 Jul  5 21:08 /dev/snd/pcmC0D2p
crw-rw----+ 1 root audio 116,  3 Jul  5 21:08 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  2 Jul  5 21:08 /dev/snd/pcmC0D4p
crw-rw----+ 1 root audio 116,  1 Jul  5 21:08 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jul  5 21:08 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jul  5 21:08 .
drwxr-xr-x 3 root root 240 Jul  5 21:08 ..
lrwxrwxrwx 1 root root  12 Jul  5 21:08 pci-0000:02:00.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [XFi]

Card hw:0 'XFi'/'Creative X-Fi 20K2 SB0880'
  Mixer name    : '20K2'
  Components    : ''
  Controls      : 29
  Simple ctrls  : 10
Simple mixer control 'Master',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 202 [79%] [-13.50dB] Capture 256 [100%] [0.00dB]
  Front Right: Playback 202 [79%] [-13.50dB] Capture 256 [100%] [0.00dB]
Simple mixer control 'PCM',0
  Capabilities: pvolume cvolume cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [off]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Center/LFE',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] [off]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Line-in',0
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume cvolume cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [on]
Simple mixer control 'S/PDIF-in',0
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [off]
Simple mixer control 'S/PDIF-out',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] [off]


!!Alsactl output
!!-------------

--startcollapse--
state.XFi {
    control.1 {
        iface MIXER
        name 'Master Playback Volume'
        value.0 202
        value.1 202
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 256'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -1350
            dbvalue.1 -1350
        }
    }
    control.2 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 256
        value.1 256
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 256'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.3 {
        iface MIXER
        name 'Line-in Playback Volume'
        value.0 256
        value.1 256
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 256'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.4 {
        iface MIXER
        name 'Mic Playback Volume'
        value.0 256
        value.1 256
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 256'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.5 {
        iface MIXER
        name 'S/PDIF-in Playback Volume'
        value.0 256
        value.1 256
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 256'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.6 {
        iface MIXER
        name 'S/PDIF-out Playback Volume'
        value.0 256
        value.1 256
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 256'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.7 {
        iface MIXER
        name 'Front Playback Volume'
        value.0 256
        value.1 256
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 256'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.8 {
        iface MIXER
        name 'Surround Playback Volume'
        value.0 256
        value.1 256
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 256'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.9 {
        iface MIXER
        name 'Center/LFE Playback Volume'
        value.0 256
        value.1 256
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 256'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.10 {
        iface MIXER
        name 'Side Playback Volume'
        value.0 256
        value.1 256
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 256'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.11 {
        iface MIXER
        name 'Master Capture Volume'
        value.0 256
        value.1 256
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 256'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.12 {
        iface MIXER
        name 'PCM Capture Volume'
        value.0 256
        value.1 256
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 256'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.13 {
        iface MIXER
        name 'Line-in Capture Volume'
        value.0 256
        value.1 256
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 256'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.14 {
        iface MIXER
        name 'Mic Capture Volume'
        value.0 256
        value.1 256
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 256'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.15 {
        iface MIXER
        name 'S/PDIF-in Capture Volume'
        value.0 256
        value.1 256
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 256'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.16 {
        iface MIXER
        name 'PCM Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.17 {
        iface MIXER
        name 'Line-in Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.18 {
        iface MIXER
        name 'Mic Capture Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.19 {
        iface MIXER
        name 'S/PDIF-in Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.20 {
        iface MIXER
        name 'Line-in Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.21 {
        iface MIXER
        name 'S/PDIF-out Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.22 {
        iface MIXER
        name 'S/PDIF-in Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.23 {
        iface MIXER
        name 'Front Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.24 {
        iface MIXER
        name 'Surround Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.25 {
        iface MIXER
        name 'Center/LFE Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.26 {
        iface MIXER
        name 'Side Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.27 {
        iface PCM
        device 4
        name 'IEC958 Playback Mask'
        value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.28 {
        iface PCM
        device 4
        name 'IEC958 Playback Default'
        value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.29 {
        iface PCM
        device 4
        name 'IEC958 Playback PCM Stream'
        value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
vesafb
binfmt_misc
nvidia
snd_ctxfi
snd_pcm
snd_seq_midi
ppdev
firewire_ohci
snd_rawmidi
usbhid
firewire_core
psmouse
ahci
parport_pc
snd_seq_midi_event
asus_atk0110
snd_seq
serio_raw
snd_timer
snd_seq_device
snd
edac_core
edac_mce_amd
nv_tco
soundcore
k8temp
i2c_nforce2
snd_page_alloc
lp
parport
hid
r8169
libahci
crc_itu_t
pata_jmicron
pata_amd
sata_nv


!!ALSA/HDA dmesg
!!------------------


```

---

### Post by Xruptor on 2011-07-09
Why I bother posting in these forums is beyond me.  Seems like too many threads are created and most questions usually don't get responses.  I got a better response from LaunchPad then asking questions here.

Note:  I've asked two questions so far and no responses for either.  Still the community in Ubuntu is friendlier then I thought (in terms of Launchpad).

This question has been solved here: 
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/163939](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/163939)

---


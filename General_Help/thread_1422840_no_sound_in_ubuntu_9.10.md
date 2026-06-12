---
title: "no sound in ubuntu 9.10"
date: 2010-03-05
forum: General Help
---

### Post by lotsamuffins on 2010-03-05
ok i had sound for a while everything made a sound perfect then it went away. i have no idea why. any help?

matthew@matthew-desktop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)
04:00.0 Ethernet controller: Intel Corporation 82573E Gigabit Ethernet Controller (Copper) (rev 03)
04:00.3 Serial controller: Intel Corporation Active Management Technology - SOL (rev 03)
04:00.4 IPMI SMIC interface: Intel Corporation 82573E KCS (Active Management) (rev 03)
05:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:02.0 Audio device: Creative Labs SB X-Fi
05:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)


matthew@matthew-desktop:~$ sudo lsmod
Module                  Size  Used by
xt_limit                3236  8 
xt_tcpudp               3616  13 
ipt_LOG                 6404  8 
ipt_MASQUERADE          2944  0 
xt_DSCP                 3744  0 
ipt_REJECT              3584  1 
nf_conntrack_irc        6552  0 
nf_conntrack_ftp        9016  0 
xt_state                2432  6 
binfmt_misc            10220  1 
snd_usb_audio         102976  0 
snd_ctxfi              99016  3 
snd_hda_codec_idt      73008  1 
snd_usb_lib            19648  1 snd_usb_audio
arc4                    2144  2 
iptable_nat             6656  0 
snd_hda_intel          31880  1 
ecb                     3296  2 
nf_nat                 22452  2 ipt_MASQUERADE,iptable_nat
snd_hda_codec          87584  2 snd_hda_codec_idt,snd_hda_intel
nf_conntrack_ipv4      16376  9 iptable_nat,nf_nat
snd_pcm_oss            44704  1 
nf_conntrack           80800  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  6 snd_usb_audio,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_pcm_oss
nf_defrag_ipv4          2400  1 nf_conntrack_ipv4
snd_hwdep               9352  2 snd_usb_audio,snd_hda_codec
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
iptable_mangle          4192  0 
b43                   137032  0 
snd_seq_midi            8192  0 
snd_rawmidi            27296  2 snd_usb_lib,snd_seq_midi
mac80211              210040  1 b43
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               65260  0 
iptable_filter          3872  1 
snd_timer              26992  2 snd_pcm,snd_seq
nvidia              10316904  46 
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              21200  3 iptable_nat,iptable_mangle,iptable_filter
cfg80211              109144  2 b43,mac80211
psmouse                57124  0 
led_class               5256  1 b43
videodev               43360  1 uvcvideo
lp                     11908  0 
x_tables               25832  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
i82975x_edac            5192  0 
ipmi_msghandler        40024  0 
serio_raw               6596  0 
edac_core              48876  1 i82975x_edac
snd                    77096  19 snd_usb_audio,snd_ctxfi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
v4l1_compat            16644  2 uvcvideo,videodev
ppdev                   8232  0 
v4l2_compat_ioctl32    13344  1 videodev
soundcore               9088  2 snd
parport_pc             37352  1 
joydev                 13088  0 
parport                40528  3 lp,ppdev,parport_pc
usbhid                 43968  0 
usb_storage            66304  0 
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
ssb                    41072  1 b43
e1000e                138768  0 
matthew@matthew-desktop:~$ 


help

---

### Post by lotsamuffins on 2010-03-05
now when i go to the sys->pref-->sound it says waiting for sound system to respond.

edit
***pulseaudio was reinstalled now the sound menu comes up but no sound.***

---

### Post by lotsamuffins on 2010-03-05
[LIST=1]
[*][COLOR=brown][FONT=monospace]**################################**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**ALSA Information Script v 0.4.59**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**################################**[/FONT][/COLOR]
[*]
[*][COLOR=brown][FONT=monospace]**Script ran on: Sat Mar  6 03:26:27 UTC 2010**[/FONT][/COLOR]
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Linux Distribution**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**------------------**[/FONT][/COLOR]
[*]
[*]Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"
[*]
[*]
[*][COLOR=brown][FONT=monospace]**DMI Information**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**---------------**[/FONT][/COLOR]
[*]
[*]Manufacturer:      Gateway
[*]Product Name:      FX530
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Kernel Information**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**------------------**[/FONT][/COLOR]
[*]
[*]Kernel release:    2.6.31-20-generic
[*]Operating System:  GNU/Linux
[*]Architecture:      x86_64
[*]Processor:         unknown
[*]SMP Enabled:       Yes
[*]
[*]
[*][COLOR=brown][FONT=monospace]**ALSA Version**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**------------**[/FONT][/COLOR]
[*]
[*]Driver version:     1.0.20
[*]Library version:    1.0.20
[*]Utilities version:  1.0.20
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Loaded ALSA modules**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**-------------------**[/FONT][/COLOR]
[*]
[*]snd_hda_intel
[*]snd_ctxfi
[*]snd_usb_audio
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Sound Servers on this system**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**----------------------------**[/FONT][/COLOR]
[*]
[*]Pulseaudio:
[*]      Installed - Yes (/usr/bin/pulseaudio)
[*]      Running - Yes
[*]
[*]ESound Daemon:
[*]      Installed - Yes (/usr/bin/esd)
[*]      Running - No
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Soundcards recognised by ALSA**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**-----------------------------**[/FONT][/COLOR]
[*]
[*] 0 [Intel          ]: HDA-Intel - HDA Intel
[*]                      HDA Intel at 0xd9100000 irq 22
[*] 1 [XFi            ]: SB-XFi - Creative X-Fi
[*]                      Creative X-Fi 20K1 UAA
[*] 2 [Webcam         ]: USB-Audio - Monitor Webcam
[*]                      OmniVision Technologies, Inc.538-2640-08.09.09.1 Monitor Webcam at usb-0000:00:
[*]
[*]
[*][COLOR=brown][FONT=monospace]**PCI Soundcards installed in the system**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**--------------------------------------**[/FONT][/COLOR]
[*]
[*]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
[*]05:02.0 Audio device: Creative Labs SB X-Fi
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Advanced information - PCI Vendor/Device/Susbsystem ID's**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**--------------------------------------------------------**[/FONT][/COLOR]
[*]
[*]00:1b.0 0403: 8086:27d8 (rev 01)
[*]        Subsystem: 107b:604a
[*]--
[*]05:02.0 0403: 1102:0005
[*]        Subsystem: 1102:6007
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Modprobe options (Sound related)**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**--------------------------------**[/FONT][/COLOR]
[*]
[*]snd-atiixp-modem: index=-2
[*]snd-intel8x0m: index=-2
[*]snd-via82xx-modem: index=-2
[*]snd-usb-audio: index=-2
[*]snd-usb-us122l: index=-2
[*]snd-usb-usx2y: index=-2
[*]snd-usb-caiaq: index=-2
[*]snd-cmipci: mpu_port=0x330 fm_port=0x388
[*]snd-pcsp: index=-2
[*]snd-hda-intel: power_save=10 power_save_controller=N
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Loaded sound module options**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**--------------------------**[/FONT][/COLOR]
[*]
[*][COLOR=brown][FONT=monospace]**Module: snd_hda_intel**[/FONT][/COLOR]
[*]        bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
[*]        enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
[*]        enable_msi : 0
[*]        id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
[*]        index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
[*]        model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
[*]        position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
[*]        power_save : 10
[*]        power_save_controller : N
[*]        probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
[*]        probe_only : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
[*]        single_cmd : N
[*]
[*][COLOR=brown][FONT=monospace]**Module: snd_ctxfi**[/FONT][/COLOR]
[*]        enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
[*]        id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
[*]        index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
[*]        multiple : 2
[*]        reference_rate : 48000
[*]        use_system_timer : N
[*]
[*][COLOR=brown][FONT=monospace]**Module: snd_usb_audio**[/FONT][/COLOR]
[*]        async_unlink : Y
[*]        device_setup : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
[*]        enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
[*]        id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
[*]        ignore_ctl_error : N
[*]        index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
[*]        nrpacks : 8
[*]        pid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
[*]        vid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
[*]
[*]
[*][COLOR=brown][FONT=monospace]**HDA-Intel Codec information**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**---------------------------**[/FONT][/COLOR]
[*][(following section hidden - click to display)]("javascript:showColl(1)")
[/LIST]

[LIST]
[*]
[*]Codec: SigmaTel STAC9271X
[*]Address: 2
[*]Function Id: 0x1
[*]Vendor Id: 0x83847626
[*]Subsystem Id: 0x107b604a
[*]Revision Id: 0x100201
[*]No Modem Function Group found
[*]Default PCM:
[*]    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
[*]    bits [0xe]: 16 20 24
[*]    formats [0x1]: PCM
[*]Default Amp-In caps: ofs=0x00, nsteps=0x0e, stepsize=0x05, mute=0
[*]Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
[*]GPIO: io=3, o=0, i=0, unsolicited=1, wake=1
[*]  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
[*]  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
[*]  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
[*]Analog Loopback: 0x00
[*]Node 0x02 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
[*]  Amp-Out caps: N/A
[*]  Amp-Out vals:  [0x7f 0x7f]
[*]  Converter: stream=5, channel=0
[*]  Power: setting=D0, actual=D0
[*]  Delay: 13 samples
[*]Node 0x03 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
[*]  Amp-Out caps: N/A
[*]  Amp-Out vals:  [0xff 0xff]
[*]  Converter: stream=5, channel=0
[*]  Power: setting=D0, actual=D0
[*]  Delay: 13 samples
[*]Node 0x04 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
[*]  Amp-Out caps: N/A
[*]  Amp-Out vals:  [0xff 0xff]
[*]  Converter: stream=0, channel=0
[*]  Power: setting=D3, actual=D3
[*]  Delay: 13 samples
[*]Node 0x05 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
[*]  Amp-Out caps: N/A
[*]  Amp-Out vals:  [0x7f 0x7f]
[*]  Converter: stream=5, channel=0
[*]  Power: setting=D0, actual=D0
[*]  Delay: 13 samples
[*]Node 0x06 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
[*]  Amp-Out caps: N/A
[*]  Amp-Out vals:  [0x7f 0x7f]
[*]  Converter: stream=5, channel=0
[*]  Power: setting=D0, actual=D0
[*]  Delay: 13 samples
[*]Node 0x07 [Audio Input] wcaps 0x1d0541: Stereo
[*]  Converter: stream=0, channel=0
[*]  SDI-Select: 0
[*]  Power: setting=D0, actual=D0
[*]  Delay: 13 samples
[*]  Connection: 1
[*]     0x1b
[*]  Processing caps: benign=0, ncoeff=0
[*]Node 0x08 [Audio Input] wcaps 0x1d0541: Stereo
[*]  Converter: stream=0, channel=0
[*]  SDI-Select: 0
[*]  Power: setting=D0, actual=D0
[*]  Delay: 13 samples
[*]  Connection: 1
[*]     0x1c
[*]  Processing caps: benign=0, ncoeff=0
[*]Node 0x09 [Audio Input] wcaps 0x1d0541: Stereo
[*]  Converter: stream=0, channel=0
[*]  SDI-Select: 0
[*]  Power: setting=D0, actual=D0
[*]  Delay: 13 samples
[*]  Connection: 1
[*]     0x1d
[*]  Processing caps: benign=0, ncoeff=0
[*]Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
[*]  Pincap 0x0000173f: IN OUT HP Detect Trigger ImpSense
[*]    Vref caps: HIZ 50 GRD 80
[*]  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
[*]    Conn = 1/8, Color = Green
[*]    DefAssociation = 0x1, Sequence = 0xf
[*]  Pin-ctls: 0x00: VREF_HIZ
[*]  Unsolicited: tag=01, enabled=1
[*]  Connection: 3
[*]     0x02 0x03 0x06*
[*]Node 0x0b [Pin Complex] wcaps 0x400181: Stereo
[*]  Pincap 0x0000173f: IN OUT HP Detect Trigger ImpSense
[*]    Vref caps: HIZ 50 GRD 80
[*]  Pin Default 0x01111012: [Jack] Speaker at Ext Rear
[*]    Conn = 1/8, Color = Black
[*]    DefAssociation = 0x1, Sequence = 0x2
[*]  Pin-ctls: 0x40: OUT VREF_HIZ
[*]  Unsolicited: tag=00, enabled=0
[*]  Connection: 3
[*]     0x02 0x03* 0x06
[*]Node 0x0c [Pin Complex] wcaps 0x400181: Stereo
[*]  Pincap 0x00001737: IN OUT Detect Trigger ImpSense
[*]    Vref caps: HIZ 50 GRD 80
[*]  Pin Default 0x0181302e: [Jack] Line In at Ext Rear
[*]    Conn = 1/8, Color = Blue
[*]    DefAssociation = 0x2, Sequence = 0xe
[*]  Pin-ctls: 0x20: IN VREF_HIZ
[*]  Unsolicited: tag=03, enabled=1
[*]  Connection: 1
[*]     0x03
[*]Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
[*]  Pincap 0x0000173f: IN OUT HP Detect Trigger ImpSense
[*]    Vref caps: HIZ 50 GRD 80
[*]  Pin Default 0x01114010: [Jack] Speaker at Ext Rear
[*]    Conn = 1/8, Color = Green
[*]    DefAssociation = 0x1, Sequence = 0x0
[*]  Pin-ctls: 0x40: OUT VREF_HIZ
[*]  Unsolicited: tag=00, enabled=0
[*]  Connection: 1
[*]     0x02
[*]Node 0x0e [Pin Complex] wcaps 0x400181: Stereo
[*]  Pincap 0x00001737: IN OUT Detect Trigger ImpSense
[*]    Vref caps: HIZ 50 GRD 80
[*]  Pin Default 0x01a19020: [Jack] Mic at Ext Rear
[*]    Conn = 1/8, Color = Pink
[*]    DefAssociation = 0x2, Sequence = 0x0
[*]  Pin-ctls: 0x24: IN VREF_80
[*]  Unsolicited: tag=02, enabled=1
[*]  Connection: 1
[*]     0x04
[*]Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
[*]  Pincap 0x00001737: IN OUT Detect Trigger ImpSense
[*]    Vref caps: HIZ 50 GRD 80
[*]  Pin Default 0x01117011: [Jack] Speaker at Ext Rear
[*]    Conn = 1/8, Color = Yellow
[*]    DefAssociation = 0x1, Sequence = 0x1
[*]  Pin-ctls: 0x40: OUT VREF_HIZ
[*]  Unsolicited: tag=00, enabled=0
[*]  Connection: 1
[*]     0x05
[*]Node 0x10 [Pin Complex] wcaps 0x400181: Stereo
[*]  Pincap 0x00000037: IN OUT Detect Trigger ImpSense
[*]  Pin Default 0x01452130: [Jack] SPDIF Out at Ext Rear
[*]    Conn = Optical, Color = Grey
[*]    DefAssociation = 0x3, Sequence = 0x0
[*]    Misc = NO_PRESENCE
[*]  Pin-ctls: 0x40: OUT
[*]  Unsolicited: tag=00, enabled=0
[*]  Connection: 1
[*]     0x04
[*]Node 0x11 [Pin Complex] wcaps 0x400181: Stereo
[*]  Pincap 0x00000037: IN OUT Detect Trigger ImpSense
[*]  Pin Default 0x400000fd: [N/A] Line Out at Ext N/A
[*]    Conn = Unknown, Color = Unknown
[*]    DefAssociation = 0xf, Sequence = 0xd
[*]  Pin-ctls: 0x00:
[*]  Unsolicited: tag=00, enabled=0
[*]  Connection: 1
[*]     0x03
[*]Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
[*]  Pincap 0x00000020: IN
[*]  Pin Default 0x503301f0: [N/A] CD at Int N/A
[*]    Conn = ATAPI, Color = Unknown
[*]    DefAssociation = 0xf, Sequence = 0x0
[*]    Misc = NO_PRESENCE
[*]  Pin-ctls: 0x00:
[*]Node 0x13 [Vendor Defined Widget] wcaps 0xf00001: Stereo
[*]Node 0x14 [Vendor Defined Widget] wcaps 0xf00001: Stereo
[*]Node 0x15 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Connection: 9
[*]     0x0e* 0x12 0x0f 0x0b 0x0c 0x0d 0x0a 0x10 0x11
[*]Node 0x16 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Connection: 9
[*]     0x0e* 0x12 0x0f 0x0b 0x0c 0x0d 0x0a 0x10 0x11
[*]Node 0x17 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
[*]  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
[*]  Amp-Out vals:  [0x00 0x00]
[*]  Connection: 9
[*]     0x0e* 0x12 0x0f 0x0b 0x0c 0x0d 0x0a 0x10 0x11
[*]Node 0x18 [Audio Selector] wcaps 0x300103: Stereo Amp-In
[*]  Amp-In caps: N/A
[*]  Amp-In vals:  [0x00 0x00]
[*]  Connection: 1
[*]     0x15
[*]Node 0x19 [Audio Selector] wcaps 0x300103: Stereo Amp-In
[*]  Amp-In caps: N/A
[*]  Amp-In vals:  [0x00 0x00]
[*]  Connection: 1
[*]     0x16
[*]Node 0x1a [Audio Selector] wcaps 0x300103: Stereo Amp-In
[*]  Amp-In caps: N/A
[*]  Amp-In vals:  [0x00 0x00]
[*]  Connection: 1
[*]     0x17
[*]Node 0x1b [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
[*]  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-Out vals:  [0x80 0x80]
[*]  Connection: 1
[*]     0x18
[*]Node 0x1c [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
[*]  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-Out vals:  [0x80 0x80]
[*]  Connection: 1
[*]     0x19
[*]Node 0x1d [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
[*]  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
[*]  Amp-Out vals:  [0x80 0x80]
[*]  Connection: 1
[*]     0x1a
[*]Node 0x1e [Audio Output] wcaps 0x40211: Stereo Digital
[*]  Converter: stream=5, channel=0
[*]  Digital:
[*]  Digital category: 0x0
[*]  PCM:
[*]    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
[*]    bits [0xe]: 16 20 24
[*]    formats [0x5]: PCM AC3
[*]  Delay: 4 samples
[*]Node 0x1f [Vendor Defined Widget] wcaps 0xf30201: Stereo Digital
[*]  Delay: 3 samples
[*]Node 0x20 [Audio Input] wcaps 0x140311: Stereo Digital
[*]  Converter: stream=0, channel=0
[*]  SDI-Select: 0
[*]  Digital:
[*]  Digital category: 0x0
[*]  PCM:
[*]    rates [0x160]: 44100 48000 96000
[*]    bits [0xe]: 16 20 24
[*]    formats [0x5]: PCM AC3
[*]  Delay: 4 samples
[*]  Connection: 1
[*]     0x22
[*]Node 0x21 [Pin Complex] wcaps 0x400301: Stereo Digital
[*]  Pincap 0x00000010: OUT
[*]  Pin Default 0x01442170: [Jack] SPDIF Out at Ext Rear
[*]    Conn = RCA, Color = Grey
[*]    DefAssociation = 0x7, Sequence = 0x0
[*]    Misc = NO_PRESENCE
[*]  Pin-ctls: 0x00:
[*]  Connection: 5
[*]     0x1e* 0x1f 0x1b 0x1c 0x1d
[*]Node 0x22 [Pin Complex] wcaps 0x430681: Stereo Digital
[*]  Pincap 0x00010024: IN EAPD Detect
[*]  EAPD 0x0:
[*]  Pin Default 0x81c42090: [Fixed] SPDIF In at Ext Rear
[*]    Conn = RCA, Color = Grey
[*]    DefAssociation = 0x9, Sequence = 0x0
[*]  Pin-ctls: 0x20: IN
[*]  Unsolicited: tag=00, enabled=0
[*]  Power: setting=D0, actual=D0
[*]  Delay: 3 samples
[*]Node 0x23 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
[*]  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=0
[*]  Amp-Out vals:  [0x00]
[*]Node 0x24 [Volume Knob Widget] wcaps 0x600000: Mono
[*]  Volume-Knob: delta=1, steps=127, direct=1, val=127
[*]  Connection: 5
[*]     0x02 0x03 0x04 0x05 0x06
[*](end collapsed section)
[/LIST]

[LIST]
[*]
[*]
[*][COLOR=brown][FONT=monospace]**ALSA Device nodes**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**-----------------**[/FONT][/COLOR]
[*]
[*]crw-rw----  1 root audio 116, 16 Mar  5 21:25 /dev/snd/controlC0
[*]crw-rw----  1 root audio 116, 10 Mar  5 21:25 /dev/snd/controlC1
[*]crw-rw----  1 root audio 116, 18 Mar  5 22:24 /dev/snd/controlC2
[*]crw-rw----  1 root audio 116, 15 Mar  5 21:25 /dev/snd/hwC0D2
[*]crw-rw----  1 root audio 116, 14 Mar  5 22:23 /dev/snd/pcmC0D0c
[*]crw-rw----  1 root audio 116, 13 Mar  5 21:28 /dev/snd/pcmC0D0p
[*]crw-rw----  1 root audio 116, 12 Mar  5 21:25 /dev/snd/pcmC0D1c
[*]crw-rw----  1 root audio 116, 11 Mar  5 21:25 /dev/snd/pcmC0D1p
[*]crw-rw----  1 root audio 116,  9 Mar  5 21:25 /dev/snd/pcmC1D0c
[*]crw-rw----  1 root audio 116,  8 Mar  5 22:24 /dev/snd/pcmC1D0p
[*]crw-rw----  1 root audio 116,  7 Mar  5 21:25 /dev/snd/pcmC1D1p
[*]crw-rw----  1 root audio 116,  6 Mar  5 21:25 /dev/snd/pcmC1D2p
[*]crw-rw----  1 root audio 116,  5 Mar  5 21:25 /dev/snd/pcmC1D3p
[*]crw-rw----  1 root audio 116,  4 Mar  5 21:25 /dev/snd/pcmC1D4p
[*]crw-rw----  1 root audio 116, 17 Mar  5 22:24 /dev/snd/pcmC2D0c
[*]crw-rw----  1 root audio 116,  3 Mar  5 21:25 /dev/snd/seq
[*]crw-rw----  1 root audio 116,  2 Mar  5 21:25 /dev/snd/timer
[*]
[*]/dev/snd/by-id:
[*]total 0
[*]drwxr-xr-x 2 root root  60 Mar  5 22:24 .
[*]drwxr-xr-x 4 root root 420 Mar  5 22:24 ..
[*]lrwxrwxrwx 1 root root  12 Mar  5 22:24 usb-OmniVision_Technologies__Inc.538-2640-08.09.09.1_Monitor_Webcam-02 -> ../controlC2
[*]
[*]/dev/snd/by-path:
[*]total 0
[*]drwxr-xr-x 2 root root 100 Mar  5 22:24 .
[*]drwxr-xr-x 4 root root 420 Mar  5 22:24 ..
[*]lrwxrwxrwx 1 root root  12 Mar  5 21:25 pci-0000:00:1b.0 -> ../controlC0
[*]lrwxrwxrwx 1 root root  12 Mar  5 22:24 pci-0000:00:1d.7-usb-0:6.1:1.2 -> ../controlC2
[*]lrwxrwxrwx 1 root root  12 Mar  5 21:25 pci-0000:05:02.0 -> ../controlC1
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Aplay/Arecord output**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**------------**[/FONT][/COLOR]
[*]
[*]APLAY
[*]
[*]**** List of PLAYBACK Hardware Devices ****
[*]card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
[*]  Subdevices: 0/1
[*]  Subdevice #0: subdevice #0
[*]card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
[*]  Subdevices: 1/1
[*]  Subdevice #0: subdevice #0
[*]card 1: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
[*]  Subdevices: 8/8
[*]  Subdevice #0: subdevice #0
[*]  Subdevice #1: subdevice #1
[*]  Subdevice #2: subdevice #2
[*]  Subdevice #3: subdevice #3
[*]  Subdevice #4: subdevice #4
[*]  Subdevice #5: subdevice #5
[*]  Subdevice #6: subdevice #6
[*]  Subdevice #7: subdevice #7
[*]card 1: XFi [Creative X-Fi], device 1: ctxfi [Surround]
[*]  Subdevices: 8/8
[*]  Subdevice #0: subdevice #0
[*]  Subdevice #1: subdevice #1
[*]  Subdevice #2: subdevice #2
[*]  Subdevice #3: subdevice #3
[*]  Subdevice #4: subdevice #4
[*]  Subdevice #5: subdevice #5
[*]  Subdevice #6: subdevice #6
[*]  Subdevice #7: subdevice #7
[*]card 1: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
[*]  Subdevices: 8/8
[*]  Subdevice #0: subdevice #0
[*]  Subdevice #1: subdevice #1
[*]  Subdevice #2: subdevice #2
[*]  Subdevice #3: subdevice #3
[*]  Subdevice #4: subdevice #4
[*]  Subdevice #5: subdevice #5
[*]  Subdevice #6: subdevice #6
[*]  Subdevice #7: subdevice #7
[*]card 1: XFi [Creative X-Fi], device 3: ctxfi [Side]
[*]  Subdevices: 8/8
[*]  Subdevice #0: subdevice #0
[*]  Subdevice #1: subdevice #1
[*]  Subdevice #2: subdevice #2
[*]  Subdevice #3: subdevice #3
[*]  Subdevice #4: subdevice #4
[*]  Subdevice #5: subdevice #5
[*]  Subdevice #6: subdevice #6
[*]  Subdevice #7: subdevice #7
[*]card 1: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
[*]  Subdevices: 1/1
[*]  Subdevice #0: subdevice #0
[*]
[*]ARECORD
[*]
[*]**** List of CAPTURE Hardware Devices ****
[*]card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
[*]  Subdevices: 3/3
[*]  Subdevice #0: subdevice #0
[*]  Subdevice #1: subdevice #1
[*]  Subdevice #2: subdevice #2
[*]card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
[*]  Subdevices: 1/1
[*]  Subdevice #0: subdevice #0
[*]card 1: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
[*]  Subdevices: 1/1
[*]  Subdevice #0: subdevice #0
[*]card 2: Webcam [Monitor Webcam], device 0: USB Audio [USB Audio]
[*]  Subdevices: 1/1
[*]  Subdevice #0: subdevice #0
[*]
[*][COLOR=brown][FONT=monospace]**Amixer output**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**-------------**[/FONT][/COLOR]
[*]
[*][COLOR=brown][FONT=monospace]**-------Mixer controls for card 0 [Intel]**[/FONT][/COLOR]
[*]
[*]Card hw:0 'Intel'/'HDA Intel at 0xd9100000 irq 22'
[*]  Mixer name        : 'SigmaTel STAC9271X'
[*]  Components        : 'HDA:83847626,107b604a,00100201'
[*]  Controls      : 38
[*]  Simple ctrls  : 23
[*]Simple mixer control 'Master',0
[*]  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
[*]  Playback channels: Mono
[*]  Limits: Playback 0 - 64
[*]  Mono: Playback 64 [100%] [0.00dB] [on]
[*]Simple mixer control 'Headphone',0
[*]  Capabilities: pvolume pswitch
[*]  Playback channels: Front Left - Front Right
[*]  Limits: Playback 0 - 64
[*]  Mono:
[*]  Front Left: Playback 64 [100%] [0.00dB] [on]
[*]  Front Right: Playback 64 [100%] [0.00dB] [on]
[*]Simple mixer control 'PCM',0
[*]  Capabilities: pvolume
[*]  Playback channels: Front Left - Front Right
[*]  Limits: Playback 0 - 255
[*]  Mono:
[*]  Front Left: Playback 255 [100%] [0.00dB]
[*]  Front Right: Playback 255 [100%] [0.00dB]
[*]Simple mixer control 'Center',0
[*]  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
[*]  Playback channels: Mono
[*]  Limits: Playback 0 - 64
[*]  Mono: Playback 64 [100%] [0.00dB] [on]
[*]Simple mixer control 'LFE',0
[*]  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
[*]  Playback channels: Mono
[*]  Limits: Playback 0 - 64
[*]  Mono: Playback 64 [100%] [0.00dB] [on]
[*]Simple mixer control 'Line Jack Mode',0
[*]  Capabilities: enum
[*]  Items: 'Mic In' 'Line In'
[*]  Item0: 'Line In'
[*]Simple mixer control 'Mic Jack Mode',0
[*]  Capabilities: enum
[*]  Items: 'Mic In' 'Line In'
[*]  Item0: 'Mic In'
[*]Simple mixer control 'IEC958',0
[*]  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
[*]  Playback channels: Mono
[*]  Capture channels: Mono
[*]  Mono: Playback [off] Capture [off]
[*]Simple mixer control 'IEC958 Default PCM',0
[*]  Capabilities: pswitch pswitch-joined
[*]  Playback channels: Mono
[*]  Mono: Playback [on]
[*]Simple mixer control 'IEC958 Playback Source',0
[*]  Capabilities: enum
[*]  Items: 'Digital Playback' 'ADAT' 'Analog Mux 1' 'Analog Mux 2' 'Analog Mux 3'
[*]  Item0: 'Digital Playback'
[*]Simple mixer control 'Capture',0
[*]  Capabilities: cvolume cswitch
[*]  Capture channels: Front Left - Front Right
[*]  Limits: Capture 0 - 14
[*]  Front Left: Capture 0 [0%] [0.00dB] [off]
[*]  Front Right: Capture 0 [0%] [0.00dB] [off]
[*]Simple mixer control 'Capture',1
[*]  Capabilities: cvolume cswitch
[*]  Capture channels: Front Left - Front Right
[*]  Limits: Capture 0 - 14
[*]  Front Left: Capture 0 [0%] [0.00dB] [off]
[*]  Front Right: Capture 0 [0%] [0.00dB] [off]
[*]Simple mixer control 'Capture',2
[*]  Capabilities: cvolume cswitch
[*]  Capture channels: Front Left - Front Right
[*]  Limits: Capture 0 - 14
[*]  Front Left: Capture 0 [0%] [0.00dB] [off]
[*]  Front Right: Capture 0 [0%] [0.00dB] [off]
[*]Simple mixer control 'Input Source',0
[*]  Capabilities: cenum
[*]  Items: 'Mic' 'Line'
[*]  Item0: 'Mic'
[*]Simple mixer control 'Input Source',1
[*]  Capabilities: cenum
[*]  Items: 'Mic' 'Line'
[*]  Item0: 'Mic'
[*]Simple mixer control 'Input Source',2
[*]  Capabilities: cenum
[*]  Items: 'Mic' 'Line'
[*]  Item0: 'Mic'
[*]Simple mixer control 'Mux',0
[*]  Capabilities: cvolume
[*]  Capture channels: Front Left - Front Right
[*]  Limits: Capture 0 - 4
[*]  Front Left: Capture 0 [0%] [0.00dB]
[*]  Front Right: Capture 0 [0%] [0.00dB]
[*]Simple mixer control 'Mux',1
[*]  Capabilities: cvolume
[*]  Capture channels: Front Left - Front Right
[*]  Limits: Capture 0 - 4
[*]  Front Left: Capture 0 [0%] [0.00dB]
[*]  Front Right: Capture 0 [0%] [0.00dB]
[*]Simple mixer control 'Mux',2
[*]  Capabilities: cvolume
[*]  Capture channels: Front Left - Front Right
[*]  Limits: Capture 0 - 4
[*]  Front Left: Capture 0 [0%] [0.00dB]
[*]  Front Right: Capture 0 [0%] [0.00dB]
[*]Simple mixer control 'PC Beep',0
[*]  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
[*]  Playback channels: Mono
[*]  Limits: Playback 0 - 3
[*]  Mono: Playback 0 [0%] [-18.00dB] [off]
[*]Simple mixer control 'Speaker',0
[*]  Capabilities: pvolume pswitch
[*]  Playback channels: Front Left - Front Right
[*]  Limits: Playback 0 - 64
[*]  Mono:
[*]  Front Left: Playback 64 [100%] [0.00dB] [on]
[*]  Front Right: Playback 64 [100%] [0.00dB] [on]
[*]Simple mixer control 'Speaker',1
[*]  Capabilities: pvolume pswitch
[*]  Playback channels: Front Left - Front Right
[*]  Limits: Playback 0 - 64
[*]  Mono:
[*]  Front Left: Playback 64 [100%] [0.00dB] [off]
[*]  Front Right: Playback 64 [100%] [0.00dB] [off]
[*]Simple mixer control 'Swap Center/LFE',0
[*]  Capabilities: pswitch pswitch-joined
[*]  Playback channels: Mono
[*]  Mono: Playback [off]
[*]
[*][COLOR=brown][FONT=monospace]**-------Mixer controls for card 1 [XFi]**[/FONT][/COLOR]
[*]
[*]Card hw:1 'XFi'/'Creative X-Fi 20K1 UAA'
[*]  Mixer name        : '20K1'
[*]  Components        : ''
[*]  Controls      : 29
[*]  Simple ctrls  : 10
[*]Simple mixer control 'Master',0
[*]  Capabilities: pvolume cvolume
[*]  Playback channels: Front Left - Front Right
[*]  Capture channels: Front Left - Front Right
[*]  Limits: Playback 0 - 256 Capture 0 - 256
[*]  Front Left: Playback 0 [0%] [-99999.99dB] Capture 205 [80%] [-12.75dB]
[*]  Front Right: Playback 0 [0%] [-99999.99dB] Capture 205 [80%] [-12.75dB]
[*]Simple mixer control 'PCM',0
[*]  Capabilities: pvolume cvolume cswitch cswitch-joined
[*]  Playback channels: Front Left - Front Right
[*]  Capture channels: Front Left - Front Right
[*]  Limits: Playback 0 - 256 Capture 0 - 256
[*]  Front Left: Playback 0 [0%] [-99999.99dB] Capture 205 [80%] [-12.75dB] [on]
[*]  Front Right: Playback 0 [0%] [-99999.99dB] Capture 205 [80%] [-12.75dB] [on]
[*]Simple mixer control 'Front',0
[*]  Capabilities: pvolume pswitch pswitch-joined
[*]  Playback channels: Front Left - Front Right
[*]  Limits: Playback 0 - 256
[*]  Mono:
[*]  Front Left: Playback 0 [0%] [-99999.99dB] [on]
[*]  Front Right: Playback 0 [0%] [-99999.99dB] [on]
[*]Simple mixer control 'Surround',0
[*]  Capabilities: pvolume pswitch pswitch-joined
[*]  Playback channels: Front Left - Front Right
[*]  Limits: Playback 0 - 256
[*]  Mono:
[*]  Front Left: Playback 0 [0%] [-99999.99dB] [on]
[*]  Front Right: Playback 0 [0%] [-99999.99dB] [on]
[*]Simple mixer control 'Center/LFE',0
[*]  Capabilities: pvolume pswitch pswitch-joined
[*]  Playback channels: Front Left - Front Right
[*]  Limits: Playback 0 - 256
[*]  Mono:
[*]  Front Left: Playback 256 [100%] [0.00dB] [off]
[*]  Front Right: Playback 256 [100%] [0.00dB] [off]
[*]Simple mixer control 'Side',0
[*]  Capabilities: pvolume pswitch pswitch-joined
[*]  Playback channels: Front Left - Front Right
[*]  Limits: Playback 0 - 256
[*]  Mono:
[*]  Front Left: Playback 256 [100%] [0.00dB] [on]
[*]  Front Right: Playback 256 [100%] [0.00dB] [on]
[*]Simple mixer control 'Line-in',0
[*]  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined
[*]  Playback channels: Front Left - Front Right
[*]  Capture channels: Front Left - Front Right
[*]  Limits: Playback 0 - 256 Capture 0 - 256
[*]  Front Left: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [on]
[*]  Front Right: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [on]
[*]Simple mixer control 'Mic',0
[*]  Capabilities: pvolume cvolume cswitch cswitch-joined
[*]  Playback channels: Front Left - Front Right
[*]  Capture channels: Front Left - Front Right
[*]  Limits: Playback 0 - 256 Capture 0 - 256
[*]  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
[*]  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
[*]Simple mixer control 'S/PDIF-in',0
[*]  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined
[*]  Playback channels: Front Left - Front Right
[*]  Capture channels: Front Left - Front Right
[*]  Limits: Playback 0 - 256 Capture 0 - 256
[*]  Front Left: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [on]
[*]  Front Right: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [on]
[*]Simple mixer control 'S/PDIF-out',0
[*]  Capabilities: pvolume pswitch pswitch-joined
[*]  Playback channels: Front Left - Front Right
[*]  Limits: Playback 0 - 256
[*]  Mono:
[*]  Front Left: Playback 256 [100%] [0.00dB] [off]
[*]  Front Right: Playback 256 [100%] [0.00dB] [off]
[*]
[*][COLOR=brown][FONT=monospace]**-------Mixer controls for card 2 [Webcam]**[/FONT][/COLOR]
[*]
[*]Card hw:2 'Webcam'/'OmniVision Technologies, Inc.538-2640-08.09.09.1 Monitor Webcam at usb-0000:00:'
[*]  Mixer name        : 'USB Mixer'
[*]  Components        : 'USB05a9:2649'
[*]  Controls      : 4
[*]  Simple ctrls  : 3
[*]Simple mixer control 'Mic',0
[*]  Capabilities: cvolume cvolume-joined cswitch cswitch-joined
[*]  Capture channels: Mono
[*]  Limits: Capture 0 - 34656
[*]  Mono: Capture 34656 [100%] [-128.00dB] [on]
[*]Simple mixer control 'Auto Gain Control',0
[*]  Capabilities: pswitch pswitch-joined
[*]  Playback channels: Mono
[*]  Mono: Playback [off]
[*]Simple mixer control 'Loudness',0
[*]  Capabilities: pswitch pswitch-joined
[*]  Playback channels: Mono
[*]  Mono: Playback [off]
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Alsactl output**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**-------------**[/FONT][/COLOR]
[*]
[*][(following section hidden - click to display)]("javascript:showColl(2)")
[/LIST]

[LIST]
[*]state.Intel {
[*]        control.1 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 14'
[*]                comment.dbmin 0
[*]                comment.dbmax 2100
[*]                iface MIXER
[*]                name 'Capture Volume'
[*]                value.0 0
[*]                value.1 0
[*]        }
[*]        control.2 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 2
[*]                iface MIXER
[*]                name 'Capture Switch'
[*]                value.0 false
[*]                value.1 false
[*]        }
[*]        control.3 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 14'
[*]                comment.dbmin 0
[*]                comment.dbmax 2100
[*]                iface MIXER
[*]                name 'Capture Volume'
[*]                index 1
[*]                value.0 0
[*]                value.1 0
[*]        }
[*]        control.4 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 2
[*]                iface MIXER
[*]                name 'Capture Switch'
[*]                index 1
[*]                value.0 false
[*]                value.1 false
[*]        }
[*]        control.5 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 14'
[*]                comment.dbmin 0
[*]                comment.dbmax 2100
[*]                iface MIXER
[*]                name 'Capture Volume'
[*]                index 2
[*]                value.0 0
[*]                value.1 0
[*]        }
[*]        control.6 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 2
[*]                iface MIXER
[*]                name 'Capture Switch'
[*]                index 2
[*]                value.0 false
[*]                value.1 false
[*]        }
[*]        control.7 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 64'
[*]                comment.dbmin -4800
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'Speaker Playback Volume'
[*]                value.0 64
[*]                value.1 64
[*]        }
[*]        control.8 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 2
[*]                iface MIXER
[*]                name 'Speaker Playback Switch'
[*]                value.0 true
[*]                value.1 true
[*]        }
[*]        control.9 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 64'
[*]                comment.dbmin -4800
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'Speaker Playback Volume'
[*]                index 1
[*]                value.0 64
[*]                value.1 64
[*]        }
[*]        control.10 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 2
[*]                iface MIXER
[*]                name 'Speaker Playback Switch'
[*]                index 1
[*]                value.0 false
[*]                value.1 false
[*]        }
[*]        control.11 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 1
[*]                comment.range '0 - 64'
[*]                comment.dbmin -4800
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'Center Playback Volume'
[*]                value 64
[*]        }
[*]        control.12 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'Center Playback Switch'
[*]                value true
[*]        }
[*]        control.13 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 1
[*]                comment.range '0 - 64'
[*]                comment.dbmin -4800
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'LFE Playback Volume'
[*]                value 64
[*]        }
[*]        control.14 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'LFE Playback Switch'
[*]                value true
[*]        }
[*]        control.15 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'Swap Center/LFE Playback Switch'
[*]                value false
[*]        }
[*]        control.16 {
[*]                comment.access 'read write'
[*]                comment.type ENUMERATED
[*]                comment.count 1
[*]                comment.item.0 'Mic In'
[*]                comment.item.1 'Line In'
[*]                iface MIXER
[*]                name 'Mic Jack Mode'
[*]                value 'Mic In'
[*]        }
[*]        control.17 {
[*]                comment.access 'read write'
[*]                comment.type ENUMERATED
[*]                comment.count 1
[*]                comment.item.0 'Mic In'
[*]                comment.item.1 'Line In'
[*]                iface MIXER
[*]                name 'Line Jack Mode'
[*]                value 2
[*]        }
[*]        control.18 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 1
[*]                comment.range '0 - 3'
[*]                comment.dbmin -1800
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'PC Beep Playback Volume'
[*]                value 0
[*]        }
[*]        control.19 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'PC Beep Playback Switch'
[*]                value false
[*]        }
[*]        control.20 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 64'
[*]                comment.dbmin -4800
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'Headphone Playback Volume'
[*]                value.0 64
[*]                value.1 64
[*]        }
[*]        control.21 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 2
[*]                iface MIXER
[*]                name 'Headphone Playback Switch'
[*]                value.0 true
[*]                value.1 true
[*]        }
[*]        control.22 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 4'
[*]                comment.dbmin 0
[*]                comment.dbmax 4000
[*]                iface MIXER
[*]                name 'Mux Capture Volume'
[*]                value.0 0
[*]                value.1 0
[*]        }
[*]        control.23 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 4'
[*]                comment.dbmin 0
[*]                comment.dbmax 4000
[*]                iface MIXER
[*]                name 'Mux Capture Volume'
[*]                index 1
[*]                value.0 0
[*]                value.1 0
[*]        }
[*]        control.24 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 4'
[*]                comment.dbmin 0
[*]                comment.dbmax 4000
[*]                iface MIXER
[*]                name 'Mux Capture Volume'
[*]                index 2
[*]                value.0 0
[*]                value.1 0
[*]        }
[*]        control.25 {
[*]                comment.access 'read write'
[*]                comment.type ENUMERATED
[*]                comment.count 1
[*]                comment.item.0 Mic
[*]                comment.item.1 Line
[*]                iface MIXER
[*]                name 'Input Source'
[*]                value Mic
[*]        }
[*]        control.26 {
[*]                comment.access 'read write'
[*]                comment.type ENUMERATED
[*]                comment.count 1
[*]                comment.item.0 Mic
[*]                comment.item.1 Line
[*]                iface MIXER
[*]                name 'Input Source'
[*]                index 1
[*]                value Mic
[*]        }
[*]        control.27 {
[*]                comment.access 'read write'
[*]                comment.type ENUMERATED
[*]                comment.count 1
[*]                comment.item.0 Mic
[*]                comment.item.1 Line
[*]                iface MIXER
[*]                name 'Input Source'
[*]                index 2
[*]                value Mic
[*]        }
[*]        control.28 {
[*]                comment.access 'read write'
[*]                comment.type ENUMERATED
[*]                comment.count 1
[*]                comment.item.0 'Digital Playback'
[*]                comment.item.1 ADAT
[*]                comment.item.2 'Analog Mux 1'
[*]                comment.item.3 'Analog Mux 2'
[*]                comment.item.4 'Analog Mux 3'
[*]                iface MIXER
[*]                name 'IEC958 Playback Source'
[*]                value 'Digital Playback'
[*]        }
[*]        control.29 {
[*]                comment.access read
[*]                comment.type IEC958
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'IEC958 Playback Con Mask'
[*]                value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
[*]        }
[*]        control.30 {
[*]                comment.access read
[*]                comment.type IEC958
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'IEC958 Playback Pro Mask'
[*]                value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
[*]        }
[*]        control.31 {
[*]                comment.access 'read write'
[*]                comment.type IEC958
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'IEC958 Playback Default'
[*]                value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
[*]        }
[*]        control.32 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'IEC958 Playback Switch'
[*]                value false
[*]        }
[*]        control.33 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'IEC958 Default PCM Playback Switch'
[*]                value true
[*]        }
[*]        control.34 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'IEC958 Capture Switch'
[*]                value false
[*]        }
[*]        control.35 {
[*]                comment.access read
[*]                comment.type IEC958
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'IEC958 Capture Default'
[*]                value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
[*]        }
[*]        control.36 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 1
[*]                comment.range '0 - 64'
[*]                comment.dbmin -4800
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'Master Playback Volume'
[*]                value 64
[*]        }
[*]        control.37 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'Master Playback Switch'
[*]                value true
[*]        }
[*]        control.38 {
[*]                comment.access 'read write user'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 255'
[*]                comment.tlv '0000000100000008ffffec1400000014'
[*]                comment.dbmin -5100
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'PCM Playback Volume'
[*]                value.0 255
[*]                value.1 255
[*]        }
[*]}
[*]state.XFi {
[*]        control.1 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 256'
[*]                comment.dbmin -6400
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'Master Playback Volume'
[*]                value.0 0
[*]                value.1 0
[*]        }
[*]        control.2 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 256'
[*]                comment.dbmin -6400
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'PCM Playback Volume'
[*]                value.0 0
[*]                value.1 0
[*]        }
[*]        control.3 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 256'
[*]                comment.dbmin -6400
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'Line-in Playback Volume'
[*]                value.0 256
[*]                value.1 256
[*]        }
[*]        control.4 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 256'
[*]                comment.dbmin -6400
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'Mic Playback Volume'
[*]                value.0 0
[*]                value.1 0
[*]        }
[*]        control.5 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 256'
[*]                comment.dbmin -6400
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'S/PDIF-in Playback Volume'
[*]                value.0 256
[*]                value.1 256
[*]        }
[*]        control.6 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 256'
[*]                comment.dbmin -6400
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'S/PDIF-out Playback Volume'
[*]                value.0 256
[*]                value.1 256
[*]        }
[*]        control.7 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 256'
[*]                comment.dbmin -6400
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'Front Playback Volume'
[*]                value.0 0
[*]                value.1 0
[*]        }
[*]        control.8 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 256'
[*]                comment.dbmin -6400
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'Surround Playback Volume'
[*]                value.0 0
[*]                value.1 0
[*]        }
[*]        control.9 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 256'
[*]                comment.dbmin -6400
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'Center/LFE Playback Volume'
[*]                value.0 256
[*]                value.1 256
[*]        }
[*]        control.10 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 256'
[*]                comment.dbmin -6400
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'Side Playback Volume'
[*]                value.0 256
[*]                value.1 256
[*]        }
[*]        control.11 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 256'
[*]                comment.dbmin -6400
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'Master Capture Volume'
[*]                value.0 205
[*]                value.1 205
[*]        }
[*]        control.12 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 256'
[*]                comment.dbmin -6400
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'PCM Capture Volume'
[*]                value.0 205
[*]                value.1 205
[*]        }
[*]        control.13 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 256'
[*]                comment.dbmin -6400
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'Line-in Capture Volume'
[*]                value.0 256
[*]                value.1 256
[*]        }
[*]        control.14 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 256'
[*]                comment.dbmin -6400
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'Mic Capture Volume'
[*]                value.0 0
[*]                value.1 0
[*]        }
[*]        control.15 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 2
[*]                comment.range '0 - 256'
[*]                comment.dbmin -6400
[*]                comment.dbmax 0
[*]                iface MIXER
[*]                name 'S/PDIF-in Capture Volume'
[*]                value.0 256
[*]                value.1 256
[*]        }
[*]        control.16 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'PCM Capture Switch'
[*]                value true
[*]        }
[*]        control.17 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'Line-in Capture Switch'
[*]                value true
[*]        }
[*]        control.18 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'Mic Capture Switch'
[*]                value false
[*]        }
[*]        control.19 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'S/PDIF-in Capture Switch'
[*]                value true
[*]        }
[*]        control.20 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'Line-in Playback Switch'
[*]                value false
[*]        }
[*]        control.21 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'S/PDIF-out Playback Switch'
[*]                value false
[*]        }
[*]        control.22 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'S/PDIF-in Playback Switch'
[*]                value false
[*]        }
[*]        control.23 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'Front Playback Switch'
[*]                value true
[*]        }
[*]        control.24 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'Surround Playback Switch'
[*]                value true
[*]        }
[*]        control.25 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'Center/LFE Playback Switch'
[*]                value false
[*]        }
[*]        control.26 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'Side Playback Switch'
[*]                value true
[*]        }
[*]        control.27 {
[*]                comment.access read
[*]                comment.type IEC958
[*]                comment.count 1
[*]                iface PCM
[*]                device 4
[*]                name 'IEC958 Playback Mask'
[*]                value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
[*]        }
[*]        control.28 {
[*]                comment.access 'read write'
[*]                comment.type IEC958
[*]                comment.count 1
[*]                iface PCM
[*]                device 4
[*]                name 'IEC958 Playback Default'
[*]                value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
[*]        }
[*]        control.29 {
[*]                comment.access 'read write'
[*]                comment.type IEC958
[*]                comment.count 1
[*]                iface PCM
[*]                device 4
[*]                name 'IEC958 Playback PCM Stream'
[*]                value '0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
[*]        }
[*]}
[*]state.Webcam {
[*]        control.1 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'Mic Capture Switch'
[*]                value true
[*]        }
[*]        control.2 {
[*]                comment.access 'read write'
[*]                comment.type INTEGER
[*]                comment.count 1
[*]                comment.range '0 - 34656'
[*]                comment.dbmin -12800
[*]                comment.dbmax -12800
[*]                iface MIXER
[*]                name 'Mic Capture Volume'
[*]                value 34656
[*]        }
[*]        control.3 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name 'Auto Gain Control'
[*]                value false
[*]        }
[*]        control.4 {
[*]                comment.access 'read write'
[*]                comment.type BOOLEAN
[*]                comment.count 1
[*]                iface MIXER
[*]                name Loudness
[*]                value false
[*]        }
[*]}
[*](end collapsed section)
[/LIST]

[LIST]
[*]
[*]
[*][COLOR=brown][FONT=monospace]**All Loaded Modules**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**------------------**[/FONT][/COLOR]
[*]
[*]Module
[*]uvcvideo
[*]videodev
[*]v4l1_compat
[*]v4l2_compat_ioctl32
[*]snd_usb_audio
[*]snd_usb_lib
[*]xt_limit
[*]xt_tcpudp
[*]ipt_LOG
[*]ipt_MASQUERADE
[*]xt_DSCP
[*]ipt_REJECT
[*]nf_conntrack_irc
[*]nf_conntrack_ftp
[*]xt_state
[*]binfmt_misc
[*]arc4
[*]ecb
[*]b43
[*]mac80211
[*]snd_hda_codec_idt
[*]lp
[*]psmouse
[*]cfg80211
[*]snd_ctxfi
[*]led_class
[*]snd_hda_intel
[*]snd_hda_codec
[*]snd_hwdep
[*]snd_pcm_oss
[*]snd_mixer_oss
[*]snd_pcm
[*]snd_seq_dummy
[*]snd_seq_oss
[*]snd_seq_midi
[*]snd_rawmidi
[*]snd_seq_midi_event
[*]snd_seq
[*]snd_timer
[*]snd_seq_device
[*]ppdev
[*]parport_pc
[*]parport
[*]ipmi_msghandler
[*]serio_raw
[*]iptable_nat
[*]nf_nat
[*]nf_conntrack_ipv4
[*]nf_conntrack
[*]nf_defrag_ipv4
[*]iptable_mangle
[*]iptable_filter
[*]ip_tables
[*]x_tables
[*]joydev
[*]nvidia
[*]snd
[*]soundcore
[*]i82975x_edac
[*]snd_page_alloc
[*]edac_core
[*]usbhid
[*]usb_storage
[*]ohci1394
[*]ssb
[*]ieee1394
[*]e1000e
[*]
[*]
[*][COLOR=brown][FONT=monospace]**Sysfs Files**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**-----------**[/FONT][/COLOR]
[*]
[*]/sys/class/sound/hwC0D2/init_pin_configs:
[*]0x0a 0x0221401f
[*]0x0b 0x01111012
[*]0x0c 0x0181302e
[*]0x0d 0x01114010
[*]0x0e 0x01a19020
[*]0x0f 0x01117011
[*]0x10 0x01452130
[*]0x11 0x400000fd
[*]0x12 0x503301f0
[*]0x21 0x01442170
[*]0x22 0x81c42090
[*]
[*]/sys/class/sound/hwC0D2/driver_pin_configs:
[*]
[*]/sys/class/sound/hwC0D2/user_pin_configs:
[*]
[*]/sys/class/sound/hwC0D2/init_verbs:
[*]
[*]
[*][COLOR=brown][FONT=monospace]**ALSA/HDA dmesg**[/FONT][/COLOR]
[*][COLOR=brown][FONT=monospace]**------------------**[/FONT][/COLOR]
[*]
[*][   14.243561]   alloc kstat_irqs on node 0
[*][   14.243567] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[*][   14.243599] HDA Intel 0000:00:1b.0: setting latency timer to 64
[*][   14.368829] lp0: using parport0 (interrupt-driven).
[*]--
[*][   14.690846] type=1505 audit(1267842348.272:15): operation="profile_replace" pid=973 name=/usr/lib/connman/scripts/dhclient-script
[*][   14.690898] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[*][   14.694595] type=1505 audit(1267842348.272:16): operation="profile_replace" pid=974 name=/usr/bin/evince
[*]--
[*][   15.132551] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[*][   15.150156] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[*][   15.150223] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[*][   15.150278] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[*][   15.150329] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[*][   15.150377] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[*][   15.150423] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[*][   15.213400] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[/LIST]

---

### Post by lotsamuffins on 2010-03-05
trying this

matthew@matthew-desktop:~$ cat /proc/asound/cards; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; aplay -l;  sudo lshw -C sound; sudo lshw -short;ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn;  sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg|grep irmware; sudo /etc/init.d/sl-modem-daemon status; lsmod | grep snd

---


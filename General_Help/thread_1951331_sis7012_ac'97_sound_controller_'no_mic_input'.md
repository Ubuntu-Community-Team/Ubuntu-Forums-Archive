---
title: "sis7012 ac'97 sound controller 'no mic input'"
date: 2012-04-02
forum: General Help
---

### Post by Stephen Pink on 2012-04-02
sound output ok, but input nothing, not muted.
under sound settings, input tab there is no sound level showing, tried record nothing,
I am a newbee to linux, pls advise
 
-----------------------------------------
 
```
sean@sean-MS-6785:~$ wget -O alsa-info.sh [[COLOR=#0033aa]http://www.alsa-project.org/alsa-info.sh[/COLOR]]("http://www.alsa-project.org/alsa-info.sh") && chmod +x ./alsa-info.sh && ./alsa-info.sh
--2012-03-26 21:23:32-- [[COLOR=#0033aa]http://www.alsa-project.org/alsa-info.sh[/COLOR]]("http://www.alsa-project.org/alsa-info.sh")
Resolving [www.alsa-project.org](www.alsa-project.org)... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80](www.alsa-project.org|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [[COLOR=#0033aa]http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh[/COLOR]]("http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh") [following]
--2012-03-26 21:23:38-- [[COLOR=#0033aa]http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh[/COLOR]]("http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh")
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'
    [ <=> ] 27,247 135K/s in 0.2s
2012-03-26 21:23:39 (135 KB/s) - `alsa-info.sh' saved [27247]
ALSA Information Script v 0.4.60
--------------------------------
This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.
  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)
See './alsa-info.sh --help' for command line options.
Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ... Done!
Your ALSA information is located at [[COLOR=#0033aa]http://www.alsa-project.org/db/?f=3d2007a13da3e511fd82d6af247c31fcc362fa42[/COLOR]]("http://www.alsa-project.org/db/?f=3d2007a13da3e511fd82d6af247c31fcc362fa42")
 
----------------------------
 
!!################################
!!ALSA Information Script v 0.4.60
!!################################
!!Script ran on: Mon Mar 26 20:23:41 UTC 2012
!!Linux Distribution
!!------------------
Ubuntu 11.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.10"
!!DMI Information
!!---------------
Manufacturer: MEDIONPC
Product Name: MS-6785
Product Version:
!!Kernel Information
!!------------------
Kernel release: 3.0.0-16-generic
Operating System: GNU/Linux
Architecture: i686
Processor: i686
SMP Enabled: Yes
!!ALSA Version
!!------------
Driver version: 1.0.24
Library version: 1.0.24.1
Utilities version: 1.0.24.2
!!Loaded ALSA modules
!!-------------------
snd_intel8x0
snd_mpu401
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
 0 [SI7012 ]: ICH - SiS SI7012
                      SiS SI7012 with CMI9739 at irq 18
 1 [UART ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10
!!PCI Soundcards installed in the system
!!--------------------------------------
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)
!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------
00:02.7 0401: 1039:7012 (rev a0)
 Subsystem: 1462:7850
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
!!Module: snd_intel8x0
 ac97_clock : 0
 ac97_quirk : (null)
 buggy_irq : N
 buggy_semaphore : N
 enable : N
 id : (null)
 index : -1
 joystick : 0
 spdif_aclink : 0
 xbox : N
!!Module: snd_mpu401
 enable : Y,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
 id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
 index : -2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2,-2
 irq : 10,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535,65535
 pnp : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
 port : 816,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
 uart_enter : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
!!AC97 Codec information
!!---------------------------
--startcollapse--
0-0/0: C-Media Electronics CMI9739
PCI Subsys Vendor: 0x1462
PCI Subsys Device: 0x7850
Flags: c0
Capabilities :
DAC resolution : 16-bit
ADC resolution : 16-bit
3D enhancement : No 3D Stereo Enhancement
Current setup
Mic gain : 0dB [ 0dB]
POP path : pre 3D
Sim. stereo : off
3D enhancement : off
Loudness : off
Mono output : MIX
Mic select : Mic1
ADC/DAC loopback : off
Double rate slots: 10/11
Extended ID : codec=0 rev=1 LDAC SDAC CDAC DSA=0 SPDIF DRA
Extended status : SPCV LDAC SDAC CDAC SPDIF=3/4 SPDIF
SPDIF Control : Consumer PCM Category=0x2 Generation=1 Rate=48kHz
0:00 = 0000
0:02 = 0000
0:04 = 8000
0:06 = 801f
0:08 = 0000
0:0a = 801e
0:0c = 801f
0:0e = 801f
0:10 = 9f1f
0:12 = 9f1f
0:14 = 9f1f
0:16 = 9f1f
0:18 = 0000
0:1a = 0404
0:1c = 0505
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 05c6
0:2a = 05c4
0:2c = 0000
0:2e = 0000
0:30 = 0000
0:32 = 0000
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2824
0:3c = 0000
0:3e = 0000
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0000
0:4e = 0000
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 0000
0:5e = 0612
0:60 = 0000
0:62 = 0000
0:64 = 2008
0:66 = 0004
0:68 = 0000
0:6a = 0000
0:6c = 0001
0:6e = 0000
0:70 = 0100
0:72 = 0020
0:74 = 0000
0:76 = 0000
0:78 = 0000
0:7a = 0000
0:7c = 434d
0:7e = 4961
--endcollapse--
!!ALSA Device nodes
!!-----------------
crw-rw---- 1 root audio 116, 7 Mar 26 20:28 /dev/snd/controlC0
crw-rw---- 1 root audio 116, 3 Mar 26 20:28 /dev/snd/controlC1
crw-rw---- 1 root audio 116, 2 Mar 26 20:28 /dev/snd/midiC1D0
crw-rw---- 1 root audio 116, 6 Mar 26 20:48 /dev/snd/pcmC0D0c
crw-rw---- 1 root audio 116, 5 Mar 26 21:06 /dev/snd/pcmC0D0p
crw-rw---- 1 root audio 116, 4 Mar 26 20:28 /dev/snd/pcmC0D1c
crw-rw---- 1 root audio 116, 1 Mar 26 20:28 /dev/snd/seq
crw-rw---- 1 root audio 116, 33 Mar 26 20:28 /dev/snd/timer
/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root 60 Mar 26 20:28 .
drwxr-xr-x 3 root root 220 Mar 26 20:28 ..
lrwxrwxrwx 1 root root 12 Mar 26 20:28 pci-0000:00:02.7 -> ../controlC0
!!Aplay/Arecord output
!!------------
APLAY
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ARECORD
**** List of CAPTURE Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SI7012 [SiS SI7012], device 1: Intel ICH - MIC ADC [SiS SI7012 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
!!Amixer output
!!-------------
!!-------Mixer controls for card 0 [SI7012]
Card hw:0 'SI7012'/'SiS SI7012 with CMI9739 at irq 18'
  Mixer name : 'C-Media Electronics CMI9739'
  Components : 'AC97a:434d4961'
  Controls : 43
  Simple ctrls : 27
Simple mixer control 'Master',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB] [on]
  Front Right: Playback 255 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [on]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mic Boost ( 20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Capture Monitor',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Capture Valid',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'Analog' 'Digital'
  Item0: 'Analog'
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 5 [33%] [7.50dB] [on]
  Front Right: Capture 5 [33%] [7.50dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
!!-------Mixer controls for card 1 [UART]
Card hw:1 'UART'/'MPU-401 UART at 0x330, irq 10'
  Mixer name : ''
  Components : ''
  Controls : 0
  Simple ctrls : 0
!!Alsactl output
!!-------------
--startcollapse--
state.SI7012 {
 control.1 {
  iface MIXER
  name 'Master Playback Switch'
  value true
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.2 {
  iface MIXER
  name 'Center Playback Switch'
  value true
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.3 {
  iface MIXER
  name 'Center Playback Volume'
  value 31
  comment {
   access 'read write'
   type INTEGER
   count 1
   range '0 - 31'
   dbmin -4650
   dbmax 0
   dbvalue.0 0
  }
 }
 control.4 {
  iface MIXER
  name 'LFE Playback Switch'
  value true
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.5 {
  iface MIXER
  name 'LFE Playback Volume'
  value 31
  comment {
   access 'read write'
   type INTEGER
   count 1
   range '0 - 31'
   dbmin -4650
   dbmax 0
   dbvalue.0 0
  }
 }
 control.6 {
  iface MIXER
  name 'Surround Playback Switch'
  value.0 true
  value.1 true
  comment {
   access 'read write'
   type BOOLEAN
   count 2
  }
 }
 control.7 {
  iface MIXER
  name 'Surround Playback Volume'
  value.0 31
  value.1 31
  comment {
   access 'read write'
   type INTEGER
   count 2
   range '0 - 31'
   dbmin -4650
   dbmax 0
   dbvalue.0 0
   dbvalue.1 0
  }
 }
 control.8 {
  iface MIXER
  name 'Master Mono Playback Switch'
  value false
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.9 {
  iface MIXER
  name 'Master Mono Playback Volume'
  value 0
  comment {
   access 'read write'
   type INTEGER
   count 1
   range '0 - 31'
   dbmin -4650
   dbmax 0
   dbvalue.0 -4650
  }
 }
 control.10 {
  iface MIXER
  name 'Beep Playback Switch'
  value false
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.11 {
  iface MIXER
  name 'Beep Playback Volume'
  value 0
  comment {
   access 'read write'
   type INTEGER
   count 1
   range '0 - 15'
   dbmin -4500
   dbmax 0
   dbvalue.0 -4500
  }
 }
 control.12 {
  iface MIXER
  name 'Phone Playback Switch'
  value false
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.13 {
  iface MIXER
  name 'Phone Playback Volume'
  value 0
  comment {
   access 'read write'
   type INTEGER
   count 1
   range '0 - 31'
   dbmin -3450
   dbmax 1200
   dbvalue.0 -3450
  }
 }
 control.14 {
  iface MIXER
  name 'Mic Playback Switch'
  value false
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.15 {
  iface MIXER
  name 'Mic Playback Volume'
  value 0
  comment {
   access 'read write'
   type INTEGER
   count 1
   range '0 - 31'
   dbmin -3450
   dbmax 1200
   dbvalue.0 -3450
  }
 }
 control.16 {
  iface MIXER
  name 'Mic Boost ( 20dB)'
  value false
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.17 {
  iface MIXER
  name 'Line Playback Switch'
  value false
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.18 {
  iface MIXER
  name 'Line Playback Volume'
  value.0 0
  value.1 0
  comment {
   access 'read write'
   type INTEGER
   count 2
   range '0 - 31'
   dbmin -3450
   dbmax 1200
   dbvalue.0 -3450
   dbvalue.1 -3450
  }
 }
 control.19 {
  iface MIXER
  name 'CD Playback Switch'
  value false
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.20 {
  iface MIXER
  name 'CD Playback Volume'
  value.0 0
  value.1 0
  comment {
   access 'read write'
   type INTEGER
   count 2
   range '0 - 31'
   dbmin -3450
   dbmax 1200
   dbvalue.0 -3450
   dbvalue.1 -3450
  }
 }
 control.21 {
  iface MIXER
  name 'Video Playback Switch'
  value false
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.22 {
  iface MIXER
  name 'Video Playback Volume'
  value.0 0
  value.1 0
  comment {
   access 'read write'
   type INTEGER
   count 2
   range '0 - 31'
   dbmin -3450
   dbmax 1200
   dbvalue.0 -3450
   dbvalue.1 -3450
  }
 }
 control.23 {
  iface MIXER
  name 'Aux Playback Switch'
  value false
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.24 {
  iface MIXER
  name 'Aux Playback Volume'
  value.0 0
  value.1 0
  comment {
   access 'read write'
   type INTEGER
   count 2
   range '0 - 31'
   dbmin -3450
   dbmax 1200
   dbvalue.0 -3450
   dbvalue.1 -3450
  }
 }
 control.25 {
  iface MIXER
  name 'PCM Playback Switch'
  value true
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.26 {
  iface MIXER
  name 'Capture Source'
  value.0 Line
  value.1 Line
  comment {
   access 'read write'
   type ENUMERATED
   count 2
   item.0 Mic
   item.1 CD
   item.2 Video
   item.3 Aux
   item.4 Line
   item.5 Mix
   item.6 'Mix Mono'
   item.7 Phone
  }
 }
 control.27 {
  iface MIXER
  name 'Capture Switch'
  value true
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.28 {
  iface MIXER
  name 'Capture Volume'
  value.0 5
  value.1 5
  comment {
   access 'read write'
   type INTEGER
   count 2
   range '0 - 15'
   dbmin 0
   dbmax 2250
   dbvalue.0 750
   dbvalue.1 750
  }
 }
 control.29 {
  iface MIXER
  name 'Mono Output Select'
  value Mix
  comment {
   access 'read write'
   type ENUMERATED
   count 1
   item.0 Mix
   item.1 Mic
  }
 }
 control.30 {
  iface MIXER
  name 'Mic Select'
  value Mic1
  comment {
   access 'read write'
   type ENUMERATED
   count 1
   item.0 Mic1
   item.1 Mic2
  }
 }
 control.31 {
  iface MIXER
  name 'IEC958 Playback Con Mask'
  value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
  comment {
   access read
   type IEC958
   count 1
  }
 }
 control.32 {
  iface MIXER
  name 'IEC958 Playback Pro Mask'
  value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
  comment {
   access read
   type IEC958
   count 1
  }
 }
 control.33 {
  iface MIXER
  name 'IEC958 Playback Default'
  value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
  comment {
   access 'read write'
   type IEC958
   count 1
  }
 }
 control.34 {
  iface MIXER
  name 'IEC958 Playback Switch'
  value true
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.35 {
  iface MIXER
  name 'IEC958 Playback AC97-SPSA'
  value 0
  comment {
   access 'read write'
   type INTEGER
   count 1
   range '0 - 3'
  }
 }
 control.36 {
  iface MIXER
  name 'IEC958 Playback Source'
  value Analog
  comment {
   access 'read write'
   type ENUMERATED
   count 1
   item.0 Analog
   item.1 Digital
  }
 }
 control.37 {
  iface MIXER
  name 'IEC958 Capture Valid Switch'
  value false
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.38 {
  iface MIXER
  name 'IEC958 Capture Monitor'
  value false
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.39 {
  iface MIXER
  name 'IEC958 Capture Switch'
  value false
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.40 {
  iface MIXER
  name 'Surround Jack Mode'
  value Shared
  comment {
   access 'read write'
   type ENUMERATED
   count 1
   item.0 Shared
   item.1 Independent
  }
 }
 control.41 {
  iface MIXER
  name 'Channel Mode'
  value '2ch'
  comment {
   access 'read write'
   type ENUMERATED
   count 1
   item.0 '2ch'
   item.1 '4ch'
   item.2 '6ch'
  }
 }
 control.42 {
  iface MIXER
  name 'External Amplifier'
  value true
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
 }
 control.43 {
  iface MIXER
  name 'PCM Playback Volume'
  value.0 255
  value.1 255
  comment {
   access 'read write user'
   type INTEGER
   count 2
   range '0 - 255'
   tlv '0000000100000008ffffec1400000014'
   dbmin -5100
   dbmax 0
   dbvalue.0 0
   dbvalue.1 0
  }
 }
}
state.UART {
 control {
 }
}
--endcollapse--
!!All Loaded Modules
!!------------------
Module
bnep
rfcomm
bluetooth
pci_stub
vboxpci
vboxnetadp
vboxnetflt
vboxdrv
dm_crypt
ppdev
snd_wavefront
arc4
snd_cs4236
snd_wss_lib
snd_opl3_lib
snd_hwdep
snd_mpu401
snd_mpu401_uart
rt61pci
snd_seq_midi
rt2x00pci
rt2x00lib
mac80211
snd_rawmidi
psmouse
serio_raw
snd_seq_midi_event
snd_intel8x0
snd_ac97_codec
ac97_bus
cfg80211
eeprom_93cx6
snd_seq
snd_pcm
snd_seq_device
snd_timer
i2c_sis96x
snd_page_alloc
snd
ns558
gameport
soundcore
shpchp
parport_pc
binfmt_misc
lp
parport
radeon
ttm
drm_kms_helper
drm
sis900
firewire_ohci
i2c_algo_bit
firewire_core
crc_itu_t
sis_agp
floppy
!!ALSA/HDA dmesg

---------------
 
here are the results of the bars in alsamixer: (no means no bar, or unable to change)
 
master= no
master m=no
pcm=yes fully
sourround= yes fully
sourround= shared
center=yes fully
LFE=yes fully
line= no
CD=no
mic=no
mic boos=no
mic sele=mic 1
video=no
phone=no
S/PDIF= no
S/PDIF C= no
S/PDIF C =no
S/PDIF P =no
S/PDIF P =anolog
Beep=no
Aux =no
Mono Out = mix
Channel = 2 ch
External=no
 
```
--------
 
Rgds
Steve Pink

---


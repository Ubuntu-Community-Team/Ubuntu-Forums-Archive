---
title: "HDMI Audio out problem with Alsa+pulseaudio and Maverick"
date: 2010-12-07
forum: General Help
---

### Post by manion on 2010-12-07
Hi, 

**Preliminary**

I've installed Ubuntu maverick 10.10 on an  ZBOX HD-ID11. The system definitely supports HDMI out as It working under another distro. 
[B]
The Problem[/B]

Sound wasn't working for certain media files, so I attempted to upgrade pulseaudio to the latest version. After reboot, I've no hdmi sound at all. Aplay presented the following output 

[QUOTE=aplay -l ]
**** List of PLAYBACK Hardware Devices ****
xcb_connection_has_error() returned true
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
[/QUOTE]

As I understand it the xcb_connection_has_error() returned true just means pulseaudio wasn't able to connect to an x session.

The interesting thing is what aplay -L produces the following output without any nvidia devices. 

[QUOTE= aplay -L]
xcb_connection_has_error() returned true
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output
[/QUOTE]Theres no nvidia devices to be found at all. I guess this explains the lack of sound. However, I've no idea how to fix it. Any help at all would be greatly appreciated. 

In my previous /etc/pulse/default.pa I had a line

[QUOTE=/etc/pulse/default.pa]
load-module module-alsa-sink device=hw:1,3[/QUOTE]

But that command is now causing some difficulty. Apparently pulse now autodetects devices and loads appropriate drivers. The snd_hda_codec_nvhdmi is available on this system and should be loaded.

[QUOTE= lsmod | grep snd]
snd_hda_codec_nvhdmi    12879  1
snd_hda_codec_realtek   217980  1
snd_hda_intel          22107  2
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
[/QUOTE]

Finally, I have the following configured in /etc/asound.conf

[QUOTE=/etc/asound.conf]pcm.!default hdmi:NVidia
pcm:iec958 hdmi:NVidia
[/QUOTE]

---


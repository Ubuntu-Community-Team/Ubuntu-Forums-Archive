---
title: "Sound output works fine but no sound input with Intel ICH7"
date: 2010-12-18
forum: General Help
---

### Post by zoubidoo on 2010-12-18
I have had no sound input for the last 4 ubuntu releases so I'd really like to fix it!  Any help would be much appreciated.

Sound output works fine on ubuntu and windows. Sound input works fine under windows but not ubuntu.

```
$ arecord  -d 10 -t wav foobar.wav
```
Records but the file contains only noise on playback.

I have tried changing the alsamixer settings while watching the pulseaudio volume meter (capture device and volume settings).  No success.

lspci returns:
```
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)

```

```
$ cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x502c0000 irq 45
 1 [U0x46d0x8b0    ]: USB-Audio - USB Device 0x46d:0x8b0
                      USB Device 0x46d:0x8b0 at usb-0000:00:1d.2-1, full speed

```

head -n 1 /proc/asound/card*/codec#*
```
Codec: SigmaTel STAC9221 A1
```

arecord -l returns:
```
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: U0x46d0x8b0 [USB Device 0x46d:0x8b0], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
$ dpkg -l | grep alsa
ii  alsa-base                                  1.0.23+dfsg-1ubuntu4                                 ALSA driver configuration files
ii  alsa-oss                                   1.0.17-4                                             ALSA wrapper for OSS applications
ii  alsa-utils                                 1.0.23-2ubuntu3.4                                    Utilities for configuring and using ALSA
ii  bluez-alsa                                 4.69-0ubuntu2                                        Bluetooth audio support
ii  gstreamer0.10-alsa                         0.10.30-2                                            GStreamer plugin for ALSA
rc  libsdl1.2debian-alsa                       1.2.13-4ubuntu4                                      Simple DirectMedia Layer (with X11 and ALSA options)

```

Up to date Maverick ```
$ uname -a
Linux gateway 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux
```

Suitable sound modules seem to be loaded in the kernel:
```
$ lsmod | grep snd
snd_hda_codec_idt      54887  1 
snd_hda_intel          22107  5 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_usb_audio          86480  1 
snd_pcm                71475  4 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_hwdep               5040  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        17413  1 snd_usb_audio
snd_seq_midi            4588  0 
snd_rawmidi            17783  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49006  22 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm

```
What should I try next?

---

### Post by zoubidoo on 2010-12-27
bump.  Advice would be much appreciated to help move away from windows.

---

### Post by zoubidoo on 2010-12-27
bump.  Advice would be much appreciated to help move away from windows.

---

### Post by efflandt on 2010-12-27
What does **aplay -l** (small L) show for devices?  And does **alsamixer** show Mic or Front Mic unmuted (something other than MM).  Pressing **m** on an input or output will toggle mute on/off.

---

### Post by zoubidoo on 2010-12-27
> **efflandt said:**
> What does **aplay -l** (small L) show for devices?  And does **alsamixer** show Mic or Front Mic unmuted (something other than MM).  Pressing **m** on an input or output will toggle mute on/off.

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

In alsamixer I tried pressing 'm' but it only has an effect on "master" and "speaker" (the two sliders on the left of the attached image)  Could that be a problem?

---


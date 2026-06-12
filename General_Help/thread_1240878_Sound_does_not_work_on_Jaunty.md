---
title: "Sound does not work on Jaunty"
date: 2009-08-15
forum: General Help
---

### Post by mwjones on 2009-08-15
Sound is not working on my desktop.  I have spent hours going through docs online and fidgeting with settings all ending in failure.  Does anyone have any idea what needs to be done to fix this?

Here are some outputs from commands that seem to be used in diagnosing hardware:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: MobilePre [MobilePre], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
$ lspci -v

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: ASUSTeK Computer Inc. Device 82fe
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

I tried following [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) but my card isn't in /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz so I can't provide the right line for /etc/modprobe.d/alsa-base.conf  Though, the module is loaded:

```
$ sudo lsmod | grep snd_hda_intel
snd_hda_intel         557492  3 
snd_pcm                99464  3 snd_usb_audio,snd_pcm_oss,snd_hda_intel
snd                    78920  19 snd_usb_audio,snd_pcm_oss,snd_hda_intel,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm

```

Help, please.  This sucks not having sound :(

---

### Post by mwjones on 2009-08-15
Ok, sound magically started working now after a reboot.  No settings changed.  A reboot?  Seriously?  Windows, is that you?  :confused:

---

### Post by wojox on 2009-08-15
It's always nice to have sound. :P

---


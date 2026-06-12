---
title: "Sound went strange during song"
date: 2009-12-10
forum: General Help
---

### Post by _sleeper on 2009-12-10
hi there. among hundreds of sound problems people are facing out there, here's mine to be added.

about an hour ago i was listening to mp3's in amarok, when in the middle of a song playing, the sound went nuts. at one moment i was listening the song and at the other the sound was like when you turn on the radio, but there is no station. and the thing is that since then every sound is like that. i tried firefox, vlc, even the login/logout sound is like that.

i have pulseaudio removed and i'm using alsa, because of the problems pulseaudio has with simultaneous sounds from different applications. i've never faced any other issues with my soundcard and alsa in the past.

i hope these outputs help

```
iraklis@panisxyros:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 0d8c:0201 C-Media Electronics, Inc. CM6501
Bus 002 Device 003: ID 0c45:60c0 Microdia PC Camera with Mic (SN9C105)
Bus 002 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
iraklis@panisxyros:~$ dmesg | grep audio
[   16.125369] usbcore: registered new interface driver snd-usb-audio

```


```
iraklis@panisxyros:~$ lsmod | grep audio
snd_usb_audio          84224  5
snd_pcm                75296  3 snd_usb_audio,snd_pcm_oss
snd_usb_lib            16284  1 snd_usb_audio
snd_hwdep               7200  1 snd_usb_audio
snd                    59204  16 snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```


thanx

---

### Post by _sleeper on 2009-12-10
just an update here. i tried booting with older kernels, but the problem remained. i, also, tried backtrack and fedora 2009 live cd's to no avail, everytime this broken-radio sound. so i switced off the pc, turned off the power supply and waited a few seconds before i turned everything again on. and now, voila, i'm having sound again. so i guess there was a hardware glitch, it overheated or something, i really can't figure it out.

anyway, i consider it as solved.

---


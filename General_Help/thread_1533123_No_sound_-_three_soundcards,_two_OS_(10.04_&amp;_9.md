---
title: "No sound - three soundcards, two OS (10.04 &amp; 9.10)"
date: 2010-07-17
forum: General Help
---

### Post by dchurch24 on 2010-07-17
Hi all,

I'm currently building a MAME machine. I got everything setup on a machine that I already had Xubuntu 9.10 running on. Everything was working but the sound. I put it down to the USB speakers I was using and decided (for a variety of reasons) to upgrade to Ubuntu 10.04.

Sadly, I still had no sound, so tried some headphones in the phones socket - no sound.
I figured that maybe the on-board sound wasn't being detected, so did aplay -l - and sure enough it was there.

I plugged in a USB phone that I have, and still no sound - although the device was listed.

I then plugged in a SoundBlaster USB SB0490 - and sure enough, the device is listed - but still no sound.

I've scoured the forum and google - and have tried a multitude of things - removed Pulse installed esound etc... but still I have no sound.

I went into the bios and removed the VIA on-board sound.

I rebooted and then tried to go into the System/Preferences/Sound, but now all I see is a messagebox saying "Waiting for sound system".

I went back into the bios and re-enabled it, but I still get the same message when trying to open sound prefs.
aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: External [SB Live! 24-bit External], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


dmesg |grep audio
```

[   20.269488] usbcore: registered new interface driver snd-usb-audio

```

mplayer /home/mame/Desktop/backinblack.mp3 

gets this:
```

MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/mame/Desktop/backinblack.mp3.
Audio only file format detected.
Clip info:
 Title: Back In Black
 Artist: AC DC
 Album: AC/DC In The 20th Century: Bac
 Year: 2000
 Comment: originally released: 1980
 Track: 6
 Genre: Rock
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
waitpid(): No child processes
AO: [pulse] Init failed: Internal error
Failed to initialize audio driver 'pulse'
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  12.8 (12.8) of 255.0 (04:15.0)  0.6% 

MPlayer interrupted by signal 2 in module: play_audio
A:  12.9 (12.8) of 255.0 (04:15.0)  0.6% 
Exiting... (Quit)

```

If I put headphones on and reboot, I can hear when the USB card gets connected.

The last time I rebooted, I can no longer see the volume applet in the menu bar.

If I load alsamixer, I can see both cards and the volumes for both the on-board and the USB card seem fine.

Can anyone shed any light on this?

---

### Post by dchurch24 on 2010-07-17
Not quite sure what I did but it's working!

From memory, I reinstalled pulseaudio and gnome alsa mixer, disabled the onboard card and a few other things that I can't remember.

The main thing I think was the reinstall of pulse.

---


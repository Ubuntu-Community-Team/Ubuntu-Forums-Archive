---
title: "Recordmydesktop - changing sound device."
date: 2012-01-03
forum: General Help
---

### Post by spotsnz on 2012-01-03
Hi guys. Happy first post to me, and my apologies if this post isn't appropriate.

So I'm trying to record audio from the desktop with recordmydesktop.

the [man page]("http://recordmydesktop.sourceforge.net/manpage.php") says use
>   -device SOUND_DEVICE

    Sound device(default hw:0,0 or /dev/dsp, depending on whether ALSA or OSS is used). 

> $aplay -l
gives me:
> card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: WE [DJ Console (WE)], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

The device I'm wanting to use is that DJ Console. 

My first question is - what's the syntax for referring to an audio device?

> $recordmydesktop -device USB Audio *did* run, but didn't record the sound. If we can establish that I wrote the command right, then get on with working out how to make it record sound.

---


---
title: "No sound - affecting one user profile"
date: 2010-03-20
forum: General Help
---

### Post by steve_k on 2010-03-20
I appear to be experiencing an annoying issue with my soundcard. As you can see from the images below, the soundcard is detected, but not when it comes to the "output". This is only affecting one user (my admin account is fine, as was a new user set up to test it).

I've looked at [this page]("http://ubuntuforums.org/showthread.php?t=205449&highlight=user+profile") and have attempted reinstalling alsa, but to no success.

The results from *aplay -l* are:
> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [SB Live! 5.1 [SB0220]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Live [SB Live! 5.1 [SB0220]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Live [SB Live! 5.1 [SB0220]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The results from *grep 'audio' /etc/group* are:
> audio: x:29 : pulse,stevek,timidity

"stevek" being the user that I'm having difficulty with. I suspect that I might need to recreate part of my user profile, but I'm not sure where start.

Any help will be greatly appreciated.

Thanks
Steve

---

### Post by steve_k on 2010-03-20
Colour me embarrassed. 

I've just realised that for some reason the setting was "input" only and all I needed to do was alter the setting to "input and output".

It's only taken me a couple of hours to spot the bleeding obvious!

---


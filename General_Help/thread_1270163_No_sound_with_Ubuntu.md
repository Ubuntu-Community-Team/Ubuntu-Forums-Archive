---
title: "No sound with Ubuntu"
date: 2009-09-19
forum: General Help
---

### Post by gjoellee on 2009-09-19
I got no sound in Ubuntu, but I do in Win7 which I am dual booting with. Sound worked before in Ubuntu with the same sound card, but with other speakers. I am using 2.1 sound (two speakers and one subwoofer).

aplay -l:
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [SB Audigy 2 [Unknown]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Audigy2 [SB Audigy 2 [Unknown]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [SB Audigy 2 [Unknown]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [SB Audigy 2 [Unknown]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by gjoellee on 2009-09-19
2 hour BUMP...I am not patient when my sound is gone!

---

### Post by AmerNewbieInDE on 2009-09-19
try going into windows and turn the volume up. i dont understand why, but i had very low sound in ubuntu untill someone told me to turn the sound up in windows. dont understand it, but it was like the computer remembered windows sound settings...

---

### Post by csi_guy on 2009-09-19
Welcome to the Ubuntu NO SOUND club.  I have been fighting with mine for three days now.

---

### Post by gjoellee on 2009-09-20
> **AmerNewbieInDE said:**
> try going into windows and turn the volume up. i dont understand why, but i had very low sound in ubuntu untill someone told me to turn the sound up in windows. dont understand it, but it was like the computer remembered windows sound settings...

That does not help.

---

### Post by bodyharvester on 2009-09-20
i havent had sound for over a month now, im hoping updating to karmic will fix this

its only in web browsers though, totem and exaile and others like those work, just not opera ff epiphany and any other web browser so i havent been able to play quake live in ages

i had to change my sound output devices to get totem et al to work EDIT: SYSTEM>PREFERENCES>SOUND

---

### Post by gjoellee on 2009-09-20
> **bodyharvester said:**
> i havent had sound for over a month now, im hoping updating to karmic will fix this

its only in web browsers though, totem and exaile and others like those work, just not opera ff epiphany and any other web browser so i havent been able to play quake live in ages

i had to change my sound output devices to get totem et al to work EDIT: SYSTEM>PREFERENCES>SOUND

Well I am using Karmic. This does also happen with other Ubuntu versions though.

---

### Post by missmoondog on 2009-09-22
> **csi_guy said:**
> Welcome to the Ubuntu NO SOUND club.  I have been fighting with mine for three days now.


the no sound club, huh? :guitar:

have this issue on another machine of mine with via integrated everything. i believe the sound card is a realtek though.

---


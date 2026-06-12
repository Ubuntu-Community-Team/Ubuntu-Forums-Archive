---
title: "Sound Extremely Low"
date: 2011-12-03
forum: General Help
---

### Post by bveenema on 2011-12-03
I just switched my older Gateway 7510GX laptop over to Ubuntu 11.10 and am a new linux user.  I have a problem where I cannot hear any audio unless I turn the system audio all the way up and my external speakers all the way up and it's still really quiet.  I have tried going into the Alsamixer controls and setting everything to max but this doesn't help at all.

The weird thing is that I will restart the computer and sometimes the audio will be at a normal volume.  It worked for 2 or 3 days in a row, but today it has decided to stop working (I have restarted many times today).  This cycle has happened a couple times now and I can't figure out what ends up "fixing" it.

Any suggestions would be really helpful.  Thanks.

---

### Post by mikewhatever on 2011-12-03
Looks like a configuration issue. Can you post the outputs of the following:
```
aplay -l 

dmesg | grep -i hda
```

---

### Post by bveenema on 2011-12-03
```
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```When I enter: "dmesg | grep -i hda" I don't get anything... it just starts a new line

---

### Post by mikewhatever on 2011-12-03
Thanks. The output identifies the sound hardware, so now I have something to google. ;)

---

### Post by bveenema on 2011-12-04
Well it's working today when I boot up.  I tried the aplay command again and got this
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```The number of Subdevices is now 0/1 whereas yesterday (when it wasn't working) it was 1/1

This means just about nothing to me but it's the only difference I can find between not working and working.

---


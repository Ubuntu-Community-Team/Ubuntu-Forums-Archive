---
title: "aplay / default audio problem"
date: 2011-12-13
forum: General Help
---

### Post by capleton on 2011-12-13
I'm currently running audio through HDMI.

In order to get it to work, I first have to run aplay -l and then I'll get a list similar to 
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Then I have to test each one with ```
aplay -D plughw:0,7 test.wav
```

Finally, I have to create the file */etc/asound.conf* and populate it with the device that works from my test above. 
```
pcm.!default {
     type plug
     slave.pcm {
         type hw
         card 0
         device 7
     }
}
```

Then I have to reboot, and the audio will work.

********My problem is that if I ever turn off or reboot the PC, the card number has changed.. it typically goes from card 0 to card 2 and back again.   This is really frustrating because I have to change it each and every time, and it will take a few reboots until I can get sound working again (testing, changing card, rebooting, then having to test again and reboot again).   Do you guys know why that card number might be changing?   and/or, how can I fix this problem?

And help would be GREATLY appreciated!!!

---

### Post by capleton on 2011-12-13
Buuuump.   Also, could anyone change the title to "Device / HDMI problem"?

---


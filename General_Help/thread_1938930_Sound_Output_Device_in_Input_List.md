---
title: "Sound Output Device in Input List"
date: 2012-03-10
forum: General Help
---

### Post by proxess on 2012-03-10
I've got an M-Audio FastTrack Pro. Until yesterday it was working well. Unfortunately it suddenly stopped working, the sound settings couldn't detect it. I unplugged it and plugged it back in and it was detected, but now an Output Device is in the Input devices list and I've got no Input device. Here as some screenies.

[http://dl.dropbox.com/u/1298388/Printscreens/Screenshot%20from%202012-03-10%2020%3A39%3A12.png]("http://dl.dropbox.com/u/1298388/Printscreens/Screenshot%20from%202012-03-10%2020%3A39%3A12.png")
[http://dl.dropbox.com/u/1298388/Printscreens/Screenshot%20from%202012-03-10%2020%3A39%3A20.png]("http://dl.dropbox.com/u/1298388/Printscreens/Screenshot%20from%202012-03-10%2020%3A39%3A20.png")

As you can see, the Output device is the same as the Input device. The proper Input device has "Input" as a name.

---

### Post by proxess on 2012-03-11
*bump*

---

### Post by proxess on 2012-03-15
I was able to fix it myself. I'll share the fix in case someone else gets the same problem.


It seems that alsa started reading the devices in a different way.

After listing my cards and devices in /proc/asound, I realized my M-Audio's Channel A was in fact hw:1,1:

**cat /proc/asound/devices && cat /proc/asound/devices**
```

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0600000 irq 44
 1 [Pro            ]: USB-Audio - FastTrack Pro
                      M-Audio FastTrack Pro at usb-0000:00:1a.0-1.2, full speed
 2 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xcfedc000 irq 46
  1:        : sequencer
  2: [ 0- 2]: digital audio capture
  3: [ 0- 1]: digital audio playback
  4: [ 0- 0]: digital audio playback
  5: [ 0- 0]: digital audio capture
  6: [ 0- 1]: hardware dependent
  7: [ 0- 0]: hardware dependent
  8: [ 0]   : control
  9: [ 1- 0]: raw midi
 10: [ 1- 1]: digital audio playback
 11: [ 1- 1]: digital audio capture
 12: [ 1- 0]: digital audio playback
 14: [ 1]   : control
 15: [ 2- 3]: digital audio playback
 16: [ 2- 0]: hardware dependent
 17: [ 2]   : control
 33:        : timer

```

I looked at my profiles and they looked like this:
**cat /usr/share/pulseaudio/alsa-mixer/profile-sets/maudio-fasttrack-pro.conf**
```
(...)
[Mapping analog-stereo-a-output]
description = Analog Stereo Channel A Output
device-strings = hw:%f,0,0
channel-map = left,right
direction = output

[Mapping analog-stereo-a-input]
description = Analog Stereo Channel A Input
device-strings = hw:%f,0,0
channel-map = left,right
direction = input

[Mapping analog-stereo-b-output]
description = Analog Stereo Channel B Output
device-strings = hw:%f,1,0
channel-map = left,right
direction = output
(...)
```

I made it look like this:
**nano /usr/share/pulseaudio/alsa-mixer/profile-sets/maudio-fasttrack-pro.conf**
```
(...)
[Mapping analog-stereo-a-output]
description = Analog Stereo Channel A
device-strings = hw:%f,0,0
channel-map = left,right
direction = output

[Mapping analog-stereo-a-input]
description = Analog Stereo Channel A
device-strings = hw:%f,1,0
channel-map = left,right
direction = input

[Mapping analog-stereo-b-output]
description = Analog Stereo Channel B
device-strings = hw:%f,1,0
channel-map = left,right
direction = output
(...)
```

A reboot and voilá.

EDIT: You can forget Duplex A + Analog B. It won't work.

---


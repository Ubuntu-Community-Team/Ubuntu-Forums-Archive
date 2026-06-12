---
title: "Mic works with skype &amp; sound recorder but not google talk"
date: 2011-07-03
forum: General Help
---

### Post by peperomia on 2011-07-03
My mic works with Skype and Sound Recorder, but not with Google Chat with other Google Chat users in voice/video chat.  However, if I use the 'Call Phone' feature in Google Chat, my mic works fine.  

In the Google chat settings, I've tried both the Internal Audio Analog Stereo and Default device setting for the microphone.

Output from      
```
wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
```is [here]("http://www.alsa-project.org/db/?f=a8f95066d13fddf6b745b05b71e51376106de29b").

---

### Post by peperomia on 2011-10-19
It turns out this wasn't a problem on my end, but is instead a problem from Windows Vista. So the person I called who was using Vista needed to make the adjustments described [here]("http://www.google.com/support/forum/p/Talk/thread?tid=285917b11f0659b2&hl=en") in order to hear me.[INDENT]Type Sound on Vista Start Menu. Select Sound Properties from the list in  the menu. Check out the current working device (it will show an green  arrow mark for the device, which is currently in use). Generally that  device is "independent speakers" or something. Select that device and  click properties. Go to "Advanced" tab. Under "exclusive mode" uncheck  both of the check-boxes. Click "Ok" twice, and you are done.[/INDENT]

---


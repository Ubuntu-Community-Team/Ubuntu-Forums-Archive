---
title: "Sound Profiles?"
date: 2010-12-31
forum: General Help
---

### Post by blakep2 on 2010-12-31
I am trying to make and receive calls using google voice and gmail. But the problem is that when I have my headset plugged into the computer I cannot hear the ringing of incoming calls. Therefore I leave the headset unplugged when not in use. But when I plug in the headset I have to go to the sound settings to set the use to the headset speakers and microphone. Is there a way to automatically changing the settings just by plugging in the usb on the headset. Or any other solutions for this problem. Thanks

---

### Post by kostkon on 2010-12-31
Yes, install and use the PulseAudio Volume Control utility. Start a call in google voice, open the volume control and set your usb headset as the input and/or output device for its audio stream. PulseAudio will remember your choice. The next time you start a call, just connect your headset and pulseaudio will automatically redirect the google voice audio to it.

---

### Post by blakep2 on 2011-01-01
Its not remembering my choices.  Better yet is there a way to configure the settings so as soon as I plug in my usb headset both the audio and input switch to the headset and when I unplug they use the default settings

---

### Post by kostkon on 2011-01-01
> **blakep2 said:**
> Its not remembering my choices.  Better yet is there a way to configure the settings so as soon as I plug in my usb headset both the audio and input switch to the headset and when I unplug they use the default settings
Try setting you headset as the default input and output device. PulseAudio will then treat your sound card as a fallback device and will use it every time you remove your headset; and, in theory, it should automatically send any input/output audio to your headset when you reconnect it.

---

### Post by blakep2 on 2011-01-01
> **kostkon said:**
> Try setting you headset as the default input and output device. PulseAudio will then treat your sound card as a fallback device and will use it every time you remove your headset; and, in theory, it should automatically send any input/output audio to your headset when you reconnect it.

I tried that and it couldn't see the  my default sound card, until I switched back.

---


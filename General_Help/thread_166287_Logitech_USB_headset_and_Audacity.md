---
title: "Logitech USB headset and Audacity"
date: 2006-04-26
forum: General Help
---

### Post by alexsingleton on 2006-04-26
I am trying to get Ubuntu Linux working with a Logitech USB headset.

When I go into Ubuntu Linux’s System Preferences for Sound, I am offered an option for the default sound card - either the motherboard or the Logitech USB headset (I want to use the latter). That’s very simple and some programs then use the USB.

But others have their own settings. I got Skype to work with the headset by going into its Options window and selection /dev/dsp1 instead of /dev/dsp as the audio device.

My problem is in Audacity: it only offers /dev/dsp. Any ideas?

---

### Post by alexsingleton on 2006-04-26
I worked it out. I had to install something called alsa-oss which is the thing that lets programs written with OSS in mind work under ALSA. Then at the command line, I typed aoss audacity and up came Audacity with the /dev/dsp1 option available to select.

---


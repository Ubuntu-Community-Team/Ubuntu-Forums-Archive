---
title: "Changing Audio Device"
date: 2010-09-25
forum: General Help
---

### Post by dodle on 2010-09-25
Does anyone know how to change the default audio device in Lubuntu?  I want to use my bluetooth headset.  In Ubuntu I just went to System -> Preferences -> Sound... errr, something like that.  But I can't find any sound device settings for Lubuntu.  I would just put Ubuntu on my laptop, but it's very old and runs Lubuntu much smoother.

---

### Post by dodle on 2010-09-27
*bump*

Lubuntu uses alsa without PulseAudio.  I am trying to use my bluetooth headset, which works great in Ubuntu (gnome), but alsa doesn't seem to detect it.  I have successfully connected the headset in Lubuntu, I just can't switch to it as the default audio device.  I don't really think that this is a bluetooth/bluez issue, but I could be wrong.

---

### Post by fuzetsu490 on 2010-10-03
I'm not an expert on the subject or anything but you can control sound to a certain degree using the terminal command "alsamixer" (without the quotes) there you can select your sound card but I'm not sure if thats what will do it :/ I've been having trouble getting my built in mic to work >< lubuntu needs to get a better way to configure audio devices.

---

### Post by dodle on 2010-10-04
I've checked out alsamixer but my bluetooth headset does not show up.

---

### Post by Matt Harrison on 2010-11-09
If you just install the pulseaudio package it will takeover.  Get the pavucontrol package as well to get the volume control gui to configure it.
It will then show up in "Sound & Video" in your Lubuntu menu.

---


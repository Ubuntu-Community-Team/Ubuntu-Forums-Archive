---
title: "disturbing noise from speakers"
date: 2009-07-24
forum: General Help
---

### Post by alphageek89 on 2009-07-24
when i close my laptop lid a screeching noise comes from my speakers because of the inbuilt mic.It wasn't there before and i cannot play loud music from my speakers for the same.

Its a lenovo r61 and yes I have muted the microphone tab under volume control and the device reads hda intel (alsa mixer) and the problem goes away when i mute my master control.

---

### Post by infiniah on 2009-07-24
change the device in volume control to the mic device and mute it

---

### Post by wojox on 2009-07-24
Open a terminal:

```
sudo gedit /etc/modprobe.d/alsa-base
```

After that, find the line that says "options snd-hda-intel" and change it to "options snd-hda-intel model=lenovo" then restart.

---

### Post by alphageek89 on 2009-07-24
under device:
hda intel (alsa mixer)-mic is muted
analog devices oss mixer-mic is muted
playback hda intel (pulse audio mixer)-master full
capture hda intel (pulsesudio mixer)-muted.

and i hate to say this but its working fine in windows.:(

---

### Post by alphageek89 on 2009-07-24
this didnt work,
options snd-hda-intel wasn't present so i added options snd-hda=lenovo to the end of the fike and restarted and still the problem persists.

---

### Post by alphageek89 on 2009-08-02
help someone.

---


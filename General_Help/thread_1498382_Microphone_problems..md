---
title: "Microphone problems."
date: 2010-05-31
forum: General Help
---

### Post by iBlackJack on 2010-05-31
I am a new ubuntu user but I used linux mint before ubuntu and I had the same problem there. My microphone only works when 1 program is running, but if I load a game or something my microphone stops working. I can't seem to figure out why, any ideas or solutions would be greatly appreciated.

---

### Post by lidex on 2010-05-31
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by iBlackJack on 2010-05-31
Linux danny-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
Advanced Linux Sound Architecture Driver Version 1.0.21.
Codec: Realtek ALC861

Emachines W3502

---

### Post by lidex on 2010-05-31
Please also include the make/model of your PC/Laptop.

---

### Post by iBlackJack on 2010-05-31
Its up there now^ edited.

---

### Post by lidex on 2010-05-31
Try an alsa upgrade via the alsa-upgrade link in my sig.

---


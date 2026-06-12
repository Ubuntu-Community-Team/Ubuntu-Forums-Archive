---
title: "Microphone not working..!!!"
date: 2010-04-18
forum: General Help
---

### Post by chris.jericho on 2010-04-18
Hey there..
I had recently install the lucid lynx beta 2......  but yesterday when I went to use my microphone.... it wasn't working.... I checked everything... the wiring and stuff..  but there was no problem...

i tried the sound recorder.... but couldn't record anything,,,,,,

How do I use my microphone... please help!!!

---

### Post by lidex on 2010-04-18
Have you checked alsamixer or gnome-alsamixer levels? What is your PC make and model? Can you post the output of these terminal commands for me:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags.

---

### Post by chris.jericho on 2010-04-18
This was the result

```

chris@chris-desktop:~$ uname -a
Linux chris-desktop 2.6.32-21-generic #31-Ubuntu SMP Tue Apr 13 20:37:36 UTC 2010 x86_64 GNU/Linux
chris@chris-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
chris@chris-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
chris@chris-desktop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC1200
chris@chris-desktop:~$ 

```

---

### Post by lidex on 2010-04-18
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1159334]("http://ubuntuforums.org/showthread.php?t=1159334")

---


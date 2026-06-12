---
title: "Sound Issues"
date: 2010-04-15
forum: General Help
---

### Post by Prominence on 2010-04-15
I've been having this issue now for ages and I do not know how to fix it, I've put up with it for long enough so now I'm asking for help. 

I have two small speakers and a compact subwoofer, but no matter what set of speakers I use, sound will only come out of the right speaker, I'm curious as to why, and how can I fix this? 

~Ubuntu 10.04

---

### Post by Prominence on 2010-04-15
If I don't receive any help on this matter I'm going to reinstall the system

---

### Post by lidex on 2010-04-15
What's the PC make and model? Can you post the output of these commands for me:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```

---

### Post by Prominence on 2010-04-15
grayson@Providence:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
grayson@Providence:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
grayson@Providence:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC1200

---

### Post by lidex on 2010-04-15
> **Prominence said:**
> grayson@Providence:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
grayson@Providence:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
grayson@Providence:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC1200

And the first one:
```
uname -a 
```

---

### Post by lidex on 2010-04-15
Have a look here.
[http://ubuntuforums.org/showthread.php?t=1159334]("http://ubuntuforums.org/showthread.php?t=1159334")
When using gedit as root the correct syntax is 'gksudo', not 'sudo' as shown on that thread.

---

### Post by Prominence on 2010-04-15
Linux Providence 2.6.32-21-generic #31-Ubuntu SMP Tue Apr 13 20:37:36 UTC 2010 x86_64 GNU/Linux

---


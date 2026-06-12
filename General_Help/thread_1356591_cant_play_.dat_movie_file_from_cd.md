---
title: "cant play .dat movie file from cd"
date: 2009-12-16
forum: General Help
---

### Post by shaon3343 on 2009-12-16
[SIZE=3]**hi there, in my ubuntu 9.10 i cant play  .dat movie files from cdrom. but they are playing nicely when i copy them in my hard-disk. can anyone tell me what is the reason?**[/SIZE]

---

### Post by DaVince21 on 2009-12-16
What media player are you using, and how are you trying to open the VCD(?) in it? "Play from disc" would usually try to interpret the disc as a DVD-ROM, so try to open the .dat files directly instead if you didn't already.

---

### Post by shaon3343 on 2009-12-16
**my default player is totem, but these .dat files are playing in my hard-disk by smplayer.**

---

### Post by Djuice512 on 2010-03-26
[SIZE=3][B]hi there, in my ubuntu 9.10 i cant play .dat movie files from cdrom / H.D.D. what should i do??????????? 

_________________________________________
i am loving it=>Ubuntu
-----------------------------------------------
Ubunt/Lunux for all
[/B][/SIZE]

---

### Post by Garibaldi3489 on 2010-03-26
Try installing vlc - it can open pretty much anything

---

### Post by eltonw on 2010-03-26
> **shaon3343 said:**
> [SIZE=3]**hi there, in my ubuntu 9.10 i cant play  .dat movie files from cdrom. but they are playing nicely when i copy them in my hard-disk. can anyone tell me what is the reason?**[/SIZE]
Files on a CD / DVD are *read-only*, once you copy the file to hd, they normally should be readable / writable. IMHO, your problem is a matter of permissions. Certain files cannot be played from a data laser-disk, e.g: you cannot 'look inside" a zip file on a CD /DVD, but once you copy it to the hd, you can see its contents. I would venture such is the case with the dat files, because they need to be either 'extracted on the fly' or the program needs to write to the file, in order to run it.

---


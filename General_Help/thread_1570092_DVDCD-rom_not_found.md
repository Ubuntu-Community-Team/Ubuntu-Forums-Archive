---
title: "DVD/CD-rom not found"
date: 2010-09-07
forum: General Help
---

### Post by MooPi on 2010-09-07
```
Can't find device /dev/dvd
``` is the output from lsdvd. Similarly mplayer spits out ```
libdvdread: Can't stat /dev/dvd 
no such file or directory
Couldn't open DVD device: /dev/dvd
```
k3b recognizes the drive and whatever is loaded in the tray and I can rip a cd with cdparanoia but eject no longer works ? wtf
Any clue how to correct this ?

---

### Post by JohnHeikkila on 2010-09-07
Perhaps it's not /dev/dvd, maybe it's /dev/dvdrw like I have.
Check the k3b settings if this could be changed.

---

### Post by MooPi on 2010-09-07
No that doesn't seem to matter as no device is being recognized. the command ```
eject
``` comes back with > unable to find or open device for:'cdrom' This a complete mystery to me. I can't mount but k3b see's and names disk. Cdparanoia can rip a cd but I can't play it. Pcmanfm see's the disk and I can brows files and open .VOB files but mplayer will not play the dvd.

---

### Post by MooPi on 2010-09-07
Hardware issue ,motherboard controller I suspect for sata devices.

---


---
title: "Live CD X server problem"
date: 2006-02-23
forum: General Help
---

### Post by fallen_seraph on 2006-02-23
Hello all.
I've been self teaching myself linux for a while now as I slowly make the transition from windows to linux. I currently have two computers, one desktop and one very old (POS) laptop. The laptop has Ubuntu installed on it, and I tired of waiting for the very slow processor, and therefore I wanted to finally play with it on my much nicer desktop. So, I used the live cd.

It boots, but at the end it brings an error with X server and leaves me at a command prompt. I've looked at the logs, and I've tried to get a copy so I could post it here, but no luck. I tried to copy the Xorg.0.log file to a floppy with no success as I got an empty file the first time and an unformatted floppy the second. :\

Anyhow, onto the details of the problem that I can describe...
It gives me a "X10: Fatal IO error 104 (Connection reset by peer) on X server"
I googled around and saw some similar problems that were addressed by changing a .conf file in /etc/X11/ , but that directory and file are non existant? Go figure, it could be an older version they were addressing is my guess. At the end it displays something like "Error: no screens found"

So here is my hardware and I'll check back as much as I can, any and all help is very much welcome.

ATI x800XL Video Card
Viewsonic 17" G70fmb Graphic Series monitor
AMD Athlon 64 3200+ 2.0Ghz
2GB DDR Kingston RAM
ASUS A8V-E Deluxe Motherboard

Thanks in advance. :]

---

### Post by dcstar on 2006-02-24
[QUOTE=fallen_seraph]Hello all.
I've been self teaching myself linux for a while now as I slowly make the transition from windows to linux. I currently have two computers, one desktop and one very old (POS) laptop. The laptop has Ubuntu installed on it, and I tired of waiting for the very slow processor, and therefore I wanted to finally play with it on my much nicer desktop. So, I used the live cd.

It boots, but at the end it brings an error with X server and leaves me at a command prompt. I've looked at the logs, and I've tried to get a copy so I could post it here, but no luck. I tried to copy the Xorg.0.log file to a floppy with no success as I got an empty file the first time and an unformatted floppy the second. :\
.......[/QUOTE]
I can only suggest you do a proper install, then you can get the system up with basic X stuff by using the "vesa" driver, and after that work on the correct video drivers.

---


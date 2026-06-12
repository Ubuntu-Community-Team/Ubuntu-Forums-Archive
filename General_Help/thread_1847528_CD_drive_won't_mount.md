---
title: "CD drive won't mount"
date: 2011-09-20
forum: General Help
---

### Post by kerryhall on 2011-09-20
CD is in the drive of course. When I open computer:/// I see CD/DVD Drive and also cdrom0 for some reason. I double click CD/DVD drive, and nothing happens. The most infuriating thing ever, no error message, nothing. :P When I double click cdrom0, I get : "Unable to mount location, mount: special device /dev/hdc does not exist"

$ls /dev/cd* gives 

/dev/cdrom1 /dev/cdrw1

I tried 
$sudo mount /dev/cdrom1 /media/cdrom
but get
mount: /dev/sr0: unknown device

Here is the weird thing. If I pop in a DVD, it will autoplay and from there I can select vlc and it plays fine. (It seems to have mounted to a location /media/UNDEFINED) Any other disk has no effect though. Oh, and after the DVD autoplays, the eject button on my cd drive no longer works, I have to software eject.

---

### Post by kerryhall on 2011-09-30
Bump

---

### Post by kerryhall on 2011-12-04
Bump

---

### Post by kerryhall on 2011-12-08
Bump

---

### Post by KaitlinM on 2011-12-08
> **kerryhall said:**
> CD is in the drive of course. When I open computer:/// I see CD/DVD Drive and also cdrom0 for some reason. I double click CD/DVD drive, and nothing happens. The most infuriating thing ever, no error message, nothing. :P When I double click cdrom0, I get : "Unable to mount location, mount: special device /dev/hdc does not exist"

$ls /dev/cd* gives 

/dev/cdrom1 /dev/cdrw1

I tried 
$sudo mount /dev/cdrom1 /media/cdrom
but get
mount: /dev/sr0: unknown device

Here is the weird thing. If I pop in a DVD, it will autoplay and from there I can select vlc and it plays fine. (It seems to have mounted to a location /media/UNDEFINED) Any other disk has no effect though. Oh, and after the DVD autoplays, the eject button on my cd drive no longer works, I have to software eject.

Strange. Well, the CD isn't blank, right? It does have a mountable file system?

---

### Post by kerryhall on 2011-12-09
Yeah, I tried quite a few different CDs.

---

### Post by kerryhall on 2011-12-10
Bump

---

### Post by dandnsmith on 2011-12-10
I haven't seen, in this thread so far, any meaningful listing of those devices.
Need to use *ls -l* to show what devices are being linked to (look at /dev/cd* and /dev/sr* ), and listing from *lshw* might help.

It sounds as if something has gone awry with the setup - I'm not sure when that CD/DVD entry gets created, and from what.

---

### Post by kerryhall on 2011-12-10
Thanks! Wasn't sure what debugging info to provide! I'll get right on that.

---


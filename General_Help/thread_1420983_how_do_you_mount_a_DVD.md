---
title: "how do you mount a DVD?"
date: 2010-03-03
forum: General Help
---

### Post by harryliddic on 2010-03-03
do you mount a dvd when the BIOS does even have a setting for DVD's?

---

### Post by gumpish on 2010-03-03
With a standard Ubuntu install DVD media should automatically mount. (It should appear in your file browser and on the desktop.) What happens when you put in a CD-ROM? Or an audio CD?

When you say that your BIOS doesn't have an option for DVDs, it's not uncommon for a BIOS to refer to any optical drive as "CDROM".

---

### Post by harryliddic on 2010-03-03
I was using acidripper and got and error "no /dev/dvd"

---

### Post by harryliddic on 2010-03-03
I have since edited the /etc/fstab using the cd-rom as a template but that didn't work
the line of code was```
/dev/dvd	/media/dvd0	auto    rw,user,noauto,exec,utf8 0        0
```

---

### Post by bart.vanaudenhove on 2010-05-01
I had a related problem on my HP Laptop: any data cd or DVD would read  and write fine, but audio cds and movie dvds would not be recognized, not "mounted".

For me the solution was to physically slip the optical drive out of the  computer (unscrew a vise in the back and push the drive a bit out) =  unplugged and power off off course =, plug it back in, and at next  startup everything was fine. (I found it in another post somewhere)

From time to time the same problem reappears and the same solutions  works for a while...

This is in Ubuntu 9.10.

---


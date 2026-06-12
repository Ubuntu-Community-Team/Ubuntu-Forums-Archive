---
title: "List Drives"
date: 2010-07-07
forum: General Help
---

### Post by Seeked on 2010-07-07
Hello All...

My drives are all working fine, automatically mounting and accessible via Nautilus etc.  

However I need there specific hardware location (ie /dev/dvdrom) not just a mount point.  I am able to list the hard disks with "fdisk -l" but I need the locations of the other devices (dvd roms).

Thank you in advance.

---

### Post by kanikilu on 2010-07-07
I guess you could get the logical names of your dvd drives from something like:

```
sudo lshw -class disk
```

Or if you want to see everything about what is in your computer:

```
sudo lshw -html > ~/Desktop/hardware.html; firefox ~/Desktop/hardware.html
```

---

### Post by Seeked on 2010-07-08
Thank you kanikilu.
Exactly what I was looking for.

---


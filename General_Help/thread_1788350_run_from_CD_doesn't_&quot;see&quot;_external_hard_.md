---
title: "run from CD doesn't &quot;see&quot; external hard drive"
date: 2011-06-22
forum: General Help
---

### Post by engine on 2011-06-22
Hoping to retrieve data from my normal hard drive, which has spontaneously decided to make the root directory unreadable … start from a bootable CD (9.10), and I can at least see the (remains of?) the 247 Gb file system. But I can't see my USB external hard drive, though judging by the power indicator the USB port itself is OK.

Is there some special trick I need to carry out to make the external drive visible as a storage device so I can start rescuing files? and (apart from take a backup the day before) any tips on persuading data out of "unreadable" folders?

Thanks in advance!

---

### Post by iclestu on 2011-06-22
> **engine said:**
> Hoping to retrieve data from my normal hard drive, which has spontaneously decided to make the root directory unreadable … start from a bootable CD (9.10), and I can at least see the (remains of?) the 247 Gb file system. But I can't see my USB external hard drive, though judging by the power indicator the USB port itself is OK.

Is there some special trick I need to carry out to make the external drive visible as a storage device so I can start rescuing files? and (apart from take a backup the day before) any tips on persuading data out of "unreadable" folders?

Thanks in advance!

what does 
```

lsusb
```

say? can it find the device? (if so then it is just not mounted - see this guide:

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by engine on 2011-06-22
> **iclestu said:**
> what does 
```

lsusb
```

say? can it find the device? (if so then it is just not mounted - see this guide:

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

D'uh! so many years since I've had to mount a device by hand I never even thought of it. I'll give that a try and let you know.

---


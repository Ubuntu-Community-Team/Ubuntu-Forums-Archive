---
title: "Add a slower swap partition"
date: 2010-03-28
forum: General Help
---

### Post by Arancaytar on 2010-03-28
I currently have a system with 2GB RAM as well as a 2GB swap partition on my system SSD drive. This is nice and fast under normal conditions, but it rapidly grinds to a halt when the swap space is full, since there is a kind of gridlock. This particularly happens with lots of open applications, or when running calculations that have a big memory footprint - 4GB are easier to fill than it sounds.

I had decided to put the swap space on the SSD drive rather than the data HD drive for the read-write speed (after reading that even heavy use wouldn't deteriorate it in less than 5-10 years; plenty of time for new hardware). But now it seems that I need a larger "swap swap" space for my swap space to expand into, which would be on the HD drive.

Ideally, this slow swap space should be at the bottom of the "pyramid" - ie. the system should use it to store the least accessed data. So my question is: Is it possible to assign a kind of preference to a swap partition when adding it to the /etc/fstab file?

---

### Post by vanadium on 2010-03-28
See "man swapon"
```
Add pri=value to the option field of /etc/fstab for use with  swapon -a.
```

---

### Post by srs5694 on 2010-03-28
If you're regularly using as much swap space as you have RAM, you need more RAM, not more swap space.

---

### Post by Arancaytar on 2010-03-28
The massive usage comes primarily from having applications open in the background, where they don't need to access the memory anyway. Paging will take a few moments when switching, but I'm not convinced that I'd see a performance boost worth the price of two 2GB modules.

> Add pri=value to the option field of /etc/fstab for use with  swapon -a.

Thanks, that's awesome! :)

---


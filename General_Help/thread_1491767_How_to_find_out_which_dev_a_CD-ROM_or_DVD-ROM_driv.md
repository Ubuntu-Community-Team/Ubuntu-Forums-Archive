---
title: "How to find out which /dev/ a CD-ROM or DVD-ROM drive is?"
date: 2010-05-24
forum: General Help
---

### Post by murderslastcrow on 2010-05-24
Hi. I'm trying to find out which file in /dev/ represents my dvd drive- wondering if there's a terminal command to find out which of those devices is currently active/filled/mounted.

Reason is, I got PCSX2 working perfectly on 64-bit, except that the CDVD plugin only takes input as /dev/<devicehere>, not as /media/cdrom, mnt/whatever, just an actual link to a real device. So I can't really mount an and have it link to it.

Thanks in advance for any assistance- I really wanna' get this working since the PS2 bios runs really fast on my machine. O_O I'm really excited to play some of my games.

---

### Post by jbrown96 on 2010-05-24
Usually it's /dev/sr0, but /dev/cdrom and /dev/dvd are conveniant links to that device. They are both the same, so a DVD can be read through /dev/cdrom or /dev/dvd and vice versa.

---

### Post by murderslastcrow on 2010-05-24
Thanks- /dev/cdrom did the trick!

---


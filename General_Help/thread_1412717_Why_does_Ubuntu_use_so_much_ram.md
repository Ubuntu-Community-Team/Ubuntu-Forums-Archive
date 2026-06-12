---
title: "Why does Ubuntu use so much ram?"
date: 2010-02-21
forum: General Help
---

### Post by gymophett on 2010-02-21
I have 3GB of DDR2 ram. I run 64-bit OS's.
Ubuntu 9.10 with Gnome idling uses around 26-30% of ram. 
Arch with Gnome idling uses around 9-14% idling.
Fedora 12 with Gnome uses anywhere from 9-12% of ram idling.

Why does Ubuntu use so much compared to other distros?

---

### Post by The Real Dave on 2010-02-21
I can only presume it's due to whatever's running in the background. Stuff like Compiz and Nautilus use a lot of RAM. There's also a big jump in RAM usage betten x86 Ubuntu and x86_64.

---

### Post by wcutrombonekid on 2010-02-21
have you checked to see if anything is running?
i have 4 gbs but only 2.7 is recognized on my ubuntu partition, and it idles around 7%

---

### Post by MaxIBoy on 2010-02-21
Unused RAM is wasted RAM. (I seem to remember telling you this in the past. :D)

When RAM is otherwise unneeded, the Linux kernel will attempt to cache commonly-used files (such as shared libraries) in RAM to speed up access times. If you need the RAM for something else, it can easily be freed up.

---


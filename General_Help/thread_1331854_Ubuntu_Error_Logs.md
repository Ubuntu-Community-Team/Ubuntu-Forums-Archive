---
title: "Ubuntu Error Logs"
date: 2009-11-19
forum: General Help
---

### Post by amaz1ng on 2009-11-19
NOTE: Google Chrome is having some issues with drop-down lists and I can't see them, would a mod please change the prefix to the appropriate one?I Think [Ubuntu] is good enough, but if there's a better one... Thanks.

So I just got a crash with some numbers and a "not enough swap space" error, and I'm wondering if there's an error log that Ubuntu wrote somewhere. Any help? I think it's an OS issue and not a program issue.

Thanks in advance.

Edit: I'm on Ubuntu 9.10 with 4 gigs of RAM.

Edit2: More System Information
Hard Drive: Ubuntu 9.10 32-bit partition, 18 gigs. Windows 7 64-bit and Files partition, NTFS.
RAM: 4 GB PC3-8500 DDR3 SDRAM 1067MHz SODIMM Memory (2 DIMM
Intel Core 2 Duo processor P8700 (2.53GHz 1066MHz 3MBL2)
Gfx: ATI Mobility Radeon 3470 with 256MB

---

### Post by bodhi.zazen on 2009-11-19
That is an odd error . How much RAM do you have and what are you doing that is so memory intense ?

---

### Post by amaz1ng on 2009-11-19
I have 4 gigs, but i DID have a bunch of stuff open -- probably 15 tabs in Google Chrome, 5 in Firefox, 7ish Open Office Writer documents, skype, thunderbird, empathy, rythmbox, transmission. Some nice Compiz effects as well, desktop cube, reflections... but still, 4 gigs is a LOT of RAM, and I don't think I was even close to hitting the limit, as the System Monitor in my panel showed.

Does Ubuntu look for swap space only in the partition it's installed in?

---

### Post by NoaHall on 2009-11-19
Had you sent it into hibernate any time beforehand?

---

### Post by amaz1ng on 2009-11-19
Yup, crash appeared just after I opened my laptop from hibernation mode.

---

### Post by wojox on 2009-11-19
Sounds like you need to increase swap. What's your swappiness by the way:

```
cat /proc/sys/vm/swappiness
```

---

### Post by amaz1ng on 2009-11-19
> **wojox said:**
> sounds like you need to increase swap. What's your swappiness by the way:

```
cat /proc/sys/vm/swappiness
```

60.

---

### Post by wojox on 2009-11-19
How big is memory:

```
free -m
```

---

### Post by amaz1ng on 2009-11-19
Just got another crash, not sure of the cause, but I assume it's related. I just saw a black screen and two lines of text. Didn't catch what they said. Happened during normal use, not just after a hibernate/reboot.

What I was doing: running 6 tabs in Chrome, the most strenuous of which was a loading Youtube video. Installing Guild Wars via WINE ([http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine](http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine)), Guild Wars was downloading a bunch of updates, and listening to music in Rythmbox.

System Monitor gave roughly 20% of memory used by programs and 75% used as cache soon before the crash,

I'll re-edit the first post with my full system information.

---

### Post by amaz1ng on 2009-11-19
> **wojox said:**
> How big is memory:

```
free -m
```

Here're the results, taken after reboot from second crash:

```
 my_name@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2479       1584        895          0        560        719
-/+ buffers/cache:        304       2175
Swap:          255          0        255

```

---

### Post by bodhi.zazen on 2009-11-20
Your swap partition is too small.

If you wish to use features such as hibernation you need a swap partition as large as your RAM, in your case it appears close ot 2.5 Gb RAM , so you need a 2.5 Gb swap partition.

You can resize your swap partition from the live CD with gparted if you wish.

---

### Post by amaz1ng on 2009-11-20
I'm wondering, can 32-bit Ubuntu recognize more than 2 gigs or RAM? the 2479 number makes me suspicious.

---

### Post by bodhi.zazen on 2009-11-20
> **amaz1ng said:**
> I'm wondering, can 32-bit Ubuntu recognize more than 2 gigs or RAM? the 2479 number makes me suspicious.

Yes.

The standard 32 bit kernel can recognize up to 3.2 Gb.

The PAE kernel can recognize up to 64 Gb.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

The PAE kernel is in the (9.10) repositories.

---


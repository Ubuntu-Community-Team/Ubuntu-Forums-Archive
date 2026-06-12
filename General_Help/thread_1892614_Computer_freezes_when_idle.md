---
title: "Computer freezes when idle"
date: 2011-12-08
forum: General Help
---

### Post by Noob_Zaiboot on 2011-12-08
I'm running a dual boot system with ubuntu and windows 7. Recently when i have left my computer and come back after a few minutes it has completely frozen and i have to reset it to get it working again. This only happens occasionally but has happened on both operating systems, but more frequently on ubuntu.

Otherwise the system runs fine when i am doing something on it, its only when its left idle. 

The specs for my system are:
asrock p67 extreme4 (B3) socket 1155
intel core i5-2500k CPU @3.30
AMD Radeon HD6950 Series
8 gb corsair
Corsair Hydro Series H80 CPU Cooler 

I really hope its not a hardware problem as i only built the computer 2 and a half months ago!

---

### Post by 2F4U on 2011-12-08
Did you look into the log files whether they contain any hints? Did you run memtest?

---

### Post by Noob_Zaiboot on 2011-12-08
Thanks for the reply. I wouldn't know what log files to look at or how to look at them. Could you tell me how to do that? I didn't run a memtest but i will and i will post hte result

---

### Post by bluexrider on 2011-12-08
having issues on both OS's would say overheating to me. Fan controllers working, venting properly.

check memory at boot

 Memtest86+ scans your RAM for errors.

This tester runs independently of any OS - it is run at computer
boot-up, so that it can test *all* of your memory.  You may want to
look at `memtester', which allows to test your memory within Linux,
but this one won't be able to test your whole RAM.

It can output a list of bad RAM regions usable by the BadRAM kernel
patch, so that you can still use your old RAM with one or two bad bits.

Memtest86+ is based on memtest86 3.0, and adds support for recent
hardware, as well as a number of general-purpose improvements,
including many patches to memtest86 available from various sources.

Both memtest86 and memtest86+ are being worked on in parallel.

A convenience script is also provided to make a grub-based floppy or
image.

---

### Post by Noob_Zaiboot on 2011-12-08
Funny you should say that. This only started happening when i installed a new fan. I had the corsair h80 cooling system pulling air in the back and blowing it out the front through a 140 x 25 mm fan and the computer ran fine but then i installed a 120 mm fan on the top pulling more air in. Thats when this started happening. Maybe there's too much air being taken in?

I also ran the memtest and it said passed with no errors

---


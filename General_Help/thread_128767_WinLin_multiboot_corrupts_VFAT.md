---
title: "Win/Lin multiboot corrupts VFAT"
date: 2006-02-12
forum: General Help
---

### Post by oleg_myrk on 2006-02-12
Hi,

I have the following problem:
* I have multiboot laptop (FS Amilo L1300): Windows XP & Ubuntu 5.04
* I do mostly my work in Linux
* When I reboot to Windows and then back to Linux, my shared VFAT partition gets corrupted

Any ideas?

One idea I have myself is that I mostly hibernate Windows so the reason for 
corrupted VFAT might be because when resuming Windows VFAT buffers are not 
flushed or smth.

I didn't test this theory - and, admittedly, I am not very inclined to do
statistically relevant tests on my VFAT full on useful files :)

OM

---


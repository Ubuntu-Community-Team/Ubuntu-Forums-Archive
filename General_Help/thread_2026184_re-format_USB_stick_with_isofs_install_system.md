---
title: "re-format USB stick with isofs install system?"
date: 2012-07-14
forum: General Help
---

### Post by scradock on 2012-07-14
Hi - can anyone suggest how to proceed in this interesting situation?

I wanted to try out the CrunchBang distro, so I downloaded it and put the install files onto an 2GB USB stick. Didn't work; won't boot. 

OK, I'll wipe the stick and use it for the next thing...

But the stick is formatted with the isofs file system, and Gparted doesn't allow me to reformat it - in fact Gparted can't see anything on the stick, says it has no partition table, and that it can't add a new one. Windows tells me the same.

The irritating thing is that Ubuntu mounts the stick and shows the files perfectly well. How can I format the stick (VFAT) from ubuntu? No man entries for "format" or "makefs"...

Any help gratefully received - no need to waste a stick!

---

### Post by scradock on 2012-07-15
The answer was "sudo fdisk -c /dev/sdc"

then "o" to make a new msdos partition table

then "w" to write the new partition table

HTH someone else

---


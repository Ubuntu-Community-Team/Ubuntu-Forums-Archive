---
title: "swapping cpu's?"
date: 2010-04-15
forum: General Help
---

### Post by BigCdaAnswer3 on 2010-04-15
hello all, i recently did a fresh install of lucid beta 2 on my desktop machine which has an intel atom cpu in it. i have a need to use a older cpu in this machine, namely a amd geode lx. however, whenever i put the geode in and fire it up, i get stopped during the boot sequence with this:

"Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/{reallylongstring} does not exist. dropping to a shell!

which then drops me into a busybox shell. like i said above, all i did was change the cpus, no changes to the hard drive, grub, etc. any ideas???

---

### Post by BigCdaAnswer3 on 2010-04-15
when i do a cat/proc/modules from the busybox shell, i get nothing back. am i missing some geode modules? it looks like from the kernel config the cpu type is 586

---

### Post by ian dobson on 2010-04-15
Hi,

From what I understand atom and amd geode are both soldered onto the motherboard (no CPU socket) so did you replace/swap the motheroard? If so I'd imagine your missing the IDE/SATA drivers for the geode board.

Have a look in the internet for the geode board your using looking for which drivers are required. Maybe try booting from a live CD then go to the terminal and do a lsmod to see what modules are loaded.

Regards
Ian Dobson

---

### Post by BigCdaAnswer3 on 2010-04-15
> **ian dobson said:**
> Hi,

From what I understand atom and amd geode are both soldered onto the motherboard (no CPU socket) so did you replace/swap the motheroard? If so I'd imagine your missing the IDE/SATA drivers for the geode board.

Have a look in the internet for the geode board your using looking for which drivers are required. Maybe try booting from a live CD then go to the terminal and do a lsmod to see what modules are loaded.

Regards
Ian Dobson

I have a ETX interface for both CPUs on this motherboard, so it's pretty much just plug and play. However, after I posted this, I figured I would try a fresh lucid beta 2 install with the Geode in place, but I got a similar result. During the install process, it said it couldn't find any available disks to install onto....how could this be? Surely the ubuntu installer isn't missing the necessary IDE drivers to install onto a Geode platform? I had a Geode CPU working back in the days of Ubuntu 8.04?!?!?!

What gives?

---

### Post by ian dobson on 2010-04-16
Hi,

It could well be that kernel support for your IDE driver has been droped in the kernel. What's actually on the ETX board (only CPU or CPU/Chipset) I'd imagine it's the second as atom and geode are totally different animals.

Maybe google abit for your geode board, maybe someone else has had the same problem and also solved it.

Regards
Ian Dobson

---

### Post by BigCdaAnswer3 on 2010-04-29
this issue has been resolved with the official release of 10.04. thanks for the replies

---


---
title: "GParted Live runaway loop upon attempted boot"
date: 2011-11-28
forum: General Help
---

### Post by The_Third on 2011-11-28
I'm attempting to dual boot clonezilla-live-1.2.10-14-amd64 and gparted-live-0.10.0-3 from a 4gb USB flash drive. I split the USB flash drive into 3 partitions: the first for Clonezilla, the second for GParted, and the third for the GRUB2 boot files. Clonezilla works fine. GParted gets mired in "request module: runaway loop modprobe binfmt-464c" errors and freezes so that I have to hold the power switch to turn off my laptop. From what I can find online the runaway loop has something to do with trying to run a 32bit process on a 64bit processor. The weird thing is that GParted worked fine when it existed all alone on the flash drive. Attached is the grub.cfg file for the flash. Any help would be much appreciated.

Edit: Forgot to mention, I used UNetbootin on ISOs to install GParted and Clonezilla to their partitions.

---


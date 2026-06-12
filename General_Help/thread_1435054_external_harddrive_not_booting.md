---
title: "external harddrive not booting"
date: 2010-03-21
forum: General Help
---

### Post by R3N3G4D3 on 2010-03-21
I installed Ubuntu on a portable harddrive so that I can use it independently of my computer (when I visit my parents or my g/f). I performed the installation using a bootable Ubuntu thumbdrive, everything went fine but when I unplugged the thumbdrive and rebooted I got a kernel panic. I was able to boot into Ubuntu on my external drive once (I think it might have been due to reordering boot order in BIOS). My guess is that the kernel panic occurs due to the drive letter changing (sdb -> sdc) depending on which external devices are plugged in, but I'm not sure how to make sure that's the case. And if it is, how would I prevent this from happening?

---

### Post by DawieS on 2010-03-21
You could edit the **/etc/fstab** file on the portable drive, and delete all lines referring to other hard drives (leave only the CD/DVD ROM and boot drive (usually denoted by UUID ...)
If you now plug it into other computers, first set the BIOS boot sequence. It will pick up other drives automatically, and wont get confused about nonexistent drives that is now referred to in the **/etc/fstab** file.:grin:

---

### Post by meijer.o on 2010-03-21
I tried the same. Linux loads grub2, from the external hard-drive but cannot find the file-systems, so it does not load the kernel and the initrd. Who knows a solution, please help

Kind regards,

Otto Meijer

---


---
title: "Recover NTFS partition from linux"
date: 2010-05-07
forum: General Help
---

### Post by molfar on 2010-05-07
There is a hdd on the three partitions of NTFS. Windows one of them did not see - shows, but when you try to access it offers to format referring to an error in the data OCR. But in linux this partition is available, the files are read from it. Prompt please how you can restore the full performance of this partition? Standard check of the drive from the Windows impossible, chkdsk also refuses to work.

---

### Post by dino99 on 2010-05-07
the normal way is to run windoz

from ubuntu: sudo shutdown -F -r now (force a fsck on next boot)

sudo dpkg --configure -a

install mountmanager to tweak your devices and partitions preferences

external tools: [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by molfar on 2010-05-07
I tried "sudo shutdown -F -r now" - the PC just rebooted, nothing happened.
Installed mountmanager - I cant find there something like check disk...

---

### Post by dino99 on 2010-05-07
mountmanager: on the left pane you choose the device or partition, then on the right pane you set your prefs

---


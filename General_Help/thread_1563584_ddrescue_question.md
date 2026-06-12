---
title: "ddrescue question"
date: 2010-08-29
forum: General Help
---

### Post by sr_guy on 2010-08-29
I want to boot a test computer with a ubuntu bootable usb stick (this pc has no harddrive), and use ddrescue to recover data from a damaged 120gb hdd. Is there a way to have ddrescue copy the image to a network drive share on a different computer since the test pc won't have a large enough drive to store the image?

Here is the command I used to copy from the hdd to another directory, I want to modify it so that it copies the image to a networked drive instead:

ddrescue -n /dev/sdb4 /mnt/recovery/recovered.img

---

### Post by jerome1232 on 2010-08-29
I understand you can use netcat to do that, although I don't actually know HOW to use netcat. Googling dd netcat looked like there were some promising guides on how to do it.

---


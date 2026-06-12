---
title: "Cannot Read WD Hard Drive"
date: 2010-12-26
forum: General Help
---

### Post by sting547 on 2010-12-26
Hi, I have a simple WD external USB hard drive, but when I plug it into my computer nothing happens. Not only is there nothing popping up, but I cannot access it through the file browser. The light on the hard drive turns on as usual. Please help!!!

Thanks in advance

---

### Post by mikewhatever on 2010-12-26
Replug it, then post the outputs of the following:

dmesg | tail -n20

---

### Post by efflandt on 2010-12-26
Also see if **sudo fdisk -l** (small L) shows anything.  Even if partitions got corrupted from failing to Safely remove it, or bad sectors, that should at least show something if the electronics are working.

---

### Post by sting547 on 2010-12-26
When I typed in the first command, the last message it gave me was "waiting for device to settle before scanning." Then the light on the HD flickers, and a folder pops up called My Passport. The folder immediately disappears and goes back to the media folder. Same with the second command.

---


---
title: "How do I check HD with Ubuntu boot disk"
date: 2012-05-25
forum: General Help
---

### Post by etrexuser on 2012-05-25
I have my Ubuntu 12.04 boot disk.  I booted with it and tried to check the HD using System>Administration>Disk Utility but it reported the HD was still mounted.

Please advise how I can check the HD with the boot disk.

Update:  I had not booted with 12.04.  Now I have.  Please tell me where to click to check the HD from the 12.04 boot disk.

---

### Post by kanikilu on 2012-05-25
If you are booting into the Live CD, can you not unmount it within Disk Utility? I'm pretty sure it's an option once you click on the hard drive in the list on the left...

If all else fails, you can unmount manually: ```
sudo umount /dev/sda1
``` *replace sda1 with whatever matches your system (you can find this in Disk Utility)

---

### Post by etrexuser on 2012-05-25
> **kanikilu said:**
> If you are booting into the Live CD, can you not unmount it within Disk Utility? I'm pretty sure it's an option once you click on the hard drive in the list on the left...

If all else fails, you can unmount manually: ```
sudo umount /dev/sda1
``` *replace sda1 with whatever matches your system (you can find this in Disk Utility)


Update:  I had not booted with 12.04.  Now I have.  Please tell me where to click to check the HD from the 12.04 boot disk.

Ok, my fault.  I see it.  Now that I did the unmount and checked the file system, it only took a split second.  I expected a more thorough check of the sectors that would take a while when the HD was unmounted.  Surely that didn't check much of my HD's viability did it?

---

### Post by WorMzy on 2012-05-25
```
sudo smartctl -a /dev/sda
```

---


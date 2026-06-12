---
title: "No space on encrypted drive"
date: 2012-09-01
forum: General Help
---

### Post by giantpc on 2012-09-01
Hi,

I used the alternate CD and selected "Guided - Encrypt whole hard disk LVM" and was told during setup that I could set a size for the encrypted volume and partition the remaining space later. So, I entered 100 GB of the 320GB hard drive.

But now, I just went to install a second OS (for duel-boot) but the installer is saying there is no available space because ubuntu marked the whole hard drive as used and encrypted.

I was wondering if it is possible to take out about 50 GB of the free space on my encrypted install and move it to a completely separate partition. I was going to try to resize the current partition to see if that will automatically make more space available for the second OS install, but I did not want to proceed until I was certain that it would work. Is there any other way, better way?

---

### Post by jerome1232 on 2012-09-01
It might be helpful to show us what your paritions and your lvm setup look like, also what OS are you trying to install (a Linux one which can read LVM and LUKS or say Windows, which can't)

```
sudo fdisk -l
sudo pvdisplay
sudo vgdisplay
sudo lvdisplay
```

---

### Post by giantpc on 2012-09-01
Yeah I'm installing windows and the setup is on my laptop so I can't copy and paste the results from terminal.

---

### Post by giantpc on 2012-09-01
So can it be done? I seen that the mapper was showing 100GB for the system partition as I entered when installing. Can create a separate partition or unallocated space out of the remaining space on the hard drive, say 50 GB?

---

